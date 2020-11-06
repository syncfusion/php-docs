---
layout: post
title: Getting started with Rating 
description: To get start with Rating 
platform: php
control: Rating
documentation: ug
keywords: Rating, rating
---

# Getting Started

This section explains briefly about how to create a **Rating** control in your application with **PHP**. **Rating** helps to select the number of stars that represent Rating. Here, you can learn how to create **Rating** control in a real-time movie download application and also learn how to rate the application.

The following screenshot illustrates the functionality of a Rating widget with a Rating range of 0 to 5. 

![](Getting-Started_images/Getting-Started_img1.png) 

The external script dependencies of the Rating widget is,

* [jQuery 1.7.1](http://jquery.com/) and later versions.

And the internal script dependencies of the Rating widget are:

<table>
	<tr>
		<th>File </th>
		<th>Description / Usage </th>
	</tr>
	<tr>
		<td>ej.core.min.js</td>
		<td>Must be referred always before using all the JS controls.</td>
	</tr>
	<tr>
		<td>ej.rating.min.js</td>
		<td>The rating’s main file</td>
	</tr>
	<tr>
		<td>ej.tooltip.min.js</td>
		<td>Should be referred when using tooltip</td>
	</tr>
</table>

For getting started you can use the ‘ej.web.all.min.js’ file, which encapsulates all the 'ej' controls and frameworks in one single file.<br/> 

For themes, you can use the ‘ej.web.all.min.css’ CDN link from the snippet given. To add the themes in your application, please refer [this link](http://help.syncfusion.com/js/theming-in-essential-javascript-components#adding-specific-theme-to-your-application).


## Preparing HTML document

You can create a PHP Project and add necessary scripts and styles with the help of the given PHP Getting Started Documentation.

Create a first PHP file in Xampp and name it appropriately with `.php` extension and also place it under the newly created sample folder. For example, say Index.php with the initial code as shown below -

Refer the required scripts and CSS files in your PHP page as mentioned below in order to render the Rating control - 

{% highlight html %}

    <!DOCTYPE html>
       <html>
        <head>
                <title>Getting Started - Rating</title>
                <link href="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/flat-azure/ej.web.all.min.css" rel="stylesheet" />
                <link href="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/responsive-css/ej.responsive.css" rel="stylesheet" />
                <script src="http://cdn.syncfusion.com/js/assets/external/jquery-3.0.0.min.js"></script>
                <script src="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/ej.web.all.min.js"></script>
        </head>
        <body>
           <?php require_once 'EJ/AutoLoad.php'; ?>
        </body>
    </html>

{% endhighlight %}

##Create a Rating Widget

The **Rating** widget is provided with built-in features such as precision, orientation and flexible API’s. 

The Rating can be created in **PHP** by using the below given code.

{% highlight html %}
    <?php
		$rating1 =new EJ\Rating('mosRating');
		echo $rating1->value(2)->render();
		?> 

{% endhighlight %}

 Add movies list in the table to render Rating control. Here, you can add corresponding images in the images folder and give the accurate image path.

{% highlight html %}

<div class="content-container-fluid">
        <div class="row">
            <div class="cols-sample-area">
                <div style="width: 500px">
                    <?php	
                        $tab =new EJ\Tab("moviesTab");	
                        $tab->templateStart();
                    ?>	 
                        <ul>
                            <li><a href="#steelman">Man of Steel</a></li>
                            <li><a href="#woldwar">World War Z</a></li>
                            <li><a href="#unive">Monsters University</a></li>
                        </ul>
                        <div id="steelman">
                            <div>
                                <table>
                                    <tr>
                                        <td class="movies-img" valign="top">
                                            <img src="../Content/mos.png" alt="mos" />
                                        </td>
                                        <td valign="top">
                                            <div>
                                                <span class="movie-header">Man of Steel</span><br />
                                                Rating :
                                                        <br />
															<?php
                                                            $rating1 =new EJ\Rating('mosRating');
                                                            echo $rating1->value(2)->render();
                                                            ?> 
                                                <span>Movie Info:</span>
                                                <p>
                                                    A young boy learns that he has extraordinary powers and is not of this Earth.
                                                </p>
                                            </div>
                                        </td>
                                    </tr>
                                </table>
                            </div>
                        </div>
                        <div id="woldwar">
                            <table>
                                <tr>
                                    <td class="movies-img" valign="top">
                                        <img src="../Content/wwz.png" alt="mos" />
                                    </td>
                                    <td valign="top">
                                        <div>
                                            <span class="movie-header">World War Z</span><br />
                                            Rating :
                                                    <br />
														<?php
                                                        $rating1 =new EJ\Rating('wwzRating');
                                                        echo $rating1->value(4)->render();
                                                        ?> 
                                            <span>Movie Info:</span>
                                            <p>
                                                The story revolves around United Nations employee Gerry Lane (Pitt).
                                            </p>
                                        </div>
                                    </td>
                                </tr>
                            </table>
                        </div>
                        <div id="unive">
                            <table>
                                <tr>
                                    <td class="movies-img" valign="top">
                                        <img src="../Content/mu.png" alt="mos" />
                                    </td>
                                    <td valign="top">
                                        <div>
                                            <span class="movie-header">Monsters University</span><br />
                                            Rating :
                                                    <br />
														<?php
                                                        $rating1 =new EJ\Rating('univRating');
                                                        echo $rating1->value(4)->render();
                                                        ?> 
                                            <span>Movie Info:</span>
                                            <p>
                                                Mike Wazowski and James P. Sullivan are an inseparable pair, but that wasn't always the case. 
                                            </p>
                                        </div>
                                    </td>
                                </tr>
                            </table>
                        </div>
                    </div>
                    <?php
                    $tab->templateEnd();
                    echo $tab->width("500px")->render();
                    ?>
                </div>
            </div>
        </div>
    </div>


{% endhighlight %}


 Apply the following styles to show the Rating widget in the horizontal order.

{% highlight css %}

<style type="text/css" class="cssStyles">
    .movies-img {
        width: 125px;
    }
    
    .movie-header {
        font-size: 20px;
        font-weight: 600;
    }
</style>


{% endhighlight %}



 The following screenshot displays a Rating widget.

![](Getting-Started_images/Getting-Started_img2.png) 

##Set the Min and Max Value

In a real-time scenario, you can extend the range by using the properties **minValue** and **maxValue** in the **Rating** widget. 

{% highlight html %}

<body>
<div class="content-container-fluid">
        <div class="row">
            <div class="cols-sample-area">
                <div class="frame">
                    <table>
                        <tr>
                            <td valign="top">Rate:
                            </td>
                            <td>
                                <?php									
                                    require_once '../EJ/AutoLoad.php';						 
                                    $rating1 =new EJ\Rating('fullRating');
                                    echo $rating1->value(4)->minValue(2)->maxValue(10)->render();
                                ?> 
                            </td>
                            </tr>
                    </table>
                </div>
            </div>
        </div>
    </div>
</body>


{% endhighlight %}

The above code example displays the following output.

![](Getting-Started_images/Getting-Started_img3.png)

##Set Precision

In a real-time movie **Rating** scenario, you can set precision in between two whole numbers, such as 2.5 or 3.7 and it is done using the property **precision** by changing the value to **half** or **exact.**

{% highlight html %}

<body>
<?php
    require_once '../EJ/AutoLoad.php';
?> 
<div class="content-container-fluid">
        <div class="row">
            <div class="cols-sample-area">
                <div class="frame">
                    <table>
                        <tr>
                            <td valign="top">Full Precision :
                            </td>
                            <td>
                                <?php							 
                                $rating1 =new EJ\Rating('fullRating');
                                echo $rating1->value(4)->render();
                                ?> 
                            </td>
                        </tr>
                        <tr>
                            <td valign="top">Half Precision :
                            </td>
                            <td>
                               <?php
                                $rating1 =new EJ\Rating('halfRating');
                                echo $rating1->value(3.5)->precision("half")->render();
                                ?> 
                            </td>
                        </tr>
                        <tr>
                            <td valign="top">Exact Precision :
                            </td>
                            <td>
                                <?php
                                $rating1 =new EJ\Rating('exactRating');
                                echo $rating1->value(3.7)->precision("exact")->render();
                                ?> 
                            </td>
                        </tr>
                    </table>
                </div>
            </div>
        </div>
    </div>
    <style type="text/css" class="cssStyles">
        .frame
        {
            width: 277px;
        }
    </style>
</body>


{% endhighlight %}


The above code example displays the following output.

![](Getting-Started_images/Getting-Started_img4.jpeg)

You can also add additional functionalities such as orientation, event tracer and API’s to the **Rating**. 

