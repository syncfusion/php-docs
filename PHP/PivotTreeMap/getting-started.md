---
title: Getting Started for React JS PivotTreeMap
description: How to create a PivotTreeMap with data source.
platform: PHP
control: PivotTreeMap
documentation: ug
keywords: ejpivottreemap, pivottreemap, php pivottreemap
---

# Getting Started

This section explains you the steps required to populate the PivotTreeMap in your application with **PHP** wrapper classes of EJ controls. This section covers only the minimal features that you need to know to get started with the PivotTreeMap.

## Create PivotTreeMap widget

You can create a PHP Project and add necessary scripts and styles with the help of the given PHP Getting Started Documentation.

Create a first PHP file in Xampp and name it appropriately with `.php` extension and also place it under the newly created sample folder. For example, say Index.php with the initial code as shown below -

Refer the required scripts and CSS files in your PHP page as mentioned below in order to render the PivotTreeMap control - 

{% highlight html %}

<!DOCTYPE html>
<html>
	<head>
			<title>Getting Started - PivotTreeMap</title>
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

Add the following code example to add list of items to the **PivotTreeMap** and initialize the **PivotTreeMap** widget with OLAP data source.

{% highlight html %}

<?php
$row = new EJ\PivotTreeMap\Row();
$row=array($row->fieldName('[Date].[Fiscal]'));
$column = new EJ\PivotTreeMap\Column();
$column=array($column->fieldName('[Customer].[Customer Geography]'));
$value = new EJ\PivotTreeMap\Value();
$field = new EJ\PivotTreeMap\Measure();
$value=array($value->measures(array($field->fieldName('[Measures].[Internet Sales Amount]')))->axis('columns'));

$pivottreemap=  new EJ\PivotTreeMap('PivotTreeMap1');
$datasource = new EJ\PivotTreeMap\DataSource();
$datasource->data('//bi.syncfusion.com/olap/msmdpump.dll')->catalog('Adventure Works DW 2008 SE')->cube('Adventure Works')->rows($row)->columns($column)->values($value);
echo $pivottreemap->dataSource($datasource)->render();
?>
</div>
<script id='tooltipTemplate' type='application/jsrender'>
		<div style='background:White; color:black; font-size:12px; font-weight:normal; border: 1px solid #4D4D4D; white-space: nowrap;border-radius: 2px; margin-right: 25px; min-width: 110px;padding-right: 5px; padding-left: 5px; padding-bottom: 2px ;width: auto; height: auto;'>
				<div>Measure(s) : {{:~Measures(#data)}}</div><div>Row : {{:~Row(#data)}}</div><div>Column : {{:~Column(#data)}}</div><div>Value : {{:~Value(#data)}}</div>
		</div>
</script> 

{% endhighlight %}

The above code will generate a simple PivotTreeMap with internet sales amount over a period of fiscal years across different customer geographic locations.

![](getting-started_images/Olap.png)
