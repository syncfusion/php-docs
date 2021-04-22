---
title: Getting started with PHP Barcode Control | Syncfusion
description: Learn here about getting started with Syncfusion Essential Studio PHP Barcode Control, its elements, and more.
platform: php
control: Barcode
documentation: ug
keywords: ejBarcode, Barcode
---

# Getting started with PHP Barcode

The Syncfusion Essential JS Barcode widget enables rendering of one dimension and two dimension barcodes in web page. Barcode provides you a simple and inexpensive method of encoding text information that can be easily read by electronic readers.

**Key Features**

* Supports 10 one-dimensional barcodes including Code 39 and Code 32 barcodes.
* Supports 2 two-dimensional barcodes such as QR and Data Matrix barcodes.

## Getting Started

This section explains briefly about how to create a **Barcode** control in your application with **PHP** wrapper classes of EJ controls.

## Create your first Barcode in PHP

1.Create an HTML file and add the following necessary scripts and CSS files to the HTML file.

{% highlight html %}

    <!DOCTYPE html>
    <html xmlns="http://www.w3.org/1999/xhtml">
        <head>
            <meta name="viewport"content="width=device-width, initial-scale=1.0"/>
            <meta charset="utf-8" />
            <link href=" http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/flat-azure/ej.web.all.min.css" rel="stylesheet"/>
            <script src="http://cdn.syncfusion.com/js/assets/external/jquery-1.10.2.min.js"></script>
            <script src="http://cdn.syncfusion.com/js/assets/external/jsrender.min.js"></script>
            <script src="http://cdn.syncfusion.com/js/assets/external/jquery.globalize.min.js"></script>
            <script src="http://cdn.syncfusion.com/js/assets/external/jquery.easing.1.3.min.js"></script>
            <script src="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/ej.web.all.min.js" type="text/javascript"></script>
        </head>
        <body>
        <!--Add Barcode control here -->
        </body>
    </html>

{% endhighlight %}

2.Render the PHP **Barcode** control as show below.

{% highlight js %}

<body>
    <?php
        $barcode = new EJ\Barcode("Barcode");
        echo $barcode->symbologyType('qrbarcode')->text('http://www.syncfusion.com')->render();
    ?>
</body>
{% endhighlight %}

The following screenshot illustrates the output of the above code example.

![PHP Barcode Getting Started Image](getting-started-images/default.png)
