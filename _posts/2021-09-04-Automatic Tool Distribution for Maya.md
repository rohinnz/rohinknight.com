---
layout: post
title:  "Automatic Tool Distribution for Maya"
date:   2021-09-04 17:00:00 +1300
categories: techart
---

While I was working for [PikPok](https://pikpok.com/) as a Technical Artist, I built a pipeline for automatically distributing Maya tools to Artists.

I put a custom userSetup.py file in the artist's Maya preferences folder.

Then each time Maya was launched, this script would download and run a startup module which will then download a zip archive containing the latest tools.

On our CI server, I wrote a script to create a new zip archive with every update to the main git branch.

![Tech Art Tools Update Diagram](/assets/NZGDC-techart-tools-update.jpg)

```python
# userSetup.py
# This file is stored in the Maya scripts folder. E.g.
# C:\Documents and Settings\artist\My Documents\maya\2022\scripts
import os
import shutil
import maya

# Download latest startup module from network drive
source_path = r'I:\Maya\Scripts\startup.py'
destination_path = os.path.join(os.environ['MAYA_APP_DIR'],\
  maya.cmds.about(version=True), r'scripts\startup.py')

if os.path.isfile(source_path):
  shutil.copy(source_path, destination_path)

# Import and run startup module which will download lates
# tools .zip and add it to the Maya path and update 
# custom shelves
import startup
startup.run()
```

I gave a talk at NZGDC 2021 where I covered how this works.

<iframe
    width="640"
    height="480"
    src="https://www.youtube.com/embed/rg0VOf-2TW8?t=12m50s"
    frameborder="0"
    allow="autoplay; encrypted-media"
    allowfullscreen
>
</iframe>