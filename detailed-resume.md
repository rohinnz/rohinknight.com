---
layout: post
title: "Detailed Resume"
exclude: true
permalink: /resume/detailed
---

```
This page is still under construction. Last updated 2023-01-27.
```

## Experience
### Blockchain Game Developer
*2021-12 - present*

Building a Web3 puzzle game where players can mint their own puzzles as NFTs. Players can win prizes for solving on-chain puzzles and earn royalties when their NFTs are used to construct larger puzzles.

I have solved many challenges like how to prevent front-running to sumitted solutions and finding a feasible solution to an expensive on-chain puzzle solver.

Currently learning zkSync and Cairo and plan to integrate them soon.

Hardhat project on Github: [github.com/rohinnz/Block-Miner-Smart-Contracts](https://github.com/rohinnz/Block-Miner-Smart-Contracts)

I have also written two posts on Solidity security and gas optimization:
* [Reentrancy Attacks](https://rohinknight.com/solidity/2023/01/15/Reentrancy-Attacks)
* [Solidity Gas Optimization](https://rohinknight.com/solidity/2023/01/20/Solidity-Gas-Optimization)

Also, the game client is being built in Unity. I currently have a WebGL prototype that can interact with the smart contracts on the Goerli testnet. I will upload it to this website very soon.

### Senior Unity Engineer
**Myria** - [myria.com](https://myria.com/)<br />*2022-03 - 2022-12*

Myria is an Ethereum Layer 2 solution for game and app developers. It allows NFTs to be minted and transacted at lightning speed with no transaction fees.

I worked on [Moonville Farms](https://myria.com/game-detail/?gameId=moonville-farms) (A play-and-earn tycoon farming simulator) as the second lead programmer. It was a fully remote team across multiple time zones. I joined right at the start with the lead programmer, and together we wrote the TDD, designed the initial architecture and then interviewed programmer candidates and scaled up the team.

Some of my achievements include
* Interviewing candidates (sometimes as the sole interviewer), including for roles above my knowledge (i.e. .NET Server Dev)
* Writing code for our .NET Server, including setting up unit tests.
* Writing documentation for the team. This included our C# coding standards and step-by-step guides for setting up projects and how to use Git with SSH on Windows (Non-programmer friendly).
* Setting up the world map. There were several challenges, such as max WebGL texture size, pathfinding, and the pipeline for updating tile data.
* Setting up town water shader. We needed a seamless transition between two water shaders (Ocean and river), and the water surrounding the town could require any combination of the two.


### Lead Technical Artist
**PikPok** - [pikpok.com](https://pikpok.com/)<br />*2018-06 - 2022-03*

PikPok (www.pikpok.com, formerly Sidhe Interactive) is one of New Zealand’s oldest and largest game studios. They have over 200 employees and have published games for Console, Steam and Mobile. Their mobile games alone have been downloaded more than 350 million times.

I was the lead tech artist of a two-person team, providing support for projects via tooling, ensuring robust pipelines, performance optimisation, and shader/URP work.

Games I worked on included
* Agent Intercept
* Rival Stars Horse Racing
* Into the Dead 2
* Breakneck
* Breakneck - Gamblit Gaming
* Rival Stars College Football
* I Am Monster
* Zombie Rescue Squad
* Four Letters
* (game still in soft launch).

And I’ve done live ops work on 
* Into the Dead
* Shadow Wars
* Dungeon Inc
* Rival Stars Basketball
* Flick Kick Football Legends
* Turbo Fast
* Robot Unicorn Attack 2.

Unity Achievements:
* Built a UI scroll grid pooling system that allowed scrolling of thousands of items. Had an auto-layout feature with items able to span multiple rows/ columns. This package is now being used in all our projects.
* Built a 2D Soft Mask package with support for nested 9-slice masks. Optimised performance via shader variants and precalculated some parts outside shader to avoid shader branching for mobile.
* Added SpeedTree wind support to a custom shader. Also needed to build an editor tool to fix old SpeedTree assets.
* Added Unity's terrain height blending to an old terrain shader. I used albedo alpha for height so I could exclude the mask texture and reduce the size.
* Wrote a water shader with shore foam using the depth buffer.
* Backported shadow fade for a game using an old custom URP.
* Fixed distant tunnel lighting for a game that didn’t use baked shadows: Modified shaders to use vertex colour and then built a Unity/Blender tool to modify vertex colour on every mesh used in tunnels.
* Built gradient skybox shader and set up Cinemachine cameras for boss fight scene
* Built several tools for animations, including copying animation events with relative or absolute time scales.
* Built a tool for duplicating whole game environments. Would duplicate Unity assets with materials and nested prefabs (Unity editor and Python script)
* Built an editor tool for multi-prop placement, with the ability to change brush size and randomize selection, rotations, scale, etc. (Despite being an editor tool, it still required some performance optimisation, including the use of square magnitude for comparing distances.)
* Built an editor tool for taking screenshots. Captured multiple resolutions in all available languages.
* Built iOS plugin for 3D Touch Support (before Unity had their solution)
* Updated in-house iOS & Android plugins for In-app purchases and Ads.

Maya and Photoshop Achievements:
* Gave a presentation at NZGDC 2021: [www.youtube.com/watch?v=rg0VOf-2TW8](www.youtube.com/watch?v=rg0VOf-2TW8)
* Updated Maya script distribution, so scripts get compiled and zipped on CI Server. Also, set up Sentry reporting and unit testing.
* Rebuilt tool for reporting UV usage (Used the more complex API OpenMaya for better performance and improved math, using triangle area formula instead of Heron’s formula)
* Built a tool for bulk animation import, bake, playblasts, and export. Also added a feature to save clip notes and search through all clips in projects and the mocap library.
* Built multiple Photoshop plugins using UXP. The most complex one would export screenshots in multiple languages and ensure they were below a target file size.

Other Achievements:
* Built Windows app to bulk install Unity versions with script templates and sync with Unity Hub. The tool included a self-update feature. Now used by everyone in Studio.
* Wrote npm script and pre-commit git hook for our Unity packages to enforce consistent namespaces and correct format for changelog updates.


### Game Programmer
**PikPok** - [pikpok.com](https://pikpok.com/)<br />*2015-01 -2018-06*

* Built a complex Pyramid (Python) server app with a complex web scraper. This server app was used to track the top 200 apps in the Play store in every category for every country. Used Celery and Redis for handling multiple scraper tasks on an AWS server.
* Built a company floor plan web app (Flask) during a lab day. Could drag and drop people and furniture. Previously someone had to constantly update a PSD document.
* Did a lot of Live Ops work on our legacy C++ titles, fixing hard-to-repro bugs, Upgrading ad plugins, configuring build settings, etc.



### Mobile App Developer
**Bank of New Zealand** - [bnz.co.nz](https://www.bnz.co.nz/)<br />*2013-08 - 2015-01*

* iOS and Android app development. Worked on the Mobile Banking Apps.
* Was sent to WWDC14 in San Francisco to do social networking and discover ways of improving our development processes.
* Helped write unit tests and refactor code to separate business logic from platform
specific code.
* Built and presented multiple prototypes during innovation days to a large audience. Managed to convince management to prioritise adding Chinese language support.

### Mobile App Developer
**Contact Software Ltd** - [harvestyourdata.com](https://www.harvestyourdata.com/)<br />*2011-04 - 2013-08*

* iOS development and some Android development (Objective-C, C/C++, Java).
* Added a signature feature which converted touch input to smooth Bézier curves.
* Built a new survey engine using a TDD approach.
* Customized app to add white labelling support
* Migrating code to Objective-C ARC and ensuring correct memory management patterns
applied in code
* Correctly handling bridging between Foundation and Core Foundation code.
* Constantly added new features, such as a signature question which captured smooth user
input as Bézier curves.
* Created an HTML5 prototype while investigating moving to HTML5 so we could have one codebase for iOS and Android.
* Wrote custom build scripts and set up a Hudson build server.

### English Teacher in China
*2010-01 - 2010-12*

Took a year off to teach English in China and practise my Mandarin. It was amazing!

* Continued C++ programming work part-time for ConSit Systems Ltd 
* Taught myself Python by making a game using PyGame.

### Website Developer
**Catalyst IT Ltd** - [catalyst.net.nz](https://www.catalyst.net.nz/)<br />*2008-02 - 2010-01*

Catalyst is New Zealand's largest open source specialist. During my time there I worked soley in a Linux environment and became familiar with the Ubuntu OS.

Languages and tools used: Drupal, PHP, HTML, CSS, JavaScript, JQuery, Ajax, SQL, MySQL, PostgreSQL, Xdebug, Apache, mod_rewrite, Linux VServers, and bash scripting.

Achievements:<br />
* Wrote a bash script to automate site deployment to staging and production.
* Helped develop and maintain multiple Drupal websites. During most projects, I worked directly
with the clients.
* Built a phpList newsletter system for the Civil Aviation Authority. (http://notifications.caa.govt.nz/). I was very careful while developing this to avoid making changes to the the phpList package so it would be possible to update it in the future. I achieved this with Apache mod_rewrite scripting.

### C++ Developer
**ConSit Systems Ltd**<br />*2007-10 - 2008-02*

* Built a standalone Windows app and a plugin for Archicad (A tool for architects). The the assistant app would detect user input in Archicad via the plugin and perform certian actions. For example if the Architect added a wall, the app would them prompt the architect to state whether the wall was load bearing, etc.
* Build a second standalone which was an editor tool for visually creating questions and complex flow rules to be used in the assistant app.
* The assistant app communicated with the plugin using interprocess communication.


## Old Projects 

### Websites

Websites I built while working as a freelancer. First two built using Drupal CMS and the third build using GetSimple CMS.

{% include lightbox.html src="resume/website-infuture-design.jpg" title="Website: Infuture Design" style="width: 300px" %}{% include lightbox.html src="resume/website-chris-photography.jpg" title="Website: Chris Photography" style="width: 300px" %}
{% include lightbox.html src="resume/website-voice-and-presence.png" title="Website: Voice and Presence" style="width: 300px" %}

### Adventures of Vallus

A side-scroller game I built in order to teach myself Python while I was living in China.
I built it using PyGame and designed the code to strickly follow the Model-View-Controller architecture pattern.

{% include lightbox.html src="resume/adventures-of-vallus1.png" title="Game: Adventures of Vallus - 1 of 2" style="width: 300px" %}{% include lightbox.html src="resume/adventures-of-vallus2.png" title="Game: Adventures of Vallus - 2 of 2" style="width: 300px" %}

[//]: # (Add link to download code)


### VDA Project

![VDA Project](/assets/resume/vda-project.png)

As part of the VDA Project I developed two windows applications and a plug-in for ArchiCAD.

The software was developed in C++ using Borland Builder 6 and MS Visual Studio 2003. One of the applications built used a lot of OO and polymorphism.

[//]: # (Find less blurry picture)

### Brutal Chess RV2AJ

{% include lightbox.html src="resume/brutal-chess1.png" title="Brutal Chess - Image 1 of 4" %}{: style="float: right"}
{% include lightbox.html src="resume/brutal-chess2.png" title="Brutal Chess - Image 2 of 4" %}

For my final year project for the Bachelor of IT degree, I modified an open source Chess engine to control a Mitsubishi robotic arm and make it mimic all behaviour on a chess board. The project could handle capturing pieces, resetting the board, and also dragging pieces along the board when there was a clear path.

The first challenge was to figure out how to communicate with the robotic arm, because this was not documented anywhere. Fortunately, there was commercial software loaded onto the terminal PC which could control the arm, so I installed a serial port monitor to discover which commands were being sent when controlling the arm.

Towards the end of the project, many people had heard about my project and came to watch, including a chess group from a local primary school. Then the film school came and interviewed me and the footage was aired on triangle TV. Finally, the advertising department came and decided to use photos of the project in their 2007 Mechatronics course brochure.

{% include lightbox.html src="resume/brutal-chess3.png" title="Brutal Chess - Image 3 of 4" style="width: 280px" %}{: style="float: right"}
{% include lightbox.html src="resume/brutal-chess4.png" title="Brutal Chess - Image 4 of 4" style="width: 280px" %}

### Kana Invaders

<iframe
    width="640"
    height="480"
    src="https://www.youtube.com/embed/71SgkFh5rlM"
    frameborder="0"
    allow="autoplay; encrypted-media"
    allowfullscreen
>
</iframe>

This is the first C++ game I wrote using the SDL framework. It is an educational game for learning the Japanese Hiragana and Katakana.

The user must quickly enter the Kana's romanji as it falls from the top of the screen. Each time a kana character gets hit, the pronunciation sound for that kana will play.

When I wrote this game I also wrote my own game library, which was complete with a scene manager, timers, font loader, and image loader.

The game exe can be downloaded from Source Forge: [sourceforge.net/projects/kanainvaders](http://sourceforge.net/projects/kanainvaders/)<br />The source code can be downloaded from the above link or [here]({% link assets/kanainvaders-0.3beta4-src.zip %}).

### Math Invaders

<iframe
    width="640"
    height="480"
    src="https://www.youtube.com/embed/O9Gty6KN38E"
    frameborder="0"
    allow="autoplay; encrypted-media"
    allowfullscreen
>
</iframe>

An educational game I built in Java using J2ME. J2ME was used to build games before Android.

### Experimental Subjects

![Experimental Subjects](/assets/resume/experimental-subjects.png)

Experimental Subjects is a text adventure game with written in Java. You wake up in an underground base and quickly discover you have some form of drug-induced amnesia. The only way to survive is to kill "the hunters".

I also built a dynamic map for the game so it was always clear which directions you could travel in.
