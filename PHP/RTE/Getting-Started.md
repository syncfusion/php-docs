---
layout: post
title: Getting started with RichTextEditor
description: To get start with RichTextEditor
platform: php
control: RichTextEditor
documentation: ug
keywords: RichTextEditor, richtexteditor
---
# Getting Started

This section helps to understand the getting started of RTE control with the step-by-step instruction.

The external script dependencies of the RichTextEditor widget is,

* [jQuery 1.7.1](http://jquery.com/) and later versions.

And the internal script dependencies of the RichTextEditor widget are:

<table>
	<tr>
		<th>File </th>
		<th>Description / Usage </th>
	</tr>
	<tr>
		<td>ej.core.min.js</td>
		<td>Must be referred always before using all the controls.</td>
	</tr>
    <tr>
		<td>ej.data.min.js</td>
		<td>Used to handle data operation and should be used while binding data to controls.</td>
	</tr>
    <tr>
		<td>ej.draggable.min.js</td>
		<td>Should be referred when using dragging in RichTextEditor</td>
	</tr>
	<tr>
		<td>ej.scroller.min.js</td>
		<td>Should be referred when using scroller in RichTextEditor</td>
	</tr>
    <tr>
		<td>ej.button.min.js</td>
		<td>Should be referred when using button in RichTextEditor</td>
	</tr>
    <tr>
		<td>ej.togglebutton.min.js</td>
		<td>Should be referred when using togglebutton in RichTextEditor</td>
	</tr>
    <tr>
		<td>ej.splitbutton.min.js</td>
		<td>Should be referred when using splitbutton in RichTextEditor</td>
	</tr>
    <tr>
		<td>ej.checkbox.min.js</td>
		<td>Should be referred when using checkbox in RichTextEditor</td>
	</tr>
    <tr>
		<td>ej.radiobutton.min.js</td>
		<td>Should be referred when using radiobutton in RichTextEditor</td>
	</tr>
    <tr>
		<td>ej.dropdownlist.min.js</td>
		<td>Should be referred when using dropdownlist in RichTextEditor</td>
	</tr>
    <tr>
		<td>ej.dialog.min.js</td>
		<td>Should be referred when using dialog in RichTextEditor</td>
	</tr>
    <tr>
		<td>ej.toolbar.min.js</td>
		<td>Should be referred when using toolbar in RichTextEditor</td>
	</tr>
    <tr>
		<td>ej.editor.min.js</td>
		<td>Should be referred when using editor in RichTextEditor</td>
	</tr>
    <tr>
		<td>ej.menu.min.js</td>
		<td>Should be referred when using menu in RichTextEditor</td>
	</tr>
    <tr>
		<td>ej.tab.min.js</td>
		<td>Should be referred when using tab in RichTextEditor</td>
	</tr>
    <tr>
		<td>ej.slider.min.js</td>
		<td>Should be referred when using slider in RichTextEditor</td>
	</tr>
    <tr>
		<td>ej.treeview.min.js</td>
		<td>Should be referred when using treeview in RichTextEditor</td>
	</tr>
    <tr>
		<td>ej.uploadbox.min.js</td>
		<td>Should be referred when using uploadbox in RichTextEditor</td>
	</tr>
    <tr>
		<td>ej.splitter.min.js</td>
		<td>Should be referred when using splitter in RichTextEditor</td>
	</tr>
    <tr>
		<td>ej.colorpicker.min.js</td>
		<td>Should be referred when using colorpicker in RichTextEditor</td>
	</tr>
    <tr>
		<td>ej.fileexplorer.min.js</td>
		<td>Should be referred when using fileexplorer in RichTextEditor</td>
	</tr>
    <tr>
		<td>ej.grid.min.js</td>
		<td>Should be referred when using grid in RichTextEditor</td>
	</tr>
    <tr>
		<td>ej.tooltip.min.js</td>
		<td>Should be referred when using tooltip in RichTextEditor</td>
	</tr>
</table>

For getting started you can use the ‘ej.web.all.min.js’ file, which encapsulates all the 'ej' controls and frameworks in one single file.<br/> 

For themes, you can use the ‘ej.web.all.min.css’ CDN link from the snippet given. To add the themes in your application, please refer [this link](http://help.syncfusion.com/js/theming-in-essential-javascript-components#adding-specific-theme-to-your-application).


## Preparing HTML document

You can create a PHP Project and add necessary scripts and styles with the help of the given PHP Getting Started Documentation.

Create a first PHP file in Xampp and name it appropriately with `.php` extension and also place it under the newly created sample folder. For example, say Index.php with the initial code as shown below -

Refer the required scripts and CSS files in your PHP page as mentioned below in order to render the RichTextEditor control - 

{% highlight html %}

    <!DOCTYPE html>
       <html>
        <head>
                <title>Getting Started - RichTextEditor</title>
                <link href="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/flat-azure/ej.web.all.min.css" rel="stylesheet" />
                <link href="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/responsive-css/ej.responsive.css" rel="stylesheet" />
                <script src="http://cdn.syncfusion.com/js/assets/external/jquery-3.0.0.min.js"></script>
                <script src="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/ej.web.all.min.js"></script>
        </head>
        <body>
           <?php require_once 'EJ/AutoLoad.php'; ?>
        </body>
    </html>

{% endhighlight %}

## Control Initialization

The basic rendering of **RichTextEditor** is achieved by the default functionality.

{% highlight html %}
<div id="controls">
	 <div class="cols-sample-area">	 
        <?php
        require_once '../EJ/AutoLoad.php';
        $toolsList = array("style", "lists", "doAction", "links", "images");
        $rte =new EJ\RTE('texteditor');
        $rte->templateStart();
        ?>
        The RichTextEditor (RTE) control enables you to edit the contents with insert table and images,
        it also provides a toolbar that helps to apply rich text formats to the content entered in the TextArea
        <?php
        $rte->templateEnd();
        echo $rte->render();
        ?>
     </div>
</div>
{% endhighlight %}


## Setting and Getting Content

You can set the content of the editor as follows.

{% highlight javascript %}
$("#texteditor").ejRTE({
value: "The RichTextEditor (RTE) control enables you to edit the contents with insert table and images," +
" it also provides a toolbar that helps to apply rich text formats to the content entered in the TextArea.",
});
{% endhighlight %}

To retrieve the editor contents,

{% highlight javascript %}
var currentValue = $("#texteditor").ejRTE("model.value");
{% endhighlight %}


