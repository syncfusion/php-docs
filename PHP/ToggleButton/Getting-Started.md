---
layout: post
title: Getting-Started
description: getting started
platform: php
control: Toggle Button
documentation: ug
---

# Getting Started

This section explains briefly about the necessary steps required to render and configure EJ ToggleButton control using PHP wrapper classes.

Create a PHP Project and add necessary scripts and styles with the help of the given PHP [Getting Started](https://help.syncfusion.com/php/getting-started) Documentation.


## Create ToggleButton

Create a ToggleButton control by instantiating the PHP wrapper class available in EJ namespace as shown below.

{% highlight html %}

    <?php
    $button =  new EJ\ToggleButton("check15");
    echo $button ->showRoundedCorner(true)->defaultText("Play")->activeText("Pause")->size("large")
    ->contentType("textandimage")->defaultPrefixIcon("e-icon e-mediaplay")->activePrefixIcon("e-icon e-mediapause")->render();                
    ?>

{% endhighlight %}

The following screenshot illustrates the output of above code.

![](/php/ToggleButton/Getting-Started_images/Getting-Started_img1.JPG) 

![](/php/ToggleButton/Getting-Started_images/Getting-Started_img2.JPG) 

