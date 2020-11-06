---
layout: post
title: Getting-Started for Menu
description: getting started for Menu
platform:php
control: Menu
documentation: ug
keywords:ejmenu, php menu, menu
---

# Getting Started 

This section explains briefly about how to create a **Menu** control in your application with **PHP**. The **EJ PHP** **Menu** supports displaying a **Menu** of list-out items. This **Menu** is based on ul-li hierarchy, where the sub-list items are rendered as the sub-menu items. The **Menu** control can also be rendered with local and remote data source.  From the following guidelines, you can learn how to customize the **Menu** control for a website. In this case, **Syncfusion's** website **Menu** is discussed. The following screenshot displays the appearance of **Menu**.

![](Getting-Started_images/Getting-Started_img1.png) 

## Create a Menu

**EJ PHP Menu** widgets are basically provided with built-in features like keyboard navigation, show and hide **Menu** items with animations, and flexible API's. From the following guidelines, you can learn how to render **Menu** control with local data source value.

You can create a PHP Project and add necessary scripts and styles with the help of the given PHP Getting Started Documentation.

Create a first PHP file in Xampp and name it appropriately with `.php` extension and also place it under the newly created sample folder. For example, say Index.php with the initial code as shown below -

Refer the required scripts and CSS files in your PHP page as mentioned below in order to render the Menu control - 

{% highlight html %}

    <!DOCTYPE html>
    <html>
        <head>
                <title>Getting Started - Menu</title>
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

## Configure parent Menu items

Every **Menu** has a list of **Menu** items with list of sub level **Menu** items. From the following guidelines, you can learn how to initialize the root level elements of **Menu** control with Local data source value.  Initialize the **Menu** with data source value as illustrated in the following code example. 

{% highlight html %}

        <?php
    $menu = new EJ\Menu('syncfusionProducts');
    $Item1 = new EJ\Menu\MenuItem();
    $Item1->text('Products');
    $Item2 = new EJ\Menu\MenuItem();
    $Item2->text('Support');
    $Item3 = new EJ\Menu\MenuItem();
    $Item3->text('Purchase');

    $Item4 = new EJ\Menu\MenuItem();
    $Item4->text('Downloads');
       
  
	$Item5 = new EJ\Menu\MenuItem();
    $Item5->text('Resources');
       
	$menu->AddItem($Item1,$Item2,$Item3,$Item4,$Item5);
    echo $menu->render();
    ?>

{% endhighlight %}

Add following styles for menu

{% highlight css %}

       <style>
 
        .e-menu {
           height: 40px;
          }
      </style>

{% endhighlight %}

The following screenshot displays output.

![](Getting-Started_images/Getting-Started_img3.jpg) 

## Initialize sub-level Menu items

Every **Menu** items have a list of sub level **Menu** items. From the following guidelines, you can learn how to initialize the sub level items of **Menu** control. 								

The following code example describes how to initialize first level sub menu items of product **Menu** item.

{% highlight html %}

         <?php
     $menu = new EJ\Menu('syncfusionProducts');
     $Item1 = new EJ\Menu\MenuItem();
     $Item1->text('Products');
        $Item11 = new EJ\Menu\MenuItem();
        $Item11->text('ASP.NET');
        $Item12 = new EJ\Menu\MenuItem();
        $Item12->text('ASP.NET MVC');
        $Item13 = new EJ\Menu\MenuItem();
        $Item13->text('Mobile MVC');
        $Item14 = new EJ\Menu\MenuItem();
        $Item14->text('Silverlight');
        
     $Item1->AddItem($Item11,$Item12,$Item13,$Item14);
     $Item2 = new EJ\Menu\MenuItem();
     $Item2->text('Support');
        $Item21 = new EJ\Menu\MenuItem();
        $Item21->text('Direct-Trac Support');
        $Item22 = new EJ\Menu\MenuItem();
        $Item22->text('Community Forums');
        $Item23 = new EJ\Menu\MenuItem();
        $Item23->text('Knowledge Base');
        
        $Item24 = new EJ\Menu\MenuItem();
        $Item24->text('Services');
            
    $Item2->AddItem($Item21,$Item22,$Item23,$Item24);

    $Item3 = new EJ\Menu\MenuItem();
    $Item3->text('Purchase');

    $Item4 = new EJ\Menu\MenuItem();
    $Item4->text('Downloads');
        $Item41 = new EJ\Menu\MenuItem();
        $Item41->text('Evaluation');
        $Item42 = new EJ\Menu\MenuItem();
        $Item42->text('Free E-Books');
        $Item43 = new EJ\Menu\MenuItem();
        $Item43->text('Metro Studio');
        $Item44 = new EJ\Menu\MenuItem();
        $Item44->text('Latest Version');
        
    $Item4->AddItem($Item41,$Item42,$Item43,$Item44);

	$Item5 = new EJ\Menu\MenuItem();
    $Item5->text('Resources');
        $Item51 = new EJ\Menu\MenuItem();
        $Item51->text('Technology Resource Portal');
           
        $Item52 = new EJ\Menu\MenuItem();
        $Item52->text('Case Studies');
        $Item53 = new EJ\Menu\MenuItem();
        $Item53->text('Bouchers & Datasheets');
        $Item54 = new EJ\Menu\MenuItem();
        $Item54->text('FAQ');
    $Item5->AddItem($Item51,$Item52,$Item53,$Item54);
	$menu->AddItem($Item1,$Item2,$Item3,$Item4,$Item5);
    echo $menu->render();
    ?>


{% endhighlight %}

Execute the above code example to render the following output.

![](Getting-Started_images/Getting-Started_img4.png) 

## Define multiple level Menu items

You can define the sub-menu items to multiple levels in **Menu** control. Refer the below given code to  render sub level **Menu** item for the **Menu** items.

To initialize multiple levels sub menu items, use the following code example.

{% highlight html %}

        <?php
     $menu = new EJ\Menu('syncfusionProducts');
     $Item1 = new EJ\Menu\MenuItem();
     $Item1->text('Products');
        $Item11 = new EJ\Menu\MenuItem();
        $Item11->text('ASP.NET');
        $Item12 = new EJ\Menu\MenuItem();
        $Item12->text('ASP.NET MVC');
        $Item13 = new EJ\Menu\MenuItem();
        $Item13->text('Mobile MVC');
        $Item14 = new EJ\Menu\MenuItem();
        $Item14->text('Silverlight');
        
     $Item1->AddItem($Item11,$Item12,$Item13,$Item14);
     $Item2 = new EJ\Menu\MenuItem();
     $Item2->text('Support');
        $Item21 = new EJ\Menu\MenuItem();
        $Item21->text('Direct-Trac Support');
        $Item22 = new EJ\Menu\MenuItem();
        $Item22->text('Community Forums');
        $Item23 = new EJ\Menu\MenuItem();
        $Item23->text('Knowledge Base');
        
        $Item24 = new EJ\Menu\MenuItem();
        $Item24->text('Services');
            $Item241 = new EJ\Menu\MenuItem();
            $Item241->text('Consulting');
            $Item242 = new EJ\Menu\MenuItem();
            $Item242->text('Training');
        $Item24->AddItem($Item241,$Item242);
    $Item2->AddItem($Item21,$Item22,$Item23,$Item24);

    $Item3 = new EJ\Menu\MenuItem();
    $Item3->text('Purchase');

    $Item4 = new EJ\Menu\MenuItem();
    $Item4->text('Downloads');
        $Item41 = new EJ\Menu\MenuItem();
        $Item41->text('Evaluation');
        $Item42 = new EJ\Menu\MenuItem();
        $Item42->text('Free E-Books');
        $Item43 = new EJ\Menu\MenuItem();
        $Item43->text('Metro Studio');
        $Item44 = new EJ\Menu\MenuItem();
        $Item44->text('Latest Version');
        
    $Item4->AddItem($Item41,$Item42,$Item43,$Item44);

	$Item5 = new EJ\Menu\MenuItem();
    $Item5->text('Resources');
        $Item51 = new EJ\Menu\MenuItem();
        $Item51->text('Technology Resource Portal');
           
        $Item52 = new EJ\Menu\MenuItem();
        $Item52->text('Case Studies');
        $Item53 = new EJ\Menu\MenuItem();
        $Item53->text('Bouchers & Datasheets');
        $Item54 = new EJ\Menu\MenuItem();
        $Item54->text('FAQ');
    $Item5->AddItem($Item51,$Item52,$Item53,$Item54);
	$menu->AddItem($Item1,$Item2,$Item3,$Item4,$Item5);
    echo $menu->render();
    ?>

{% endhighlight %}

The following screenshot is the output.

![](Getting-Started_images/Getting-Started_img1.png) 

By following the above mentioned steps, you can render the **Menu** control with multiple level sub items . You can simply customize the **Menu** widget in an efficient manner.

In summary of this getting started, you have now simulated the **Syncfusion�s** website **Menu** with **EJ PHP Menu**. You have utilized and learn the appearance customization etc.  

By following the above mentioned steps, you can render the **Menu** control with multiple level sub items. You can simply customize the **Menu** in an efficient manner.

