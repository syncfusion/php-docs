---
layout: post
title: Getting-Started
description: getting started
platform: php
control: Accordion 
documentation: ug
keywords: ejaccordion,accordion, php accordion 
---

# Getting Started

This section explains briefly about how to create an **Accordion** in your application with **PHP** wrapper classes of EJ controls..

## Configure Accordion

You can create a PHP Project and add necessary scripts and styles with the help of the given PHP Getting Started Documentation.

This section encompasses the details on how you can configure the **Accordion** control in your application and customize it with various properties such as multiple open, rounded corner and icons for the **Accordion** header according to your requirement.

The following screenshot illustrates you the usage of **Accordion** control in listing the controls under the Essential Studio products. 

![](Getting-Started_images/Getting-Started_img1.png) 

The usage of **Accordion** control is described in the following sections.

## Create a Simple Accordion in PHP

Create a first PHP file in Xampp and name it appropriately with `.php` extension and also place it under the newly created sample folder. For example, say Index.php with the initial code as shown below -

Refer the required scripts and CSS files in your PHP page as mentioned below in order to render the Accordion control - 

{% highlight html %}

    <!DOCTYPE html>
    <html>
        <head>
                <title>Getting Started - Accordion</title>
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

Create an Accordion control as shown below

{% highlight html %}

     <div class="cols-sample-area">
     <?php
      $acr = new EJ\Accordion('multiAccordion');
      $acr->width('550px');

     $acrItem = new EJ\Accordion\AccordionItem();
     $acrItem->text('Essential Studio ASP.NET')->templateStart();
     ?>
    <div>
             <ul>
            <li>
                <h4>DocIO</h4>
            </li>
            <li>
                <h4>Pdf  </h4>
            </li>
            <li>
                <h4>Gauge  </h4>
            </li>
            <li>
                <h4>Schedule  </h4>
            </li>
            <li>
                <h4>Diagram  </h4>
            </li>
            <li>
                <h4>Tools </h4>
            </li>
        </ul>
    </div>
    <?php
    $acrItem->templateEnd();
    $acr->AddItem($acrItem);
    $acrItem2 = new EJ\Accordion\AccordionItem();
    $acrItem2->text('Essential Studio ASP.NET MVC')->templateStart();
    ?>
    <div>
         <ul>
            <li>
                <h4>Chart </h4>
            </li>
            <li>
                <h4>Grid  </h4>
            </li>
            <li>
                <h4>Gantt  </h4>
            </li>
            <li>
                <h4>Schedule  </h4>
            </li>
            <li>
                <h4>Diagram  </h4>
            </li>
        </ul>    </div>
    <?php
    $acrItem2->templateEnd();
    $acr->AddItem($acrItem2);
    $acrItem3 = new EJ\Accordion\AccordionItem();
    $acrItem3->text('Essential Studio Javascript')->templateStart();
    ?>
    <div>
     <ul>
            <li>
                <h4>Chart </h4>
            </li>
            <li>
                <h4>Grid  </h4>
            </li>
            <li>
                <h4>Gantt  </h4>
            </li>
            <li>
                <h4>Schedule  </h4>
            </li>
            <li>
                <h4>Diagram  </h4>
            </li>
        </ul>	
    </div>
    <?php
    $acrItem3->templateEnd();
    $acr->AddItem($acrItem3);
    echo $acr->render();
    ?>
    </div>

{% endhighlight %}

You can execute the above code example to display the Accordion control with simple control list.

![](Getting-Started_images/Getting-Started_img2.png) 

You can customize the Accordion control using various properties. The Accordion control properties and its default values are described in the following section.

## Configure Multiple Open

You can have multiple **Accordion** tabs opened to view all products at a time. To achieve this set the **enableMultipleOpen** property of the **Accordion** control to true.

N> enableMultipleOpen property is false by default.

You can also open all the panels during initialization using the **selectedItems** property of the **Accordion** control. The following code sample illustrates the opening of multiple tabs by passing the tab index values of tab.

{% highlight html %}

     <?php
    $acr = new EJ\Accordion('multiAccordion');
    $acr->width('550px');

    $acrItem = new EJ\Accordion\AccordionItem();
    $acrItem->text('Essential Studio ASP.NET')->templateStart();
    ?>
    <div>
             <ul>
            <li>
                <h4>DocIO</h4>
            </li>
            <li>
                <h4>Pdf  </h4>
            </li>
            <li>
                <h4>Gauge  </h4>
            </li>
            <li>
                <h4>Schedule  </h4>
            </li>
            <li>
                <h4>Diagram  </h4>
            </li>
            <li>
                <h4>Tools </h4>
            </li>
        </ul>
    </div>
    <?php
    $acrItem->templateEnd();
    $acr->AddItem($acrItem);
    $acrItem2 = new EJ\Accordion\AccordionItem();
    $acrItem2->text('Essential Studio ASP.NET MVC')->templateStart();
    ?>
    <div>
         <ul>
            <li>
                <h4>Chart </h4>
            </li>
            <li>
                <h4>Grid  </h4>
            </li>
            <li>
                <h4>Gantt  </h4>
            </li>
            <li>
                <h4>Schedule  </h4>
            </li>
            <li>
                <h4>Diagram  </h4>
            </li>
        </ul>    </div>
    <?php
    $acrItem2->templateEnd();
    $acr->AddItem($acrItem2);
    $acrItem3 = new EJ\Accordion\AccordionItem();
    $acrItem3->text('Essential Studio Javascript')->templateStart();
    ?>
    <div>
     <ul>
            <li>
                <h4>Chart </h4>
            </li>
            <li>
                <h4>Grid  </h4>
            </li>
            <li>
                <h4>Gantt  </h4>
            </li>
            <li>
                <h4>Schedule  </h4>
            </li>
            <li>
                <h4>Diagram  </h4>
            </li>
        </ul>	
    </div>
    <?php
    $acrItem3->templateEnd();
    $acr->AddItem($acrItem3);
    echo $acr->enableMultipleOpen(true)->selectedItems([0,1,2])->render();
    ?>

{% endhighlight %}

**Accordion** control with **enableMultipleOpen** property is illustrated in the following screen shot.

![](Getting-Started_images/Getting-Started_img3.png) 

### Setting rounded corner

**Accordion** control, by default, is rendered in a regular rectangle. You can modify the regular rectangles with rounded corners by setting the **showRoundedCorner** property to **True**.

N> showRoundedCorner property is False by default.

{% highlight html %}

      <?php
    $acr = new EJ\Accordion('multiAccordion');
    $acr->width('550px');

    $acrItem = new EJ\Accordion\AccordionItem();
    $acrItem->text('Essential Studio ASP.NET')->templateStart();
    ?>
    <div>
             <ul>
            <li>
                <h4>DocIO</h4>
            </li>
            <li>
                <h4>Pdf  </h4>
            </li>
            <li>
                <h4>Gauge  </h4>
            </li>
            <li>
                <h4>Schedule  </h4>
            </li>
            <li>
                <h4>Diagram  </h4>
            </li>
            <li>
                <h4>Tools </h4>
            </li>
        </ul>
    </div>
    <?php
    $acrItem->templateEnd();
    $acr->AddItem($acrItem);
    $acrItem2 = new EJ\Accordion\AccordionItem();
    $acrItem2->text('Essential Studio ASP.NET MVC')->templateStart();
    ?>
    <div>
         <ul>
            <li>
                <h4>Chart </h4>
            </li>
            <li>
                <h4>Grid  </h4>
            </li>
            <li>
                <h4>Gantt  </h4>
            </li>
            <li>
                <h4>Schedule  </h4>
            </li>
            <li>
                <h4>Diagram  </h4>
            </li>
        </ul>    </div>
    <?php
    $acrItem2->templateEnd();
    $acr->AddItem($acrItem2);
    $acrItem3 = new EJ\Accordion\AccordionItem();
    $acrItem3->text('Essential Studio Javascript')->templateStart();
    ?>
    <div>
     <ul>
            <li>
                <h4>Chart </h4>
            </li>
            <li>
                <h4>Grid  </h4>
            </li>
            <li>
                <h4>Gantt  </h4>
            </li>
            <li>
                <h4>Schedule  </h4>
            </li>
            <li>
                <h4>Diagram  </h4>
            </li>
        </ul>	
    </div>
    <?php
    $acrItem3->templateEnd();
    $acr->AddItem($acrItem3);
    echo $acr->enableMultipleOpen(true)->showRoundedCorner(true)->selectedItems([0,1,2])->render();
    ?>    

{% endhighlight %}

The following screenshot illustrates the **Accordion** control with rounded corners.

![](Getting-Started_images/Getting-Started_img4.png) 

## Customize Icon

You can customize the **Header** icon using **customIcon** property. This property has two features such as **header** and **selectedHeader**. By default, the classes of **header** and **selectedHeader** are **e-collapse** and **e-expand** respectively**.**

You can change the + and - symbols in the **Accordion** header, that are the default icons with Up or Down arrow icons. 

Up or Down arrow icons are available in **e-arrowheadup** and **e-arrowheaddown** classes respectively in the ej.widgets.core.min.css stylesheets from the sample. 

You can set the Up or Down arrow icon to **Accordion** header, by adding **e-arrowheadup** and **e-arrowheaddown** class to **selectedHeader** and **header** properties respectively.

{% highlight html %}

      <?php
    $acr = new EJ\Accordion('multiAccordion');
    $acr->width('550px');

    $acrItem = new EJ\Accordion\AccordionItem();
    $acrItem->text('Essential Studio ASP.NET')->templateStart();
    ?>
    <div>
             <ul>
            <li>
                <h4>DocIO</h4>
            </li>
            <li>
                <h4>Pdf  </h4>
            </li>
            <li>
                <h4>Gauge  </h4>
            </li>
            <li>
                <h4>Schedule  </h4>
            </li>
            <li>
                <h4>Diagram  </h4>
            </li>
            <li>
                <h4>Tools </h4>
            </li>
        </ul>
    </div>
    <?php
    $acrItem->templateEnd();
    $acr->AddItem($acrItem);
    $acrItem2 = new EJ\Accordion\AccordionItem();
    $acrItem2->text('Essential Studio ASP.NET MVC')->templateStart();
    ?>
    <div>
         <ul>
            <li>
                <h4>Chart </h4>
            </li>
            <li>
                <h4>Grid  </h4>
            </li>
            <li>
                <h4>Gantt  </h4>
            </li>
            <li>
                <h4>Schedule  </h4>
            </li>
            <li>
                <h4>Diagram  </h4>
            </li>
        </ul>    </div>
    <?php
    $acrItem2->templateEnd();
    $acr->AddItem($acrItem2);
    $acrItem3 = new EJ\Accordion\AccordionItem();
    $acrItem3->text('Essential Studio Javascript')->templateStart();
    ?>
    <div>
     <ul>
            <li>
                <h4>Chart </h4>
            </li>
            <li>
                <h4>Grid  </h4>
            </li>
            <li>
                <h4>Gantt  </h4>
            </li>
            <li>
                <h4>Schedule  </h4>
            </li>
            <li>
                <h4>Diagram  </h4>
            </li>
        </ul>	
    </div>
    <?php
    $acrItem3->templateEnd();
    $acr->AddItem($acrItem3);
	$acrIcon = new EJ\Accordion\CustomIcon();
    $acrIcon->header("e-arrowheaddown")->selectedHeader("e-arrowheadup");
    echo $acr->enableMultipleOpen(true)->showRoundedCorner(true)->CustomIcon($acrIcon)->render();
    ?>
  
{% endhighlight %}

The following screenshot illustrates the customization of **selectedHeader** and **header** of the **Accordion** control.

![](Getting-Started_images/Getting-Started_img5.png) 

