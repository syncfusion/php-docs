---
layout: post
title: Getting started with Syncfusion Essential HeatMap for PHP
description: Getting started walk through to create your first Heat map.
platform: PHP
control: ejHeatMap
keywords: HeatMap, PHP heatmap, Populating data
---

# Getting Started

To get start with the HeatMap control using PHP wrapper classes, either of the following prerequisites needs to be installed in your machine to deploy and run those samples locally.

* [PHP tools for Visual Studio](https://visualstudiogallery.msdn.microsoft.com/6eb51f05-ef01-4513-ac83-4c5f50c95fb5)
* [Xampp](https://www.apachefriends.org/download.html)

In this section, let's see how to get started of the HeatMap component for PHP using Xampp server.

## Creating a Sample Folder 

Usually, the Xampp gets installed in **C:\\** drive. Now, create a new sample folder namely **HeatMap** within `C:\\xampp\\htdocs` and place all the below mentioned folders within it.   

* Scripts - Includes all the script files necessary to render the control. [Optional, if cdn links are used in the sample]
* CSS - Includes all the required stylesheet files. [Optional, if cdn links are used in the sample] 
* PHP Class Libraries - Includes the individual PHP wrapper class files for all the controls. [Mandatory] 
* Sample PHP file (with .php extension). [Mandatory]

### Adding Scripts and CSS files

The required scripts and CSS files can be copied into the above created sample folder namely **HeatMap** and then can be manually referred on the sample page or else the cdn links can be referred directly. In case, if you are manually referring the scripts and CSS files in your PHP sample, refer this [topic](https://help.syncfusion.com/js/control-initialization#manual-reference-of-scripts-and-style-sheets-in-a-html-page) to know how to copy the required scripts and CSS from the installed location.  

### Adding PHP Class libraries

Copy the PHP class libraries into your sample folder, which are the collection of PHP wrapper files created individually for all the controls in order to access and process its server-side values and then send it back to the client-side. These libraries are available within the following installed location - 

* **(Installed Location)\\Syncfusion\\Essential Studio\\{{ site.releaseversion }}\\PHP\\Src** 
## Create a PHP file

Create a first PHP file in Xampp and name it appropriately with `.php` extension and also place it under the newly created sample folder **HeatMap**. For example, say Index.php with the initial code as shown below -

{% highlight html %}

    <!DOCTYPE html>
    <html>
        <head>
            <title>Getting Started - HeatMap</title>
            <!--Dependency files references-->
        </head>
        <body>
            <?php
            ?>
        </body>
    </html>

{% endhighlight %}

## Scripts and CSS references

Refer the required scripts and CSS files in your PHP page as mentioned below in order to render the HeatMap control - 

{% highlight html %}

    <!DOCTYPE html>
    <html>
        <head>
                <title>Getting Started - HeatMap</title>
                <link href="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/flat-azure/ej.web.all.min.css" rel="stylesheet" />
                <link href="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/responsive-css/ej.responsive.css" rel="stylesheet" />
                <script src="http://cdn.syncfusion.com/js/assets/external/jquery-3.0.0.min.js"></script>
                <script src="http://cdn.syncfusion.com/js/assets/external/jsrender.min.js"></script>
                <script src="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/ej.web.all.min.js"></script>
        </head>
        <body>
            <?php
            ?>
        </body>
    </html>

{% endhighlight %}

## AutoLoad file reference

Include the PHP AutoLoad file reference within the `body` section of the PHP page.

{% highlight html %}

    <!DOCTYPE html>
    <html>
        <head>
                <title>Getting Started - HeatMap</title>
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

### Initialize HeatMap

Create the HeatMap control object by accessing the HeatMap namespace `EJ\\HeatMap` using `new` keyword. Define its properties and then output the HeatMap control by echoing the result object.

### Prepare and Populate data

Populate product information in a collection called `ItemsSource`.

### Map data into HeatMap

Now data is ready, next we need to configure data source and map rows and columns to visualize. For that, need to prepare `ItemsMapping` add it in resource and set items source and mapping.
Next we can configure color range for these values using color mapping and also configure items mapping based on items source.
 
{% highlight javascript %}
<body>
<?php
    require_once 'EJ\AutoLoad.php';
    $heatmap=new EJ\HeatMap("HeatMap1");

        $colorMap1=new EJ\HeatMap\ColorMappingCollection();
        $label1=new EJ\HeatMap\Label();
        $label1->text("0");
        $colorMap1->color("#8ec8f8")->value(0)->label($label1);

        $colorMap2=new EJ\HeatMap\ColorMappingCollection();
        $label2=new EJ\HeatMap\Label();
        $label2->text("100");
        $colorMap2->color("#0d47a1")->value(100)->label($label2);


        $columns = array("Vegie-spread", "Tofuaa", "Alice Mutton", "Konbu", "Fløtemysost", "Perth Pasties", "Boston Crab Meat", "Raclette Courdavault");
        $itemSource = array();
        for ($i = 0; $i < count($columns); $i++)
        {
        for ($j = 0; $j < 8; $j++)
        {
        $value1 = rand(0,100);
        $itemObj=new ItemSourceClass();
        array_push($itemSource, $itemObj->ProductName($columns[$i])->Year("Y".(2011+$j))->Value($value1));
        }
        }

        $column=new EJ\HeatMap\Column();
        $column->displayName("Product Name")->propertyName("ProductName");

        $row= new EJ\HeatMap\Row();
        $row->displayName("Year")->propertyName("Year");

        $value= new EJ\HeatMap\Value();
        $value->propertyName("Value");

        $columnMapping0=new EJ\HeatMap\Column();
        $columnMapping0->displayName( $columns[0])->propertyName($columns[0]);
        $columnMapping1=new EJ\HeatMap\Column();
        $columnMapping1->displayName( $columns[1])->propertyName($columns[1]);
        $columnMapping2=new EJ\HeatMap\Column();
        $columnMapping2->displayName( $columns[2])->propertyName($columns[2]);
        $columnMapping3=new EJ\HeatMap\Column();
        $columnMapping3->displayName( $columns[3])->propertyName($columns[3]);
        $columnMapping4=new EJ\HeatMap\Column();
        $columnMapping4->displayName( $columns[4])->propertyName($columns[4]);
        $columnMapping5=new EJ\HeatMap\Column();
        $columnMapping5->displayName( $columns[5])->propertyName($columns[5]);
        $columnMapping6=new EJ\HeatMap\Column(); 
        $columnMapping6->displayName( $columns[6])->propertyName($columns[6]);
        $columnMapping7=new EJ\HeatMap\Column();
        $columnMapping7->displayName( $columns[7])->propertyName($columns[7]);
        $columnMapping8=new EJ\HeatMap\Column();

        $headerMapping=new EJ\HeatMap\HeaderMapping();
        $columnStyle=new EJ\HeatMap\ColumnStyle();
        $columnStyle->width(105)->textAlign("right");
        $headerMapping->propertyName("Year")->displayName("Year")->columnStyle($columnStyle);


        $itemsMapping= new EJ\HeatMap\ItemsMapping();
        $itemsMapping->column($column)->row($row)->value($value)->columnMapping(array($columnMapping0,$columnMapping1,$columnMapping2))->headerMapping($headerMapping);

        echo $heatmap->width("810")->colorMappingCollection(array($colorMap1,$colorMap2))->itemsMapping($itemsMapping)->itemsSource($itemSource)->isResponsive(true)->render();

        class ItemSourceClass{
        public function ProductName ($value){
        $this -> ProductName = $value;
        return $this;
        }
        public function Year ($value){
        $this -> Year = $value;
        return $this;
        }
        public function Value ($value){
        $this -> Value = $value;
        return $this;
        }
        }

{% endhighlight %}

![](Getting-Started_images/Getting-Started_img1.png)

### Initialize Legend

A legend control is used to represent range value in a gradient, create a legend with the same color mapping as shown below.
 
{% highlight javascript %}
<?php
    $heatmaplegnd =new EJ\HeatMapLegend("heatmap_legend");
        $colorMap1=new EJ\HeatMap\ColorMappingCollection();
        $label1=new EJ\HeatMap\Label();
        $label1->text("0");
        $colorMap1->color("#8ec8f8")->value(0)->label($label1);
        
        $colorMap2=new EJ\HeatMap\ColorMappingCollection();
        $label2=new EJ\HeatMap\Label();
        $label2->text("100");
        $colorMap2->color("#0d47a1")->value(3)->label($label2); 

        echo $heatmaplegnd->width("75%")->height("50px")->colorMappingCollection(array($colorMap1,$colorMap2))->isResponsive(true)->render();

            ?>
{% endhighlight %}

![](Getting-Started_images/Getting-Started_img2.png)