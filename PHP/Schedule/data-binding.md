---
title: Data binding with Schedule	
description: Binding local and remote data to Scheduler
platform: php
control: schedule
documentation: ug
keywords: data binding, local data, remote data
---
# Data Binding

## Appointment Fields

The below listed names are the appointment fields which holds the appropriate column names from the dataSource.

<table>
    <tr>
        <th>Field name<br/><br/></th>
        <th>Description<br/><br/></th>
    </tr>
    <tr>
        <td>id<br/><br/></td>
        <td>Binds the <b>id</b> field name for indexing and performing CRUD operation on the appointments. It’s optional.<br/><br/></td>
    </tr>
    <tr>
        <td>startTime<br/><br/></td>
        <td>Binds the appointment start time field name which is <b>mandatory</b> and also its related validation rules.<br/><br/></td>
    </tr>
    <tr>
        <td>startTimeZone<br/><br/></td>
        <td>Binds the name of the start timezone field in the dataSource and also its related validation rules. If the <b>startTimeZone</b> field is not mentioned, then the appointment makes use of the Scheduler timeZone or System timeZone.<br/><br/></td>
    </tr>
    <tr>
        <td>endTime<br/><br/></td>
        <td>Binds the appointment end time field name which is <b>mandatory</b> and also its related validation rules.<br/><br/></td>
    </tr>
    <tr>
        <td>endTimeZone<br/><br/></td>
        <td>Binds the name of the end timezone field in the dataSource and also its related validation rules. If the <b>endTimeZone</b> field is not mentioned, then the appointment makes use of the Scheduler timeZone or System timeZone.<br/><br/></td>
    </tr>
    <tr>
        <td>subject<br/><br/></td>
        <td>Binds the appointment subject field name which holds the summary of the appointment and also its related validation rules. <br/><br/></td>
    </tr>
    <tr>
        <td>location<br/><br/></td>
        <td>Binds the name of the location field and also its related validation rules. It indicates the appointment location/occurrence place. This field needs to be bind to the Scheduler, when an API <b>showLocationField</b> is set to true.<br/><br/></td>
    </tr>
    <tr>
        <td>description<br/><br/></td>
        <td>Binds the appointment description field name and also its related validation rules.<br/><br/></td>
    </tr>
    <tr>
        <td>allDay<br/><br/></td>
        <td>Binds the name of the `allDay` field. It accepts the <b>boolean</b> value and indicates whether the appointment is an all-day appointment or not.<br/><br/></td>
    </tr>
    <tr>
        <td>categorize<br/><br/></td>
        <td>Binds the name of the categorize field and also its related validation rules. It indicates the category or status value (red categorize, green, yellow and so on). <br/><br/></td>
    </tr>
    <tr>
        <td>priority<br/><br/></td>
        <td>Binds the name of the priority field, its related validation rules and also indicates the priority (high, low, medium and none) of the appointments. This field should be bind to the Scheduler, when <b>prioritySettings.enable</b> is set to true.<br/><br/></td>
    </tr>
    <tr>
        <td>resourceFields<br/><br/></td>
        <td>Binds one or more fields in the resource collection. It maps the resource field names with the appointments, denoting to which resource the appointments actually belongs.<br/><br/></td>
    </tr>
    <tr>
        <td>recurrence<br/><br/></td>
        <td>Binds the name of the recurrence field. It accepts the <b>boolean</b> value and indicates whether the appointment is a recurrence appointment or not.<br/><br/></td>
    </tr>
    <tr>
        <td>recurrenceRule<br/><br/></td>
        <td>Binds the name of the recurrenceRule field. It holds the recurrence pattern associated with the appointments.<br/><br/></td>
    </tr>
    <tr>
        <td>recurrenceId<br/><br/></td>
        <td>Binds the recurrence Id field which acts as a parent id for Scheduler recurrence appointments.<br/><br/></td>
    </tr>
    <tr>
        <td>recurrenceExDate<br/><br/></td>
        <td>Binds the recurrence Exception field which accepts the recurrence Exception date values.<br/><br/></td>
    </tr>
</table>

The below example depicts the appointment fields accepting the string type mapper fields,

{% highlight javascript %}

<?php
    require_once '../EJ/AutoLoad.php';

    $data = array(
        array(
            'Id' => 1,
            'Subject' => 'Music Class',
            'StartTime' => new DateTime('2016/5/5 12:00'),
            'StartTimeZone' => 'UTC +05:30',
            'EndTime' => new DateTime('2016/5/5 14:30'),
            'EndTimeZone' => 'UTC +05:30',
            'Description' => 'Never Give up on Obstacles',
            'location' => 'US',
            'AllDay' => false,
            'Recurrence' => true,
            'RecurrenceRule' => 'FREQ=WEEKLY;BYDAY=MO,TU;INTERVAL=1;COUNT=15',
            'Categorize' => '1',
            'Priority' => 'medium',
            'ownerId' => 3,
            'RecurrenceId' => 1,
            'RecurrenceExDate' => null
        )
    );
    $categoryData = new EJ\Schedule\CategorizeSetting();
    $categoryData->enable(true);

    $priorityData = new EJ\Schedule\PrioritySettings();
    $priorityData->enable(true);

    $groupData = new EJ\Schedule\Group();
    $groupData->resources(array('Owners'));

    $res =new EJ\Schedule\Resource();
    $resSettings =new EJ\Schedule\ResourceSetting();
    $resData ='[
        {'text':'Nancy','id':1,'color':'#f8a398'},
        {'text':'Steven','id':3,'color':'#56ca85'},
        {'text':'Michael','id':5,'color':'#51a0ed'}
    ]';
    $resData = json_decode($resData,true);
    $resSettings->text('text')->id('id')->color('color')->dataSource($resData);
    $res->allowMultiple(true)->field('ownerId')->name('Owners')->title('Owner')->resourceSettings($resSettings);
    $resourceData = array($res);

    $appointment = new EJ\Schedule\AppointmentSetting();
    $appointment->dataSource($data)->id('Id')->startTime('StartTime')->endTime('EndTime')->subject('Subject')->description('Description')->allDay('AllDay')->recurrence('Recurrence')->recurrenceRule('RecurrenceRule')->resourceFields('ownerId');

    $schedule = new EJ\Schedule('defaultSchedule');
    echo $schedule->width('100%')->height('525px')->currentDate(new DateTime('2017/6/5'))->showLocationField(true)->categorizeSettings($categoryData)->prioritySettings($priorityData)->group($groupData)->resources($resourceData)->appointmentSettings($appointment)->render();
?>

{% endhighlight %}

## Appointment Field Validation

It is possible to validate the required fields of the appointment window from client-side before submitting it, by adding appropriate validation rules to each fields. The appointment fields have been extended to accept both String and object type values. Therefore, in order to perform validations, it is necessary to specify object values for the appointment fields.

Refer the appointment fields specified with validation rules from the following code example.

{% highlight html %}

<script type="text/javascript">
    $(function () {
        $.validator.addMethod("customRule", function (value, element, options) {
            var expression = /^[a-zA-Z0-9- ]*$/; //new RegExp(options);
            return expression.test(value);
        }, "Special character(s) not allowed in Location field");
    });
</script>

{% endhighlight %}

{% highlight javascript %}

<?php
    require_once '../EJ/AutoLoad.php';

    $data = json_decode(file_get_contents('ScheduleData.json'), true);
    $categorizedData= '[
        {'text':'Blue Category','id':1,'color':'#43b496','fontColor':'#ffffff'},
        {'text':'Green Category','id':2,'color':'#7f993e','fontColor':'#ffffff'},
        {'text':'Orange Category','id':3,'color':'#cc8638','fontColor':'#ffffff'},
        {'text':'Purple Category','id':4,'color':'#ab54a0','fontColor':'#ffffff'},
        {'text':'Red Category','id':5,'color':'#dd654e','fontColor':'#ffffff'},
        {'text':'Yellow Category','id':6,'color':'#d0af2b','fontColor':'#ffffff'}
    ]';
    $categoryData = new EJ\Schedule\CategorizeSetting();
    $categoryData->enable(true)->allowMultiple(false)->dataSource($categorizedData)->text('text')->id('id')->color('color')->fontColor('fontColor');

    $appointment = new EJ\Schedule\AppointmentSetting();
    $appointment->dataSource($data)
                ->id("Id")
                ->subject(json_decode('{"field":"Subject","validationRules":{"required":true}}',true))
                ->location(json_decode('{"field":"Location","validationRules":{"required":true,"customRule":"/^[a-zA-Z0-9- ]*$/"}}',true))
                ->startTime(json_decode('{"field":"StartTime","validationRules":{"required":true}}',true))
                ->endTime(json_decode('{"field":"EndTime","validationRules":{"required":true}}',true))
                ->description(json_decode('{"field":"Description","validationRules":{"required":true,"minlength":5,"maxlength":500}}',true))
                ->allDay("AllDay")
                ->recurrence("Recurrence")
                ->recurrenceRule("RecurrenceRule")
                ->categorize(json_decode('{"field":"Categorize","validationRules":{"required":true,"messages":{"required":"Categories are required."}}}',true));

    $schedule = new EJ\Schedule('defaultSchedule');
    echo $schedule->width('100%')->height('525px')->currentDate(new DateTime('2017/6/5'))->showLocationField(true)->categorizeSettings($categoryData)->appointmentSettings($appointment)->render();
?>

{% endhighlight %}

## Binding to JSON Data Array

To bind the Scheduler events data as array of JSON objects, refer the below code example.

**Example** - Array of JSON Data Binding

{% highlight javascript %}

<?php
    require_once '../EJ/AutoLoad.php';

    $data = array(
        array(
            'Id' => 1,
            'Subject' => 'Music Class',
            'StartTime' => new DateTime('2016/5/5 06:00'),
            'EndTime' => new DateTime('2016/5/5 07:30')
        ),
        array(
            'Id' => 2,
            'Subject' => 'Music Class',
            'StartTime' => new DateTime('2016/5/5 09:00'),
            'EndTime' => new DateTime('2016/5/5 14:30')
        )
    );

    $appointment = new EJ\Schedule\AppointmentSetting();
    $appointment->dataSource($data);

    $schedule = new EJ\Schedule('defaultSchedule');
    echo $schedule->width('100%')->height('525px')->currentDate(new DateTime('2016/5/5'))->appointmentSettings($appointment)->render();
?>

{% endhighlight %}

## Binding Remote Data Service

The appointment data can be bound to the Scheduler through the [Odata](http://www.odata.org) remote services, where the service URL is mapped with [Data manager](/js/datamanager/overview) and then configured to the Schedule dataSource API.

{% highlight javascript %}

<?php
    require_once '../EJ/AutoLoad.php';

    $dataManager  = new EJ\DataManager();
    $dataManager->url('http://mvc.syncfusion.com/OdataServices/Northwnd.svc/');

    $queryManager = new EJ\Query();
    $queryManager->from("Events")->take(10);

    $appointment = new EJ\Schedule\AppointmentSetting();
    $appointment->dataSource($dataManager)->query($queryManager);

    $schedule = new EJ\Schedule('defaultSchedule');
    echo $schedule->width('100%')->height('525px')->currentDate(new DateTime('2016/5/5'))->appointmentSettings($appointment)->render();
?>

{% endhighlight %}

## OData V4

The OData v4 is an improved version of OData protocols and the DataManager can also retrieve and consume appointment data from [OData v4](http://www.odata.org/documentation) services.

{% highlight javascript %}

<?php
    require_once '../EJ/AutoLoad.php';

    $dataManager  = new EJ\DataManager();
    $dataManager->url('http://services.odata.org/V4/Northwind/Northwind.svc/Orders/')->adaptor('ODataV4Adaptor');

    $appointment = new EJ\Schedule\AppointmentSetting();
    $appointment->dataSource($dataManager)->subject('ShipName')->startTime('OrderDate')->endTime('RequiredDate')->description('ShipAddress');

    $schedule = new EJ\Schedule('defaultSchedule');
    echo $schedule->width('100%')->height('525px')->currentDate(new DateTime('2016/5/5'))->appointmentSettings($appointment)->render();
?>

{% endhighlight %}

## WebAPI Binding

The Schedule appointment data can be bound through the Web API service and it is a programmatic interface to define the request and response messages system that is mostly exposed in **JSON** or **XML**.

{% highlight javascript %}

<?php
    require_once '../EJ/AutoLoad.php';

    $dataManager  = new EJ\DataManager();
    $dataManager->url('http://mvc.syncfusion.com/OdataServices/api/ScheduleData/')->crossDomain(true);

    $appointment = new EJ\Schedule\AppointmentSetting();
    $appointment->dataSource($dataManager);

    $schedule = new EJ\Schedule('defaultSchedule');
    echo $schedule->width('100%')->height('525px')->currentDate(new DateTime('2016/5/5'))->appointmentSettings($appointment)->render();
?>

{% endhighlight %}

The server-side code to retrieve the appointments are as follows.

{% highlight javascript %}

<?php

require_once 'require/ScheduleCrud.php';
$crudManager = new ScheduleCrud();
header("Content-type:application/json");
$json_param = file_get_contents('php://input');
$param = json_decode($json_param,true);
$getData = $crudManager->selectEvent();
$json = array();
foreach($getData as $r) {
    array_push($json, array('Id' => $r['Id'],'Location' => $r['Location'],'Subject' => $r['Subject'],'StartTime' => $r['StartTime'], 'StartTimeZone' => $r['StartTimeZone'],'Description' => $r['Description'], 'EndTime' => $r['EndTime'], 'EndTimeZone' => $r['EndTimeZone'],'AllDay' => $r['AllDay'],'Recurrence' => $r['Recurrence'],'RecurrenceRule' => $r['RecurrenceRule'] ));
}
echo json_encode($json, JSON_NUMERIC_CHECK);

?>

{% endhighlight %}

## Data binding using OLEDB

The appointment data can also be bound to the Scheduler using OLEDB database as depicted below.

{% highlight javascript %}

<?php
    require_once '../EJ/AutoLoad.php';

    $dataManager  = new EJ\DataManager();
    $dataManager->url('ScheduleCrud.php')->crudUrl('ScheduleCrud.php')->adaptor('UrlAdaptor');

    $appointment = new EJ\Schedule\AppointmentSetting();
    $appointment->dataSource($dataManager)
                ->id('Id')
                ->subject('Subject')
                ->startTime('StartTime')
                ->endTime('EndTime')
                ->startTimeZone('StartTimeZone')
                ->endTimeZone('EndTimeZone')
                ->description('Description')
                ->allDay('AllDay')
                ->recurrence('Recurrence')
                ->recurrenceRule('RecurrenceRule');

    $schedule = new EJ\Schedule('defaultSchedule');
    echo $schedule->width('100%')->height('525px')->currentDate(new DateTime('2016/5/5'))->appointmentSettings($appointment)->render();
?>

{% endhighlight %}

The server-side controller code to handle the CRUD operation are as follows.

{% highlight javascript %}

<?php
require_once 'require/ScheduleCrud.php';

$crudManager = new ScheduleCrud();

header("Content-type:application/json");
$json_param = file_get_contents('php://input');
$param = json_decode($json_param,true);
if (isset($param['action'])) {
    if ($param['action'] == "insert" || ($param['action'] == "batch" && !empty($param['added']))) {
        if ($param['action'] == "insert") {
            $id = null;
            $subject = isset($param['value']['Subject']) ? $param['value']['Subject'] : null;
            $location = isset($param['value']['Location']) ? $param['value']['Location'] : null;
            $ownerId = isset($param['value']['OwnerId']) ? $param['value']['OwnerId'] : null;
            $description = isset($param['value']['Description']) ? $param['value']['Description'] : null;
            $allDay = isset($param['value']['AllDay']) ? $param['value']['AllDay'] : null;
            $startTime = isset($param['value']['StartTime']) ? $param['value']['StartTime'] : null;
            $startTimeZone = isset($param['value']['StartTimeZone']) ? $param['value']['StartTimeZone'] : null;
            $endTime = isset($param['value']['EndTime']) ? $param['value']['EndTime'] : null;
            $endTimeZone = isset($param['value']['EndTimeZone']) ? $param['value']['EndTimeZone'] : null;
            $recurrence = isset($param['value']['Recurrence']) ? $param['value']['Recurrence'] : null;
            $recurrenceRule = isset($param['value']['RecurrenceRule']) ? $param['value']['RecurrenceRule'] : null;

            $startTime = clone new DateTime($startTime);
            $timezone = new DateTimeZone('Europe/Paris');
            $startTime->setTimezone($timezone);
            $startTime = $startTime->format('Y-m-d H:i:s');
            $endTime = clone new DateTime($endTime);
            $timezone = new DateTimeZone('Europe/Paris');
            $endTime->setTimezone($timezone);
            $endTime = $endTime->format('Y-m-d H:i:s');

            $crudManager->insert($id,$subject,$location,$startTime,$startTimeZone,$endTime,$endTimeZone,$description,$allDay,$recurrence,$recurrenceRule,$ownerId);
        }
        else if ($param['action'] == "batch" && !empty($param['added'])) {
            foreach($param['added'] as $add) {
                $id = null;
                $subject = isset($add['Subject']) ? $add['Subject'] : null;
                $location = isset($add['Location']) ? $add['Location'] : null;
                $ownerId = isset($add['OwnerId']) ? $add['OwnerId'] : null;
                $description = isset($add['Description']) ? $add['Description'] : null;
                $allDay = isset($add['AllDay']) ? $add['AllDay'] : null;
                $startTime = isset($add['StartTime']) ? $add['StartTime'] : null;
                $startTimeZone = isset($add['StartTimeZone']) ? $add['StartTimeZone'] : null;
                $endTime = isset($add['EndTime']) ? $add['EndTime'] : null;
                $endTimeZone = isset($add['EndTimeZone']) ? $add['EndTimeZone'] : null;
                $recurrence = isset($add['Recurrence']) ? $add['Recurrence'] : null;
                $recurrenceRule = isset($add['RecurrenceRule']) ? $add['RecurrenceRule'] : null;

                $startTime = clone new DateTime($startTime);
                $timezone = new DateTimeZone('Europe/Paris');
                $startTime->setTimezone($timezone);
                $startTime = $startTime->format('Y-m-d H:i:s');
                $endTime = clone new DateTime($endTime);
                $timezone = new DateTimeZone('Europe/Paris');
                $endTime->setTimezone($timezone);
                $endTime = $endTime->format('Y-m-d H:i:s');

                $crudManager->insert($id,$subject,$location,$startTime,$startTimeZone,$endTime,$endTimeZone,$description,$allDay,$recurrence,$recurrenceRule,$ownerId);
            }
        }
    }

    if ($param['action'] == "update" || ($param['action'] == "batch" && !empty($param['changed']))) {
        if ($param['action'] == "update") {
            $id = isset($param['value']['Id']) ? $param['value']['Id'] : null;
            $subject = isset($param['value']['Subject']) ? $param['value']['Subject'] : null;
            $location = isset($param['value']['Location']) ? $param['value']['Location'] : null;
            $ownerId = isset($param['value']['OwnerId']) ? $param['value']['OwnerId'] : null;
            $description = isset($param['value']['Description']) ? $param['value']['Description'] : null;
            $allDay = isset($param['value']['AllDay']) ? $param['value']['AllDay'] : null;
            $startTime = isset($param['value']['StartTime']) ? $param['value']['StartTime'] : null;
            $startTimeZone = isset($param['value']['StartTimeZone']) ? $param['value']['StartTimeZone'] : null;
            $endTime = isset($param['value']['EndTime']) ? $param['value']['EndTime'] : null;
            $endTimeZone = isset($param['value']['EndTimeZone']) ? $param['value']['EndTimeZone'] : null;
            $recurrence = isset($param['value']['Recurrence']) ? $param['value']['Recurrence'] : null;
            $recurrenceRule = isset($param['value']['RecurrenceRule']) ? $param['value']['RecurrenceRule'] : null;

            $startTime = clone new DateTime($startTime);
            $timezone = new DateTimeZone('Europe/Paris');
            $startTime->setTimezone($timezone);
            $startTime = $startTime->format('Y-m-d H:i:s');
            $endTime = clone new DateTime($endTime);
            $timezone = new DateTimeZone('Europe/Paris');
            $endTime->setTimezone($timezone);
            $endTime = $endTime->format('Y-m-d H:i:s');

            $crudManager->update($id,$subject,$location,$startTime,$startTimeZone,$endTime,$endTimeZone,$description,$allDay,$recurrence,$recurrenceRule,$ownerId);
        }
        else if ($param['action'] == "batch" && !empty($param['changed'])) {
            foreach($param['changed'] as $update) {
                $id = isset($update['Id']) ? $update['Id'] : null;
                $subject = isset($update['Subject']) ? $update['Subject'] : null;
                $location = isset($update['Location']) ? $update['Location'] : null;
                $ownerId = isset($update['OwnerId']) ? $update['OwnerId'] : null;
                $description = isset($update['Description']) ? $update['Description'] : null;
                $allDay = isset($update['AllDay']) ? $update['AllDay'] : null;
                $startTime = isset($update['StartTime']) ? $update['StartTime'] : null;
                $startTimeZone = isset($update['StartTimeZone']) ? $update['StartTimeZone'] : null;
                $endTime = isset($update['EndTime']) ? $update['EndTime'] : null;
                $endTimeZone = isset($update['EndTimeZone']) ? $update['EndTimeZone'] : null;
                $recurrence = isset($update['Recurrence']) ? $update['Recurrence'] : null;
                $recurrenceRule = isset($update['RecurrenceRule']) ? $update['RecurrenceRule'] : null;

                $startTime = clone new DateTime($startTime);
                $timezone = new DateTimeZone('Europe/Paris');
                $startTime->setTimezone($timezone);
                $startTime = $startTime->format('Y-m-d H:i:s');
                $endTime = clone new DateTime($endTime);
                $timezone = new DateTimeZone('Europe/Paris');
                $endTime->setTimezone($timezone);
                $endTime = $endTime->format('Y-m-d H:i:s');

                $crudManager->update($id,$subject,$location,$startTime,$startTimeZone,$endTime,$endTimeZone,$description,$allDay,$recurrence,$recurrenceRule,$ownerId);
            }
        }
    }

    if ($param['action'] == "remove" || ($param['action'] == "batch" && !empty($param['deleted']))) {
        if ($param['action'] == "remove") {
            $id = $param['key'];
            $crudManager->remove($id);
        }
        else if ($param['action'] == "batch" && !empty($param['deleted'])) {
            foreach($param['deleted'] as $delete) {
                $id = $delete['Id'];
                $crudManager->remove($id);
            }
        }
    }
}

$getData = $crudManager->getData();
$json = array();
foreach($getData as $r) {
    array_push($json, array('Id' => $r['Id'],'Location' => $r['Location'],'Subject' => $r['Subject'], 'OwnerId' => $r['OwnerId'], 'StartTime' => $r['StartTime'], 'StartTimeZone' => $r['StartTimeZone'],'Description' => $r['Description'], 'EndTime' => $r['EndTime'], 'EndTimeZone' => $r['EndTimeZone'],'AllDay' => $r['AllDay'],'Recurrence' => $r['Recurrence'],'RecurrenceRule' => $r['RecurrenceRule'] ));
}
echo json_encode($json, JSON_NUMERIC_CHECK);
?>

{% endhighlight %}

## Loading Data on Demand

Load on demand feature allows the Scheduler to retrieve only the filtered appointment data (for the current Scheduler date range) from the service/database during **loading time**, and that too only for the current Scheduler view. There are 3 parameters made available on the server-side namely **CurrentDate**, **CurrentView** and **CurrentAction** through which only the necessary appointments are retrieved from the database and then assigned to the Scheduler dataSource. With this kind of Scheduler action, consuming only lesser data will reduce the usage of network bandwidth size and loading time.

The **enableLoadOnDemand** property is used to enable or disable the load on demand functionality of the schedule.

{% highlight javascript %}

<?php
    require_once '../EJ/AutoLoad.php';

    $dataManager  = new EJ\DataManager();
    $dataManager->url('http://mvc.syncfusion.com/OdataServices/api/ScheduleData/')->crossDomain(true);

    $appointment = new EJ\Schedule\AppointmentSetting();
    $appointment->dataSource($dataManager);

    $schedule = new EJ\Schedule('defaultSchedule');
    echo $schedule->width('100%')->height('525px')->currentDate(new DateTime('2016/5/5'))->enableLoadOnDemand(true)->appointmentSettings($appointment)->render();
?>

{% endhighlight %}

The server-side code to handle the load on demand is as follows.

{% highlight c# %}

// retrieve the appointments based on the current date.
public IEnumerable<Event> GetData(String CurrentDate, String CurrentView, String CurrentAction)
{
    var dateString = Regex.Match(CurrentDate.ToString(), @"^(\w+\b.*?){4}").ToString();
    string format = "ddd MMM dd yyyy";
    DateTime dateTimeValue;
    try
    {
        dateTimeValue = DateTime.ParseExact(dateString, format, CultureInfo.InvariantCulture);
    }
    catch(FormatException)
    {
        var dateSplit = CurrentDate.Split(' ');//For IE<=10 Fri Mar 20 11:00:22 UTC+0530 2015
        if (dateSplit[2].Length == 1) dateSplit[2] = string.Concat("0", dateSplit[2]);
        dateString = string.Concat(dateSplit[0], ' ', dateSplit[1], ' ', dateSplit[2], ' ', dateSplit[dateSplit.Length - 1]);
        dateTimeValue = DateTime.ParseExact(dateString, format, CultureInfo.InvariantCulture);
    }
    // AppointmentDeposit is a user-defined class within which the FilterAppointment method is defined. 
    AppointmentDeposit rep = new AppointmentDeposit();
    var data = rep.FilterAppointment(dateTimeValue, CurrentAction, CurrentView); 
    return data;
}

// Method to filter the appointments based on the date range
public List<Event> FilterAppointment(DateTime CurrentDate, String CurrentAction, String CurrentView)
{
    DateTime CurrDate = Convert.ToDateTime(CurrentDate);
    DateTime StartDate = FirstWeekDate(CurrDate.Date);
    DateTime EndDate = FirstWeekDate(CurrDate.Date);
    List<Event> appointmentList = new NORTHWNDEntities().Events.ToList();
    switch (CurrentView)
    {
        case "day":
            StartDate = CurrentDate;
            EndDate = CurrentDate;
            break;
        case "week":
            EndDate = EndDate.AddDays(7);
            break;
        case "workweek":
            EndDate = EndDate.AddDays(5);
            break;
        case "month":
            StartDate = CurrDate.Date.AddDays(-CurrDate.Day + 1);
            EndDate = StartDate.AddMonths(1);
            break;
    }
    appointmentList = new NORTHWNDEntities().Events.ToList().Where(app =>
    ((Convert.ToDateTime(app.StartTime).Date >= Convert.ToDateTime(StartDate.Date)) &&
    (Convert.ToDateTime(app.EndTime).Date <= Convert.ToDateTime(EndDate.Date)))).ToList();
    return appointmentList;
}

internal static DateTime FirstWeekDate(DateTime CurrentDate)
{
    try
    {
        DateTime FirstDayOfWeek = CurrentDate;
        DayOfWeek WeekDay = FirstDayOfWeek.DayOfWeek;
        switch (WeekDay)
        {
            case DayOfWeek.Sunday:
                break;
            case DayOfWeek.Monday:
                FirstDayOfWeek = FirstDayOfWeek.AddDays(-1);
                break;
            case DayOfWeek.Tuesday:
                FirstDayOfWeek = FirstDayOfWeek.AddDays(-2);
                break;
            case DayOfWeek.Wednesday:
                FirstDayOfWeek = FirstDayOfWeek.AddDays(-3);
                break;
            case DayOfWeek.Thursday:
                FirstDayOfWeek = FirstDayOfWeek.AddDays(-4);
                break;
            case DayOfWeek.Friday:
                FirstDayOfWeek = FirstDayOfWeek.AddDays(-5);
                break;
            case DayOfWeek.Saturday:
                FirstDayOfWeek = FirstDayOfWeek.AddDays(-6);
                break;
        }
        return (FirstDayOfWeek);
    }
    catch
    {
        return DateTime.Now;
    }
}

{% endhighlight %}
