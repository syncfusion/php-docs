---
layout: post
title: Getting-Started
description: getting started
platform: php
control: RadialMenu
documentation: ug
---

# Getting Started

This section helps to get started of the RadialMenu control in a PHP application.

![](Getting_Started_images/Getting_Started_img1.png)

## Create a RadialMenu

The following steps guide you to add a RadialMenu control.

Refer the common PHP Getting Started Documentation to create a PHP application and add necessary scripts and styles for rendering Essential PHP controls.

Create a simple RadialMenu object by referring the below code, **EJ\RadialMenu** object is created by using ‘new’ keyword. Define its properties and use **render()** method for rendering the control. We need to call the rendering element in echo statement. 


{% highlight php %}


     <?php

        $radial=new EJ\RadialMenu("defaultradialmenu");
         echo $radial->items($itemsr)->imageClass("imageclass")->backImageClass("backimageclass")->targetElementId("radialtarget1")->render();
     ?>  


{% endhighlight %}

This will render an empty RadialMenu control on executing.

## Configure Items

For adding items to RadialMenu, create an object for **EJ\RadialMenu\Item()** class. You can set the images for each item by giving the image URL in the **imageUrl** property and text to **text** property for the Item object. In order to display items in RadialMenu control, you need to map the items fields to RadialMenu items array. The required mapping field are listed as follows. 

    * `text` - Map the item name to use as `text` values to items.
    * `imageUrl` - Map the image for items to use as image to items within `Field` object.

In order to display items in RadialMenu control, you need to use **Item** class of **EJ\RadialMenu** object.

Refer to the following code example. Initialize Radial Menu control with items and set its target content as follows.

{% highlight php %}

    <?php
    $radial=new EJ\RadialMenu("defaultradialmenu");
    $ritem1=new EJ\RadialMenu\Item();
    $ritem1->text("Bold")->imageUrl("content/images/RadialMenu/font.png");
    $ritem2=new EJ\RadialMenu\Item();
    $ritem2->text("Italic")-> imageUrl("content/images/RadialMenu/f1.png");
    $ritem3=new EJ\RadialMenu\Item();
    $ritem3->text("Redo")-> imageUrl("content/images/RadialMenu/redo.png")->enabled(false);
    $ritem4=new EJ\RadialMenu\Item();
    $ritem4->text("Undo")-> imageUrl("content/images/RadialMenu/undo.png")->enabled(false);
    $itemsr= array($ritem1,$ritem2,$ritem3,$ritem4);
    echo $radial->items($itemsr)->imageClass("imageclass")->backImageClass("backimageclass")->targetElementId("radialtarget1")->render();
    ?>


{% endhighlight %}

Refer to the following code example to add target content to the Radial Menu.

{% highlight html %}

    <div id="radialtarget1" style="position:relative;">
        <div class="cols-sample-area">
            <textarea id="rteSample1" rows="10" cols="70" style="height: 550px">
    <p>Model-view-controller (MVC) is a software architecture pattern which separates the representation of information from the user's interaction with it.
    The model consists of application data, business rules, logic, and functions. A view can be any output representation of data, such as a chart or a diagram.
    Multiple views of the same data are possible, such as a bar chart for management and a tabular view for accountants.
    The controller mediates input, converting it to commands for the model or view.The central ideas behind MVC are code reusability and in addition to dividing the application into three kinds of controls, the MVC design defines the interactions between them.</p>

    <p>A controller can send commands to its associated view to change the view's presentation of the model (e.g., by scrolling through a document). It can also send commands to the model to update the model's state (e.g., editing a document).</p>

    <p>A model notifies its associated views and controllers when there has been a change in its state. This notification allows the views to produce updated output, and the controllers to change the available set of commands. A passive implementation of MVC omits these notifications, because the application does not require them or the software platform does not support them.</p>

    <p>A view requests from the model the information that it needs to generate an output representation to the user.</p>
                        </textarea>
    </div>
    </div>


{% endhighlight %}

Add the following styles in your code.

{% highlight css %}

    .e-radialmenu .imageclass {
                background-image: url(content/images/RadialMenu/settings.png);
        }

    .e-radialmenu .backimageclass {
                background-image: url(content/images/RadialMenu/Back_button.png);
        }


{% endhighlight %}

## Displaying RadialMenu

Display Radial Menu control within the div element and set its target content in script as follows.

{% highlight javascript %}

    var rteObj, rteEle = $("#rteSample1"), radialEle = $('#defaultradialmenu'), action = 0, 
    forRedo = 0;
        $(function () {
                    rteEle.ejRTE({ width: "100%", minWidth: "10px", change: "rteChange", select: "radialShow", showToolbar: false, showContextMenu: false });
                    rteObj = rteEle.data("ejRTE");
                    $(window).resize(function(){
                if(ej.isMobile() && ej.isPortrait())
                $('#defaultradialmenu').css({"left":25});
            
                    });
        });

{% endhighlight %}

You can display the **Radial Menu** by performing desired action on the target content while selecting the text inside the target. Therefore, call the **radialShow** method in the select action of the content. Refer to the following code example and add it to the script.

{% highlight javascript %}

    function radialShow(e) {
                var target = $("#radialtarget1"), radialRadius = 150, radialDiameter = 2 * radialRadius,
                // To get Iframe positions
                iframeY = target.offset().top + e.event.clientY, iframeX = target.offset().left + e.event.clientX,
                // To set Radial Menu position within target
                x = iframeX > target.width () - radialRadius? target.width() - radialDiameter : (iframeX > radialRadius ? iframeX - radialRadius : 0),
                y = iframeY > target.height () - radialRadius? target.height() - radialDiameter : (iframeY > radialRadius ? iframeY - radialRadius : 0);
            radialEle.ejRadialMenu("setPosition", x, y);
            radialEle.focus();
        }

{% endhighlight %}

## RadialMenu item functionalities

You can add functionalities for each item by using the **click** function. Refer to the following code example. Define click function for Radial Menu control items as follows.

{% highlight php %}

    <?php
    $radial=new EJ\RadialMenu("defaultradialmenu");
    $ritem1=new EJ\RadialMenu\Item();
    $ritem1->text("Bold")->click("bold")->imageUrl("content/images/RadialMenu/font.png");
    $ritem2=new EJ\RadialMenu\Item();
    $ritem2->text("Italic")->click("italic")->imageUrl("content/images/RadialMenu/f1.png");
    $ritem3=new EJ\RadialMenu\Item();
    $ritem3->text("Redo")->click("redo")->imageUrl("content/images/RadialMenu/redo.png")->enabled(false);
    $ritem4=new EJ\RadialMenu\Item();
    $ritem4->text("Undo")->click("undo")->imageUrl("content/images/RadialMenu/undo.png")->enabled(false);
    $itemsr= array($ritem1,$ritem2,$ritem3,$ritem4);
    echo $radial->items($itemsr)->imageClass("imageclass")->backImageClass("backimageclass")->targetElementId("radialtarget1")->render();
    ?>


{% endhighlight %}

Refer to the following code example to add click functions for RadialMenu items.

{% highlight javascript %}

            function bold(e) {
            rteObj.executeCommand("bold");
            data = rteObj._getSelectedHtmlString() ? true : false;
            if (data) action += 1;
            forRedo = action;
            radialEle.focus();
        }
            function italic(e) {
            rteObj.executeCommand("italic");
            data = rteObj._getSelectedHtmlString() ? true : false;
            if (data) action += 1;
            forRedo = action;
            radialEle.focus();
        }
        function undo(e) {
            rteObj.executeCommand("undo");
            action -= 1;
            if (action == 0)
                radialEle.ejRadialMenu("disableItem", "Undo");
            radialEle.ejRadialMenu("enableItem", "Redo");
            radialEle.focus();
        }
        function redo(e) {
            rteObj.executeCommand("redo");
            action += 1;
            if (forRedo == action) radialEle.ejRadialMenu("disableItem", "Redo");
            radialEle.ejRadialMenu("enableItem", "Undo");
            radialEle.focus();
        }


{% endhighlight %}

After rendered RadialMenu in browser, click **bold** item in RadialMenu control, you can get the following output.

![](Getting_Started_images/Getting_Started_img2.png)

> _Note:_ _You can find the RadialMenu properties from the_ [API reference](https://help.syncfusion.com/api/js/ejradialmenu) _document_
