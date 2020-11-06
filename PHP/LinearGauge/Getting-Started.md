---
layout: post
title: Getting Started with PHP Linear Gauge control | Syncfusion
description: You can learn here about getting started with Syncfusion Essential PHP Linear Gauge control and more details.
platform: php
control: Linear Gauge
documentation: ug
---

# Getting Started with PHP Linear Gauge

This section briefly explains on how to create a **Linear Gauge** control for your application.

* You can provide data for a **Linear Gauge** and display them in a required way. You can also customize the default **Linear Gauge** appearance to meet your requirements. 

* In this example, you will learn how to create a **Linear Gauge** and how to design a thermometer, which can be used to check the body temperature of a person.



![Visual representation of Thermometer using Linear Gauge in PHP](Getting-Started_images/Getting-Started_img1.png)

## Adding PHP EJ source and script reference

Create a first PHP file in Xampp and name it appropriately with .php extension and also place it under the newly created sample folder. Now refer AutoLoad.php file from EJ source of PHP in the sample page. For example, say Index.php with the initial code as shown below -

Refer the required scripts files in your PHP page as mentioned below in order to render the LinearGauge control.


{% highlight html %}

<!DOCTYPE html>
<html>
<head>
<!--  jquery script  -->
    <script type="text/javascript" src="//cdn.syncfusion.com/js/assets/external/jquery-3.0.0.min.js"></script>    
    <!-- Essential JS UI widget -->
    <script type="text/javascript" src="//cdn.syncfusion.com/14.3.0.49/js/web/ej.web.all.min.js"></script>
</head>
<body>
<!--Refer AutoLoad.php common source to render the control-->
   <?php
      require_once '../EJ/AutoLoad.php';
    ?>
</body>
</html>


{% endhighlight %}

In the above code, ej.web.all.min.js script reference has been added for demonstration purpose. It is not recommended to use this for deployment purpose, as its file size is larger since it contains all the widgets. Instead, you can use [`CSG`](http://csg.syncfusion.com/) utility to generate a custom script file with the required widgets for deployment purpose.

## Initialize LinearGauge

Add the following code in the index.php file to create the LinearGauge control in index page.

{% highlight html %}

<div>

    <?php
    require_once '../EJ/AutoLoad.php';
    ?>

    <?php
        $linear=new EJ\LinearGauge("container");    
        echo $linear->render();
    ?>
</div>


{% endhighlight %}


On executing the above code sample renders a default **Linear Gauge** with default values as follows.


![Initialize Linear Gauge in PHP](Getting-Started_images/Getting-Started_img2.png)

## Set Height and Width values

* Basic attributes of each canvas elements are height and width properties. 

* You can set the height and width of the gauge as shown in the following code example.



{% highlight html %}

 <?php
    $linear=new EJ\LinearGauge("container");    
	
    echo $linear->width(550)->height(500)->render();
    ?>

{% endhighlight %}


On executing the above code sample renders a default **Linear Gauge** with height and width.


![Set Height and Width values using Linear Gauge in PHP](Getting-Started_images/Getting-Started_img3.png)

## Set animate option and Label Color

* You can draw the Thermometer with Label color and set animate property to _True_.  

* Initially set the animate property to _False_ to avoid unwanted script loads.



{% highlight html %}

<?php
    $linear=new EJ\LinearGauge("container");    
	
    echo $linear->width(550)->height(500)->labelColor("#8c8c8c")->enableAnimation(false)->render();
    ?>


{% endhighlight %}



On executing the above code sample renders a customized **Linear Gauge** as follows.

![Set animate option and Label Color using Linear Gauge in PHP](Getting-Started_images/Getting-Started_img4.png)

## Provide scale values

* You can change the Scale Style of Thermometer using **type** property.

* You can set the Minimum temperature up to -10 and maximum body temperature up to 110. 

* You can set the Minimum scale value as -10 and maximum value as 110.

* You can set the Location values such as vertical and horizontal position in the thermometer.

* You can set the thermometer height using **length** property.

* You can set the Minor Interval value as 5 to get the exact temperature of the patient.



{% highlight html %}

    <?php
    $linear=new EJ\LinearGauge("container"); 
	
	$position = new EJ\LinearGauge\Position();
	$position->x(50)->y(18);
	$border = new EJ\LinearGauge\Border();
	$border->width(0.5);
    $scale = new EJ\LinearGauge\Scale();
	$scale->type("thermometer")->backgroundColor("transparent")->minimum(-10)
	       ->maximum(110)->minorIntervalValue(5)->width(20)->length(335)
		   ->border($border)->position($position);
	
	$scales=array($scale);
	
    echo $linear->width(550)->height(500)->labelColor("#8c8c8c")->enableAnimation(false)
	            ->scales($scales)->render();
    ?>

    
{% endhighlight %}



On executing the above code sample renders a customized gauge with ranges as follows.

![Provide scale values using Linear Gauge in PHP](Getting-Started_images/Getting-Started_img5.png)

## Add pointers data

In **Linear gauge** there are two types of pointers available such as marker pointer and bar pointer.

* **Marker pointer** displays as a pointer device which shows the actual values. In this example, there is no need to show a marker pointer in a thermometer, therefore, you can hide it by setting the **Opacity** property to ‘0’.

* **Bar pointer** displays as a mercury metal that shows the exact temperature of the person. You can set the basic properties of the bar pointer such as **width**, **distanceFromScale**, **Value** and **backgroundColor**.



{% highlight html %}

     <?php
    $linear=new EJ\LinearGauge("container"); 
	
	$marker = new EJ\LinearGauge\MarkerPointer();
	$marker->opacity(0);
	$markers = array($marker);
	
	$bar = new EJ\LinearGauge\BarPointer();
	$bar->width(10)->distanceFromScale(-0.5)->value(37)->backgroundColor("#DB3738");
	$barPointers = array($bar);
	
    $scale = new EJ\LinearGauge\Scale();
	$scale->type("thermometer")->backgroundColor("transparent")->minimum(-10)
	       ->maximum(110)->minorIntervalValue(5)->width(20)->length(335)
		   ->markerPointers($markers)->barPointers($barPointers);
	
	$scales=array($scale);
	
    echo $linear->width(550)->height(500)->labelColor("#8c8c8c")->enableAnimation(false)
	            ->scales($scales)->render();
    ?>


{% endhighlight %}



On executing the above code sample renders a **Linear Gauge** with bar marker as follows.

![Add pointers data using Linear Gauge in PHP](Getting-Started_images/Getting-Started_img6.png)

## Add Label Customization

* You can display the label value on both sides to get temperature in different scales. For that you can add two label values in an array.

* You can use the scale labels to display the value in the gauge. You can customize the label placement, font (including its style and family) and  its distance from scale.



{% highlight html %}

         <?php
    $linear=new EJ\LinearGauge("container"); 
	
	$marker = new EJ\LinearGauge\MarkerPointer();
	$marker->opacity(0);
	$markers = array($marker);
	
	$bar = new EJ\LinearGauge\BarPointer();
	$bar->width(10)->distanceFromScale(-0.5)->value(37)->backgroundColor("#DB3738");
	$barPointers = array($bar);
	
	$font1 = new EJ\LinearGauge\Font();
	$font1->size("10px")->fontFamily("Segoe UI")->fontStyle("Normal");
	$label1 = new EJ\LinearGauge\Label();
	$label1->placement("near")->font($font1);
	
	$distanceFromScale = new EJ\LinearGauge\DistanceFromScale();
	$distanceFromScale->x(25);
	$label2 = new EJ\LinearGauge\Label();
	$label2->placement("fat")->distanceFromScale($distanceFromScale);
	$labels = array($label1, $label2);
	
	$position = new EJ\LinearGauge\Position();
	$position->x(50)->y(18);
	$border = new EJ\LinearGauge\Border();
	$border->width(0.5);

    $scale = new EJ\LinearGauge\Scale();
	$scale->type("thermometer")->backgroundColor("transparent")->minimum(-10)
	       ->maximum(110)->minorIntervalValue(5)->width(20)->length(335)
		   ->markerPointers($markers)->barPointers($barPointers)->border($border)->position($position)->labels($labels);
	
	$scales=array($scale);
	
    echo $linear->width(550)->height(500)->labelColor("#8c8c8c")->enableAnimation(false)
	            ->scales($scales)->render();
    ?>


{% endhighlight %}



On executing the above code sample renders a customized **Linear Gauge** as follows.

![Add Label Customization using Linear Gauge in PHP](Getting-Started_images/Getting-Started_img7.png)

## Add Ticks Details

* You can set the width and height of the major ticks greater than the Minor ticks. You can set dark background for tick Color to have a better visibility.

* You can also use four ticks for both the sides, each having two minor ticks and major ticks.



{% highlight html %}

 <?php
    $linear=new EJ\LinearGauge("container");
      //……….
      //…… . . 
      $dfrmScale=new EJ\LinearGauge\DistanceFromScale();
	$dfrmScale->y(-4);
	$tick1 = new EJ\LinearGauge\Tick();
	$tick1->type("majorinterval")->height(8)->width(1)->color("#8c8c8c")->distanceFromScale($dfrmScale);
	
	$tick2 = new EJ\LinearGauge\Tick();
	$tick2->type("minorinterval")->height(4)->width(1)->color("#8c8c8c")->distanceFromScale($dfrmScale);
	
	$tick3 = new EJ\LinearGauge\Tick();
	$tick3->type("majorinterval")->height(8)->width(1)->color("#8c8c8c")->placement("far")->distanceFromScale($dfrmScale);
	
	$tick4 = new EJ\LinearGauge\Tick();
	$tick4->type("minorinterval")->height(4)->width(1)->color("#8c8c8c")->placement("far")->distanceFromScale($dfrmScale);
	$ticks = array($tick1, $tick2, $tick3, $tick4);

       $scale = new EJ\LinearGauge\Scale();
	$scale->type("thermometer")->ticks($ticks);
	
	$scales=array($scale);
	
    echo $linear->width(550)->height(500)->labelColor("#8c8c8c")->enableAnimation(false)
	            ->scales($scales)->render();
?>

{% endhighlight %}



On executing the above code sample renders a **Linear Gauge** with custom labels as follows.

![Add Ticks Details using Linear Gauge in PHP](Getting-Started_images/Getting-Started_img8.png)

## Add Custom Label Details

* You can specify the texts using **Custom labels** which displays in the gauge and customize them using various properties.

* You can change the **showIndicators** property as **True** to show the custom labels.



The following code example illustrates how to use custom texts.

{% highlight html %}

      <?php
    $linear=new EJ\LinearGauge("container");

              $position1 = new EJ\LinearGauge\Position();
	$position1->x(44)->y(78);
	$customLbl1 = new EJ\LinearGauge\CustomLabel();
	$customLbl1->value("(C)")->position($position1);
	
	$position2 = new EJ\LinearGauge\Position();
	$position2->x(56)->y(78);
	$customLbl2 = new EJ\LinearGauge\CustomLabel();
	$customLbl2->value("(F)")->position($position2);
	$customLabels = array($customLbl1, $customLbl2);

              $scale = new EJ\LinearGauge\Scale();
	$scale->type("thermometer")->
                                 //Add the pointers customization code here
                //Add the labels customization code here
                //Add the ticks customization code here
                //Add the Custom labels customization code here
		   ->showCustomLabels(true)->customLabels($customLabels);
	
	$scales=array($scale);
	
    echo $linear->width(550)->height(500)->labelColor("#8c8c8c")->enableAnimation(false)
	            ->scales($scales)->render();
    ?>


{% endhighlight %}



On executing the above code sample renders a customized **Linear Gauge** as follows. 

![Add Custom Label Details using Linear Gauge in PHP](Getting-Started_images/Getting-Started_img9.png)

## Change scale Degree to Fahrenheit

You can add a function to convert the temperature from Degrees to Fahrenheit values in the label by having index value as 1.



{% highlight html %}

<?php
    $linear=new EJ\LinearGauge("container");
    
     //. . . 
     //. . . 
    echo $linear->width(550)->height(500)->drawLabels("DrawLabel")->render();
?>
<script> 
 function DrawLabel(args) { 
        if (args.label.index == 1) {
            args.style.textValue = (args.label.value * (9 / 5)) + 32;
            args.style.font = "Normal 10px Segoe UI";
        }
    }
</script>


{% endhighlight %}



On executing the above code sample renders a **Linear Gauge** with values in Degrees and Fahrenheit as follows.



![Change scale Degree to Fahrenheit using Linear Gauge in PHP](Getting-Started_images/Getting-Started_img10.png)

## Add Custom label for Current Value

You can add the function that displays the current temperature value in the custom label.



{% highlight html %}

<?php
    $linear=new EJ\LinearGauge("container");
    
     //. . . 
     //. . . 
    echo $linear->width(550)->height(500)->drawLabels("DrawLabel")
                          ->drawCustomLabel("DrawCustomLabel")->render();
?>
<script> 
 function DrawLabel(args) { 
        if (args.label.index == 1) {
            args.style.textValue = (args.label.value * (9 / 5)) + 32;
            args.style.font = "Normal 10px Segoe UI";
        }
    }
	 function DrawCustomLabel(args) {	 
        if (args.customLabelIndex == 2) {
            var temp = args.scaleElement.barPointers[0].value;
            var fahValue = (temp * (9 / 5)) + 32;
            if (temp == -10) {
                args.style.textValue = "Very Cold Weather" + "(" + fahValue.toFixed(1) + "° F)";
            }
            else if ((temp > -10 && temp < 0) || (temp > 0 && temp < 15)) {
                args.style.textValue = "Cool Weather" + " (" + fahValue.toFixed(1) + "° F)";
            }
            else if (temp == 0) {
                args.style.textValue = "Freezing point of Water" + " (" + fahValue.toFixed(1) + "° F)";
            }
            else if (temp >= 15 && temp < 30) {
                args.style.textValue = "Room Temperature" + " (" + fahValue.toFixed(1) + "° F)";
            }
            else if (temp == 30) {
                args.style.textValue = "Beach Weather" + " (" + fahValue.toFixed(1) + "° F)";
            }
            else if (temp == 37) {
                args.style.textValue = "Body Temperature" + " (" + fahValue.toFixed(1) + "° F)";
            }
            else if (temp == 40) {
                args.style.textValue = "Hot Bath Temperature" + " (" + fahValue.toFixed(1) + "° F)";
            }
            else if (temp > 40 && temp < 100) {
                args.style.textValue = "Very Hot Temperature" + " (" + fahValue.toFixed(1) + "° F)";
            }
            else if (temp == 100) {
                args.style.textValue = "Boiling point of Water" + " (" + fahValue.toFixed(1) + "° F)";
            }
        }
    }
</script>


{% endhighlight %}



The following screen shot displays a linear gauge with all the customizations discussed earlier.

![Add Custom label for Current Value using Linear Gauge in PHP](Getting-Started_images/Getting-Started_img11.png)

