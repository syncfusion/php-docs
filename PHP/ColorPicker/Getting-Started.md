---
title: Getting Started with ColorPicker | ColorPicker | PHP | Syncfusion
description: Getting Started with ColorPicker
platform: php
control: ColorPicker
documentation: ug
keywords: Colorpicker getting started, Colorpicker php
---

# Getting Started

This section illustrates the details on how to render and configure a ColorPicker control using the methods available in PHP wrapper classes. 

Create a PHP Project and add necessary scripts and styles with the help of the given PHP [Getting Started](https://help.syncfusion.com/php/getting-started) Documentation.

## Create ColorPicker

Create a ColorPicker control by instantiating the ColorPicker class available in EJ namespace and configure it.

{% highlight html %}

    <?php
        $color = new \EJ\ColorPicker("ColorPicker");
        echo $color->value("#278787")->render();
    ?>

{% endhighlight %} 

The following screenshot illustrates the output of above code.

![ColorPicker Control](Getting-Started_images/colorpicker.png)

