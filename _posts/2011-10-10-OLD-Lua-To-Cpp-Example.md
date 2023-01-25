---
layout: post
title:  "[Old] Joining LUA to C++ Example"
date:   2011-10-10 17:00:00 +1300
categories: cpp
---
**This information is from my old website and may no longer be relevant**

This example demonstrates how to join LUA to C++ classes with very little coding.

tolua++ is an extended version of tolua. tolua is a tool which makes it easier to combine LUA and C/C++. It generates binding C/C++ code. tolua++ offers additional features and is designed for C++

You can download toLua++ from [https://github.com/LuaDist/toluapp](https://github.com/LuaDist/toluapp)

And the source code for this example can be downloaded [here]({% link assets/LuaToCppExample.zip %})

**Genereating tolua source files**

Type the following in the command prompt. You can prefix the source files with anything you like. My preference is to use the prefix "tolua_".

```console
tolua++ -o tolua_Player.cpp -H tolua_Player.h -n Player Player.pkg
```
The pkg file tells toLua++ what functions to make available to LUA.

When I run the exe I get the following output:

![example exe output](/assets/LuaToCppExample.png)


### Code
```c++
// main.cpp
#include <iostream>
#include <string>
using namespace std;

#include <tolua++.h>
#include <lua.hpp>
#include <lualib.h>
#include <lauxlib.h>

#include "Player.h"
#include "tolua_Player.h"

int main()
{
    //
    // Perform initalization. TODO: Add error checking for tolua?
    //
    lua_State *L = lua_open();

    if (NULL == L) {
        cout << "Error Initializing lua\n";
        return -1;
    }

    luaL_openlibs(L);   // initalize all lua standard library functions
    tolua_open(L);          // initalize tolua
    tolua_Player_open(L);   // make Player class accessible from LUA

    //
    //  Run lua script to create player. This could also have been done using luaL_dostring().
    //
    luaL_dofile(L, "loadplayer.lua");

    //
    // Get the player object from lua
    //
    lua_getglobal(L, "player");
    Player* player = (Player*)tolua_tousertype(L, -1, 0);

    //
    // Display health and change value
    //
    cout << "\nC++: Player's health is " << player->getHealth() << " - Now setting it to 6";
    player->setHealth(6);
    cout << "\nC++: Player's health is now " << player->getHealth() << "\n";

    //
    // The player object in LUA should now be updated. This code could also be put inside a lua script.
    //
    luaL_dostring(L, "io.write(\"LUA: Player's health is \"..player:getHealth()..\" - Now setting it to 11\")");
    luaL_dostring(L, "player:setHealth(11)");
    cout << endl;
    luaL_dostring(L, "io.write(\"LUA: Player's health is now \"..player:getHealth())");

    //
    // Perform cleanup.
    //
    lua_close(L);
    return 0;
}
```

```c++
// Player.h
#ifndef PLAYER_H
#define PLAYER_H

class Player {
    private:
        int health;
    public:
        Player();
        ~Player();
        void setHealth(int _health);
        int getHealth();
};

#endif // PLAYER_H
```

```c++
// Player.cpp
#include "Player.h"

Player::Player()
{
    health = 0;
}

Player::~Player()
{

}

void Player::setHealth(int _health)
{
    health = _health;
}

int Player::getHealth()
{
    return health;
}
```

```c++
// Player.pkg
$#include "Player.h"

class Player {
    Player();
    ~Player();
    void setHealth(int _health);
    int getHealth();
};
```

```lua
-- loadplayer.lua
-- Create new Player object and set health
player = Player:new()
player:setHealth(4)

-- Display players health
io.write("LUA: Player's health is "..player:getHealth());
```
