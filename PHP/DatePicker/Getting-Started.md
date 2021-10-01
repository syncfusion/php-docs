---
title: Getting Started with DatePicker | DatePicker | PHP | Syncfusion
description: Learn here all about getting started with Syncfusion Essential PHP DatePicker Control, its elements, and more.
platform: php
control: DatePicker
documentation: ug
keywords: Datepicker getting started, php Datepicker
---

# Getting Started with PHP DatePicker

This section explains briefly about the necessary steps required to render and configure EJ DatePicker control using PHP wrapper classes.

Create a PHP Project and add necessary scripts and styles with the help of the given PHP [Getting Started](https://help.syncfusion.com/php/getting-started) Documentation.


## Create DatePicker

Create a PHP DatePicker control by instantiating the PHP wrapper class available in EJ namespace as shown below.

{% highlight html %}

     <?php
        $date = new EJ\DatePicker("datePicker");
        echo $date->value(new DateTime())->render();
    ?>

{% endhighlight %}

The following screenshot illustrates the output of above code.

![Getting_Started_Image1](getting-started_images/datePicker.png) 

## Configuring DatePicker

### Set minDate and maxDate 

EJ DatePicker provides API through which you can set the maximum and minimum allowed date values. Min and Max date values can be set at initialization as show below.

{% highlight html %}

    <?php
        $date = new EJ\DatePicker("datePicker");
        echo $date->value(new DateTime())->minDate(new DateTime("11/1/2016"))->maxDate(new DateTime("11/24/2016"))->render();
    ?>

{% endhighlight %} 

The following screenshot illustrates the output of above code.

![Getting_Started_Image2](getting-started_images/minmaxDate.png) 

## Blackout Dates

You can disable a set of Dates in Datepicker calendar by using this API. Refer the below code snippet.

{% highlight html %}

    <?php
        $date_blackout = new EJ\DatePicker("datePicker_blackout");
        echo $date_blackout->value(new DateTime())->blackoutDates(array(new DateTime("11/5/2016"), new DateTime("11/14/2016"), new DateTime("11/22/2016")))->render();
    ?>

{% endhighlight %} 

The following screenshot illustrates the output of above code.

![Getting_Started_Image3](getting-started_images/blackout.png) 

## Special Dates

You can format the appearance of certain days in the calendar popup to indicate special days using this API. Refer the below code snippet.

{% highlight html %}

    <?php 
        $today = date("Y/m/d");
        $special= array( array("date" => $today, "tooltip" => "In Australia", "iconClass"=> "flags sprite-Australia") ,
                            array("date" => date('Y-m-d', strtotime($today. ' + 8 days')) , "tooltip"=>"In France", "iconClass"=> "flags sprite-France" ),
                            array("date" => date('Y-m-d', strtotime($today. ' + 10 days')) , "tooltip"=>"In USA", "iconClass"=> "flags sprite-USA" ),
                            array("date" => date('Y-m-d', strtotime($today. ' + 16 days')) , "tooltip"=>"In Germany", "iconClass"=> "flags sprite-Germany" ),
                            array("date" => date('Y-m-d', strtotime($today. ' + 4 days')) , "tooltip"=>"In India", "iconClass"=> "flags sprite-India" ));
        $date_special = new EJ\DatePicker("datePicker_special");
        echo $date_special->value(new DateTime())->specialDates($special)->render();
    ?>

{% endhighlight %} 

The fields API lets you customize the Special dates in calendar.

The following screenshot illustrates the output of above code.

![Getting_Started_Image4](getting-started_images/specialdates.png) 