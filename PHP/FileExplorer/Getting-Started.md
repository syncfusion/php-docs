---
layout: post
title: Getting-Started with FileExplorer
description: getting started
platform: php
control: File Explorer
documentation: ug
---

# Getting Started

To get start with the FileExplorer control using PHP wrapper classes, either of the following prerequisites needs to be installed in your machine to deploy and run those samples locally.

* [PHP tools for Visual Studio](https://visualstudiogallery.msdn.microsoft.com/6eb51f05-ef01-4513-ac83-4c5f50c95fb5)
* [Xampp](https://www.apachefriends.org/download.html)

In this section, let's see how to create, deploy and run the FileExplorer samples using Xampp server.

## Creating a Sample Folder 

Usually, the Xampp gets installed in **C:\\** drive. Now, create a new sample folder namely **FileExplorerPHP** within `C:\\xampp\\htdocs` and place all the below mentioned folders within it.   

* Scripts - Includes all the script files necessary to render the control. [Optional, if cdn links are used in the sample]
* CSS - Includes all the required style sheet files. [Optional, if cdn links are used in the sample] 
* PHP Class Libraries - Includes the individual PHP wrapper class files for all the controls. [Mandatory] 
* Sample PHP file (with .php extension). [Mandatory]
* "FileBrowser" folder content, which is exposed by FileExplorer. [Mandatory]

### Adding Scripts and CSS files

The required scripts and CSS files can be copied into the above created sample folder namely **FileExplorerPHP** and then can be manually referred on the sample page or else the cdn links can be referred directly. In case, if you are manually referring the scripts and CSS files in your PHP sample, refer this [topic](https://help.syncfusion.com/js/control-initialization#manual-reference-of-scripts-and-style-sheets-in-a-html-page) to know how to copy the required scripts and CSS from the installed location.  

### Adding PHP Class libraries

Copy the PHP class libraries into your sample folder, which are the collection of PHP wrapper files created individually for all the controls in order to access and process its server-side values and then send it back to the client-side. These libraries are available within the following installed location.

* **(Installed Location)\\Syncfusion\\Essential Studio\\{{ site.releaseversion }}\\PHP\\Src** 

Copy the files from this location and paste it in following location

* **C:\\xampp\\htdocs\\FileExplorerPHP\\EJ**

### Adding "FileBrowser" folder

Create "**FileBrowser**" folder under **C:\\xampp\\htdocs\\FileExplorerPHP** path and add your necessary files that are need to be exposed by our FileExplorer component.

## Create a PHP file

Create a first PHP file in Xampp and name it appropriately with `.php` extension and also place it under the newly created sample folder **FileExplorerPHP**. For example, say Index.php with the initial code as shown below.

{% highlight html %}

    <!DOCTYPE html>
    <html>
        <head>
            <title>Getting Started - FileExplorer</title>
            <!--Dependency files references-->
        </head>
        <body>
            <?php
            ?>
        </body>
    </html>

{% endhighlight %}

## Scripts and CSS references

Refer the required scripts and CSS files in your PHP page as mentioned below in order to render the FileExplorer control.

{% highlight html %}

    <!DOCTYPE html>
    <html>
        <head>
                <title>Getting Started - FileExplorer</title>
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

Here, the CDN links are used. In case, if the individual scripts are required to render the FileExplorer control, refer [here](/php/FileExplorer/dependencies).

## AutoLoad file reference

Include the PHP AutoLoad file reference within the `body` section of the PHP page.

{% highlight html %}

    <!DOCTYPE html>
    <html>
        <head>
                <title>Getting Started - FileExplorer</title>
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

## Create a FileExplorer

Create the FileExplorer control object by accessing the FileExplorer namespace `EJ\\FileExplorer` using `new` keyword. Define its properties and then output the FileExplorer control by echoing the result object.

{% highlight html %}

        <body>
                <?php                
                $fileexplorer=new EJ\FileExplorer('default');
                echo $fileexplorer
                    ->path('FileExplorerPHP/FileBrowser/')
                    ->ajaxAction('EJ/Services/FileExplorer')
                    ->ajaxDataType('jsonp')
                    ->enableThumbnailCompress(true)
                    ->width('100%')
                    ->isResponsive(true)
                    ->render();
                ?>
        </body>

{% endhighlight %}

N> It is mandatory to define the render() method at last as given in the above syntax, in order to display the FileExplorer on the browser. 

N> Here "**ajaxAction**" property specifies the path of file action handling method and "**path**" property denotes the location of directory, which is exposed by FileExplorer.



## Running the PHP file

The above created sample is now ready to run. Therefore, open the **XAMPP control panel** and start the **Apache** module as shown in the below image

![](Getting-Started_images/Getting-Started_img2.png)

Now, the sample can be run directly on the browser through localhost with appropriate port numbers, on which the Apache server is currently listening. For example, say if the Apache is configured to listen on port 7777, then type http://localhost:7777/ on your browser and press enter. Also, make sure that your sample folder is present within this location `C:\\xampp\\htdocs` as mentioned earlier.

The following FileExplorer output shows up on the browser, when you type http://localhost:7777/FileExplorerPHP/index.php and press enter

![](Getting-Started_images/Getting-Started_img1.png)

N> In case, if you face any problem with default port 80 while running your sample, make the Apache to listen on some other different ports. The port number changes needs to be done on both the `httpd.conf` and `httpd-ssl.conf` files, in order to get rid of this problem.(Refer [here](http://stackoverflow.com/questions/20558410/xampp-port-80-in-use-by-unable-to-open-process-with-pid-4-12)) 

