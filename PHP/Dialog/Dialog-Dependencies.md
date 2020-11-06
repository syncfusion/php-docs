---
layout: post
title: Dialog-Dependencies
description: dialog-dependencies
platform: php
control: Dialog
documentation: ug
---

# Dialog Dependencies

The external script dependencies of the Dialog control are,

•	jQuery 1.7.1 and later versions.

And the internal script dependencies of the Dialog control are:

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
ej.data.min.js</td><td>
Used to handle data manager operation and should be used while binding data to JS controls.</td></tr>
<tr>
<td>
ej.touch.min.js</td><td>
For providing touch support.</td></tr>
<tr>
<td>
ej.dialog.min.js</td><td>
This is the main source file specific for rendering Dialog.</td></tr>
<tr>
<td>
ej.scroller.min.js</td><td>
Providing ejScroller for our Dialog.</td></tr>
<tr>
<td>
ej.draggable.min.js</td><td>
Used to drag the dialog in anywhere in the browser.</td></tr>
</table>

To get the real appearance of the Dialog, the dependent CSS file `ej.web.all.min.css` (which includes styles of all the controls) should also needs to be referred.

>Note: Uncompressed version of library files are also available which is used for development or debugging purpose and can be generated from the custom script [here](http://csg.syncfusion.com/).
