---
title: Schedule - Customization	
description: Customization of working hours, date, and appointment window
platform: php
control: schedule
documentation: ug
keywords: customization, work hours, appointment window, display hours, Query cell info
---
# Customization

The Scheduler can be customized in various aspects like -

* Setting different Start/end hour limits
* Highlighting the working hours
* Setting different [date format](/php/schedule/globalization-and-localization#date-format)
* Specifying minimum and maximum date ranges
* Customize the entire appointment window with the user required fields
* Setting different time Slot duration
* Complete Scheduler customization using queryCellInfo event
* Setting different [first day of week](/php/schedule/globalization-and-localization#first-day-of-week)

## Hour Customization

It includes customization of displaying Scheduler with specific Start/End hours and also defining the working hour time range which is differentiated as business hours.

### Schedule Display Hours

It denotes the start and end hour time limits to be displayed on the Scheduler. To set this time limit, two properties namely [startHour](/api/js/ejschedule#members:starthour) and [endHour](/api/js/ejschedule#members:endhour) can be used.

* **startHour** - The hour from which the Scheduler time display actually starts.
* **endHour** - The hour on which the Scheduler time display should end.

The following code example renders the scheduler from 7.00 AM to 6.00 PM.

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
    echo $schedule->width('100%')->height('525px')->currentDate(new DateTime('2017/6/5'))->startHour(7)->endHour(18)->appointmentSettings($appointment)->render();
?>

{% endhighlight %}

### Working Hours

Working hours indicates the work hour limit within the Scheduler, which is highlighted visually with white colored work cells. To enable the highlighting of work hours on the Scheduler, set the **highlight** option available within the workHours property to **true**. By default, it is set to true. [workHour](/api/js/ejschedule#members:workhours) is a object property which contains the below specified options,

* **[highlight](/api/js/ejschedule#members:workhours-highlight)** – enables/disables the highlighting of work hours.
* **[start](/api/js/ejschedule#members:workhours-start)** - sets the start time of the working/business hour in a day.
* **[end](/api/js/ejschedule#members:workhours-end)** - sets the end time limit of the working/business hour in a day.

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

    $workhour = new EJ\Schedule\WorkHour();
    $workhour->highlight(true)->start(8)->end(17);

    $appointment = new EJ\Schedule\AppointmentSetting();
    $appointment->dataSource($data);

    $schedule = new EJ\Schedule('defaultSchedule');
    echo $schedule->width('100%')->height('525px')->currentDate(new DateTime('2017/6/5'))->workHours($workhour)->appointmentSettings($appointment)->render();
?>

{% endhighlight %}

N> By default, work hour **start** is set to **9** and **end** is set to **18**. Also, the Scheduler cells automatically scrolls up or down based on the starting work hour, to make the user to view that particular time initially.

## TimeScale

The [TimeScale](/api/js/ejschedule#members:timeScale) allows the user to set the required time slot duration for the work cells that displays on the Scheduler. It provides option to customize both the major and minor slots using template option. It includes the below properties such as,

* [enable](/api/js/ejschedule#members:timeScale-enable) - It accepts true or false value, denoting whether to show or hide the time slots. Its default value is `true`.
* [majorSlot](/api/js/ejschedule#members:timeScale-majorSlot) – Specifies the major time slot duration.
* [minorSlotCount](/api/js/ejschedule#members:timeScale-minorSlotCount) – Specifies the value, based on which the minor time slots are divided into appropriate count.
* [TimeScale templates](/php/schedule/templates#timescale-templates) - 2 template options available for customizing timeScales namely `minorSlotTemplateId` and `majorSlotTemplateId`.

The majorSlot and minorSlot can be set on the Scheduler with the following code example.

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

    $timescale = new EJ\Schedule\TimeScale();
    $timescale->enable(true)->majorSlot(60)->minorSlotCount(6);

    $appointment = new EJ\Schedule\AppointmentSetting();
    $appointment->dataSource($data);

    $schedule = new EJ\Schedule('defaultSchedule');
    echo $schedule->width('100%')->height('525px')->currentDate(new DateTime('2017/6/5'))->timeScale($timescale)->appointmentSettings($appointment)->render();
?>

{% endhighlight %}

## Hide Weekend days

The Scheduler can be customized to display only the working days, thus hiding the weekend days from it. The working days render based on the values given in the [workWeek](/api/js/ejschedule#members:workweek) property. The days that are not mentioned in the `workWeek` collection is considered to be the weekend days and it can be hidden from the Scheduler by setting `false` to the [showWeekend](/api/js/ejschedule#members:showweekend) property.

The following code example renders the Scheduler by hiding the weekend days.

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
    echo $schedule->width('100%')->height('525px')->currentDate(new DateTime('2017/6/5'))->showWeekend(false)->appointmentSettings($appointment)->render();
?>

{% endhighlight %}

## Date Customization

The date in the Scheduler can be customized by setting specific minimum and maximum date ranges and also defining various date formats to it.

### Current Date

The Current date indicates the date with which the Scheduler loads initially and based on which the appropriate date range displays in the week/workweek/month/agenda views. To set the current date to the Scheduler – use the following code example,

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
    echo $schedule->width('100%')->height('525px')->currentDate(new DateTime('2017/6/5'))->appointmentSettings($appointment)->render();
?>

{% endhighlight %}

N> By default, the System current date will be taken as Scheduler’s current date.

### MinDate and MaxDate

Providing the [minDate](/api/js/ejschedule#members:mindate) and [maxDate](/api/js/ejschedule#members:maxdate) property with some date values, allows the Scheduler to set the minimum and maximum date range. The Scheduler date that lies beyond these minimum and maximum date range will be in a disabled state, so that the date navigation is blocked beyond these specified date range. Also, the appointments that lies beyond these date ranges will not be displayed on the Scheduler.

The following code example shows how to set the minDate and maxDate properties of the Scheduler.

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
    echo $schedule->width('100%')->height('525px')->minDate(new DateTime('2017/6/5'))->maxDate(new DateTime('2017/6/10'))->appointmentSettings($appointment)->render();
?>

{% endhighlight %}

N> The **maxDate** value provided should always be greater than that of **minDate** value.

## Appointment Window Customization

It is possible to use the custom appointment window option to design it with the user-required extra fields apart from the other default available fields. To make use of the customized appointment window, it is necessary to use the [appointmentWindowOpen](/api/js/ejschedule#events:appointmentwindowopen) event within which the display of default appointment window is prevented.

The following code example lets you create the custom appointment window (using recurrence editor feature) with a single extra field for defining the appointment type.

{% highlight html %}

<!--Container for ejScheduler widget-->
<div id="Schedule1"></div>

<div id="customWindow" style="display: none">
        <div id="appWindow">
            <form id="custom">
                <table width="100%" cellpadding="5">
                    <tbody>
                        <tr style="display: none">
                            <td>
                                Id:
                            </td>
                            <td colspan="2">
                                <input id="customId" type="text" name="Id" />
                            </td>
                        </tr>
                        <tr>
                            <td>
                                Subject:
                            </td>
                            <td colspan="2">
                                <input id="subject" type="text" value="" name="Subject" onfocus="temp()" style="width: 100%" />
                            </td>
                        </tr>
                        <tr>
                            <td>
                                Description:
                            </td>
                            <td colspan="2">
                                <textarea id="customdescription" name="Description" rows="3" cols="50" style="width: 100%; resize: vertical"></textarea>
                            </td>
                        </tr>
                        <tr>
                            <td>
                                StartTime:
                            </td>
                            <td>
                                <input id="StartTime" type="text" value="" name="StartTime" />
                            </td>
                        </tr>
                        <tr>
                            <td>
                                EndTime:
                            </td>
                            <td>
                                <input id="EndTime" type="text" value="" name="EndTime" />
                            </td>
                        </tr>
                        <tr>
                            <td>Appointment Type:</td>
                            <td><input type="text" id="AppointmentType" /></td>
                        </tr>
                        <tr>
                            <td colspan="3">
                                <div class="customcheck">AllDay:</div>
                                <div class="customcheck">
                                    <input id="allDay" type="checkbox" name="AllDay" onchange="allDayCheck()" />
                                </div>
                                <div class="customcheck">Recurrence:</div>
                                <div>
                                    <input id="recurrence" type="checkbox" name="Recurrence" onchange="recurCheck()" />
                                </div>
                            </td>
                        </tr>
                        <tr id="summaryTr" style="display:none;">
                            <td colspan="3">
                                <div class="recSummary">Summary:</div>
                                <div>
                                    <label id="recSummary" name="Summary"></label>
                                </div>

                            </td>
                        </tr>
                        <tr id="editor" style="display:none;">
                            <td colspan="3">
                                <div><a id="recedit" onclick="recurrenceRule()">Edit</a></div>
                            </td>
                        </tr>
                    </tbody>
                </table>
            </form>
            <div>
                <button type="submit" onclick="cancel()" id="buttonCancel" style="float:right;margin-right:20px;margin-bottom:10px;">Cancel</button>
                <button type="submit" onclick="save()" id="buttonSubmit" style="float:right;margin-right:20px;margin-bottom:10px;">Submit</button>
            </div>
        </div>
        <div id="recWindow" style="display: none">
            <div id="recurrenceEditor"></div>
            <br />
            <div>
                <button type="submit" id="recCancel">Cancel</button>
                <button type="submit" id="recSubmit">Submit</button>
            </div>
        </div>
    </div>

{% endhighlight %}

The styles to be applied for the controls within the custom appointment window are as follows.

{% highlight html %}

<style>
    .customcheck {
        float: left;
        margin-right: 10px;
    }

    .error {
        background-color: #FF8A8A;
    }

    #custom table td {
        padding:5px;
    }
</style>

{% endhighlight %}

Now, define the Schedule control shown below.

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
    echo $schedule->width('100%')->height('525px')->appointmentWindowOpen("onAppointmentWindowOpen")->appointmentSettings($appointment)->render();
?>

{% endhighlight %}

Now, define the custom appointment window within script as shown below

{% highlight javascript %}

$(function () {

    $("#buttonCancel").ejButton({ width: '85px' });
    $("#buttonSubmit").ejButton({ width: '85px' });
    $("#recurrence").ejCheckBox({ change: "recurCheck" });
    $("#StartTime").ejDateTimePicker({ width: "150px" });
    $("#EndTime").ejDateTimePicker({ width: "150px" });
    // DataSource values for the appointment type field
    var types = [
        { text: "Tentative", id: 1 },
        { text: "Busy", id: 3 },
        { text: "Free", id: 5 },
        { text: "Out Of Office", id: 7 }
    ];
    $("#recCancel,#recSubmit").ejButton({ click: "onRecurrenceClick" });
    // defining recurrence editor control to be used as custom appointment window
    $("#recurrenceEditor").ejRecurrenceEditor({ selectedRecurrenceType: 0, frequencies: ["daily", "weekly", "monthly", "yearly", "everyweekday"] });

    // defining dropdown controls to be used within custom appointment window
    $("#AppointmentType").ejDropDownList({
        dataSource: types,
        fields: {
            text: "text",
            id: "id",
            value: "text"
        }
    });

    // defining dialog control to be used as custom appointment window
    $("#customWindow").ejDialog({
        width: 600,
        height: "auto",
        position: { X: 200, Y: 100 },
        showOnInit: false,
        enableModal: true,
        title: "Appointment Window",
        enableResize: false,
        allowKeyboardNavigation: false,
        close: "clearFields"
    });
});

{% endhighlight %}

The following function needs to be defined within script section, which gets called before the default appointment window opens.

{% highlight html %}

<script type="text/javascript">

function onAppointmentWindowOpen(args) {
    args.cancel = true; // prevents the display of default appointment window
    var schObj = $("#Schedule1").data("ejSchedule");
    // When double clicked on the Scheduler cells, fills the StartTime and EndTime fields appropriately
    $("#StartTime").ejDateTimePicker({ value: args.startTime });
    $("#EndTime").ejDateTimePicker({ value: args.endTime });
    $("#recWindow").css("display", "none");
    $("#appWindow").css("display", "");
    if (!ej.isNullOrUndefined(args.target)) {
        // When double clicked on the Scheduler cells, if the target is all day or month cells – only then enable check mark on the all day checkbox
        if ($(args.target.currentTarget).hasClass("e-alldaycells") || (args.startTime.getHours() == 0 && args.endTime.getHours() == 23))
            $("#allDay").prop("checked", true);
        else
            args.model.currentView == "month" ? $("#allDay").prop("checked", true) : $("#allDay").prop("checked", false);
        // If the target is allDay or month cells – disable the StartTime and EndTime fields
        $("#StartTime,#EndTime").ejDateTimePicker({
            enabled: ($(args.target.currentTarget).hasClass("e-alldaycells") || (args.startTime.getHours() == 0 && args.endTime.getHours() == 23) || $(args.target.currentTarget).hasClass("e-monthcells") || args.model.currentView == "month") ? false : true
        });
    }
    // If double clicked on the appointments, fill the custom appointment window fields with appropriate values.
    if (!ej.isNullOrUndefined(args.appointment)) {
        $("#customId").val(args.appointment.Id);
        $("#subject").val(args.appointment.Subject);
        $("#StartTime").ejDateTimePicker({ value: new Date(args.appointment.StartTime) });
        $("#EndTime").ejDateTimePicker({ value: new Date(args.appointment.EndTime) });
        // Fills the Appointment type dropdown with its value
        var value = args.appointment.AppointmentType;
        $("#AppointmentType").ejDropDownList("clearText");
        $("#AppointmentType").ejDropDownList({
            text: value,
            value: value
        });
        $("#allDay").prop("checked", args.appointment.AllDay);
        $("#recurrence").ejCheckBox({ checked: args.appointment.Recurrence });
        if (args.appointment.Recurrence) {
            $("#editor").css("display", "");
            $("#recSummary").html(args.appointment.RecurrenceRule);
            $("#summaryTr").css("display", "");
            recObj._recRule = args.appointment.RecurrenceRule; // app recurrence rule is stored in Recurrence editor object
            recObj.recurrenceRuleSplit(args.appointment.RecurrenceRule, args.appointment.recurrenceExDate); //splitting the recurrence rule
            recObj.showRecurrenceSummary(args.appointment.Id); // updating the recurrence rule in Recurrence editor
        }
    }
    $("#customWindow").ejDialog("open");
}

</script>

{% endhighlight %}

On clicking the **Submit** button within the Custom Appointment window, the following function gets executed – which will validate the appointment fields and then save it appropriately.

{% highlight html %}

<script type="text/javascript">

function save() {
    // checks if the subject value is not left blank before saving it.
    if ($.trim($("#subject").val()) == "") {
        $("#subject").addClass("error");
        return false;
    }
    var obj = {}, temp = {}, rType;
    var formElement = $("#customWindow").find("#custom").get(0);
    // looping through the custom form elements to get each value and form a JSON object
    for (var index = 0; index < formElement.length; index++) {
        var columnName = formElement[index].name, $element = $(formElement[index]);
        if (columnName != undefined) {
            if (columnName == "")
                columnName = formElement[index].id.replace(this._id, "");
            if (columnName != "" && obj[columnName] == null) {
                var value = formElement[index].value;
                if (columnName == "Id" && value != "")
                    value = parseInt(value);
                if ($element.hasClass("e-datetimepicker"))
                    value = new Date(value);
                if (formElement[index].type == "checkbox")
                    value = formElement[index].checked;
                obj[columnName] = value;
            }
        }
    }
    obj["RecurrenceRule"] = (obj.Recurrence) ? recurRule : null;
    var appTypeObj = $("#AppointmentType").data("ejDropDownList");
    obj["AppointmentType"] = appTypeObj.getSelectedValue();
    $("#customWindow").ejDialog("close");
    var object = $("#Schedule1").data("ejSchedule");
    object.saveAppointment(obj);
    clearFields();
}

// This function executes when the submit/cancel button in the recurrence editor window is pressed.
function onRecurrenceClick(args) {
    if ($(args.e.currentTarget).attr("id") == "recSubmit") {
        recObj = $("#recurrenceEditor").ejRecurrenceEditor('instance');
        recObj.closeRecurPublic();
        recurRule = recObj._recRule;
        $("#recSummary").html(recurRule);
    }
    else {
        if (($(args.e.currentTarget).attr("id") == "recCancel")) {
            if ($("#recSummary").html() == "") {
                $("#editor").css("display", "none");
                $("#recurrence").ejCheckBox({ checked: false });
            }
            else
                $("#recurrence").ejCheckBox({ checked: true });
        }
    }
    $("#recWindow").css("display", "none");
    $("#appWindow").css("display", "");
    if ($("#recSummary").html() != "")
        $("#summaryTr").css("display", "");
}

// This function executes when the Edit anchor tag in the edit appointment window is clicked.
function recurrenceRule() {
    $("#recWindow").css("display", "");
    $("#appWindow").css("display", "none");
}

// Clears all the field values of the custom window after saving appointments
function clearFields() {
    $("#customId").val("");
    recObj.clearRecurrenceFields();
    $("#subject").val("");
    $("#AppointmentType").val("");
    $("#recSummary").html("");
    $("#summaryTr").css("display", "none");
    $("#recurrence").ejCheckBox({ checked: false });
    $("#editor").css("display", "none");
    $("#StartTime,#EndTime").ejDateTimePicker({ enabled: true });
}

// This function executes when the recurrence checkbox is checked in the custom appointment window
function recurCheck(args) {
    if (args.isInteraction) {
        if ($("#recurrence").get(0).checked == true) {  // Displays the recurrence field, when recurrence checkbox is checked.
            $("#recWindow").css("display", "");
            $("#appWindow").css("display", "none");
            $("#editor").css("display", "");
        }
        else {
            $("#recWindow").css("display", "none");
            $("#editor").css("display", "none");
            $("#recSummary").html("");
            $("#summaryTr").css("display", "none");
        }
    }
}

// This function executes when the All-day checkbox is checked in the custom appointment window
function allDayCheck() {
    // Disables and sets the specific hours to the StartTime and EndTime fields, when the all-day checkbox is checked
    if ($("#allDay").prop("checked")) {
        var a = $("#StartTime").data("ejDateTimePicker").model.value;
        a.setHours(0, 0, 0);
        var b = $("#EndTime").data("ejDateTimePicker").model.value;
        b.setHours(23, 59, 0);
        $("#StartTime").ejDateTimePicker({ value: new Date(a), enabled: false });
        $("#EndTime").ejDateTimePicker({ value: new Date(b), enabled: false });
    }
    else {
        $("#StartTime").ejDateTimePicker({ enabled: true });
        $("#EndTime").ejDateTimePicker({ enabled: true });
    }
}

// This function executes when the subject text field is currently being focused
function temp() {
    $("#subject").removeClass("error");
}

// This function executes when the cancel button in the custom appointment window is pressed.
function cancel() {
    recObj = $("#recurrenceEditor").ejRecurrenceEditor('instance');
    clearFields();
    $("#customWindow").ejDialog("close");
}

</script>

{% endhighlight %}

## Scheduler Customization using queryCellInfo

It is possible to format and customize almost every child elements of scheduler such as work cells, header cells, time cells and so on using [queryCellInfo ](/api/js/ejschedule#events:appointmentwindowopen) event.

The following code snippet shows how to customize the appointment and work cells based on the query cell info event.

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
    echo $schedule->width('100%')->height('525px')->currentDate(new DateTime('2017/6/5'))->queryCellInfo("checkInfo")->appointmentSettings($appointment)->render();
?>

function checkInfo(args) {
    switch (args.requestType) {
        case "workcells":
            args.element.css("background-color", "#ffe9cc");
            break;
        case "monthcells":
            args.element.css("background-color", "#faa41a");
            args.element.css("border-color", "#faa41a");
            break;
    }
}

{% endhighlight %}

The Scheduler elements are listed below which can be formatted through this event. The names are listed in the format with which it can be accessed or used within the requestType argument of the event.

<table class="params">
    <thead>
        <tr>
            <th>Request Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td class="name">appointment</td>
            <td class="description">Depicts the appointment element within the Scheduler.</td>
        </tr>
        <tr>
            <td class="name">agendacells</td>
            <td class="description">Depicts the Agenda Cell element within the Scheduler.</td>
        </tr>
        <tr>
            <td class="name">alldaycells</td>
            <td class="description">Depicts the AllDay cell element within the Scheduler.</td>
        </tr>
        <tr>
            <td class="name">headercells</td>
            <td class="description">Depicts the header cell element within the Scheduler.</td>
        </tr>
        <tr>
            <td class="name">resourceheadercells</td>
            <td class="description">Depicts the resource header cell element within the Scheduler.</td>
        </tr>
        <tr>
            <td class="name">leftheadercells</td>
            <td class="description">Depicts the left empty space on header cell element within the Scheduler.</td>
        </tr>
        <tr>
            <td class="name">leftindentcells</td>
            <td class="description">Depicts the left empty space on date cell element within the Scheduler.</td>
        </tr>
        <tr>
            <td class="name">timecells</td>
            <td class="description">Depicts the left side time panel cell element within the Scheduler.</td>
        </tr>
        <tr>
            <td class="name">headerdate</td>
            <td class="description">Depicts the header date cell element within the Scheduler.</td>
        </tr>
        <tr>
            <td class="name">emptytd</td>
            <td class="description">Depicts the empty space above the vertical scroller within the Scheduler.</td>
        </tr>
        <tr>
            <td class="name">resourcegroupheader</td>
            <td class="description">Depicts the header group cell in horizontal orientation in the Scheduler.</td>
        </tr>
        <tr>
            <td class="name">monthcells</td>
            <td class="description">Depicts the month cell element within the Scheduler.</td>
        </tr>
        <tr>
            <td class="name">workcells</td>
            <td class="description">Depicts the work cell element within the Scheduler.</td>
        </tr>
    </tbody>
</table>
