---
layout: post
title: Getting-Started
description: getting started
platform: php
control: Scroller
documentation: ug
---

# Getting Started

This section explains briefly about the necessary steps required to render and configure EJ Scroller control using PHP wrapper classes.

Create a PHP Project and add necessary scripts and styles with the help of the given PHP [Getting Started](https://help.syncfusion.com/php/getting-started) Documentation.

## Create your first Scroller in PHP

**Essential PHP Scroller** control can be rendered based on the target panel height and width, and includes more customization options.

**Add Scroller Control to your PHP Application**

Create a Scroller control by instantiating the PHP wrapper class available in EJ namespace as shown below.

{% highlight html %}

<div class='control'>
        <?php
        $scroller=new EJ\Scroller('scrollcontent');
        $scroller->templateStart();
        ?>    
        <div class='sampleContent'>
            <h3 style='font-size: 20px;'>MVC</h3>
            <div>
                <p>
                    Model-view-controller (MVC) is a software architecture pattern which separates the
                    representation of information from the user's interaction with it.
                    The model consists of application data, business rules, logic, and functions. A view can be any
                    output representation of data, such as a chart or a diagram. Multiple views of the same data
                    are possible, such as a bar chart for management and a tabular view for accountants.
                    The controller mediates input, converting it to commands for the model or view.The central
                    ideas behind MVC are code reusability and n addition to dividing the application into three
                    kinds of components, the MVC design defines the interactions between them.
                </p>
                <ul>
                    <li>
                        <b>A controller </b>can send commands to its associated view to change the view's presentation of the model (e.g., by scrolling through a document).
                        It can also send commands to the model to update the model's state (e.g., editing a document).
                    </li>
                    <li>
                        <b>A model</b>notifies its associated views and controllers when there has been a change in its state. This notification allows the views to produce updated output, and the controllers to change the available set of commands.
                        A passive implementation of MVC omits these notifications, because the application does not require them or the software platform does not support them.
                    </li>
                    <li>
                        <b>A view</b>requests from the model the information that it needs to generate an output representation to the user.
                    </li>
                </ul>
            </div>
        </div>          
        <?php
        $scroller->templateEnd();
        echo $scroller->height('300px')->width('100%')->destroy('onDestroy')->render();
        ?>
    </div>
{% endhighlight %}

{% highlight javascript %}

        var scrollobj;
        $(function () {
            scrollobj = $('#scrollcontent').data('ejScroller'); // instance creation
            $(window).bind('resize', onResizeEvent);
        });
        function onDestroy(args){
            $(window).unbind('resize', onResizeEvent); // unbind the event while destroying
        }
        function onResizeEvent() {
            if ($('#scrollcontent').data('ejScroller'))
                scrollobj.refresh(); // refresh scroller on window resize
        }           
        
{% endhighlight %}

Configure the styles.

{% highlight css %}
    
<style type="text/css">
        .control {
            border: 1px solid #bbbcbb;
            width: 600px;
            margin: 0 auto;
            height: 300px;
        }
        .sampleContent {
            width: 700px;
            padding:15px;
        }
</style>

{% endhighlight %}


Execute the above code to render the following output.

![](/php/Scroller/Getting-Started_images/Getting-Started_img1.JPG)

## Thumb Scrolling

Normally the scrollbar position can be changed by dragging the scrollbar handle or clicking the arrows. The **Scroller** control allows you for panning or dragging the scroll content area to drag by dragging inside the scroll content. To achieve this in your **Scroller** control, enable the **enableTouchScroll** to true. By default the value for **enableTouchScroll** is true. When you want to prevent the panning or dragging the scroll content area, set **enableTouchScroll** as false.

The following code explains you the configuration of **enableTouchScroll** property in **Scroller**. 

{% highlight html %}

<div class='control'>
        <?php
        $scroller=new EJ\Scroller('scrollcontent');
        $scroller->templateStart();
        ?>    
        <div class='sampleContent'>
            <h3 style='font-size: 20px;'>MVC</h3>
            <div>
                <p>
                    Model-view-controller (MVC) is a software architecture pattern which separates the
                    representation of information from the user's interaction with it.
                    The model consists of application data, business rules, logic, and functions. A view can be any
                    output representation of data, such as a chart or a diagram. Multiple views of the same data
                    are possible, such as a bar chart for management and a tabular view for accountants.
                    The controller mediates input, converting it to commands for the model or view.The central
                    ideas behind MVC are code reusability and n addition to dividing the application into three
                    kinds of components, the MVC design defines the interactions between them.
                </p>
                <ul>
                    <li>
                        <b>A controller </b>can send commands to its associated view to change the view's presentation of the model (e.g., by scrolling through a document).
                        It can also send commands to the model to update the model's state (e.g., editing a document).
                    </li>
                    <li>
                        <b>A model</b>notifies its associated views and controllers when there has been a change in its state. This notification allows the views to produce updated output, and the controllers to change the available set of commands.
                        A passive implementation of MVC omits these notifications, because the application does not require them or the software platform does not support them.
                    </li>
                    <li>
                        <b>A view</b>requests from the model the information that it needs to generate an output representation to the user.
                    </li>
                </ul>
            </div>
        </div>          
        <?php
        $scroller->templateEnd();
        echo $scroller->height('300px')->width('100%')->enableTouchScroll(false)->render();
        ?>
    </div>
{% endhighlight %}


## Customizing the scroll Step

The **Scroller** control allows you to specify the scroll movement step in a pixel value, this step value is added to the scrollbar position when you press the arrow key. Based on position value, the scrollbar moves in its corresponding orientation. You can achieve this by using **scrollOneStepBy.**

Specify the **scrollOneStepBy** property in **Scroller** to change the step value when you press the arrow button.

{% highlight html %}

<div class='control'>
        <?php
        $scroller=new EJ\Scroller('scrollcontent');
        $scroller->templateStart();
        ?>    
        <div class='sampleContent'>
            <h3 style='font-size: 20px;'>MVC</h3>
            <div>
               <!-- Scroller content here as mentioned in the previous sample -->
            </div>
        </div>          
        <?php
        $scroller->templateEnd();
        echo $scroller->height('300px')->width('100%')->scrollOneStepBy(50)->render();
        ?>
    </div>
{% endhighlight %}

## RTL

The **enableRTL** API provides right-to-left functionality and features for languages that work in a right-to-left for selecting, editing. Arabic and Hebrew are written from right to left. If you have a working style from right to left, you can use this feature in scroller. You can achieve this in your **Scroller** by using **enableRTL** property. Setting this property to true, the Scroller content text is displayed in the right to left format. The vertical scrollbar move to right to left side.

The following steps explains you the configuration of **enableRTL** property in **Scroller**.

In the PHP page, add a &lt;div&gt; element to configure Scroller widget.

{% highlight html %}
	
<div class='control'>
        <?php
        $scroller=new EJ\Scroller('scrollcontent');
        $scroller->templateStart();
        ?>    
        <div class='sampleContent'>
            <h3 style='font-size: 20px;'>MVC</h3>
            <div>
               <!-- Scroller content here as mentioned in the previous sample -->
            </div>
        </div>          
        <?php
        $scroller->templateEnd();
        echo $scroller->height('300px')->width('100%')->enableRTL(true)->render();
        ?>
    </div>

{% endhighlight %}