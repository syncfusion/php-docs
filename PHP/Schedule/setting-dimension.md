---
title: Setting dimension
description: Setting dimension for Schedule control
platform: php
control: schedule
documentation: ug
keywords: dimension, cell dimension, cell width, cell height
---
# Setting Dimension

The dimension normally refers to the height and width of the element. With Scheduler, it is possible to set 2 kinds of dimensions.

* Scheduler dimension (Scheduler control height and width)
* Cell dimension (Scheduler cells height and width)

## Scheduler Dimension

The [height](/api/js/ejschedule#members:height) and [width](/api/js/ejschedule#members:width) properties can be defined to set the outer dimension of the Scheduler control.

{% highlight javascript %}

<?php
    require_once '../EJ/AutoLoad.php';

    $schedule = new EJ\Schedule('defaultSchedule');
    echo $schedule->width('70%')->height('500px')->render();
?>

{% endhighlight %}

N> The height and width properties accepts both **pixel** and **percentage** values.

## Scheduler Cell Dimensions

### Cell Height

The [cellHeight](/api/js/ejschedule#members:cellheight) property allows the Scheduler to set the height of the cells in pixels. The appointment height in vertical mode changes accordingly as per the cell size within which it renders.

{% highlight javascript %}

<?php
    require_once '../EJ/AutoLoad.php';

    $data = array(
        array(
            'Id' => 1,
            'Subject' => 'Music Class',
            'StartTime' => new DateTime('2016/5/5 06:00'),
            'EndTime' => new DateTime('2016/5/5 07:30')
        )
    );

    $appointment = new EJ\Schedule\AppointmentSetting();
    $appointment->dataSource($data);

    $schedule = new EJ\Schedule('defaultSchedule');
    echo $schedule->cellHeight('40px')->currentDate(new DateTime('2016/5/5'))->appointmentSettings($appointment)->render();
?>

{% endhighlight %}

N> In **desktop** mode, the default height value of the cells is set to **20px**, whereas for **mobile** mode – the Scheduler cells are rendered with **40px** by default.

### Cell Auto-Height

The height of the cells specifically in timeline view can be made to adjust automatically based on its exceeding appointment count. It is controlled by an API named [showOverflowButton](/api/js/ejschedule#members:showOverflowButton) which accepts true or false value, denoting whether to enable/disable the cell auto-height adjusting option. To enable this option, set the value of `showOverflowButton` as `false` whereas its default value is `true`.

In **Vertical** view, the same functionality is made applicable only in the **Month View** whereas in **Horizontal** mode, it is applicable in all the views.

{% highlight javascript %}

<?php
    require_once '../EJ/AutoLoad.php';

    $data = array(
        array(
            'Id' => 1,
            'Subject' => 'Music Class',
            'StartTime' => new DateTime('2016/5/5 06:00'),
            'EndTime' => new DateTime('2016/5/5 07:30')
        )
    );

    $appointment = new EJ\Schedule\AppointmentSetting();
    $appointment->dataSource($data);

    $schedule = new EJ\Schedule('defaultSchedule');
    echo $schedule->width('100%')->height('525px')->currentDate(new DateTime('2016/5/5'))->currentView('month')->showOverflowButton(false)->appointmentSettings($appointment)->render();
?>

{% endhighlight %}

### Cell Width

The [cellWidth](/api/js/ejschedule#members:cellwidth) property allows the Scheduler to set the width of the cells in pixels. The appointment width adjusts based on the cell width of the Scheduler.

{% highlight javascript %}

<?php
    require_once '../EJ/AutoLoad.php';

    $data = array(
        array(
            'Id' => 1,
            'Subject' => 'Music Class',
            'StartTime' => new DateTime('2016/5/5 06:00'),
            'EndTime' => new DateTime('2016/5/5 07:30')
        )
    );

    $appointment = new EJ\Schedule\AppointmentSetting();
    $appointment->dataSource($data);

    $schedule = new EJ\Schedule('defaultSchedule');
    echo $schedule->currentDate(new DateTime('2016/5/5'))->cellWidth('97px')->appointmentSettings($appointment)->render();
?>

{% endhighlight %}

N> When the **cellHeight** and **cellWidth** properties are set with some specific pixel values, the cell size does not adapt to the responsive behavior of the Scheduler while resizing it in desktop/mobile mode.
