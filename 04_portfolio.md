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

Building a Web3 puzzle game where players can mint their own puzzles as NFTs. Players can win prizes for solving on-chain puzzles and earn royalties when their NFTs are used to construct larger puzzles.

I have solved many challenges like how to prevent front-running to sumitted solutions and finding a feasible solution to an expensive on-chain puzzle solver.

Hardhat project on Github: [github.com/rohinnz/Block-Miner-Smart-Contracts](https://github.com/rohinnz/Block-Miner-Smart-Contracts)

I have also written two posts on Solidity security and gas optimization:
* [Reentrancy Attacks](https://rohinknight.com/solidity/2023/01/15/Reentrancy-Attacks)
* [Solidity Gas Optimization](https://rohinknight.com/solidity/2023/01/20/Solidity-Gas-Optimization)

Also, the game client is being built in Unity. I currently have a WebGL prototype that can interact with the smart contracts on the Goerli testnet. I will upload it to this website very soon.

{% include lightbox.html src="resume/block-miner-level-editor.png" title="Block Miner - Level Editor" %}{: style="width: 350px; display: inline-block"}

## Senior Unity Engineer
**Myria** - [myria.com](https://myria.com/)<br />*2022-03 - 2022-12*

Myria is an Ethereum Layer 2 solution for game and app developers. It allows NFTs to be minted and transacted at lightning speed with no transaction fees.

I worked on [Moonville Farms](https://myria.com/game-detail/?gameId=moonville-farms) (A play-and-earn tycoon farming simulator) as the second lead programmer. It was a fully remote team across multiple time zones. I joined right at the start with the lead programmer, and together we wrote the TDD, designed the initial architecture and then interviewed programmer candidates and scaled up the team.

Some of my achievements include
* Reviewing other programmers' work and giving feedback.
* Interviewing candidates (sometimes as the sole interviewer).
* Writing code for our .NET Server, including setting up unit tests.
* Writing documentation for the whole team. This included our C# coding standards and step-by-step guides for setting up projects and how to use Git with SSH on Windows which was also non-programmer friendly.
* Setting up the world map. There were several challenges, such as max WebGL texture size, pathfinding, and the pipeline for updating tile data.
* Setting up town water shader. We needed a seamless transition between two water shaders (Ocean and river), and the water surrounding the town could require any combination of the two.

Gameplay footage (Not latest so missing some features i.e. town water shader):
<iframe
    width="640"
    height="480"
    src="https://www.youtube.com/embed/tI81xqHRJBw"
    frameborder="0"
    allow="autoplay; encrypted-media"
    allowfullscreen
>
</iframe>

## Lead Technical Artist
**PikPok** - [pikpok.com](https://pikpok.com/)<br />*2018-06 - 2022-03*

PikPok (formerly Sidhe Interactive) is one of New Zealand’s oldest and largest game studios. They have over 200 employees and have published games for Console, Steam and Mobile. Their mobile games alone have been downloaded more than 350 million times.

I was the lead tech artist of a two-person team, providing support for projects via tooling, runtime components, ensuring robust pipelines, performance optimisation, and shader/URP work.

Games I worked on while a Technical Artist:
* [Agent Intercept](https://pikpok.com/games/agent-intercept/)
* [Rival Stars Horse Racing](https://pikpok.com/games/rival-stars-horse-racing/)
* [Into The Dead 2](https://pikpok.com/games/into-the-dead-2/)
* [Zombie Rescue Squad](https://pikpok.com/news/zombie-rescue-squad-launches-in-the-usa-on-new-snap-games-platform/)
* [Greedy Cats](https://pikpok.com/games/greedy-cats/)
* (a game still in soft launch).

[//]: # [My Cat Club](https://play.google.com/store/apps/details?id=com.pikpok.cats.play)

Unity Achievements:
* Built a UI scroll grid pooling system that allowed scrolling of thousands of items. Had an auto-layout feature with items able to span multiple rows/ columns. This package is now being used in all our projects.
* Built a 2D Soft Mask package with support for nested 9-slice masks. Optimised performance via shader variants and precalculated some parts outside shader to avoid shader branching for mobile.
* Added SpeedTree wind support to a custom shader. Also needed to build an editor tool to fix old SpeedTree assets.
* Added Unity's terrain height blending to an old terrain shader. I used albedo alpha for height so I could exclude the mask texture and reduce the size.
* Wrote a water shader with shore foam using the depth buffer.
* Backported shadow fade for a game using an old custom URP.
* Fixed distant tunnel lighting for a game that didn’t use baked shadows: Modified shaders to use vertex colour and then built a Unity & Blender tool to modify vertex colour on every mesh used in tunnels.
* Built several tools for animations, including copying animation events with relative or absolute time scales.
* Built a tool for duplicating whole game environments. Would duplicate Unity assets with materials and nested prefabs (Unity editor and Python script.)
* Built an editor tool for multi-prop placement, with the ability to change brush size and randomize selection, rotations, scale, etc. (Despite being an editor tool, it still required some performance optimisation, including the use of square magnitude for comparing distances.)
* Built an editor tool for taking screenshots. Captured multiple resolutions in all available languages.
* Built gradient skybox shader and set up Cinemachine cameras for boss fight scene. (I Am Monster.)

Maya and Photoshop Achievements:
* Gave my first presentation at NZGDC 2021.
* Updated Maya script distribution, so scripts get compiled and zipped on CI Server. Also, set up Sentry reporting and unit testing.
* Rebuilt tool for reporting UV usage (Used the more complex API OpenMaya for better performance and improved math, using triangle area formula instead of Heron’s formula)
* Built a tool for bulk animation import, bake, playblasts, and export. Also added a feature to save clip notes and search through all clips in projects and the mocap library.
* Built multiple Photoshop plugins using UXP. The most complex one would export screenshots in multiple languages and ensure they were below a target file size.

Other Achievements:
* Built Windows app to bulk install Unity versions with script templates and sync with Unity Hub. The tool included a self-update feature. Now used by everyone in Studio.
* Wrote npm script and pre-commit git hook for our Unity packages to enforce consistent namespaces and correct format for changelog updates.

### My NZGDC 2021 Presentation on Maya and Photoshop Tools
<iframe title="Rohin Knight - NZGDC 2021 Presentation on Maya and Photoshop Tools at PikPok" width="640" height="360" src="https://www.youtube.com/embed/rg0VOf-2TW8?feature=oembed" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen=""></iframe>

### Trailers and Gameplay Videos
<iframe title="Agent Intercept Trailer by PikPok" width="640" height="360" src="https://www.youtube.com/embed/j_IMOxtV1e0?feature=oembed" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen=""></iframe>

<iframe title="Rival Stars Horse Racing Trailer by PikPok" width="640" height="360" src="https://www.youtube.com/embed/BROasPBA2y8?feature=oembed" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen=""></iframe>

<iframe title="Into The Dead 2 Trailer by PikPok" width="640" height="360" src="https://www.youtube.com/embed/4SxSFPYvSS0?feature=oembed" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen=""></iframe>

<iframe title="Snapchat game Zombie Rescue Squad by PikPok" width="640" height="360" src="https://www.youtube.com/embed/TP-mzJrxsjU?feature=oembed" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen=""></iframe>

## Game Programmer
**PikPok** - [pikpok.com](https://pikpok.com/)<br />*2015-01 -2018-06*

* Built a complex Pyramid (Python) server app with a complex web scraper. This server app was used to track the top 200 apps in the Play store in every category for every country. Used Celery and Redis for handling multiple scraper tasks on an AWS server.
* Built a company floor plan web app (Flask) during a lab day. Could drag and drop people and furniture. Previously someone had to constantly update a PSD document.
* Did a lot of Live Ops work on our legacy C++ titles, fixing hard-to-repro bugs, Upgrading ad plugins, configuring build settings, etc.
* Built iOS plugin for 3D Touch Support (before Unity had their solution)
* Updated in-house iOS & Android plugins for In-app purchases and Ads.

Games I worked on before I was promoted to a Technical Artist:
* [Breakneck](https://pikpok.com/games/breakneck/)
* [Breakneck - Gamblit Gaming](https://pikpok.com/news/gamblit-gaming-brings-pikpoks-1-games-casino-floors/)
* [Rival Stars College Football](https://pikpok.com/games/rival-stars-college-football/)
* [I Am Monster](https://pikpok.com/games/i-am-monster/)
* [Four Letters](https://pikpok.com/games/fourletters/)
* BAGS (Baseball game that got cancelled)

I also did live ops work on
* [Into the Dead](https://pikpok.com/games/intothedead/)
* [Shadow Wars](https://pikpok.com/games/shadowwars/)
* [Dungeon Inc](https://pikpok.com/games/dungeon-inc/)
* [Rival Stars Basketball](https://pikpok.com/games/rivalstarsbasketball/) (C++)
* [Flick Kick Football Legends](https://pikpok.com/games/fkflegends/) (C++)
* [Turbo Fast](https://pikpok.com/news/turbo-fast-tops-50-million-downloads/) (C++)
* [Robot Unicorn Attack 2](https://www.youtube.com/watch?v=eEIxMmsd548) (C++)

### Trailers and Gameplay Videos
<iframe title="Breakneck Trailer by PikPok" width="640" height="360" src="https://www.youtube.com/embed/bNrolcIADqs?feature=oembed" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen=""></iframe>

<iframe title="I Am Monster Trailer by PikPok" width="640" height="360" src="https://www.youtube.com/embed/ekNfJQBq4Q8?feature=oembed" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen=""></iframe>

<iframe title="Rival Stars College Football Trailer by PikPok" width="640" height="360" src="https://www.youtube.com/embed/S4WZttMnmUg?feature=oembed" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen=""></iframe>

<iframe title="Four Letters Trailer by PikPok" width="640" height="360" src="https://www.youtube.com/embed/GyYDs4oO_g8?feature=oembed" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen=""></iframe>

<iframe title="Turbo Racing League. Developed by PikPok. Published by Dream Works" width="640" height="360" src="https://www.youtube.com/embed/In7zpnRQLQ4?feature=oembed" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen=""></iframe>

<iframe title="Robot Unicorn Attack 2. Developed by PikPok. Published by Adult Swim" width="640" height="360" src="https://www.youtube.com/embed/eEIxMmsd548?feature=oembed" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen=""></iframe>

## Mobile App Developer
**Bank of New Zealand** - [bnz.co.nz](https://www.bnz.co.nz/)<br />*2013-08 - 2015-01*

* iOS and Android app development. (Objective-C, C, Java).
* Worked on the Mobile Banking Apps.
* Was sent to WWDC14 in San Francisco to do social networking and discover ways of improving our development processes.
* Helped write unit tests and refactor code to separate business logic from platform specific code.
* Built and presented multiple prototypes to the whole digital team during innovation days. Was also able to convince management to prioritise adding Chinese language support to the apps.

## Mobile App Developer
**Contact Software Ltd** - [harvestyourdata.com](https://www.harvestyourdata.com/)<br />*2011-04 - 2013-08*

* iOS development and some Android development (Objective-C, C/C++, Java).
* Constantly added new features, such as a signature question which captured smooth user
input as Bézier curves.
* Built a new survey engine using a TDD approach.
* Customized app to add white labelling support.
* Migrating code to Objective-C ARC and ensuring correct memory management patterns
applied in code
* Correctly handling bridging between Foundation and Core Foundation code.
* Created an HTML5 prototype while investigating moving to HTML5 so we could have one codebase for iOS and Android.
* Wrote custom build scripts and set up a Hudson build server.



{% include lightbox.html src="resume/survey-app.gif" title="iSURVEY App" %}{: style="width: 350px; display: block"}
{% include lightbox.html src="resume/isurvey-1.jpg" title="iSURVEY App - 1 of 2" %}{: style="width: 350px; display: inline-block"}
{% include lightbox.html src="resume/isurvey-2.jpg" title="iSURVEY App - 2 of 2" %}{: style="width: 350px; display: inline-block"}

## English Teacher in China
*2010-01 - 2010-12*

Took a year off to teach English in China and practise my Mandarin. It was amazing!

* Continued C++ programming work part-time for ConSit Systems Ltd
* Taught myself Python by making a game using PyGame.

## Website Developer
**Catalyst IT Ltd** - [catalyst.net.nz](https://www.catalyst.net.nz/)<br />*2008-02 - 2010-01*

Catalyst is New Zealand's largest open source specialist. During my time there I worked soley in a Linux environment and became familiar with the Ubuntu OS.

Languages and tools used: Drupal, PHP, HTML, CSS, JavaScript, JQuery, Ajax, SQL, MySQL, PostgreSQL, Xdebug, Apache, mod_rewrite, Linux VServers, and bash scripting.

Achievements:<br />
* Wrote a bash script to automate site deployment to staging and production.
* Helped develop and maintain multiple Drupal websites. During most projects, I worked directly with the clients.
* Built a phpList newsletter system for the Civil Aviation Authority. (http://notifications.caa.govt.nz/). Biggest challenge was avoiding core hacks to phpList so updates would be easy in the future. I was able to mostly avoid this with Apache mod_rewrite scripting. There were however 2 places where core hacks could not be avoided, so I ensured there was plenty of documentation covering this so future updates to phpList would be smooth.

{% include lightbox.html src="resume/website-recommended.png" title="Recommended Website" %}{: style="width: 350px; display: inline-block"}
{% include lightbox.html src="resume/website-voxy.png" title="Voxy Website" %}{: style="width: 350px; display: inline-block"}


## C++ Developer
**ConSit Systems Ltd**<br />*2007-10 - 2008-02*

This was the first programming job I got. I built two standalone Windows apps and a plugin for Archicad (A tool for architects).

* The first app was called the design assistant. The plugin would automatically load this app when Archicad started. Communication between the plugin and app was done via interprocess communication.
* The assistant app would ask the architect questions during the design process. For example if a wall was added, the assitant app would ask questions like "Is this wall load bearing?"
* The second app was the question builder. It allowed the user to visually design multi-choice questions with complex flow rules. This data was then exported and loaded in the design assistant.

![VDA Project](/assets/resume/vda-project.png)

[//]: # (Find less blurry picture)

---
# Game Jams

I've taken part in many game jams over the years. They are a fantastic learning experience and provide a great networking opportunity.

## Welcome to the Chain Reaction
<iframe width="640" height="480" src="https://www.youtube.com/embed/KdHGgrNbMwo" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

[Welcome to the Chain Reaction](https://jamesgamesbro.itch.io/welcome-to-the-chain-reaction) is a horror game similar to [Welcome to the Game](https://store.steampowered.com/app/485380/Welcome_to_the_Game/).

I helped with 3d modelling (apartment and monster) and programming. I also did some earlier work on [Last Message](https://store.steampowered.com/app/1141030/Last_Message/).

## Memories
{% include lightbox.html src="resume/memories.png" title="Gamejam Game: Memories" %}

[Memories](https://globalgamejam.org/2019/games/memories-2) is a walking simulator about poetry. Built using the Unreal engine. I did the 3d modelling and C++ programming.

## Sweet-Tooth
{% include lightbox.html src="resume/sweet-tooth.png" title="Gamejam Game: Sweet-Tooth" %}

[Sweet-Tooth](https://olivieryc.itch.io/sweet-tooth) is a puzzle platformer. I modelled the characters and parts of environment.

## Synthrave
{% include lightbox.html src="resume/synthrave-1.png" title="Gamejam Game: Synthrave. 1 of 2" %}{: style="width: 350px; display: inline-block"}
{% include lightbox.html src="resume/synthrave-2.jpg" title="Gamejam Game: Synthrave. 1 of 2" %}{: style="width: 350px; float: right"}

[Synthrave](https://olivieryc.itch.io/synthrave) is a music game where you are crowd surfing while playing a guitar. You need to play different notes to get the crowd to raise or lower you in order to avoid obstacles along the way. I did the 3D modelling and most of the other artwork.

[//]: # todo: Record YouTube video

## Return to Earth
{% include lightbox.html src="resume/return-to-earth.png" title="Gamejam Game: Return to Earth" %}

[Return to Earth](https://rohin.itch.io/return-to-earth) is a simulation for restoring a destroyed earth. Almost all the art was done by me as the other artist could only attend for the first hour of the gamejam.

## Heard it Through the Space Time
{% include lightbox.html src="resume/heard-it-through-the-space-time.png" title="Gamejam Game: Heard it Through the Space Time" %}

[Heard It Through The Space Time](https://globalgamejam.org/2018/games/heard-it-through-space-time) is a 2-player competitive game where you need to spread a message to the most people during an alien party. I helped with programming and some of the art.

## Shake It
{% include lightbox.html src="resume/shakeit.png" title="Gamejam Game: Shake It" %}

[Shake It](https://globalgamejam.org/2016/games/shake-it) is a hand shaking simulator. I did level editing, environment art and used a tool to generate all the characters and hooked up animations using Mixamo.

## House for the People

{% include lightbox.html src="resume/house-for-the-people.png" title="Gamejam Game: House for the People" %}

A C++ game built during Pixel Jam. You would drop pieces just like in tetris with the goal of making X number of empty spaces. Empty spaces would then be populated with background walls, windows and doors. I did all the programming and my friend did the artwork.

[//]: # todo: Find game and record YouTube video

---
# Old Projects
Work that is over 10 years old.

## Websites

When I returned from China, I built 3 websites as a freelancer before I got a job as a mobile app developer.

The first two websites were built using Drupal CMS and the third was built using GetSimple CMS.

{% include lightbox.html src="resume/website-infuture-design.jpg" title="Website: Infuture Design" style="width: 300px" %}{% include lightbox.html src="resume/website-chris-photography.jpg" title="Website: Chris Photography" style="width: 300px" %}
{% include lightbox.html src="resume/website-voice-and-presence.png" title="Website: Voice and Presence" style="width: 300px" %}

## Marvon's Cannon

{% include lightbox.html src="resume/marvons-cannon1.jpg" title="Game: Marvon's Cannon - 1 of 3" %}

When I returned from China, I decided to teach myself iOS development by building a game. In this game you have a cannon at the top of the hill on the left and you need to take down all appraoching monsters from the right.

I didn't use any physics engine. I calculated the initial velocity for each cannon ball based on where the screen was tapped so the cannon ball would pass through that point. For the ground, I traced and then exported a path for it from GIMP and then used a line intersection calculation to keep the monsters above the ground.

I did not have an Apple computer at the time so I installed OSX in a virtual box on my laptop running linux.

I also later rebuilt this game in C++11 using Cocos2dx and animated the monsters using 2D skeletal animation.

{% include lightbox.html src="resume/marvons-cannon2.jpg" title="Game: Marvon's Cannon - 2 of 3" %}{: style="width: 350px; display: inline-block"}
{% include lightbox.html src="resume/marvons-cannon3.png" title="Game: Marvon's Cannon - 3 of 3" %}{: style="width: 350px; display: inline-block"}

## Lode Runner Style Game

{% include lightbox.html src="resume/lode-runner-style-game2.jpg" title="Game: Lode Runner Style Game - 1 of 2" %}

I built a Lode Runner style game for iPad using C++ and Cocos2dx. Used A* for path finding.

I also built a version just to demonstrate A* and created a YouTube video.

<iframe
    width="640"
    height="480"
    src="https://www.youtube.com/embed/ZOHaxjxgCN8"
    frameborder="0"
    allow="autoplay; encrypted-media"
    allowfullscreen
>
</iframe>

## Adventures of Vallus

A side-scroller game I built in order to teach myself Python while I was living in China.
I built it using PyGame and designed the code to strickly follow the Model-View-Controller architecture pattern.

Source code can be downloaded [here]({% link assets/code/AdventuresOfVallus.zip %}).

{% include lightbox.html src="resume/adventures-of-vallus1.png" title="Game: Adventures of Vallus - 1 of 2" %}{: style="width: 350px; display: inline-block"}
{% include lightbox.html src="resume/adventures-of-vallus2.png" title="Game: Adventures of Vallus - 2 of 2" %}{: style="width: 350px; display: inline-block"}

## Kana Invaders

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

The game exe can be downloaded from Source Forge: [sourceforge.net/projects/kanainvaders](http://sourceforge.net/projects/kanainvaders/)<br />The source code can be downloaded from the above link or [here]({% link assets/code/kanainvaders-0.3beta4-src.zip %}).

## Math Invaders

<iframe
    width="640"
    height="480"
    src="https://www.youtube.com/embed/O9Gty6KN38E"
    frameborder="0"
    allow="autoplay; encrypted-media"
    allowfullscreen
>
</iframe>

An educational math game I built in Java using J2ME. J2ME was used to build games before Android.

## Experimental Subjects
{% include lightbox.html src="resume/experimental-subjects.png" title="Game: Experimental Subjects" %}

Experimental Subjects is a text adventure game written in Java. You wake up in an underground base and quickly discover you have some form of drug-induced amnesia. The only way to survive is to kill "the hunters".

I added a dynamic map so the player knew where they were and where they could travel next.

## Brutal Chess RV2AJ

{% include lightbox.html src="resume/brutal-chess1.png" title="Brutal Chess - Image 1 of 4" %}{: style="float: right"}
{% include lightbox.html src="resume/brutal-chess2.png" title="Brutal Chess - Image 2 of 4" %}

For my final year project for the Bachelor of IT degree, I modified an open source Chess engine to control a Mitsubishi robotic arm and make it mimic all behaviour on a chess board. The project could handle capturing pieces, resetting the board, and also dragging pieces along the board when there was a clear path.

The first challenge was to figure out how to communicate with the robotic arm, because this was not documented anywhere. Fortunately, there was commercial software loaded onto the terminal PC which could control the arm, so I installed a serial port monitor to discover which commands were being sent when controlling the arm.

Towards the end of the project, many people had heard about my project and came to watch, including a chess group from a local primary school. Then the film school came and interviewed me and the footage was aired on triangle TV. Finally, the advertising department came and decided to use photos of the project in their 2007 Mechatronics course brochure.

{% include lightbox.html src="resume/brutal-chess3.png" title="Brutal Chess - Image 3 of 4" %}{: style="width: 350px; display: inline-block"}
{% include lightbox.html src="resume/brutal-chess4.png" title="Brutal Chess - Image 4 of 4" %}{: style="width: 350px; display: inline-block"}

---
# Custom Maps for Call Of Duty

I used to play [Call of Duty United Offensive](https://store.steampowered.com/app/2640/Call_of_Duty_United_Offensive/) a lot with friends during LAN parties.

It wasn't long before we were borded of the default maps, so I decided to build my own.

{% include lightbox.html src="cod/shot0010.jpg" title="COD Map" %}{: style="width: 350px; display: inline-block"}
{% include lightbox.html src="cod/shot0027.jpg" title="COD Map" %}{: style="width: 350px; display: inline-block"}
{% include lightbox.html src="cod/shot0020.jpg" title="COD Map" %}{: style="width: 350px; display: inline-block"}
{% include lightbox.html src="cod/shot0035.jpg" title="COD Map" %}{: style="width: 350px; display: inline-block"}
{% include lightbox.html src="cod/shot0025.jpg" title="COD Map" %}{: style="width: 350px; display: inline-block"}
{% include lightbox.html src="cod/shot0042.jpg" title="COD Map" %}{: style="width: 350px; display: inline-block"}
{% include lightbox.html src="cod/shot0047.jpg" title="COD Map" %}{: style="width: 350px; display: inline-block"}
{% include lightbox.html src="cod/shot0018.jpg" title="COD Map" %}{: style="width: 350px; display: inline-block"}
