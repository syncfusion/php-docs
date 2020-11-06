---
layout: post
title: Syncfusion NavigationDrawer-dependencies
description: navigationdrawer-dependencies
platform: php
control: navigationdrawer
documentation: ug
---

# NavigationDrawer Dependencies

The external script dependencies of the NavigationDrawer component is,

jQuery 1.7.1 and later versions.

[`jsRender`] - To render the templates

The ej.web.all.js is a bundle of all PHP controls. If you use ej.web.all.js in your application, you can leave this section or else you can try to render NavigationDrawer in your application using ej.navigationdrawer.min.js file. You can refer the following frameworks and controls in your project.

NavigationDrawer Dependency files,

<table>
<tr>
<th>
File</th><th>
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
ej.listview.min.js</td><td>
Should be referred for accessing the list view component properties</td></tr>
<tr>
<td>
ej.navigationdrawer.min.js</td><td>
Should be referred when using navigation drawer control.</td></tr>
<tr>
<td>
ej.scroller.min.js</td><td>
Should be referred to render the scroller for the list items using navigation drawer control.</td></tr>
<tr>
<td>
ej.checkbox.min.js</td><td>
Should be referred to render the checkbox for the list items using navigation drawer control.</td></tr>
</table>

To get the real appearance of the Navigation Drawer, the dependent CSS file `ej.web.all.min.css` (which includes styles of all the controls) should also needs to be referred.
Note: Uncompressed version of library files are also available which is used for development or debugging purpose and can be generated from the custom script [here](http://csg.syncfusion.com/).

