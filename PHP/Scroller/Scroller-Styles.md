---
layout: post
title: Scroller-Styles
description: scroller styles
platform: php
control: Scroller
documentation: ug
---

# Scroller Styles

The **Essential PHP Scroller** control allows you to customize the look and function of scrollbars. You can vary it significantly by setting the scrollbar button size, scrollbar position, height and width of the **Scroller** control. This section describes you the custom styles to be used when creating **Scroller**.

## Button Size

Scroller allows you to customize the scroll arrows width and height. In horizontal **scroller** the **buttonSize** customizes the top and down arrow and in vertical **scroller** the **buttonSize** customizes the left and right arrow.

## Scroller Size

The **scrollerSize** property is used to customize the scrollbar width and height. It is applicable for both horizontal and vertical scroller.

## Scroll Top

The **scrollerTop** property is used to move the **Scroller** content and scrollbars in top position with the specified value. It is used for only vertical scroller.

## Scroll Left

The **scrollerLeft** property is used to move the **Scroller** content and scrollbars in left position with the specified value. It is used for only horizontal scroller.

## Height

The height property is used to set the height for **Scroller** outer wrapper.

## Width

The width property is used to set the width for **Scroller** outer wrapper.

The following steps explains you on how to apply styles in **Scroller** control. 

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
        echo $scroller->height('300px')->width('100%')->scrollTop(50)->scrollLeft(20)->buttonSize(40)->destroy('onDestroy')->render();
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


The following screenshot displays the **Scroller** control with above mentioned styles

![](/php/Scroller/Scroller-Styles_images/Scroller-Styles_img1.JPG)