---
layout: post
title: Getting Started
description: Getting Started
platform: js
control: ListView
documentation: ug
---

## Getting Started

The **Essential PHP ListView** widget builds an interactive list view interface. This control allows you to select an item from a list-like interface and provides the infrastructure to display a set of data items in different layouts or views. Lists display data, data navigation, result lists, and data entry.

Using the following steps, we can create a PHP ListView control. The basic rendering of PHP ListView is achieved with default functionality. The following screenshot illustrates the output of a ListView in PHP.

![](Getting_Started_images\gettingstarted_img1.png)

### Create ListView Widget  


We can create a PHP Project and add necessary scripts and styles with the help of the given PHP Getting Started Documentation.

You can render the PHP ListView control with the dataSource and fields. Add the mentioned code to the corresponding view page for ListView rendering.

{% highlight php %}

<?php
    require_once '../EJ/AutoLoad.php';
    ?>
    <?php
    $data = array( array( "Texts"=> "Discover Music" ),
             array( "Texts"=>"Sales and Events" ),
             array( "Texts"=> "Categories" ),
             array( "Texts"=> "MP3 Albums" ),
             array( "Texts"=> "More in Music" ));
    $fields=array("text"=> "Texts");
    $listview1=new EJ\ListView("defaultlistview");
     echo $listview1->fieldSettings($fields)->dataSource($data)->width(400)->render();
    ?>


{% endhighlight %}



Here the dataSource is given as the array of the JSON items.

{% highlight php %}


    $data = array( array( "Texts"=> "Discover Music" ),
             array( "Texts"=>"Sales and Events" ),
             array( "Texts"=> "Categories" ),
             array( "Texts"=> "MP3 Albums" ),
             array( "Texts"=> "More in Music" ));
    $fields=array("text"=> "Texts");



{% endhighlight %}



 Run the above code to render the following output.

![](Getting_Started_images\createlistviewwidget_img1.png)

### Add Header

We can add a header for **PHP** **ListView**. Refer to the following script.

{% highlight php %}

<?php
    require_once '../EJ/AutoLoad.php';
    ?>
    <?php
    $data = array( array( "Texts"=> "Discover Music" ),
             array( "Texts"=>"Sales and Events" ),
             array( "Texts"=> "Categories" ),
             array( "Texts"=> "MP3 Albums" ),
             array( "Texts"=> "More in Music" ));
    $fields=array("text"=> "Texts");
    $listview1=new EJ\ListView("defaultlistview");
     echo $listview1->fieldSettings($fields)->dataSource($data)->width(400)->showHeader(true)->headerTitle("Music")->render();
    ?>


{% endhighlight %}



Run the above code to render the following output.

![](Getting_Started_images\addheader_img1.png)



