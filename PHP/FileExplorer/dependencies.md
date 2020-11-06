---
title: FileExplorer dependencies	
description: Dependencies required to render the FileExplorer control
platform: php
control: FileExplorer
documentation: ug
keywords: FileExplorer dependency files  
---

# External and Internal Dependencies

The FileExplorer control has the following list of external JavaScript dependencies.

* [`jQuery 1.7.1`](http://jquery.com) and later versions
* [`jsRender`](https://github.com/borismoore/jsrender) - to render the grid view

Refer to the internal dependencies in the following table.

<table>
<tr>
<th>
File</th><th>
Description/Usage</th></tr>
<tr>
<td>
ej.core.min.js<br/><br/></td><td>
Must be referred always before using all the JS controls.<br/><br/></td></tr>
<tr>
<td>
ej.data.min.js<br/><br/></td><td>
Used to handle data operation and should be used while binding data to JS controls.<br/><br/></td></tr>
<tr>
<td>
ej.draggable.min.js<br/><br/></td><td>
Used to handle the drag and drop functionality<br/><br/></td></tr>
<tr>
<td>
ej.touch.min.js<br/><br/></td><td>
Used to handle touch functionality<br/><br/></td></tr>
<tr>
<td>
ej.checkbox.min.js<br/><br/></td><td>
Used to handle multiple file selection<br/><br/></td></tr>
<tr>
<td>
ej.scroller.min.js<br/><br/></td><td>
Used to show the scroller in the layout area<br/><br/></td></tr>
<tr>
<td>
ej.button.min.js<br/><br/></td><td>
Used to display the buttons in the toolbar<br/><br/></td></tr>
<tr>
<td>
ej.splitbutton.min.js<br/><br/></td><td>
Used to display the split buttons in the toolbar<br/><br/></td></tr>
<tr>
<td>
ej.treeview.min.js<br/><br/></td><td>
Used to display the treeview in the navigation pane<br/><br/></td></tr>
<tr>
<td>
ej.uploadbox.min.js<br/><br/></td><td>
Used to perform the upload functionality <br/><br/></td></tr>
<tr>
<td>
ej.waitingpopup.min.js<br/><br/></td><td>
Used to showcase the waiting popup<br/><br/></td></tr>
<tr>
<td>
ej.dialog.min.js<br/><br/></td><td>
Used to create the alert windows <br/><br/></td></tr>
<tr>
<td>
ej.splitter.min.js<br/><br/></td><td>
Used as the body section to separate the navigation and layout area<br/><br/></td></tr>
<tr>
<td>
ej.toolbar.min.js<br/><br/></td><td>
Used to showcase the hearer section<br/><br/></td></tr>
<tr>
<td>
ej.tooltip.min.js<br/><br/></td><td>
Used to showcase the tooltip in toolbar<br/><br/></td></tr>
<tr>
<td>
ej.menu.min.js<br/><br/></td><td>
Used to showcase the context menu<br/><br/></td></tr>
<tr>
<td>
ej.grid.min.js<br/><br/></td><td>
Used to showcase the grid layout view<br/><br/></td></tr>
<tr>
<td>
ej.globalize.min.js<br/><br/></td><td>
Used to import globalization content for grid view<br/><br/></td></tr>

</table>

N> FileExplorer uses one or more sub-controls, therefore refer the `ej.web.all.min.js` (which encapsulates all the `ej` controls and frameworks in a single file) in the application instead of referring all the above specified internal dependencies. 

To get the real appearance of the FileExplorer, the dependent CSS file `ej.web.all.min.css` (which includes styles of all the widgets) should also needs to be referred.

N> Uncompressed version of library files are also available which is used for development or debugging purpose and can be generated from the custom script [here](http://csg.syncfusion.com).
