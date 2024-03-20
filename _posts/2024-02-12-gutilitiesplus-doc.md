---
layout: single
class: wide
title: "GUtilitiesPlus"
date: 2024-03-20 00:00:00 +0000
categories: Audio Editing
excerpt: A quick guide to using GUtilitiesPlus Reaper tools
toc: true
toc_sticky: true
toc_label: "GUtilitiesPlus Scripts"
toc_icon: "cog"
sidebar:
    title: "GUtilitiesPlus Links"
    nav: sidebar-GUtilitiesPlus
---
# GU_Batch importer

<img src="{{ site.url }}{{ site.baseurl }}/assets/2024-02-12-gutilitiesplus-doc/gutil_batch_import.gif">

Recursively imports all media from within a specified folder. It also creates a Track structure that mimics the folder depth of the files imported, meaning imported files can be re-exported with the same folder structure.

{:.notice--info}
You can use the *$folders* and *$track* wildcards in the **Render to File** dialog to render out the folder structure. Folders that don't exist will be created automatically.
<br><br><img src="{{ site.url }}{{ site.baseurl }}/assets/2024-02-12-gutilitiesplus-doc/gutil_render_to_file_wildcard_tip.png">

# GU_Item alias generator

<img src="{{ site.url }}{{ site.baseurl }}/assets/2024-02-12-gutilitiesplus-doc/gutil_item_alias_generator.gif">

Creates empty Items in the top-most parent Track for selected Items, based on whether the Items are overlapping in time. 

{:.notice--info}
These blank Items can be used like 2D Regions for rendering purposes. 

# GU_Item fader

Fades selected Items by the percentage of their length. 

# GU_Item renamer
<img src="{{site.baseural}}https://i.imgur.com/7kCk38I.gif">

Batch renames selected Items' active Takes, roughly following the supported wildcard in Reaper's own **Render to File** dialog.

{:.notice--info}
As a quality-of-life feature, wildcards which support round brackets can be scrolled through in the dropdown to view the various options specific to the project. This can be especially helpful in large projects that make liberal use of the special *$region()* wildcard. <br><br>Further, wildcards which support incremental numbers, such as *$itemnumber*, can use square brackets to create leading zeros. So "$itenumber[025]" will start from 025, and count up for each item. In this example, numbers bigger than 3 digits will print regularly, e.g. 999, 1000, 1001...

# GU_Set item length (before/after snap offset)
<img src="{{site.baseural}}https://i.imgur.com/XLPu4PN.gif">

Sets selected Items' lengths before or after their snap offsets.

{:.notice--info}
Useful for when you want consistent attack times across Items, snapping neatly to the grid - while also allowing a customisable "pre-entry" for audio which swells or builds. 

# GU_Source validator
<img src="{{site.baseural}}https://i.imgur.com/sGUDSPd.gif">

A powerhouse tool for viewing info about your Source Audio at a glance. A non-GUI version of the script is also provided to allow direct export to .csv for use in a separate spreadsheet software.

{:.notice--warning}
GU_Source validator only inspects Source Audio as it appears on disk. It doesn't take FX or mix adjustments into account. It's intended to be used as the last step in the chain for QA purposes.

If you're working on a project with a strict style guide, you can pull up the **Set Validation Settings** menu to colour/highlight any divergence in the main view. Most of this is self-explanatory, allowing you to inspect properties such as the number of *channels*, *sample rate*, *loudness*, etc.

*Silence Intro/Outro* indicates if there is lengthy silence taking up valuable space, and *Zero Start/End* shows whether your Source starts and ends on a zero-crossing to ensure discontinuity-free playback. 

{:.notice--info}
The settings for these can be adjusted in the **Settings → Detection** menu. Discontinuities may be so small as to be completely inaudible, so this can be used to dial in a more sensible threshold.

The *Regions* column indicates whether a Source file has embedded loop markers. Handy for ensuring your loops have been exported correctly.

Finally, *Is Mono* assists in quickly checking if a file is effectively monophonic. Any single-channel file will of course be monophonic, but it's easy to accidentally export something as a multichannel file with identical channels. 