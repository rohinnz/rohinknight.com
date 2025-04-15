---
layout: post
title:  "Automatic Tool Distribution for Maya"
categories: techart
---

While I was working for [PikPok](https://pikpok.com/) as a Technical Artist, I built a pipeline for automatically distributing Maya tools to Artists.

I put a custom userSetup.py file in the artist's Maya preferences folder.

Then each time Maya was launched, this script would download and run a startup module which would then download a zip archive containing the latest tools.

I also wrote a script on our CI server so the zip archieve would be rebuilt every time an update was made to the main git branch.

{% include lightbox.html src="mayatools/PikPokToolsDistribution.png" title="Tech Art Tools Update Diagram" %}


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

# Import and run startup module which will download latest .zip
# and add it to the Maya path. It will also update custom shelves.
import startup
startup.run()
```

I gave a talk at NZGDC 2021 where I covered how this works.

{% include youtube.html id="rg0VOf-2TW8" title="Rohin Knight's NZGDC 2021 Presentation on Maya and Photoshop Tools at PikPok" %}
