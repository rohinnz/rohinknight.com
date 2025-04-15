---
layout: post
title:  "Maya Bulk Exporter Tool"
categories: techart
---

While I was a Tech Artist at PikPok, the largest Maya tool I built was Bulk Exporter 3—a tool for bulk importing, baking, and exporting animations.

Before this tool, there was a legacy version called Bulk Exporter 2, which I took over maintaining and extending. However, I quickly discovered that a lot of my time was being wasted on unnecessary UI updates.

{% include lightbox.html src="mayatools/BulkExporter2.png" title="Legacy Bulk Exporter" %}

So, I made the decision to rebuild the tool from the ground up using Qt. I also incorporated the Qt Designer into my workflow, along with a script to automatically convert the UI XML files to Python every time I tested the tool. This approach allowed for rapid iteration during development.

{% include lightbox.html src="mayatools/BulkExporter3Qt.png" title="Bulk Exporter 3 Qt" %}

Here’s how the final tool turned out—it became much more intuitive for animators to use, and adding new features became much easier.

{% include lightbox.html src="mayatools/BulkExporter3.png" title="Bulk Exporter 3" %}


# Finding Animation Clips

The most important update in Bulk Exporter 3 was the ability to search for animation clips and store notes on them. Some clips contained valuable snippets that animators often copied and reused, but tracking them down was difficult.

I added support for per-clip notes and created a dedicated window for searching clips.

{% include lightbox.html src="mayatools/BulkExporterClipSearch.png" title="Bulk Exporter 3 Qt" %}

To make sure the notes wouldn’t get lost, I avoided saving them in separate files or databases.

Since animation clips are essentially collections of MEL commands, I wrote a plugin that automatically appends the notes to the end of the clip file upon saving.

Instead of storing just the notes, I also saved a MEL command that would reattach the notes to the clip upon import:

```mel
evalDeferred "addAttr -sn \"nts\" -ln \"notes\" -dt \"string\" \"walk01\";setAttr -type \"string\" \"walk01.notes\" \"Lorem Ipsum\"";
```

The final challenge was how to search the mocap library. Having the search window read the last line of every mocap file wasn’t feasible.

To solve this, I wrote a script that trawled through all the mocap clips on the network drive and cached the results in a SQLite database.
