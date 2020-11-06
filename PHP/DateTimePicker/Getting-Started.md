---
title: Getting Started with DateTimePicker | DateTimePicker | PHP | Syncfusion
description: Getting Started with DateTimePicker
platform: php
control: DateTimePicker
documentation: ug
keywords: Datetimepicker getting started, php datetimepicker
---

# Getting Started

This section illustrates the details on how to render and configure a DateTimePicker control using the methods available in PHP wrapper classes.

Create a PHP Project and add necessary scripts and styles with the help of the given PHP [Getting Started](https://help.syncfusion.com/php/getting-started) Documentation.

## Create DateTimePicker

Create a DateTimePicker control by instantiating the PHP wrapper class available in EJ namespace as shown below.

{% highlight html %}

    <?php
        $datetimepick = new EJ\DateTimePicker("datetime");
        echo $datetimepick->width("100%")->value(new DateTime())->render();
    ?>
    
{% endhighlight %}

The following screenshot illustrates the output of above code.

![](getting-started_images/datetime.png)   

## Configuring DateTimePicker

### Set minDateTime and maxDateTime

 EJ DateTimePicker provides API through which you can set the maximum and minimum allowed date and time values. Min and Max date and time values can be set at initialization as show below.

{% highlight html %}

    <?php
        $datetimepick_minmax = new EJ\DateTimePicker("datetime_minmax");
        echo $datetimepick_minmax->width("100%")->minDateTime(new DateTime("11/1/2016 10:00 AM"))->maxDateTime(new DateTime("11/27/2016 10:00 PM"))->render();
    ?>

{% endhighlight %}

The following screenshot illustrates the output of above code.

![](getting-started_images/minmax.png) 

### Customize button text

You can customize the value in DateTimepicker control by using the buttonText property as show below.

{% highlight html %}

    <?php
        $datetimepick_btntxt = new EJ\DateTimePicker("datetime_btntxt");
        echo $datetimepick_btntxt->width("100%")->buttonText(array("today" => "Date now", "timeNow" => "Current time"))->render();
    ?>

{% endhighlight %}

The following screenshot illustrates the output of above code.

![](getting-started_images/buttontext.png) 