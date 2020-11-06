---
layout: post
title: Getting-Started for TagCloud
description: getting started for TagCloud
platform: php
control: TagCloud
documentation: ug
keywords: TagCloud,js tagcloud,ejtagcloud
---

# Getting Started

This section explains briefly about how to create a **TagCloud** in your application with **PHP**. The **TagCloud** can be easily configured to the div element in which the tags are placed. The following screenshot illustrates the functionality of a **TagCloud** widget with a list of the topmost search engines. 

![](Getting-Started_images/Getting-Started1.jpg)

## Create TagCloud widget

You can create a PHP Project and add necessary scripts and styles with the help of the given PHP Getting Started Documentation.

Create a first PHP file in Xampp and name it appropriately with `.php` extension and also place it under the newly created sample folder. For example, say Index.php with the initial code as shown below -

Refer the required scripts and CSS files in your PHP page as mentioned below in order to render the TagCloud control - 

{% highlight html %}

    <!DOCTYPE html>
    <html>
        <head>
                <title>Getting Started - TagCloud</title>
                <link href="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/flat-azure/ej.web.all.min.css" rel="stylesheet" />
                <link href="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/responsive-css/ej.responsive.css" rel="stylesheet" />
                <script src="http://cdn.syncfusion.com/js/assets/external/jquery-3.0.0.min.js"></script>
                <script src="http://cdn.syncfusion.com/js/assets/external/jsrender.min.js"></script>
                <script src="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/ej.web.all.min.js"></script>
        </head>
        <body>
           <?php require_once 'EJ\AutoLoad.php'; ?>
        </body>
    </html>

{% endhighlight %}

Add the following code example to add list of items to the **TagCloud** and initialize the **TagCloud** widget.

{% highlight html %}

        <?php
       $websiteCollection = array(
       array('text'=> 'Google', 'url'=> 'http://www.google.com', 'frequency'=> 12),
       array('text'=> 'All Things Digital', 'url'=> 'http://allthingsd.com/', 'frequency'=> 3),
       array('text'=> 'Arts Technica', 'url'=> 'http://arstechnica.com/', 'frequency'=> 8),
       array('text'=> 'Business Week', 'url'=> 'http://www.businessweek.com/', 'frequency'=> 2),
       array('text'=> 'Yahoo', 'url'=> 'http://in.yahoo.com/', 'frequency'=> 12),
       array('text'=> 'Center Networks', 'url'=> 'http://www.centernetworks.com/', 'frequency'=> 5),
       array('text'=> 'Crave', 'url'=> 'http://news.cnet.com/crave/', 'frequency'=> 8),
       array('text'=> 'Crunch Gear', 'url'=> 'http://techcrunch.com/gadgets/', 'frequency'=> 20),
       array('text'=> 'Daily Tech', 'url'=> 'http://www.dailytech.com/', 'frequency'=> 1),
       array('text'=> 'Electronista', 'url'=> 'http://www.electronista.com/', 'frequency'=> 3),
       array('text'=> 'Engadget', 'url'=> 'http://www.engadget.com/', 'frequency'=> 5),
       array('text'=> 'Gearlog', 'url'=> 'http://www.gearlog.com/', 'frequency'=> 9),
       array('text'=> 'Information Week', 'url'=> 'http://www.informationweek.com/', 'frequency'=> 0),
       array('text'=> 'PCWorld', 'url'=>  'http://www.pcworld.com/', 'frequency'=> 11),
       array('text'=> 'Tech Republic', 'url'=> 'http://techrepublic.com/', 'frequency'=> 3),
       array('text'=> 'Valleywag', 'url'=> 'http://valleywag.gawker.com/', 'frequency'=> 6),
       array('text'=> 'Rediff', 'url'=> 'http://in.rediff.com/', 'frequency'=> 9),
       array('text'=> 'WebProNews', 'url'=> 'http://www.webpronews.com/', 'frequency'=> 2),
       );
     $tagcloud = new EJ\TagCloud('tag');
     echo $tagcloud->dataSource($websiteCollection)->titleText('Popular Sites')->render();
     ?>

{% endhighlight %}

The following screenshot displays the output of the above code example.

![](Getting-Started_images/Getting-Started1.jpg) 

## Set Min and Max Font Size

In the above code example, the **frequency** properties are used to set the min and max font size to the **TagCloud** list item.

{% highlight html%}
   
     <?php
        $websiteCollection = array(
       array('text'=> 'Google', 'url'=> 'http://www.google.com', 'frequency'=> 12),
       array('text'=> 'All Things Digital', 'url'=> 'http://allthingsd.com/', 'frequency'=> 3),
       array('text'=> 'Arts Technica', 'url'=> 'http://arstechnica.com/', 'frequency'=> 8),
       array('text'=> 'Business Week', 'url'=> 'http://www.businessweek.com/', 'frequency'=> 2),
       array('text'=> 'Yahoo', 'url'=> 'http://in.yahoo.com/', 'frequency'=> 12),
       array('text'=> 'Center Networks', 'url'=> 'http://www.centernetworks.com/', 'frequency'=> 5),
       array('text'=> 'Crave', 'url'=> 'http://news.cnet.com/crave/', 'frequency'=> 8),
       array('text'=> 'Crunch Gear', 'url'=> 'http://techcrunch.com/gadgets/', 'frequency'=> 20),
       array('text'=> 'Daily Tech', 'url'=> 'http://www.dailytech.com/', 'frequency'=> 1),
       array('text'=> 'Electronista', 'url'=> 'http://www.electronista.com/', 'frequency'=> 3),
       array('text'=> 'Engadget', 'url'=> 'http://www.engadget.com/', 'frequency'=> 5),
       array('text'=> 'Gearlog', 'url'=> 'http://www.gearlog.com/', 'frequency'=> 9),
       array('text'=> 'Information Week', 'url'=> 'http://www.informationweek.com/', 'frequency'=> 0),
       array('text'=> 'PCWorld', 'url'=>  'http://www.pcworld.com/', 'frequency'=> 11),
       array('text'=> 'Tech Republic', 'url'=> 'http://techrepublic.com/', 'frequency'=> 3),
       array('text'=> 'Valleywag', 'url'=> 'http://valleywag.gawker.com/', 'frequency'=> 6),
       array('text'=> 'Rediff', 'url'=> 'http://in.rediff.com/', 'frequency'=> 9),
       array('text'=> 'WebProNews', 'url'=> 'http://www.webpronews.com/', 'frequency'=> 2),
       );
      $tagcloud = new EJ\TagCloud('tag');
      echo $tagcloud->dataSource($websiteCollection)->titleText('Popular Sites')->render();
    ?>

{% endhighlight %}

In the above code, the min font size is 0 and max font size is 12.

## Set event to perform an operation

Here, you can set the **TagCloud** events such as create, mouseover, mouseout, click.


{% highlight html %}

      <?php
    $websiteCollection = array(
       array('text'=> 'Google', 'url'=> 'http://www.google.com', 'frequency'=> 12),
       array('text'=> 'All Things Digital', 'url'=> 'http://allthingsd.com/', 'frequency'=> 3),
       array('text'=> 'Arts Technica', 'url'=> 'http://arstechnica.com/', 'frequency'=> 8),
       array('text'=> 'Business Week', 'url'=> 'http://www.businessweek.com/', 'frequency'=> 2),
       array('text'=> 'Yahoo', 'url'=> 'http://in.yahoo.com/', 'frequency'=> 12),
       array('text'=> 'Center Networks', 'url'=> 'http://www.centernetworks.com/', 'frequency'=> 5),
       array('text'=> 'Crave', 'url'=> 'http://news.cnet.com/crave/', 'frequency'=> 8),
       array('text'=> 'Crunch Gear', 'url'=> 'http://techcrunch.com/gadgets/', 'frequency'=> 20),
       array('text'=> 'Daily Tech', 'url'=> 'http://www.dailytech.com/', 'frequency'=> 1),
       array('text'=> 'Electronista', 'url'=> 'http://www.electronista.com/', 'frequency'=> 3),
       array('text'=> 'Engadget', 'url'=> 'http://www.engadget.com/', 'frequency'=> 5),
       array('text'=> 'Gearlog', 'url'=> 'http://www.gearlog.com/', 'frequency'=> 9),
       array('text'=> 'Information Week', 'url'=> 'http://www.informationweek.com/', 'frequency'=> 0),
       array('text'=> 'PCWorld', 'url'=>  'http://www.pcworld.com/', 'frequency'=> 11),
       array('text'=> 'Tech Republic', 'url'=> 'http://techrepublic.com/', 'frequency'=> 3),
       array('text'=> 'Valleywag', 'url'=> 'http://valleywag.gawker.com/', 'frequency'=> 6),
       array('text'=> 'Rediff', 'url'=> 'http://in.rediff.com/', 'frequency'=> 9),
       array('text'=> 'WebProNews', 'url'=> 'http://www.webpronews.com/', 'frequency'=> 2),
       );
    $tagcloud = new EJ\TagCloud('tag');
    echo $tagcloud->dataSource($websiteCollection)->titleText('Popular Sites')->create('oncreate')->mouseover('onmouseover')->mouseout('onmouseout')->click('onclick')->render();
    ?>
	<script>
	    function oncreate()
		{
		   alert();
		}
		
		function onmouseover()
		{
		   alert();
		}
		
		function onmouseout()
		{
		   alert();
		}
		
		function onclick()
		{
		   alert();
		}
		
	</script>

{% endhighlight %}

In the above code example, the **alert()** function is used  to show the events that happened.

