---
layout: post
title: Tile-Dependencies
description: tile-dependencies
platform: php
control: Tile
documentation: ug
---

# Tile Dependencies

The external script dependencies of the Tile component is,

jQuery 1.7.1 and later versions.

The ej.web.all.js is a bundle of all PHP controls. If you use ej.web.all.js in your application, you can leave this section or else you can try to render Tile in your application using ej.tile.min.js file. You can refer the following frameworks and controls in your project.

Tile Dependency files,

<table>
<tr>
<th>
File                          </th><th>
Description/Usage</th></tr>
<tr>
<td>
ej.core.min.js</td><td>
Must be referred always before using all the JS controls.</td></tr>
<tr>
<td>
ej.tile.min.js</td><td>
Should be referred when using tile control.</td></tr>
</table>

To get the real appearance of the Tile, the dependent CSS file `ej.web.all.min.css` (which includes styles of all the controls) should also needs to be referred.
Note: Uncompressed version of library files are also available which is used for development or debugging purpose and can be generated from the custom script [here](http://csg.syncfusion.com/).


