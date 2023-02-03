---
layout: home
title: "Portfolio"
permalink: /portfolio
redirect_from:
  - /resume/detailed
---

* Resume: {% include resume.html %}
* LinkedIn: [linkedin.com/in/rohinknight](https://www.linkedin.com/in/rohinknight/)
* Github: [github.com/rohinnz](https://github.com/rohinnz)
* Art Station: [artstation.com/rohin](https://www.artstation.com/rohin)

---
# Work Experience
## Blockchain Engineer / Game Developer
*2021-12 - present*

I'm building a Web3 puzzle game where players can mint their own puzzles as NFTs. Players will be able to win prizes for solving on-chain puzzles and earn royalties when their NFTs are used to construct larger puzzles. Started part-time. Full-time since December 2022.

I have solved many challenges, like preventing front-running to submitted solutions and finding a feasible solution to an expensive on-chain puzzle solver.

The hardhat project is on Github: [github.com/rohinnz/Block-Miner-Smart-Contracts](https://github.com/rohinnz/Block-Miner-Smart-Contracts)

I have also written two posts on Solidity security and gas optimization:
* [How to Prevent Reentrancy Attacks in Solidity]({% link _posts/2023-01-15-Reentrancy-Attacks.md %})
* [Optimizing Smart Contract Gas Costs]({% link _posts/2023-01-20-Solidity-Gas-Optimization.md %})

And I am currently learning [Rust](https://www.rust-lang.org/) and [Substrate](https://substrate.io/).

The game client is being built in Unity using the [ChainSafe web3.unity SDK](https://gaming.chainsafe.io/). I currently have a WebGL prototype that can interact with the smart contracts on the Goerli testnet. I plan to upload it to this website soon.

{% include lightbox.html src="resume/block-miner-level-editor.png" title="Block Miner - Level Editor" %}

## Senior Unity Engineer
**Myria** - [myria.com](https://myria.com/)<br />*2022-03 - 2022-12*

[Myria](https://myria.com/) is an Ethereum Layer 2 solution for game and app developers. It allows NFTs to be minted and transacted at lightning speed with no transaction fees.

I worked on [Moonville Farms](https://myria.com/game-detail/?gameId=moonville-farms) (A play-and-earn tycoon farming simulator) as the second lead programmer. It was a fully remote team across multiple time zones. I joined right at the start with the lead programmer, and together we wrote the TDD, designed the initial architecture and then interviewed programmer candidates and scaled up the team.

Some of my achievements include
* Helping architect the game. 
* Reviewing other programmers' work and giving feedback.
* Interviewing candidates (sometimes as the sole interviewer).
* Writing code for our .NET Server, including setting up unit tests.
* Writing documentation for the whole team. This included our C# coding standards and step-by-step guides for setting up projects and how to use Git with SSH on Windows which was also non-programmer friendly.
* Setting up the world map. There were several challenges, such as max WebGL texture size, pathfinding, and the pipeline for updating tile data.
* Setting up town water shader. We needed a seamless transition between two water shaders (Ocean and river), and the water surrounding the town could require any combination of the two.

### Gameplay Footage

NOTE: Not latest so missing some features i.e. town water shader.

{% include youtube.html id="tI81xqHRJBw" title="Game: Math Invaders" %}

## Lead Technical Artist
**PikPok** - [pikpok.com](https://pikpok.com/)<br />*2018-06 - 2022-03*

[PikPok](https://pikpok.com/) (formerly Sidhe Interactive) is one of New Zealand’s oldest and largest game studios. They have over 200 employees and have published games for Console, Steam and Mobile. Their mobile games alone have been downloaded more than 350 million times.

I was the lead technical artist of a two-person team, providing support for projects via tooling, runtime components, ensuring robust pipelines, performance optimisation, and shader/URP work.

Titles I worked on:
* [Agent Intercept](https://pikpok.com/games/agent-intercept/)
* [Rival Stars Horse Racing](https://pikpok.com/games/rival-stars-horse-racing/)
* [Into The Dead 2](https://pikpok.com/games/into-the-dead-2/)
* [Zombie Rescue Squad](https://pikpok.com/news/zombie-rescue-squad-launches-in-the-usa-on-new-snap-games-platform/)
* [Greedy Cats](https://pikpok.com/games/greedy-cats/)
* (a game still in soft launch).

[//]: # [My Cat Club](https://play.google.com/store/apps/details?id=com.pikpok.cats.play)

Unity Achievements:
* Built a UI scroll grid pooling system that allowed scrolling of thousands of items. It had an auto-layout feature with items able to span multiple rows/ columns. This package is now being used in all their recent games.
* Built a 2D Soft Mask package with support for nested 9-slice masks. Optimized performance via shader variants and precalculated some parts outside shader to avoid shader branching for mobile.
* Added SpeedTree wind support to a custom shader. Also needed to build an editor tool to fix old SpeedTree assets.
* Added Unity's terrain height blending to an old terrain shader. I used albedo alpha for height so I could exclude the mask texture and reduce the size.
* Wrote a water shader with shore foam using the depth buffer.
* Backported shadow fade for a game using an old custom URP.
* Fixed distant tunnel lighting for a game that didn't use baked shadows: Modified shaders to use vertex colour and then built a Unity & Blender tool to modify vertex colour on every mesh used in tunnels.
* Built several tools for animations, including copying animation events with relative or absolute time scales.
* Built a tool for duplicating whole game environments. Would duplicate Unity assets with materials and nested prefabs (Unity editor and Python script.)
* Built an editor tool for multi-prop placement, with the ability to change brush size and randomize selection, rotations, scale, etc. (Despite being an editor tool, it still required some performance optimization, including the use of square magnitude for comparing distances.)
* Built an editor tool for taking screenshots. Captured multiple resolutions in all available languages.
* Built an editor tool to quickly show/hide objects in the scene with a visibility indicator in the hierarchy (Before Unity 2019.1 was released with the visibility controls).
* Built gradient skybox shader and set up Cinemachine cameras for the boss fight scene. (I Am Monster.)

Maya and Photoshop Achievements:
* Gave my first presentation at NZGDC 2021.
* Updated Maya tool distribution for artists so they would always have the latest each time they started Maya. Also, set up Sentry reporting and unit testing.
* Rebuilt tool for reporting UV usage (Used the more complex API OpenMaya for better performance and improved math, using triangle area formula instead of Heron’s formula)
* Built a tool for bulk animation import, bake, playblasts, and export. Also added a feature to save clip notes and search through all clips in projects and the mocap library.
* Built multiple Photoshop plugins using UXP. The most complex one would export screenshots in multiple languages and ensure they were below a target file size.

Other Achievements:
* Built Windows app with GUI to bulk install Unity versions with script templates and sync with Unity Hub. The tool included a self-update feature, and it would scan your local checkouts and show you which projects required which version. Now used by everyone in Studio.
* Wrote npm script and pre-commit git hook for our Unity packages to enforce consistent namespaces and correct format for changelog updates.

### My NZGDC 2021 Presentation on Maya and Photoshop Tools
{% include youtube.html id="rg0VOf-2TW8" title="Rohin Knight's NZGDC 2021 Presentation on Maya and Photoshop Tools at PikPok" %}

### Trailers and Gameplay Videos
{% include youtube.html id="j_IMOxtV1e0" title="Agent Intercept Trailer by PikPok" %}
{% include youtube.html id="BROasPBA2y8" title="Rival Stars Horse Racing Trailer by PikPok" %}
{% include youtube.html id="4SxSFPYvSS0" title="Into The Dead 2 Trailer by PikPok" %}
{% include youtube.html id="TP-mzJrxsjU" title="Snapchat game Zombie Rescue Squad by PikPok" %}

## Game Programmer
**PikPok** - [pikpok.com](https://pikpok.com/)<br />*2015-01 -2018-06*

* Worked on several Unity game projects.
* Did a lot of Live Ops work on our legacy C++ titles, fixing hard-to-repro bugs, Upgrading ad plugins, configuring build settings, etc.
* Updated Unity iOS & Android plugins for In-app purchases and Ads.
* Built a complex Pyramid (Python) server app with a complex web scraper. This server app was used to track the top 200 apps in the Play store in every category for every country. Used Celery and Redis for handling multiple scraper tasks on an AWS server.
* Built a company floor plan web app (Flask) during a lab day. You could drag and drop people and furniture. Previously someone had to constantly update a PSD document.
* Built Unity iOS plugin for 3D Touch Support (before Unity had its own solution)

Titles I worked on:
* [Breakneck](https://pikpok.com/games/breakneck/)
* [Breakneck - Gamblit Gaming](https://pikpok.com/news/gamblit-gaming-brings-pikpoks-1-games-casino-floors/)
* [Rival Stars College Football](https://pikpok.com/games/rival-stars-college-football/)
* [I Am Monster](https://pikpok.com/games/i-am-monster/)
* [Four Letters](https://pikpok.com/games/fourletters/)
* BAGS (Baseball game that got cancelled)

Titles I did live ops work on
* [Into the Dead](https://pikpok.com/games/intothedead/)
* [Shadow Wars](https://pikpok.com/games/shadowwars/)
* [Dungeon Inc](https://pikpok.com/games/dungeon-inc/)
* [Rival Stars Basketball](https://pikpok.com/games/rivalstarsbasketball/) (C++)
* [Flick Kick Football Legends](https://pikpok.com/games/fkflegends/) (C++)
* [Turbo Fast](https://pikpok.com/news/turbo-fast-tops-50-million-downloads/) (C++)
* [Robot Unicorn Attack 2](https://www.youtube.com/watch?v=eEIxMmsd548) (C++)

### Trailers and Gameplay Videos
{% include youtube.html id="bNrolcIADqs" title="Breakneck Trailer by PikPok" %}
{% include youtube.html id="ekNfJQBq4Q8" title="I Am Monster Trailer by PikPok" %}
{% include youtube.html id="S4WZttMnmUg" title="Rival Stars College Football Trailer by PikPok" %}
{% include youtube.html id="GyYDs4oO_g8" title="Four Letters Trailer by PikPok" %}
{% include youtube.html id="In7zpnRQLQ4" title="Turbo Racing League. Developed by PikPok. Published by Dream Works" %}
{% include youtube.html id="eEIxMmsd548" title="Robot Unicorn Attack 2. Developed by PikPok. Published by Adult Swim" %}

## Mobile App Developer
**Bank of New Zealand (BNZ)** - [bnz.co.nz](https://www.bnz.co.nz/)<br />*2013-08 - 2015-01*

[BNZ](https://www.bnz.co.nz/) was started in 1861 and is one of New Zealand's big four banks.

* Worked on the Mobile Banking Apps.
* iOS and Android app development. (Objective-C, C, Java).
* Was sent to WWDC14 in San Francisco to do social networking and discover ways of improving our development processes.
* Helped write unit tests and refactor code to separate business logic from platform-specific code.
* Built and presented multiple prototypes to the whole digital team during innovation days. I was also able to convince management to prioritise adding Chinese language support to the apps.

## Mobile App Developer
**Harvest Your Data** - [harvestyourdata.com](https://www.harvestyourdata.com/)<br />*2011-04 - 2013-08*

[Harvest Your Data](https://www.harvestyourdata.com) provide mobile apps for collecting survey results. At the time, their competitive advantage was collecting responses offline and white labelling.

* iOS and some Android development (Objective-C, C/C++, Java).
* Constantly added new features, such as a signature question which captured smooth user
input as Bézier curves.
* Built a new survey engine using a TDD approach.
* Customized app to add white labelling support.
* Migrating code to Objective-C ARC and ensuring correct memory management patterns
applied in code
* Correctly handling bridging between Foundation and Core Foundation code.
* Created an HTML5 prototype while investigating moving to HTML5 to have one codebase for iOS and Android.
* Wrote custom build scripts and set up a Hudson build server.

{% include lightbox.html src="resume/survey-app.gif" title="iSURVEY App" %}{: style="width: 350px; display: block"}
{% include lightbox.html src="resume/isurvey-1.jpg" title="iSURVEY App - 1 of 2" %}{: style="width: 350px; display: inline-block"}
{% include lightbox.html src="resume/isurvey-2.jpg" title="iSURVEY App - 2 of 2" %}{: style="width: 350px; display: inline-block"}

## Website Developer
*2011-03 - 2011-04*

I built three websites with a friend. Two using Drupal CMS and one using GetSimple CMS. I did the programming and my friend did the graphics design work.

{% include lightbox.html src="resume/website-infuture-design.jpg" title="Website: Infuture Design" %}{: style="width: 350px; display: inline-block"}
{% include lightbox.html src="resume/website-chris-photography.jpg" title="Website: Chris Photography" %}{: style="width: 360px; display: inline-block"}
{% include lightbox.html src="resume/website-voice-and-presence.png" title="Website: Voice and Presence" %}{: style="width: 350px; display: inline-block"}

## English Teacher in China
*2010-01 - 2010-12*

I took a year off in 2010 to teach English in China and practise my Mandarin, it was amazing!

During this time I
* Continued C++ programming work part-time for ConSit Systems Ltd, and
* Taught myself Python by making a game using PyGame.

## Website Developer
**Catalyst IT Ltd** - [catalyst.net.nz](https://www.catalyst.net.nz/)<br />*2008-02 - 2010-01*

[Catalyst](https://www.catalyst.net.nz/) is New Zealand's largest open source specialist. During my time there I worked soley in a Linux environment and became familiar with the Ubuntu OS.

Languages and tools used: Drupal CMS, PHP, HTML, CSS, JavaScript, JQuery, Ajax, SQL, MySQL, PostgreSQL, Xdebug, Apache, mod_rewrite, Linux VServers, and bash scripting.

Achievements:<br />
* Wrote a bash script to automate site deployment to staging and production.
* Helped develop and maintain multiple Drupal websites. During most projects, I worked directly with the clients.
* Built a phpList newsletter system for the Civil Aviation Authority ([notifications.caa.govt.nz/](http://notifications.caa.govt.nz/)). The biggest challenge was avoiding core hacks to phpList so updates would be easy in the future. I was able to avoid this mostly by using Apache mod_rewrite scripting. However, there were two places where core hacks could not be avoided, so I ensured there was plenty of documentation covering this so future updates to phpList would be smooth.

{% include lightbox.html src="resume/website-recommended.png" title="Recommended Website" %}{: style="width: 350px; display: inline-block"}
{% include lightbox.html src="resume/website-voxy.png" title="Voxy Website" %}{: style="width: 350px; display: inline-block"}

## C++ Developer
**ConSit Systems Ltd**<br />*2007-10 - 2008-02*

This was my first programming job. I built two standalone Windows apps and a plugin for Archicad (A tool for architects).

* The first app was called the Design Assistant. The plugin would automatically load this app when Archicad started. Communication between the plugin and the app was done via interprocess communication.
* The assistant app would ask the architect questions during the design process. For example, if a wall was added, the Design Assistant would ask questions like "Is this wall load-bearing?"
* The second app was the Question Builder. It allowed the user to design multi-choice questions with complex flow rules visually. This data was then exported and loaded into the Design Assistant.

![VDA Project](/assets/resume/vda-project.png)

[//]: # todo: Find less blurry picture

---
# Game Jams

I've taken part in many game jams over the years. They are a fantastic learning experience and provide a great networking opportunity.

## Welcome to the Chain Reaction

{% include youtube.html id="KdHGgrNbMwo" title="Game: Welcome to the Chain Reaction" %}

[Welcome to the Chain Reaction](https://jamesgamesbro.itch.io/welcome-to-the-chain-reaction) is a horror game similar to [Welcome to the Game](https://store.steampowered.com/app/485380/Welcome_to_the_Game/).

I helped with 3d modelling (apartment and monster) and programming and did some earlier work on [Last Message](https://store.steampowered.com/app/1141030/Last_Message/).

## Memories
{% include lightbox.html src="resume/memories.png" title="Gamejam Game: Memories" %}

[Memories](https://globalgamejam.org/2019/games/memories-2) is a walking simulator about poetry, built using the Unreal Engine. I did the 3d modelling and C++ programming.

## Sweet-Tooth
{% include lightbox.html src="resume/sweet-tooth.png" title="Gamejam Game: Sweet-Tooth" %}

[Sweet-Tooth](https://olivieryc.itch.io/sweet-tooth) is a puzzle platformer. I modelled the characters and parts of the environment.

## Synthrave
{% include lightbox.html src="resume/synthrave-1.png" title="Gamejam Game: Synthrave. 1 of 2" %}{: style="width: 350px; display: inline-block"}
{% include lightbox.html src="resume/synthrave-2.jpg" title="Gamejam Game: Synthrave. 1 of 2" %}{: style="width: 350px; float: right"}

[Synthrave](https://olivieryc.itch.io/synthrave) is a music game where you crowd surf while playing a guitar. You need to play different notes to get the crowd to raise or lower you to avoid obstacles. I did the 3D modelling and most of the other artwork.

[//]: # todo: Record YouTube video

## Return to Earth
{% include lightbox.html src="resume/return-to-earth.png" title="Gamejam Game: Return to Earth" %}

[Return to Earth](https://rohin.itch.io/return-to-earth) is a simulation for restoring Earth after its destruction. I did almost all the art as the other artist could only attend for the first hour of the game jam.

## Heard it Through the Space Time
{% include lightbox.html src="resume/heard-it-through-the-space-time.png" title="Gamejam Game: Heard it Through the Space Time" %}

[Heard It Through The Space Time](https://globalgamejam.org/2018/games/heard-it-through-space-time) is a 2-player competitive game where you must spread a message to the most people during an alien party. I helped with programming and some of the art.

## Shake It
{% include lightbox.html src="resume/shakeit.png" title="Gamejam Game: Shake It" %}

[Shake It](https://globalgamejam.org/2016/games/shake-it) is a hand shaking simulator. I did the level editing, environment art and used a tool to generate all the characters and hooked up animations using Mixamo.

## House for the People

{% include lightbox.html src="resume/house-for-the-people.png" title="Gamejam Game: House for the People" %}

A C++ game built during Pixel Jam. You would drop pieces just like in Tetris with the goal of making X number of empty spaces. Empty spaces would then be populated with background walls, windows and doors. I did all the programming, and my friend did the artwork.

[//]: # todo: Find game and record YouTube video

---
# Other Games

## Puzzle Game - C++11

{% include lightbox.html src="resume/puzzle-game-prototype3.png" title="Game: Puzzle Game Prototype 3" %}

A puzzle game I made in C++11 using Cocos2dX. The puzzles are quite challenging and no one has yet completed all 20 puzzles.

The Windows build can be downloaded [here]({% link assets/code/PuzzleGamePrototype3.zip %}).

## Puzzle Game Prototype - TypeScript

{% include lightbox.html src="resume/puzzle-game-typescript.png" title="Game: TypeScript Puzzle Game Prototype" %}

A puzzle game prototype I built to teach myself TypeScript. Uses the [Phaser 3 Framework](https://phaser.io/phaser3).
Similar to the C++ version, but moves are now turn based with an undo feature.

I've uploaded the project to GitHub: [github.com/rohinnz/Puzzle-Game-TypeScript](https://github.com/rohinnz/Puzzle-Game-TypeScript)

## Marvon's Cannon

{% include lightbox.html src="resume/marvons-cannon1.jpg" title="Game: Marvon's Cannon - 1 of 3" %}

When I returned from China, I decided to teach myself iOS development by building a game. In this game, you have a cannon at the top of the hill on the left, and you must take down all approaching monsters from the right.

I didn't use any physics engine. Instead, I calculated the initial velocity for each cannonball based on where the player tapped the screen so the cannonball would pass through that point. Then, for the ground, I traced and then exported a path for it from GIMP and then used a line intersection calculation to keep the monsters above the ground.

I later rebuilt this game in C++11 using Cocos2dx and animated the monsters using 2D skeletal animation.

{% include lightbox.html src="resume/marvons-cannon2.jpg" title="Game: Marvon's Cannon - 2 of 3" %}{: style="width: 350px; display: inline-block"}
{% include lightbox.html src="resume/marvons-cannon3.png" title="Game: Marvon's Cannon - 3 of 3" %}{: style="width: 350px; display: inline-block"}

## Lode Runner Style Game

{% include lightbox.html src="resume/lode-runner-style-game2.jpg" title="Game: Lode Runner Style Game - 1 of 2" %}

I built a Lode Runner style game for iPad using C++ and Cocos2dx. Used A* for path finding.

I also built a version just to demonstrate A* and created a YouTube video.

{% include youtube.html id="ZOHaxjxgCN8" title="Demonstration of A*" %}

## Adventures of Vallus

I built a side-scroller game to teach myself Python while living in China. I created it using the PyGame framework and designed the code to strictly follow the Model-View-Controller architecture pattern. The source code can be downloaded [here]({% link assets/code/AdventuresOfVallus.zip %}).

{% include lightbox.html src="resume/adventures-of-vallus1.png" title="Game: Adventures of Vallus - 1 of 2" %}{: style="width: 360px; display: inline-block"}
{% include lightbox.html src="resume/adventures-of-vallus2.png" title="Game: Adventures of Vallus - 2 of 2" %}{: style="width: 360px; display: inline-block"}

## Kana Invaders

{% include youtube.html id="71SgkFh5rlM" title="Game: Kana Invaders" %}

This is the first C++ game I made using the SDL framework. It is an educational game for learning the Japanese Hiragana and Katakana.

The user must quickly enter the Kana's romanji as it falls from the top of the screen. Each time a Kana character gets hit, the pronunciation sound for that Kana will play.

I wrote everything from scratch for this game, including my own game library with scene manager, timers, font and image loaders, etc.

The game exe can be downloaded from Source Forge: [sourceforge.net/projects/kanainvaders](http://sourceforge.net/projects/kanainvaders/)<br />The source code can also be downloaded from Source Forge or [here]({% link assets/code/kanainvaders-0.3beta4-src.zip %}).

## Math Invaders

{% include youtube.html id="O9Gty6KN38E" title="Game: Math Invaders" %}

An educational math game I built in Java using J2ME. J2ME was used to build games before Android.

## Experimental Subjects
{% include lightbox.html src="resume/experimental-subjects.png" title="Game: Experimental Subjects" %}

Experimental Subjects is a text-based adventure game similar to Zork. I wrote the game in Java, and to make navigation easier for the player, I added a dynamic map.

[//]: # todo: Create WebGL build of game and put on itch.io

## Brutal Chess RV2AJ

{% include lightbox.html src="resume/brutal-chess1.png" title="Brutal Chess - Image 1 of 4" %}{: style="float: right"}
{% include lightbox.html src="resume/brutal-chess2.png" title="Brutal Chess - Image 2 of 4" %}

During my final year of my Bachelor of IT degree, I modified an open source Chess engine to control a Mitsubishi robotic arm and make it mimic all behaviour on a chess board. The project could handle capturing pieces, resetting the board, and dragging pieces along the board when there was a clear path.

The first challenge was to figure out how to communicate with the robotic arm because this was not documented anywhere. Fortunately, there was commercial software loaded onto the terminal PC which could control the arm, so I installed a serial port monitor to discover which commands were being sent when controlling the arm.

Towards the end of the project, many people had heard about my project and came to watch, including a chess group from a local primary school. Then the film school came and interviewed me, and the footage was aired on triangle TV. Finally, the advertising department came and decided to use photos of the project in their 2007 Mechatronics course brochure.

{% include lightbox.html src="resume/brutal-chess3.png" title="Brutal Chess - Image 3 of 4" %}{: style="width: 360px; display: inline-block"}
{% include lightbox.html src="resume/brutal-chess4.png" title="Brutal Chess - Image 4 of 4" %}{: style="width: 360px; display: inline-block"}

---
# Custom Maps for Call Of Duty

I used to play [Call of Duty United Offensive](https://store.steampowered.com/app/2640/Call_of_Duty_United_Offensive/) a lot with friends during LAN parties.

It wasn’t long before we were bored with the default maps, so I decided to create my own.

{% include lightbox.html src="cod/cod_map_editing_v2.png" title="COD Map Tool" %}

{% include lightbox.html src="cod/shot0014.jpg" title="COD Map" %}{: style="width: 360px; display: inline-block"}
{% include lightbox.html src="cod/shot0000.jpg" title="COD Map" %}{: style="width: 360px; display: inline-block"}
{% include lightbox.html src="cod/shot0010.jpg" title="COD Map" %}{: style="width: 360px; display: inline-block"}
{% include lightbox.html src="cod/shot0027.jpg" title="COD Map" %}{: style="width: 360px; display: inline-block"}
{% include lightbox.html src="cod/shot0020.jpg" title="COD Map" %}{: style="width: 360px; display: inline-block"}
{% include lightbox.html src="cod/shot0035.jpg" title="COD Map" %}{: style="width: 360px; display: inline-block"}
{% include lightbox.html src="cod/shot0025.jpg" title="COD Map" %}{: style="width: 360px; display: inline-block"}
{% include lightbox.html src="cod/shot0042.jpg" title="COD Map" %}{: style="width: 360px; display: inline-block"}
{% include lightbox.html src="cod/shot0047.jpg" title="COD Map" %}{: style="width: 360px; display: inline-block"}
{% include lightbox.html src="cod/shot0018.jpg" title="COD Map" %}{: style="width: 360px; display: inline-block"}