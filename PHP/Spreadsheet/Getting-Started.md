---
title: Getting Started for Essential JavaScript Spreadsheet
description: How to create a Spreadsheet with data source, apply format and export it as excel file.
platform: PHP
control: Spreadsheet
documentation: ug
keywords: 
---
# Getting started

This section explains you the steps required to populate the Spreadsheet with data, format, and export it as excel file. This section covers only the minimal features that you need to know to get started with the Spreadsheet.

Create a PHP Project and add necessary scripts and styles with the help of the given PHP [Getting Started](https://help.syncfusion.com/php/getting-started) Documentation.

## Create Spreadsheet

Create a Spreadsheet control by instantiating the PHP wrapper class available in EJ namespace as shown below.

{% highlight html %}

     <?php
        $spreadsheet = new EJ\Spreadsheet("Spreadsheet");
        echo $spreadsheet ->render();
    ?>

{% endhighlight %}

The following screenshot illustrates the output of above code.

![Getting-Started_images/md_img1.png](getting-started_images/md_img1.png) 

## Configuring Spreadsheet

### Populate Spreadsheet with data

Now, this section explains how to populate JSON data to the Spreadsheet. Refer the below code snippet.

{% highlight html %}
//   "the datasource "Data.json" is referred from 'http://php.syncfusion.com/Spreadsheet/Data.json'"
    <?php
      $Json = json_decode(file_get_contents("Data.json"), true);
      $rangeSetting = new EJ\Spreadsheet\RangeSetting();
      $rangeSetting->dataSource($Json);
      $rangeSettings = array($rangeSetting);
      $sheet = new EJ\Spreadsheet\Sheet();
      $sheet->rangeSettings($rangeSettings);
      $sheets = array($sheet);
      $spreadsheet =  new EJ\Spreadsheet('Spreadsheet');
	
      echo $spreadsheet -> sheets($sheets)->render();
    ?>
    
{% endhighlight %}

![Getting-Started_images/md_img2.png](Getting-Started_images/md_img2.png)

N> For more details about `data binding` refer following [`link`](http://help.syncfusion.com/js/spreadsheet/data-binding# "link")

### Apply Conditional Formatting

Conditional formatting helps you to apply formats to a cell or range with certain color based on the cells values. You can use [`allowConditionalFormats`](http://help.syncfusion.com/js/api/ejspreadsheet#members:allowconditionalformats "allowConditionalFormats") property to enable/disable Conditional formats.

To apply conditional formats for a range use [`setCFRule`](http://help.syncfusion.com/js/api/ejspreadsheet#methods:xlcformat-setcfrule "setCFRule") method. The following code example illustrates this,


{% highlight html %}

    <?php
      $Json = json_decode(file_get_contents("Data.json"), true);
      $rangeSetting = new EJ\Spreadsheet\RangeSetting();
      $rangeSetting->dataSource($Json);
      $rangeSettings = array($rangeSetting);
      $sheet = new EJ\Spreadsheet\Sheet();
      $sheet->rangeSettings($rangeSettings);
      $sheets = array($sheet);
      $spreadsheet =  new EJ\Spreadsheet('Spreadsheet');
	                                        
      echo $spreadsheet -> sheets($sheets)->loadComplete('loadComplete')->render();
    ?>
    <script>
    function loadComplete() {                
       this.XLCFormat.setCFRule({ "action": "greaterthan", "inputs": ["10"], "color": "redft", "range": "D3:D8" });
    }
    </script>

{% endhighlight %}

![Getting-Started_images/md_img3.png](Getting-Started_images/md_img3.png)

N> For more details about `Conditional Formatting` refer following [`link`](http://help.syncfusion.com/js/spreadsheet/data-presentation#conditional-formatting "link")

## Export Spreadsheet as Excel File

The Spreadsheet can save its data, style, format into an excel file. To enable save option in Spreadsheet set [`allowExporting`](http://help.syncfusion.com/js/api/ejspreadsheet#members:exportsettings-allowexporting "allowExporting") option in [`exportSettings`](http://help.syncfusion.com/js/api/ejspreadsheet#members:exportsettings "exportSettings") as `true`. Since Spreadsheet uses server side helper to save documents set [`excelUrl`](http://help.syncfusion.com/js/api/ejspreadsheet#members:exportsettings-excelurl "excelUrl") in [`exportSettings`](http://help.syncfusion.com/js/api/ejspreadsheet#members:exportsettings "exportSettings") option. The following code example illustrates this,


{% highlight html %}

    <?php
      $Json = json_decode(file_get_contents("Data.json"), true);
      $rangeSetting = new EJ\Spreadsheet\RangeSetting();
      $rangeSetting->dataSource($Json);
      $rangeSettings = array($rangeSetting);
      $sheet = new EJ\Spreadsheet\Sheet();
      $sheet->rangeSettings($rangeSettings);
      $sheets = array($sheet);
      $spreadsheet =  new EJ\Spreadsheet('Spreadsheet');                  
      $exportSetting = new EJ\Spreadsheet\ExportSetting();
	  $exportSetting->excelUrl('http://js.syncfusion.com/demos/ejservices/api/JSXLExport/ExportToExcel')->csvUrl('http://js.syncfusion.com/demos/ejservices/api/JSXLExport/ExportToCsv')->pdfUrl('http://js.syncfusion.com/demos/ejservices/api/JSXLExport/ExportToPdf');

      echo $spreadsheet -> sheets($sheets)->exportSettings($exportSetting)->render();
    ?>

{% endhighlight %}

Use shortcut [`Ctrl + S`](http://help.syncfusion.com/js/spreadsheet/keyboard-shortcuts# "Ctrl + S") to save Spreadsheet as excel file.


N> 1. For more details about `Export` refer following [`link`](http://help.syncfusion.com/js/spreadsheet/open-and-save#save "link")
N> 2. For more details about `Server Configuration` refer following [`link`](http://help.syncfusion.com/js/spreadsheet/open-and-save#server-configuration "link")
