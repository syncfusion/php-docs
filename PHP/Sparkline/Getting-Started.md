---
layout: post
title: Getting Started for Essential PHP Sparkline
description: How to create a sparkline.
platform: php
control: Sparkline
documentation: ug
---

# Getting Started

This section explains you the steps required to populate the Sparkline with data. This section covers only the minimal features that you need to know to get started with the Sparkline.

## Adding PHP EJ source and script reference

Create a first PHP file in Xampp and name it appropriately with .php extension and also place it under the newly created sample folder. Now refer AutoLoad.php file from EJ source of PHP in the sample page. For example, say Index.php with the initial code as shown below -
Refer the required scripts files in your PHP page as mentioned below in order to render the Sparkline control.

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


## Initialize Sparkline

Add the following code in the index.php file to create the Sparkline control in index page.

{% highlight html %}

<div>

    <?php
    require_once '../EJ/AutoLoad.php';
    ?>

<?php
    $sparkline=new EJ\Sparkline("container");    
	
    echo $sparkline->render();
    ?>

</div>


{% endhighlight %}
Now, the Sparkline is rendered with some auto-generated random values and with default Line type.

![](Getting-Started_images/Getting-Started_img1.png)