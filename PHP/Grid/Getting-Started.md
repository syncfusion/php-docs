---
layout: post
title: Getting started with Grid widget for Syncfusion Essential PHP
description: How to create the Grid, data bind, enable paging, grouping, filtering and add summaries
platform: php
control: Grid
documentation: ug
---
# Getting started

This section explains briefly about how to create a Grid in your application with PHP, and also explains about how to enable basic grid operations like Paging, Filtering, Grouping and Summary. The following screenshot illustrates the Grid control.

![](Getting-Started_images/grid.png)

## Adding JavaScript and CSS references

The grid control has the following list of external JavaScript dependencies.

* [jQuery](http://jquery.com/# "") 1.7.1 and later versions
* [jsRender](https://github.com/borismoore/jsrender# "") - to render the templates

To get started, you can use the `ej.web.all.min.js` file that encapsulates all the Syncfusion controls and frameworks in one single file. So the complete boilerplate code is

{% highlight html %}
<!-- Essential Studio for JavaScript theme reference -->

<link rel="stylesheet" href="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/flat-azure/ej.web.all.min.css" />

<!-- Essential Studio for JavaScript script references -->

<script src="https://code.jquery.com/jquery-1.10.2.min.js"></script>

<script src="http://cdn.syncfusion.com/js/assets/external/jsrender.min.js"></script>

<script src="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/ej.web.all.min.js"> </script>

<!-- Add your custom scripts here -->

{% endhighlight %}

For themes, you can use the `ej.web.all.min.css` CDN link from the code example given. To add the themes in your application, please refer to [this link](http://help.syncfusion.com/js/theming-in-essential-javascript-components# "").

## Create Grid

Create a Grid control by instantiating the PHP wrapper class available in EJ namespace as shown below.

{% highlight php %}
<?php

require_once '..\EJ\AutoLoad.php';

?>

<div class="cols-sample-area">

<?php
/* the datasource is referred from Data.json */

$Json = json_decode(file_get_contents("Data.json"), true);

$col1 = new EJ\Grid\Column();

$col1->field("OrderID")->headerText("OrderID")->textAlign("right")->width(100);

$col2 = new EJ\Grid\Column();

$col2->field("CustomerID")->headerText("CustomerID")->width(70);

$col3 = new EJ\Grid\Column();

$col3->field("EmployeeID")->headerText("EmployeeID")->textAlign("right")->width(70);

$col4 = new EJ\Grid\Column();

$col4->field("ShipCountry")->headerText("ShipCountry")->width(70);

$col5 = new EJ\Grid\Column();

$col5->field("Freight")->headerText("Freight")->textAlign("right")->format("{0:C}")->width(70);

$gridColumns = array($col1,$col2,$col3,$col4,$col5);

$grid =  new EJ\Grid("Grid");

$column=new EJ\Grid\Column();

echo $grid -> dataSource($Json)->allowPaging(true)->columns($gridColumns)->render();

?>

</div>

{% endhighlight %}

![](Getting-Started_images/Grid_GettingStarted_img1.png)

## Data Binding

Data binding in the grid is achieved by assigning an array of objects to the `dataSource`property. Refer to the following code example.

{% highlight php %}
<?php

require_once '..\EJ\AutoLoad.php';

?>

<div class="cols-sample-area">

<?php
/* the datasource is referred from Data.json */
$Json = json_decode(file_get_contents("Data.json"), true);

$col1 = new EJ\Grid\Column();

$col1->field("OrderID")->headerText("OrderID")->textAlign("right")->width(100);

$col2 = new EJ\Grid\Column();

$col2->field("CustomerID")->headerText("CustomerID")->width(70);

$col3 = new EJ\Grid\Column();

$col3->field("EmployeeID")->headerText("EmployeeID")->textAlign("right")->width(70);

$col4 = new EJ\Grid\Column();

$col4->field("ShipCountry")->headerText("ShipCountry")->width(70);

$col5 = new EJ\Grid\Column();

$col5->field("Freight")->headerText("Freight")->textAlign("right")->format("{0:C}")->width(70);

$gridColumns = array($col1,$col2,$col3,$col4,$col5);

$dataManager  = new EJ\DataManager(); 

$dataManager->url('//mvc.syncfusion.com/Services/Northwnd.svc/Orders/')->offline(false);

$grid =  new EJ\Grid("Grid");

echo $grid -> dataSource( $Json)->columns($gridColumns)->allowPaging(true)->render();

?>

</div>



{% endhighlight %}

![](Getting-Started_images/Grid_GettingStarted_img2.png)

## Enable Filtering

Filtering can be enabled by setting the `allowFiltering` to true. By default, the filter bar row is displayed to perform filtering, you can change the filter type by using the `filterSettings.filterType` attribute.

{% highlight php %}
<?php

require_once '..\EJ\AutoLoad.php';

?>

<div class="cols-sample-area">

<?php
/* the datasource is referred from Data.json */
$Json = json_decode(file_get_contents("Data.json"), true);

$col1 = new EJ\Grid\Column();

$col1->field("OrderID")->headerText("OrderID")->textAlign("right")->width(100);

$col2 = new EJ\Grid\Column();

$col2->field("CustomerID")->headerText("CustomerID")->width(70);

$col3 = new EJ\Grid\Column();

$col3->field("EmployeeID")->headerText("EmployeeID")->textAlign("right")->width(70);

$col4 = new EJ\Grid\Column();

$col4->field("ShipCountry")->headerText("ShipCountry")->width(70);

$col5 = new EJ\Grid\Column();

$col5->field("Freight")->headerText("Freight")->textAlign("right")->format("{0:C}")->width(70);

$gridColumns = array($col1,$col2,$col3,$col4,$col5);

$grid =  new EJ\Grid("Grid");

$filter =new EJ\Grid\FilterSetting();

$grid =  new EJ\Grid("Grid");

echo $grid -> dataSource( $Json)->columns($gridColumns)->allowFiltering(true)->filterSettings($filter->filterType("excel"))->render();

?>

</div>



{% endhighlight %}

![](Getting-Started_images/Grid_GettingStarted_img3.png)


## Enable Grouping

Grouping can be enabled by setting the `allowGrouping` to true. Columns can be grouped dynamically by drag and drop the grid column header to the group drop area.

{% highlight php %}
<?php

require_once '..\EJ\AutoLoad.php';

?>

<div class="cols-sample-area">

<?php


/* the datasource is referred from Data.json */
$Json = json_decode(file_get_contents("Data.json"), true);

$col1 = new EJ\Grid\Column();

$col1->field("OrderID")->headerText("OrderID")->textAlign("right")->width(100);

$col2 = new EJ\Grid\Column();

$col2->field("CustomerID")->headerText("CustomerID")->width(70);

$col3 = new EJ\Grid\Column();

$col3->field("EmployeeID")->headerText("EmployeeID")->textAlign("right")->width(70);

$col4 = new EJ\Grid\Column();

$col4->field("ShipCountry")->headerText("ShipCountry")->width(70);

$col5 = new EJ\Grid\Column();

$col5->field("Freight")->headerText("Freight")->textAlign("right")->format("{0:C}")->width(70);

$gridColumns = array($col1,$col2,$col3,$col4,$col5);

$grid =  new EJ\Grid("Grid");

$column=new EJ\Grid\Column();

echo $grid -> dataSource($Json)->allowPaging(true)->allowGrouping(true)->columns($gridColumns)->render();

?>

</div>



{% endhighlight %}

![](Getting-Started_images/Grid_GettingStarted_img4.png)


Refer to the following code example for initial grouping.

{% highlight php %}
<?php

require_once '..\EJ\AutoLoad.php';

?>

<div class="cols-sample-area">

<?php


/* the datasource is referred from Data.json */
$Json = json_decode(file_get_contents("Data.json"), true);

$col1 = new EJ\Grid\Column();

$col1->field("OrderID")->headerText("OrderID")->textAlign("right")->width(100);

$col2 = new EJ\Grid\Column();

$col2->field("CustomerID")->headerText("CustomerID")->width(70);

$col3 = new EJ\Grid\Column();

$col3->field("EmployeeID")->headerText("EmployeeID")->textAlign("right")->width(70);

$col4 = new EJ\Grid\Column();

$col4->field("ShipCountry")->headerText("ShipCountry")->width(70);

$col5 = new EJ\Grid\Column();

$col5->field("Freight")->headerText("Freight")->textAlign("right")->format("{0:C}")->width(70);

$gridColumns = array($col1,$col2,$col3,$col4,$col5);

$groupColumns=array("CustomerID")

$grid =  new EJ\Grid("Grid");

$column=new EJ\Grid\Column();

echo $grid -> dataSource($Json)->allowPaging(true)->allowGrouping(true)->columns($gridColumns)->groupedColumns($groupColumns)->render();

?>

</div>



{% endhighlight %}

![](Getting-Started_images/Grid_GettingStarted_img5.png)


## Add Summaries

Summaries can be added by setting the `showSummary` to true and adding required summary rows and columns in the `summaryRows` property. For demonstration, Freight column’s sum value is displayed as summary.

{% highlight php %}
<?php

require_once '..\EJ\AutoLoad.php';

?>

<div class="cols-sample-area">

<?php

/* the datasource is referred from Data.json */

$Json = json_decode(file_get_contents("Data.json"), true);

$grid =  new EJ\Grid("Grid");

$summaryrow=new EJ\Grid\SummaryRow();

$summarycol=new EJ\Grid\SummaryColumn();

$disaplayname="Freight";

$summaryType="sum";

$datamember="Freight";

$title="Sum";

$col1 = new EJ\Grid\Column();

$col1->field("OrderID")->headerText("OrderID")->textAlign("right")->width(100);

$col2 = new EJ\Grid\Column();

$col2->field("CustomerID")->headerText("CustomerID")->width(70);

$col3 = new EJ\Grid\Column();

$col3->field("EmployeeID")->headerText("EmployeeID")->textAlign("right")->width(70);

$col4 = new EJ\Grid\Column();

$col4->field("ShipCountry")->headerText("ShipCountry")->width(70);

$col5 = new EJ\Grid\Column();

$col5->field("Freight")->headerText("Freight")->textAlign("right")->format("{0:C}")->width(70);

$gridColumns = array($col1,$col2,$col3,$col4,$col5);

$sumcol1=$summarycol->format("{0:c}")->summaryType($summaryType)->dataMember($datamember)->displayColumn($disaplayname);

$summaryColumns=array($sumcol1);

$summaryrow->summaryColumns($summaryColumns)->title($title);

$sumrow1=array($summaryrow);

echo $grid -> dataSource( $Json)->allowPaging(true)->columns($gridColumns)->summaryRows($sumrow1)->showSummary(true)->render();

?>

</div>



{% endhighlight %}

![](Getting-Started_images/Grid_GettingStarted_img6.png)


## Enable Editing

We can edit the grid row by double clicking row or by selecting the required row and clicking on edit icon in a toolbar. Similarly, you can add new record to grid by clicking on insert icon in toolbar. Save and Cancel while on edit mode is possible using respective toolbar icon in grid. Deletion of the record is possible by selecting the required row and clicking on Delete icon in toolbar.

We can enable editing property via `editSettings` property by enabling the required operation like `allowAdding`, `allowDeleting`, `allowEditing`.

We can add `toolbarItems` via `toolbarSettings` by setting the `showToolbar` as a `true`. we can also include required items which wants to displayed in toolbar like `add`, `edit`, `delete`,`update` and `cancel` . 

{% highlight php %}
<?php

require_once '..\EJ\AutoLoad.php';

?>

<div class="cols-sample-area">

<?php

/* the datasource is referred from Data.json */
$Json = json_decode(file_get_contents("Data.json"), true);

$col1 = new EJ\Grid\Column();

$col1->field("OrderID")->headerText("OrderID")->textAlign("right")->isPrimaryKey(true)->width(100);

$col2 = new EJ\Grid\Column();

$col2->field("CustomerID")->headerText("CustomerID")->width(70);

$col3 = new EJ\Grid\Column();

$col3->field("EmployeeID")->headerText("EmployeeID")->textAlign("right")->width(70);

$col4 = new EJ\Grid\Column();

$col4->field("ShipCountry")->headerText("ShipCountry")->width(70);

$col5 = new EJ\Grid\Column();

$col5->field("Freight")->headerText("Freight")->textAlign("right")->format("{0:C}")->width(70);

$gridColumns = array($col1,$col2,$col3,$col4,$col5);

$grid =  new EJ\Grid("Grid");

$edit =new EJ\Grid\EditSetting();

$toolbarItems = array("add","edit","delete","update","cancel");

$toolbar= new EJ\Grid\ToolbarSetting();

echo $grid -> dataSource($Json)->allowPaging(true)->columns($gridColumns)->editSettings($edit->allowEditing(true)->allowDeleting(true)->allowAdding(true))->toolbarSettings($toolbar->showToolbar(true)->toolbarItems($toolbarItems))->render();

?>

</div>



{% endhighlight %}

![](Getting-Started_images/Grid_GettingStarted_img7.png)


## Enable Selection

By default, we have enabled selection for grid rows. We can enable the multi row selection by setting the `selectionType` as `multiple`.

{% highlight php %}
<?php

require_once '..\EJ\AutoLoad.php';

?>

<div class='cols-sample-area'>

<?php

/* the datasource is referred from Data.json */

$Json = json_decode(file_get_contents('Data.json'), true);

$grid =  new EJ\Grid('Grid');

$col1 = new EJ\Grid\Column();

$col1->field('OrderID')->headerText('OrderID')->textAlign('right')->width(100);

$col2 = new EJ\Grid\Column();

$col2->field('CustomerID')->headerText('CustomerID')->width(70);

$col3 = new EJ\Grid\Column();

$col3->field('EmployeeID')->headerText('EmployeeID')->textAlign('right')->width(70);

$col4 = new EJ\Grid\Column();

$col4->field('ShipCountry')->headerText('ShipCountry')->width(70);

$col5 = new EJ\Grid\Column();

$col5->field('Freight')->headerText('Freight')->textAlign('right')->format('{0:C}')->width(70);

$gridColumns = array($col1,$col2,$col3,$col4,$col5);

$selection = new EJ\Grid\SelectionSetting();

echo $grid -> dataSource($Json)->columns($gridColumns)->allowPaging(true)->selectionSettings($selection)->selectionType('multiple')->render();

?>

</div>



{% endhighlight %}

![](Getting-Started_images/Grid_GettingStarted_img10.png)


## Enable Sorting

Sorting can be enabled by setting the `allowSorting` as true

{% highlight php %}
<?php

require_once '..\EJ\AutoLoad.php';

?>

<div class='cols-sample-area'>

<?php


/* the datasource is referred from Data.json */
$Json = json_decode(file_get_contents('Data.json'), true);

$grid =  new EJ\Grid('Grid');

$col1 = new EJ\Grid\Column();

$col1->field('OrderID')->headerText('OrderID')->textAlign('right')->width(100);

$col2 = new EJ\Grid\Column();

$col2->field('CustomerID')->headerText('CustomerID')->width(70);

$col3 = new EJ\Grid\Column();

$col3->field('EmployeeID')->headerText('EmployeeID')->textAlign('right')->width(70);

$col4 = new EJ\Grid\Column();

$col4->field('ShipCountry')->headerText('ShipCountry')->width(70);

$col5 = new EJ\Grid\Column();

$col5->field('Freight')->headerText('Freight')->textAlign('right')->format('{0:C}')->width(70);

$gridColumns = array($col1,$col2,$col3,$col4,$col5);

echo $grid -> dataSource($Json)->allowPaging(true)->columns($gridColumns)->allowSorting(true)->render();

?>

​

</div>



{% endhighlight %}

![](Getting-Started_images/Grid_GettingStarted_img11.png)


