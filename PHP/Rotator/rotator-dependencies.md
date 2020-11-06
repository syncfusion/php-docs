---
layout: post
title: Rotator-Dependencies
description: rotator-dependencies
platform: php
control: Rotator
documentation: ug
---

# Rotator Dependencies

The external script dependencies of the Rotator component is,

jQuery 1.7.1 and later versions.

The ej.web.all.js is a bundle of all PHP controls. If you use ej.web.all.js in your application, you can leave this section or else you can try to render rotator in your application using ej.rotator.min.js file. You can refer the following frameworks and controls in your project.

Rotator Dependency files,

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
ej.rotator.min.js</td><td>
Should be referred when using rotator control.</td></tr>
</table>

To get the real appearance of the Rotator, the dependent CSS file `ej.web.all.min.css` (which includes styles of all the controls) should also needs to be referred.
Note: Uncompressed version of library files are also available which is used for development or debugging purpose and can be generated from the custom script [here](http://csg.syncfusion.com/).


