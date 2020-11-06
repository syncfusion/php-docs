---
layout: post
title: Getting Started | PHP | Syncfusion
description: Check out the getting started documentation for the Essential JS PHP platform with more details on creating simple PHP application.
platform: php 
control: Common 
documentation: ug
---


# Essential JS for PHP

## Run the Essential JS for PHP demo web site

To run the Essential JS for PHP demo site, kindly refer the ReadMe.html file in `/Samples` location.

## Create a simple PHP Application

To use Essential JS for PHP in your PHP web site, follow the below steps:

1. Copy Essential JavaScript and CSS files from `/scripts` and `/themes` to your web site root. And include the necessary files in your PHP page.

{% highlight html %}
    <head>
        <link rel="stylesheet" href="themes/bootstrap-theme/ej.web.all.min.css" />
		<script src="scripts/external/jquery-3.1.1.min.js"></script> 
		<script src="scripts/web/ej.web.all.min.js"> </script>
    </head>
{% endhighlight %}

2. Copy the individual component source files from `/Src` to your directory. Include the Essential JS for PHP **AutoLoad.php** file available in the `/Src` directory. This file *automatically retrieves the required source class files* to render the specified controls.

{% highlight html %}
    <body>
        <?php require_once 'Src/AutoLoad.php'; ?>
        <!--Enter your code to render EJ controls -->
    </body>
{% endhighlight %}

3. Use any Essential JS for PHP wrapper. For Example, to use DatePicker refer below.

{% highlight html %}
    <?php
    $date = new \EJ\DatePicker("datepicker"); // initialize a new instance of DatePicker with id
    echo $date->width("100%")->height("40px")->watermarkText("select a date")->render(); // configure the DatePicker using the fluent API and display the output
    ?>
{% endhighlight %}

4. Run the PHP web site, the DatePicker widget will be displayed as shown below,

   ![PHP datepicker control](/PHP/Getting-Started_images/Getteing-Started_img1.JPG)

N> You can explore the release history of Essential PHP from [`here`](https://www.syncfusion.com/products/release-history/estudio/php).
