---
layout: post
title: getting started
description: getting started
platform: php
control: Signature
documentation: ug
---

# Getting Started

The Essential PHP Signature simplifies creation of a signature capture in a browser, allowing a user to draw a signature using mouse or touch.

This section explains briefly about how to create a **Signature** control in your application with PHP by the following step-by-step instructions.

The following screenshot demonstrates the output of the Signature control in PHP  

![https://help.syncfusion.com/js/signature/Getting_Started_images/gettingstarted_img1.png](Getting_Started_images\gettingstarted_img1.png)


## Create Signature control

You can create a PHP Project and add necessary scripts and styles with the help of the given [PHP Getting Started Documentation](https://help.syncfusion.com/php/getting-started).

You can render the PHP Signature control with the below mentioned code.

{% highlight php %}

        <?php

        $signature=new EJ\Signature('default');
        echo $signature->height('400px')->render();
        ?>

{% endhighlight %}

Run the above code to render the following output.

![https://help.syncfusion.com/js/signature/Getting_Started_images/createsignaturecontrol_img1.png](Getting_Started_images\createsignaturecontrol_img1.png)

## Adjusting Signature Size

You can customize the width and height of the Signature by **width** and **height** properties. These properties completely depend on signature canvas. The width and height are adjusted within the signature canvas.

The following code example is used to render the Signature component with customized width and height.

{% highlight php %}

        <?php

        $signature=new EJ\Signature('default');
        echo $signature->height('300px')->width('200px')render();
        ?>

{% endhighlight %}

The following screenshot illustrates signature with customized width and height.

![https://help.syncfusion.com/js/signature/Getting_Started_images/adjustingsignaturesize_img1.png](Getting_Started_images\adjustingsignaturesize_img1.png)
