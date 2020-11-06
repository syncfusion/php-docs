---
title: Show or Hide indicator, all day row, header, timescale
description: Show or hide time indicator, all day row, header, timescale
platform: php
control: schedule
documentation: ug
keywords: time indicator, all day, header, timescale
---
# Miscellaneous

## Time Indicator

The current system time can be depicted in a scheduler with an indication of a piece of text displaying the time over a horizontal line across today’s date (Vertical Scheduler mode). In Horizontal mode, the time indicator is displayed as a small vertical line within the header time cells (depicting current time).

It is enabled by default in Scheduler and to hide it, [showCurrentTimeIndicator](/api/js/ejschedule#members:showcurrenttimeindicator) property needs to be set as **false** as shown below.

{% highlight javascript %}

<?php
    require_once '../EJ/AutoLoad.php';

    $data = array(
        array(
            'Id' => 1,
            'Subject' => 'Music Class',
            'StartTime' => new DateTime('2016/5/5 12:00'),
            'EndTime' => new DateTime('2016/5/5 14:30')
        )
    );

    $appointment = new EJ\Schedule\AppointmentSetting();
    $appointment->dataSource($data);

    $schedule = new EJ\Schedule('defaultSchedule');
    echo $schedule->width('100%')->height('525px')->currentDate(new DateTime('2017/6/5'))->showCurrentTimeIndicator(false)->appointmentSettings($appointment)->render();
?>

{% endhighlight %}

N> When Scheduler rendered with multiple resources, multiple time indicators are displayed in Vertical mode – whereas single indicator displays for horizontal mode.

## Show/Hide All-Day Row

The All-day row cell is a single row region displayed at the top of the work cells area to hold the all-day appointments together. The Scheduler displays it by default and if it needs to be hidden, the [showAllDayRow](/api/js/ejschedule#members:showalldayrow) property can be set to **false** as shown below.

{% highlight javascript %}

<?php
    require_once '../EJ/AutoLoad.php';

    $data = array(
        array(
            'Id' => 1,
            'Subject' => 'Music Class',
            'StartTime' => new DateTime('2016/5/5 12:00'),
            'EndTime' => new DateTime('2016/5/5 14:30')
        )
    );

    $appointment = new EJ\Schedule\AppointmentSetting();
    $appointment->dataSource($data);

    $schedule = new EJ\Schedule('defaultSchedule');
    echo $schedule->width('100%')->height('525px')->currentDate(new DateTime('2017/6/5'))->showAllDayRow(false)->appointmentSettings($appointment)->render();
?>

{% endhighlight %}

N> The All-day row expands vertically, whenever more number of appointments are populated in one or more days.

## Show/Hide Header bar

The header bar is the top most region of the Scheduler which includes the date navigation icons and view navigation options – and also shown on the Scheduler by default. To hide the header bar, set the [showHeaderBar](/api/js/ejschedule#members:showheaderbar) property to **false** as shown below.

{% highlight javascript %}

<?php
    require_once '../EJ/AutoLoad.php';

    $data = array(
        array(
            'Id' => 1,
            'Subject' => 'Music Class',
            'StartTime' => new DateTime('2016/5/5 12:00'),
            'EndTime' => new DateTime('2016/5/5 14:30')
        )
    );

    $appointment = new EJ\Schedule\AppointmentSetting();
    $appointment->dataSource($data);

    $schedule = new EJ\Schedule('defaultSchedule');
    echo $schedule->width('100%')->height('525px')->currentDate(new DateTime('2017/6/5'))->showHeaderBar(false)->appointmentSettings($appointment)->render();
?>

{% endhighlight %}

## Show/Hide TimeScale

The TimeScale is the left most region of the Scheduler in vertical mode and the same is displayed at the top position in horizontal mode. It depicts the time interval either in a 12 or 24 hour mode. By default, the timeScale is displayed in the Scheduler and in order to hide it – set the [showTimeScale](/api/js/ejschedule#members:showtimescale) option to **false** as shown below.

{% highlight javascript %}

<?php
    require_once '../EJ/AutoLoad.php';

    $data = array(
        array(
            'Id' => 1,
            'Subject' => 'Music Class',
            'StartTime' => new DateTime('2016/5/5 12:00'),
            'EndTime' => new DateTime('2016/5/5 14:30')
        )
    );

    $appointment = new EJ\Schedule\AppointmentSetting();
    $appointment->dataSource($data);

    $schedule = new EJ\Schedule('defaultSchedule');
    echo $schedule->width('100%')->height('525px')->currentDate(new DateTime('2017/6/5'))->showTimeScale(false)->appointmentSettings($appointment)->render();
?>

{% endhighlight %}

## Show/Hide Location Field

The Location field in the default appointment window can be displayed or hidden from it using the [showLocationField](/api/js/ejschedule#members:showlocationfield) property. By default, this property is set to false. To display the location option in the appointment window, then set **showLocationField** to **true** and also bind the appropriate field to the location property within the appointmentSettings as shown below.

{% highlight javascript %}

<?php
    require_once '../EJ/AutoLoad.php';

    $data = array(
        array(
            'Id' => 1,
            'Subject' => 'Music Class',
            'StartTime' => new DateTime('2016/5/5 12:00'),
            'EndTime' => new DateTime('2016/5/5 14:30'),
            'EventLocation' => 'RDU'
        )
    );

    $appointment = new EJ\Schedule\AppointmentSetting();
    $appointment->dataSource($data)->location('EventLocation');

    $schedule = new EJ\Schedule('defaultSchedule');
    echo $schedule->width('100%')->height('525px')->currentDate(new DateTime('2017/6/5'))->showLocationField(true)->appointmentSettings($appointment)->render();
?>

{% endhighlight %}
