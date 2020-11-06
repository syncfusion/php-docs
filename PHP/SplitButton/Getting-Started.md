---
layout: post
title: Getting-Started
description: getting started 
platform: PHP
control: Split Button
documentation: ug
---

# Getting Started 

This section explains briefly about the necessary steps required to render and configure EJ SplitButton control using PHP wrapper classes.

Create a PHP Project and add necessary scripts and styles with the help of the given PHP [Getting Started](https://help.syncfusion.com/php/getting-started) Documentation.

**Split Button Creation**

Create SplitButton control by instantiating the PHP wrapper class available in EJ namespace as shown below.

{% highlight html %}
        <div>
            <?php
            $splitbtn = new EJ\SplitButton("SplitBtnNormal");
            $item1 = new EJ\SplitButton\SplitButtonItem();
            $item1->id("1")->text("User");
            $item2 = new EJ\SplitButton\SplitButtonItem();
            $item2->id("2")->text("Guest");
            $item3 = new EJ\SplitButton\SplitButtonItem();
            $item3->id("3")->text("Admin");
            $splitbtn->addItem($item1,$item2,$item3);
            $item11 = new EJ\SplitButton\SplitButtonItem();                   
            echo $splitbtn->text("Login")->showRoundedCorner(true)->width("120px")->height("50px")->render();
            ?>
        </div>

{% endhighlight %}

Output of above code:

![](/php/SplitButton/Getting-Started_images/Getting-Started_img1.JPG) 

