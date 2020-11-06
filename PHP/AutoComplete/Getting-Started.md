---
layout: post
title: Getting-Started
description: getting started
platform: php
control: Autocomplete 
documentation: ug
---

#Overview

The PHP AutoComplete control is a textbox control that provides a list of suggestions based on your query. When you enter text into the text box, the control performs a search operation and provides a list of results. There are several filter types available to perform the search.

# Getting Started

Using the following steps, you can create a PHP AutoComplete control. The basic rendering of PHP AutoComplete is achieved with default functionality.

## Create an PHP AutoComplete control

You can create a PHP Project and add necessary scripts and styles with the help of the given PHP Getting Started Documentation.

You can render the PHP Autocomplete control.

{% highlight html %}
    <?php
    $autocomplete=new EJ\AutoComplete('selectCar');
    echo $autocomplete->render();
    ?>

{% endhighlight %}

## Data Binding

The data for the suggestion list can be populated using the dataSource property.

{% highlight html %}
    <?php
    $countries = array('Albania', 'Andorra', 'Armenia', 'Austria', 'Azerbaijan', 'Belarus', 'Belgium',
         'Bosnia & Herzegovina', 'Bulgaria', 'Croatia', 'Cyprus', 'Czech Republic', 'Denmark', 'Estonia',
         'Finland', 'France', 'Georgia', 'Germany', 'Greece', 'Hungary', 'Iceland', 'Ireland', 'Italy',
         'Kosovo', 'Latvia', 'Liechtenstein', 'Lithuania', 'Luxembourg', 'Macedonia', 'Malta', 'Moldova',
         'Monaco', 'Montenegro', 'Netherlands', 'Norway', 'Poland', 'Portugal', 'Romania', 'Russia',
         'San Marino', 'Serbia', 'Slovakia', 'Slovenia', 'Spain', 'Sweden', 'Switzerland', 'Turkey',
         'Ukraine', 'United Kingdom', 'Vatican City');
    $autocomplete=new EJ\AutoComplete('selectCar');
    echo $autocomplete->dataSource($countries)->render();
    ?>

{% endhighlight %}

![](Getting-Started images\datasource.png)

## Enable Popup Button

This button helps you to show all the available suggestions on clicking it.

{% highlight html %}
    <?php
    $countries = array('Albania', 'Andorra', 'Armenia', 'Austria', 'Azerbaijan', 'Belarus', 'Belgium',
         'Bosnia & Herzegovina', 'Bulgaria', 'Croatia', 'Cyprus', 'Czech Republic', 'Denmark', 'Estonia',
         'Finland', 'France', 'Georgia', 'Germany', 'Greece', 'Hungary', 'Iceland', 'Ireland', 'Italy',
         'Kosovo', 'Latvia', 'Liechtenstein', 'Lithuania', 'Luxembourg', 'Macedonia', 'Malta', 'Moldova',
         'Monaco', 'Montenegro', 'Netherlands', 'Norway', 'Poland', 'Portugal', 'Romania', 'Russia',
         'San Marino', 'Serbia', 'Slovakia', 'Slovenia', 'Spain', 'Sweden', 'Switzerland', 'Turkey',
         'Ukraine', 'United Kingdom', 'Vatican City');
    $autocomplete=new EJ\AutoComplete('selectCar');
    echo $autocomplete->dataSource($countries)->showPopupButton(true)->render();
    ?>

{% endhighlight %}

![](Getting-Started images\showPopupButton.png)