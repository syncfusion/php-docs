---
layout: post
title: Syncfusion Dialog Getting-Started
description: getting started
platform: php
control: Dialog
documentation: ug
---

# Getting Started

This section helps to get started of the Dialog control in a PHP application.

## Create a Dialog

The following steps guide you to add a Dialog control.

Refer the common PHP Getting Started Documentation to create a PHP application and add necessary scripts and styles for rendering Essential PHP controls.

Create a simple Dialog object by referring the below code,**EJ\Dialog** object is created by using ‘new’ keyword. Define its properties and use **render()** method for rendering the control. We need to call the rendering element in echo statement. 
{% highlight php %}

        <?php
        $dialog = new  \EJ\Dialog("dialog");           
            echo $dialog->render();
        ?>

{% endhighlight %}

This will render an empty Dialog control on executing.

![Getting Started](Getting_Started_images/getting-started-img1.png)

## Add dialog content

You can add the content to Dialog Control. Here templateStart() is used to add content in the Dialog and templateEnd() is act as closing method of templateStart. The content given in between these will be taken as dialog content. Refer the below code for adding content in dialog control. 

{% highlight php %}

    <?php
        $dialog = new  \EJ\Dialog("dialog");
        $dialog->templateStart();
        ?>
            <div class="cnt">
            <!--dialog content-->
                <p>This is a simple dialog</p>
            </div>
        <?php    
        
        echo $dialog->templateEnd()->render();
        ?>

{% endhighlight %}

Run the above code and output renders as follows,

![Dialog content](Getting_Started_images/getting-started-img2.png)

## Set the title

You can set Dialog control title as follows.

{% highlight php %}

    <?php
        $dialog = new  \EJ\Dialog("dialog");
        $dialog->title("Dialog")->templateStart();
        ?>
            <div class="cnt">
            <!--dialog content-->
                <p>This is a simple dialog</p>
            </div>
        <?php    
        
        echo $dialog->templateEnd()->render();

        ?>


{% endhighlight %}

Run the above code and your output will be,

![Dialog Title](Getting_Started_images/getting-started-img3.png)

## Open Dialog dynamically

In most cases, the Dialog control are needed only in dynamic actions like showing some messages on clicking a button, to provide alert, etc. So the Dialog control provides “open” and “close” methods to open/close the dialogs dynamically.
The Dialog control can be hidden on initialize using **showOnInit(false)** property which should be set to false. If you want to use **showOnInit** property you need to use as like this $dialog->title("Dialog")-> showOnInit(false)->templateStart();

Use the below code in the `php` tag. The dialog will be opened on clicking the Button control.

{% highlight php %}

    <?php
        $dialog = new  \EJ\Dialog("dialog");
        $dialog->title("Dialog")->templateStart();
        ?>
            <div class="cnt">
            <!--dialog content-->
                <p>This is a simple dialog</p>
            </div>
        <?php    
        
        echo $dialog-> close("onDialogClose")->templateEnd()->render();
    $button = new \EJ\Button("button");
            echo $button->text("Click to open dialog")->type("button")->height("30px")->width("150px")->click("onButtonClick")->render();
        ?>

{% endhighlight %}

Add the following in the script section.

{% highlight javascript %}

        function onDialogClose() {
            $("#button").show()
        }
        function onButtonClick() {
                $("#dialog").ejDialog("open");
        }


{% endhighlight %}

Run the above code, you get the output as below,

![Open Dialog Dynamically](Getting_Started_images/getting-started-img4.png)

> _Note:_ _You can find the Dialog properties from the_ [API reference](https://help.syncfusion.com/api/js/ejdialog) _document_
