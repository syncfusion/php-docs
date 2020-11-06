---
layout: post
title: getting-started
description: getting-started
platform: php
control: rotator
documentation: ug
keyword: rotator, getting-started
---
# Getting Started

This section helps to get started of the Rotator control in a PHP application.

![](getting-started_images\getting-started_img1.png)

## Create a Rotator

The following steps guide you to add a Rotator control.

Refer the common PHP Getting Started Documentation to create a PHP application and add necessary scripts and styles for rendering Essential PHP controls.

Create a simple Rotator control object by creating an object for the Rotator referring the below code, here the  class **EJ\Rotator** object is created by using ‘new’ keyword. Define its properties and use **render()** method for rendering the control. We need to call the rendering element in echo statement.

{% highlight php %}

    <?php
        require_once 'EJ\AutoLoad.php';

        $rotator=new EJ\Rotator("defaultrotator");
        echo $rotator->slideWidth("600")->slideHeight("300")->render();

     ?>  

{% endhighlight %}

This will render an empty Rotator control on executing.

## Configure data

To configure images for Rotator control, define data in an array and map corresponding fields to it.

{% highlight php %}

    <?php
    require_once 'EJ\AutoLoad.php';
    $data=array(  array ( "text"=> "Colorful Night", "url"=> "http://js.syncfusion.com/demos/web/content/images/rotator/night.jpg" ),
    array ( "text"=> "Technology", "url"=> "http://js.syncfusion.com/demos/web/content/images/rotator/tablet.jpg" ),
    array ( "text"=> "Nature", "url"=> "http://js.syncfusion.com/demos/web/content/images/rotator/nature.jpg" ),
    array ( "text"=> "Snow Fall", "url"=> "http://js.syncfusion.com/demos/web/content/images/rotator/snowfall.jpg" ),
    array ( "text"=> "Credit Card", "url"=> "http://js.syncfusion.com/demos/web/content/images/rotator/card.jpg" ),
    array ( "text"=> "Beautiful Bird", "url"=> "http://js.syncfusion.com/demos/web/content/images/rotator/bird.jpg" ),
    array ( "text"=> "Amazing Sculptures", "url"=> "http://js.syncfusion.com/demos/web/content/images/rotator/sculpture.jpg" ));
    $rotator=new EJ\Rotator("defaultrotator");
    $fields=array("text"=>"text","url"=>"url");
    echo $rotator->dataSource($data)->fields($fields)->frameSpace("0px")->slideWidth("600")->slideHeight("300")->showPlayButton(true)->render();
    ?>  


{% endhighlight %}

![](getting-started_images\configure-data_img1.png)

> _Note:_ _You can find the Rotator properties from the_ [API reference](https://help.syncfusion.com/api/js/ejrotator) _document_