---
title: Getting started with Schedule component	
description: Rendering a basic Scheduler with local data
platform: php
control: schedule
documentation: ug
keywords: ejschedule, schedule, schedule widget, js schedule 
---

# Getting Started

To get start with the Schedule control using PHP wrapper classes, either of the following prerequisites needs to be installed in your machine to deploy and run those samples locally.

* [PHP tools for Visual Studio](https://visualstudiogallery.msdn.microsoft.com/6eb51f05-ef01-4513-ac83-4c5f50c95fb5)
* [XAMPP](https://www.apachefriends.org/download.html)

In this section, let's see how to create, deploy and run the Scheduler samples using XAMPP server.

## Creating a Sample Folder

Usually, the XAMPP gets installed in **C:\\** drive. Now, create a new sample folder namely **ScheduleTutorial** within `C:\\xampp\\htdocs` and place all the below mentioned folders within it.

* Scripts - Includes all the script files necessary to render the control. [Optional, if cdn links are used in the sample]
* CSS - Includes all the required stylesheet files. [Optional, if cdn links are used in the sample]
* PHP Class Libraries - Includes the individual PHP wrapper class files for all the controls. [Mandatory]
* Sample PHP file (with .php extension). [Mandatory]

### Adding Scripts and CSS files

The required scripts and CSS files can be copied into the above created sample folder namely **ScheduleTutorial** and then can be manually referred on the sample page or else the CDN links can be referred directly. In case, if you are manually referring the scripts and CSS files in your PHP sample, refer this [topic](https://help.syncfusion.com/js/control-initialization#manual-reference-of-scripts-and-style-sheets-in-a-html-page) to know how to copy the required scripts and CSS from the installed location.

### Adding PHP Class libraries

Copy the PHP class libraries into your sample folder, which are the collection of PHP wrapper files created individually for all the controls in order to access and process its server-side values and then send it back to the client-side. These libraries are available within the following installed location -

* **(Installed Location)\\Syncfusion\\Essential Studio\\{{ site.releaseversion }}\\PHP\\Src**

## Create a PHP file

Create a first PHP file in XAMPP and name it appropriately with `.php` extension and also place it under the newly created sample folder **ScheduleTutorial**. For example, say Index.php with the initial code as shown below -

{% highlight html %}

    <!DOCTYPE html>
    <html>
        <head>
            <title>Getting Started - Schedule</title>
            <!--Dependency files references-->
        </head>
        <body>
            <?php
            ?>
        </body>
    </html>

{% endhighlight %}

## Scripts and CSS references

Refer the required scripts and CSS files in your PHP page as mentioned below in order to render the Scheduler control -

{% highlight html %}

    <!DOCTYPE html>
    <html>
        <head>
                <title>Getting Started - Schedule</title>
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

Here, the CDN links are used. In case, if the individual scripts are required to render the Schedule control, refer [here](/php/schedule/dependencies).

## AutoLoad file reference

Include the PHP AutoLoad file reference within the `body` section of the PHP page.

{% highlight html %}

    <!DOCTYPE html>
    <html>
        <head>
                <title>Getting Started - Schedule</title>
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

## Control Initialization

Create the Schedule control object by accessing the Schedule namespace `EJ\\Schedule` using `new` keyword. Define its properties and then output the Schedule control by echoing the result object.

{% highlight html %}

<body>
<?php
    require_once 'EJ\AutoLoad.php';
    $schedule = new EJ\Schedule("defaultSchedule");
    echo $schedule  -> width("100%") ->render();
?>
</body>

{% endhighlight %}

N> It is mandatory to define the render() method at last as given in the above syntax, in order to display the Scheduler on the browser.

## Binding Appointment data

To add appointments to the Scheduler, the **dataSource** property of the Scheduler needs to be set. It can be assigned either with the instance of `ejDataManger` or PHP array collection.

For demo purpose, local data source is used here and the code example is as follows.

{% highlight html %}

<?php
    require_once 'EJ\AutoLoad.php';
    $data = array(
       array(
          'Id' => 1,
          'Subject' => 'Music Class',
          'StartTime' => new DateTime('2016/5/5 12:00'),
          'EndTime' => new DateTime('2016/5/5 14:30')
      ),
      array(
          'Id' => 2,
          'Subject' => "Bering Sea Gold",
          'StartTime' => new DateTime('2016/5/5 04:00'),
          'EndTime' => new DateTime('2016/5/5 05:30'),
          'AllDay' => false
      )
      );
    $appointment= new EJ\Schedule\AppointmentSetting();
    $appointment ->dataSource($data);

    $schedule = new EJ\Schedule("defaultSchedule");
    echo $schedule -> width("100%") ->height("525px")->currentDate(new DateTime('2016/5/4')) ->appointmentSettings($appointment) ->render();
?>

{% endhighlight %}

## Adding Mapper fields

The appointment fields are needed to be mapped with the appropriate column names from the dataSource as shown below.

{% highlight html %}

    <!DOCTYPE html>
    <html>
        <head>
                <title>Getting Started - Schedule</title>
                <link href="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/flat-azure/ej.web.all.min.css" rel="stylesheet" />
                <link href="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/responsive-css/ej.responsive.css" rel="stylesheet" />
                <script src="http://cdn.syncfusion.com/js/assets/external/jquery-3.0.0.min.js"></script>
                <script src="http://cdn.syncfusion.com/js/assets/external/jsrender.min.js"></script>
                <script src="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/ej.web.all.min.js"></script>
        </head>
        <body>
            <?php
                require_once 'EJ\AutoLoad.php';
                $data = array(
                    array(
                        'Id' => 1,
                        'Subject' => 'Music Class',
                        'StartTime' => new DateTime('2016/5/5 12:00'),
                        'EndTime' => new DateTime('2016/5/5 14:30')
                    ),
                    array(
                        'Id' => 2,
                        'Subject' => "Bering Sea Gold",
                        'StartTime' => new DateTime('2016/5/5 04:00'),
                        'EndTime' => new DateTime('2016/5/5 05:30'),
                        'AllDay' => false
                    )
                );
                $appointment= new EJ\Schedule\AppointmentSetting();
                $appointment ->dataSource($data)->id("Id") ->startTime("StartTime")->endTime("EndTime")->subject("Subject")->description("Description")->allDay("AllDay")->recurrence("Recurrence")->recurrenceRule("RecurrenceRule");

                $schedule = new EJ\Schedule("defaultSchedule");
                echo $schedule -> width("100%") ->height("525px")->currentDate(new DateTime('2016/5/4')) ->appointmentSettings($appointment) ->render();
            ?>
        </body>
    </html>

{% endhighlight %}

## Running the PHP file

The above created sample is now ready to run. Therefore, open the **XAMPP control panel** and start the **Apache** module as shown in the below image -

![](/php/schedule/getting-started_images/xampp-controlpanel.png)

Now, the sample can be run directly on the browser through localhost with appropriate port numbers, on which the Apache server is currently listening. For example, say if the Apache is configured to listen on port 8080, then type `http://localhost:8080/` on your browser and press enter. Also, make sure that your sample folder is present within this location `C:\\xampp\\htdocs` as mentioned earlier.

The following Scheduler output shows up on the browser, when you type `http://localhost:8080/ScheduleTutorial/index.php` and press `enter` key.

![](/php/schedule/getting-started_images/schedule.png)

N> In case, if you face any problem with default port 80 while running your sample, make the Apache to listen on some other different ports. The port number changes needs to be done on both the `httpd.conf` and `httpd-ssl.conf` files, in order to get rid of this problem.(Refer [here](http://stackoverflow.com/questions/20558410/xampp-port-80-in-use-by-unable-to-open-process-with-pid-4-12))
