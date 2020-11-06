---
title: ServerTimezoneOffset | DataManager | PHP | Syncfusion
description: ej.serverTimezoneOffset
platform: php
control: DataManager
documentation: ug
---

# ej.serverTimezoneOffset

This property is used to set the time-zone offset from UTC, in hours

### Property
<table>
    <tr> 
        <td>Name:</td> <td> ej.serverTimezoneOffset</td> 
    </tr>
    <tr>
        <td>Data type:</td> <td> number</td>
    </tr>
    <tr>
        <td>Default Value:</td> <td>  0 </td>
    </tr>
</table>

N> Suppose, application has been hosted in EST time zone and client may be in IST, GMT etc. in that case, date will differ from database. The below given solution will fix the conflict. 


<table>
    <tr>
        Time-zone offset calculation from UTC: <br>
        ej.serverTimezoneOffset = serverTimeZoneDifference(in hours) + ClientSideTimeZoneDifference(in hours); 
    </tr>
</table>

{% highlight html %}

    <div class="content-container-fluid">
        <div class="row">
            <div class="cols-sample-area">
                <div id="Grid"></div>
            </div>
        </div>
    </div>
    <script type="text/javascript">
        var serverTimeZoneDifference = -5.0   // if your server is in EST time zone (UTC -5.0) (in hours)
        var ClientSideTimeZoneDifference = new Date().getTimezoneOffset() / 60; // get client time zone difference and convert it to hours;
        ej.serverTimezoneOffset = serverTimeZoneDifference + ClientSideTimeZoneDifference;
        $(function () {
            var dataManager = ej.DataManager({ url: "http://mvc.syncfusion.com/services/Northwnd.svc/Orders" });
            $("#Grid").ejGrid({
                dataSource: dataManager,
                allowPaging: true,
                columns: ["OrderID", "EmployeeID", "CustomerID", "OrderDate", "Freight"]
            });
        });
    </script>

{% endhighlight %}

N> By default, The server time zone will be in UTC, hence server time-zone offset value for UTC is zero. if its other than the UTC, set the proper format time zone offset value to the ej.serverTimezoneOffset property. <br>
Please refer the online [link](https://en.wikipedia.org/wiki/Time_zone#List_of_UTC_offsets) for time zone offset values.

The countries that are using Eastern Standard Time (EST) when observing standard time (autumn/winter) are 5 hours behind Coordinated Universal Time (UTC−05:00).

Eastern Daylight Time (EDT), when observing daylight saving time DST (spring/summer) is 4 hours behind Coordinated Universal Time (UTC−04:00).

N> When the Daylight saving time mode is enabled in the server, take care about this time adjustment with the server time-zone offset calculation.

Let see an example, when they observe the Daylight saving time.

{% highlight html %}

    <div class="content-container-fluid">
        <div class="row">
            <div class="cols-sample-area">
                <div id="Grid"></div>
            </div>
        </div>
    </div>
    <script type="text/javascript">
        var serverTimeZoneDifference = -4.0  // if your server is in EDT time zone (UTC -4.0) (in hours)
        var ClientSideTimeZoneDifference = new Date().getTimezoneOffset() / 60; // get client time zone difference and convert it to hours;
        ej.serverTimezoneOffset = serverTimeZoneDifference + ClientSideTimeZoneDifference;
        $(function () {
            var dataManager = ej.DataManager({ url: "http://mvc.syncfusion.com/services/Northwnd.svc/Orders" });
            $("#Grid").ejGrid({
                dataSource: dataManager,
                allowPaging: true,
                columns: ["OrderID", "EmployeeID", "CustomerID", "OrderDate", "Freight"]
            });
        });
    </script>

{% endhighlight %}
