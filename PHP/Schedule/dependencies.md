---
title: Schedule dependencies	
description: Dependencies required to render the Schedule control
platform: php
control: schedule
documentation: ug
keywords: schedule dependency files  
---

# External and Internal Dependencies

The following list of external dependencies are mandatory in order to render any of the Syncfusion controls -

* [jQuery](http://jquery.com) - 1.7.1 and later versions
* [jsRender](https://github.com/borismoore/jsrender) - to render the templates

The other required internal dependencies of Scheduler are tabulated below,

<table>
    <tr>
        <th>File<br/><br/></th>
        <th>Description/Usage<br/><br/></th>
    </tr>
    <tr>
        <td>ej.core.min.js<br/><br/></td>
        <td>Must be referred always first before using all the JS controls.<br/><br/></td>
    </tr>
    <tr>
        <td>ej.data.min.js<br/><br/></td>
        <td>Used to handle data operation and should be used while binding data to JS controls.<br/><br/></td>
    </tr>
    <tr>
        <td>ej.globalize.min.js<br/><br/></td>
        <td>Must be referred to localize any of the JS control's text and content.<br/><br/></td>
    </tr>
    <tr>
        <td>ej.schedule.min.js<br/><br/></td>
        <td>Schedule core script file which includes schedule related scripts files such as <i>ej.schedule.render.js</i>, <i>ej.schedule.resources.js</i> and <i>ej.schedule.horizontal.js</i><br/><br/></td>
    </tr>
    <tr>
        <td>ej.scroller.js<br/><br/>ej.touch.js<br/><br/>ej.draggable.js<br/><br/>ej.navigationdrawerbase.js<br/><br/>ej.listviewbase.js<br/><br/>ej.listview.js<br/><br/>ej.recurrenceeditor.js<br/><br/>ej.dropdownlist.js<br/><br/>ej.radiobutton.js<br/><br/>ej.dialog.js<br/><br/>ej.button.js<br/><br/>ej.autocomplete.js<br/><br/>ej.datepicker.js<br/><br/>ej.timepicker.js<br/><br/>ej.checkbox.js<br/><br/>ej.editor.js<br/><br/>ej.menu.js<br/><br/>ej.navigationdrawer.js<br/><br/>ej.tooltip.js<br/><br/></td>
        <td>These files are referred for proper working of the sub-controls used within Scheduler.<br/><br/></td>
    </tr>
</table>

N> Scheduler uses one or more sub-controls, therefore refer the `ej.web.all.min.js` (which encapsulates all the `ej` controls and frameworks in a single file) in the application instead of referring all the above specified internal dependencies.

To get the real appearance of the Scheduler, the dependent CSS file `ej.web.all.min.css` (which includes styles of all the widgets) should also needs to be referred.

N> Uncompressed version of library files are also available which is used for development or debugging purpose and can be generated from the custom script [here](http://csg.syncfusion.com).
