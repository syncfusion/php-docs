---
layout: post
title: Getting-Started
description: getting started
platform: PHP
control: GroupButton
documentation: ug
---


# Getting Started

This section explains briefly about the necessary steps required to render and configure EJ GroupButton control using PHP wrapper classes.

Create a PHP Project and add necessary scripts and styles with the help of the given PHP [Getting Started](https://help.syncfusion.com/php/getting-started) Documentation.

## Create a GroupButton 

Create a GroupButton control by instantiating the PHP wrapper class available in EJ namespace as shown below.

{% highlight html %}
    <label class="btn_label">Appointment View</label>
    <div>
        <?php
        $data='[{ "text": "Day", "contentType": "textonly" },           
            { "text": "Week","contentType": "textonly" },
            { "text": "Month", "contentType": "textonly", "selected": "selected" },
            { "text": "Year", "contentType": "textonly" }]';
        $data=json_decode($data,true);
        $groupBtn=new EJ\GroupButton("groupBtn");
        echo $groupBtn->groupButtonMode("radiobutton")->dataSource($data)->showRoundedCorner(true)->width("100%")->render();
        ?>
    </div>

{% endhighlight %}

Add the following styles to show the **CheckBox** control in an order.

{% highlight css %}

     <style>
        .btn_label {
            display: inline-block;
            margin-bottom: 20px;
            font-weight: 500;
        }
    </style>

{% endhighlight %}

The following screenshot illustrates the output of above code.

![](/php/GroupButton/DataSource_images/Getting-Started_img1.JPG) 