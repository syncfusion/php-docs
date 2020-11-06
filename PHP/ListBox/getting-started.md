---
layout: post
title: Getting Started
description: Getting Started
platform: js
control: ListBox
documentation: ug
---

## Getting Started

The Essential PHP ListBox widget that contains a list of selectable items. It performs exceptionally well with thousands of items and supports checkboxes, single and multiple selection, keyboard navigation and virtual scrolling.

Using the following steps, we can create a Essential PHP ListBox control. The basic rendering of PHP ListBox is achieved with default functionality. The following screenshot illustrates the output of the ListBox in PHP.

![](Getting_Started_images\gettingstarted_img1.png)

### Create ListBox Widget  

We can create a PHP Project and add necessary scripts and styles with the help of the given PHP Getting Started Documentation.

You can render the PHP ListBox control with the dataSource and fields. Add the mentioned code to the corresponding view page for ListBox rendering.



{% highlight php %}

<?php
require_once '../EJ\AutoLoad.php';
$countries = array( array( "id"=> "bk1", "text"=> "Aache RTR" ), array( "id"=> "bk2", "text"=> "CBR 150-R" ), array( "id"=> "bk3", "text"=> "CBZ Xtreme" ),
                array( "id"=> "bk4", "text"=> "Discover" ), array( "id"=> "bk5", "text"=> "Dazzler" ), array( "id"=> "bk6", "text"=> "Flame" ),
                array( "id"=> "bk7", "text"=> "Fazzer" ), array( "id"=> "bk8", "text"=> "FZ-S" ), array( "id"=> "bk9", "text"=> "Pulsar" ),
                array( "id"=> "bk10", "text"=> "Shine" ), array( "id"=> "bk11", "text"=> "R15" ), array( "id"=> "bk12", "text"=> "Unicorn" ));    
?>
 <?php
    $listbox1=new EJ\ListBox("selectCountry");
    $fields=new EJ\ListBox\Field();
    $fields->id("id")->text("text");
    echo $listbox1->dataSource($countries)->fields($fields)->width("100%")->render();
 ?>


{% endhighlight %}


Here the dataSource is given as the array of the JSON items.

{% highlight php %}

<?php
require_once '../EJ\AutoLoad.php';
$countries = array( array( "id"=> "bk1", "text"=> "Aache RTR" ), array( "id"=> "bk2", "text"=> "CBR 150-R" ), array( "id"=> "bk3", "text"=> "CBZ Xtreme" ),
                array( "id"=> "bk4", "text"=> "Discover" ), array( "id"=> "bk5", "text"=> "Dazzler" ), array( "id"=> "bk6", "text"=> "Flame" ),
                array( "id"=> "bk7", "text"=> "Fazzer" ), array( "id"=> "bk8", "text"=> "FZ-S" ), array( "id"=> "bk9", "text"=> "Pulsar" ),
                array( "id"=> "bk10", "text"=> "Shine" ), array( "id"=> "bk11", "text"=> "R15" ), array( "id"=> "bk12", "text"=> "Unicorn" ));    
?>



{% endhighlight %}


Run the above code to render the following output.


![](Getting_Started_images\createlistboxwidget_img1.png)

### Selection

The Essential PHP ListBox widget supports item selection.

{% highlight php %}

<?php
require_once '../EJ\AutoLoad.php';
$countries = array( array( 'id'=> 'bk1', 'text'=> 'Aache RTR' ), array( 'id'=> 'bk2', 'text'=> 'CBR 150-R' ), array( 'id'=> 'bk3', 'text'=> 'CBZ Xtreme' ),
                array( 'id'=> 'bk4', 'text'=> 'Discover' ), array( 'id'=> 'bk5', 'text'=> 'Dazzler' ), array( 'id'=> 'bk6', 'text'=> 'Flame' ),
                array( 'id'=> 'bk7', 'text'=> 'Fazzer' ), array( 'id'=> 'bk8', 'text'=> 'FZ-S' ), array( 'id'=> 'bk9', 'text'=> 'Pulsar' ),
                array( 'id'=> 'bk10', 'text'=> 'Shine' ), array( 'id'=> 'bk11', 'text'=> 'R15' ), array( 'id'=> 'bk12', 'text'=> 'Unicorn' ));    
?>
 <?php
    $listbox1=new EJ\ListBox('selectCountry');
    $fields=new EJ\ListBox\Field();
    $fields->id('id')->text('text');
    echo $listbox1->dataSource($countries)->fields($fields)->width('100%')->selectedIndex('3')->render();
 ?>


{% endhighlight %}


Run the above code to render the following output.

![](Getting_Started_images\selection_img1.png)