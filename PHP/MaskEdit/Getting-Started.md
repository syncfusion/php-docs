---
title: Getting Started with MaskEdit | MaskEdit | PHP | Syncfusion
description: To get start with MaskEdit
platform: php
control: MaskEdit
documentation: ug
keywords: 
---
# Getting Started

This section explains briefly about how to create a **MaskEdit** control in your application with **PHP** wrapper classes of EJ controls.

## Create your first MaskEdit Widget in PHP

You can create a PHP Project and add necessary scripts and styles with the help of the given PHP Getting Started Documentation.

You can render the PHP **MaskEdit** control as show below.


    {% highlight php %}

    <?php
            $mask = new EJ\MaskEdit("mask");
            echo $mask->maskFormat("99 999-99999")->value("4242422424")->width("250")->render();
    ?>

    {% endhighlight %}


The following screenshot illustrates the output of the above code example.

![](Getting-Started_images/Getting-Started_img1.jpeg)

