---
title: Paging
description: paging
platform: php
control: DataManager
documentation: ug
keywords: custom paging, paging, skip, take, range, requiresCount
---

# Paging

Paging is a very important query in **DataManager** that is used to display only some records from the large data source. Here, you can learn the paging query in detail.

## Default

The paging index and the paging size parameters of the paging query determines the number of records to be retrieved from the data source of the **DataManager**.

Refer to the following code example for the paging options.


{% highlight html %}

    <div class="datatable">
        <table id="table1" class="table table-striped table-bordered" style="width:700px">
            <thead>
                <tr>
                    <th>Order ID</th>
                    <th>Customer ID</th>
                    <th>Employee ID</th>
                    <th>Freight</th>
                    <th>Ship Country</th>
                </tr>
            </thead>
            <tbody></tbody>
        </table>
    </div>
    <script type="text/javascript">
        $(function () {// Document is ready.
            //oData Adaptor with DataManager
            var dataManager = ej.DataManager({
                url: "http://mvc.syncfusion.com/Services/Northwnd.svc/"            
            });
            var query = ej.Query()            
                .from("Orders")
                .select("OrderID", "CustomerID", " EmployeeID", "Freight", "ShipCountry")
                .page(3,10)
                .where("CustomerID", "contains", "A", false);
            var execute = dataManager.executeQuery(query) // executing query
                    .done(function (e) {
                        $("#table1 tbody").html($("#tableTemplate").render(e.result));
                    });
        });
    </script>
    <script id="tableTemplate" type="text/x-jsrender">
        <tr>
            <td>{{"{{"}}>OrderID{{}}}}</td>
            <td>{{"{{"}}>CustomerID{{}}}}</td>
            <td>{{"{{"}}>EmployeeID{{}}}}</td>
            <td>{{"{{"}}>Freight{{}}}}</td>
            <td>{{"{{"}}>ShipCountry{{}}}}</td>       
        </tr>
    </script>

{% endhighlight %}

Result for the above code example is illustrated as follows.

![](Paging_images/Paging_img1.png) 

## Dynamic Paging

The paging operation can be dynamically performed using the **DataManager**. With the help of an external button click event, the required page records can be obtained and processed accordingly. The following code example illustrates the dynamic paging.

{% highlight html %}

    Page index: <input type="text" value="1" id="index"/>
    Page Size: <input type="text" value="1" id="size"/>
    <input type="button" value="Execute" id="paging"/>
    <br/>
    <div class="datatable">
        <table id="table1" class="table table-striped table-bordered" style="width:700px">
            <thead>
                <tr>
                    <th>Order ID</th>
                    <th>Customer ID</th>
                    <th>Employee ID</th>
                    <th>Ship City</th>
                </tr>
            </thead>
            <tbody></tbody>
        </table>
    </div>
    <script type="text/javascript">
    $(function () {// Document is ready.
        data = ej.DataManager({
        url:"http://mvc.syncfusion.com/Services/Northwnd.svc/Orders"});
        var query = ej.Query().select("OrderID", "CustomerID", "EmployeeID", "ShipCity").page(1,5)
        var execute = data.executeQuery(query) // executing query
                .done(function (e) {
                    $("#table1 tbody").html($("#tableTemplate").render(e.result));
                });
        $("#paging").click(function () {
            var query = ej.Query().select("OrderID", "CustomerID", "EmployeeID", "ShipCity").page(
            function () {
                if($('#index').val() !="")
                    return $('#index').val();
                else
                    return 1; 
            },
            function () {
                if($('#size').val() !="")
                    return $('#size').val();
                else
                    return 2; 
            });
            var execute = data.executeQuery(query) // executing query
                    .done(function (e) {
                        $("#table1 tbody").html($("#tableTemplate").render(e.result));
                    });
        });
    });             
        
    </script>
    <script id="tableTemplate" type="text/x-jsrender">
        <tr>
            <td>{{"{{"}}>OrderID{{}}}}</td>
            <td>{{"{{"}}>CustomerID{{}}}}</td>
            <td>{{"{{"}}>EmployeeID{{}}}}</td>
            <td>{{"{{"}}>ShipCountry{{}}}}</td>    
        </tr>
    </script>

{% endhighlight %}

Result of above code example is illustrated as follows.

![](Paging_images/Paging_img2.png) 

## Custom paging

In this section, you can learn how to use customized paging. The following code example illustrates the custom paging.

{% highlight html %}

    <div class="datatable">
        <table id="table1" class="table table-striped table-bordered" style="width:700px">
            <thead>
                <tr>
                <th>Order ID</th>
                <th>Customer ID</th>
                <th>Employee ID</th>
                <th>Freight</th>
                <th>Ship Country</th>
                </tr>
            </thead>
            <tbody></tbody>
        </table>
    </div>
    <script type="text/javascript">
        $(function () {// Document is ready.
            //oData Adaptor with DataManager
            var dataManager = ej.DataManager({
                url: "http://mvc.syncfusion.com/Services/Northwnd.svc/"            
            });
            var query = ej.Query()            
                .from("Orders")
                .select("OrderID", "CustomerID", " EmployeeID", "Freight", "ShipCountry")
                .addParams("PageNumber",5)
                .addParams("PageSize",5)
                .where("CustomerID", "contains", "A", false);
            var execute = dataManager.executeQuery(query) // executing query
                    .done(function (e) {
                        $("#table1 tbody").html($("#tableTemplate").render(e.result));
                    });
        });
    </script>
    <script id="tableTemplate" type="text/x-jsrender">
        <tr>
            <td>{{"{{"}}>OrderID{{}}}}</td>
            <td>{{"{{"}}>CustomerID{{}}}}</td>
            <td>{{"{{"}}>EmployeeID{{}}}}</td>
            <td>{{"{{"}}>Freight{{}}}}</td>
            <td>{{"{{"}}>ShipCountry{{}}}}</td>    
        </tr>
    </script>

{% endhighlight %}

Result of above code example is illustrated as follows.

![](Paging_images/Paging_img3.png) 

## Skip

The `skip` query is used to skip some number of records.

{% highlight html %}

    <div class="datatable">
        <table id="table1" class="table table-striped table-bordered" style="width:700px">
            <thead>
                <tr>
                    <th>Order ID</th>
                    <th>Customer ID</th>
                    <th>Employee ID</th>
                    <th>Freight</th>
                    <th>Ship Country</th>
                </tr>
            </thead>
            <tbody></tbody>
        </table>
    </div>
    <script type="text/javascript">
        $(function () {// Document is ready.
            //oData Adaptor with DataManager
            var dataManager = ej.DataManager({
                url: "http://mvc.syncfusion.com/Services/Northwnd.svc/"            
            });
            var query = ej.Query()            
                .from("Orders")
                .select("OrderID", "CustomerID", " EmployeeID", "Freight", "ShipCountry")
                .skip(820)            
            var execute = dataManager.executeQuery(query) // executing query
                    .done(function (e) {
                        $("#table1 tbody").html($("#tableTemplate").render(e.result));
                    });
        });
    </script>
    <script id="tableTemplate" type="text/x-jsrender">
        <tr>
            <td>{{"{{"}}>OrderID{{}}}}</td>
            <td>{{"{{"}}>CustomerID{{}}}}</td>
            <td>{{"{{"}}>EmployeeID{{}}}}</td>
            <td>{{"{{"}}>Freight{{}}}}</td>
            <td>{{"{{"}}>ShipCountry{{}}}}</td>         
        </tr>
    </script>

{% endhighlight %}

Result of the above code example is illustrated as follows.

![](Paging_images/Paging_img4.png) 

## Take

The `take` query is used to get some certain number of records from the data source of the **DataManager**.

{% highlight html %}

    <div class="datatable">
        <table id="table1 class="table table-striped table-bordered" style="width:700px">
            <thead>
                <tr>
                    <th>Order ID</th>
                    <th>Customer ID</th>
                    <th>Employee ID</th>
                    <th>Freight</th>
                    <th>Ship Country</th>
                </tr>
            </thead>
            <tbody></tbody>
        </table>
    </div>
    <script type="text/javascript">
        $(function () {// Document is ready.
            //oData Adaptor with DataManager
            var dataManager = ej.DataManager({
                url: "http://mvc.syncfusion.com/Services/Northwnd.svc/"            
            });
            var query = ej.Query()            
                .from("Orders")
                .select("OrderID", "CustomerID", " EmployeeID", "Freight", "ShipCountry")
                .take(10)            
            var execute = dataManager.executeQuery(query) // executing query
                    .done(function (e) {
                        $("#table1 tbody").html($("#tableTemplate").render(e.result));
                    });
        });
    </script>
    <script id="tableTemplate" type="text/x-jsrender">
        <tr>
            <td>{{"{{"}}>OrderID{{}}}}</td>
            <td>{{"{{"}}>CustomerID{{}}}}</td>
            <td>{{"{{"}}>EmployeeID{{}}}}</td>
            <td>{{"{{"}}>Freight{{}}}}</td>
            <td>{{"{{"}}>ShipCountry{{}}}}</td>         
        </tr>
    </script>

{% endhighlight %}

Result of the above code example is illustrated as follows.

![](Paging_images/Paging_img5.png) 

## RequiresCount

The `requiresCount` query is used to get the count of the total number of records in the data source of the **DataManager**.

{% highlight html %}

    <div class="datatable">
        <table id="table1" class="table table-striped table-bordered" style="width:700px">
            <thead>
                <tr>
                    <th>Order ID</th>
                    <th>Customer ID</th>
                    <th>Employee ID</th>
                    <th>Freight</th>
                    <th>Ship Country</th>
                </tr>
            </thead>
            <tbody></tbody>
        </table>
        Total Records: <span id="totalCount"></span>
    </div>
    <script type="text/javascript">
        $(function () {// Document is ready.
            //oData Adaptor with DataManager
            var dataManager = ej.DataManager({
                url: "http://mvc.syncfusion.com/Services/Northwnd.svc/"            
            });
            var query = ej.Query()            
                .from("Orders")
                .select("OrderID", "CustomerID", " EmployeeID", "Freight", "ShipCountry")
                .page(1,5)
                .requiresCount()            
            var execute = dataManager.executeQuery(query) // executing query
                    .done(function (e) {
                        $("#table1 tbody").html($("#tableTemplate").render(e.result));
                        $("#totalCount").html(e.count)
                    });
        });
    </script>
    <script id="tableTemplate" type="text/x-jsrender">
        <tr>
            <td>{{"{{"}}>OrderID{{}}}}</td>
            <td>{{"{{"}}>CustomerID{{}}}}</td>
            <td>{{"{{"}}>EmployeeID{{}}}}</td>
            <td>{{"{{"}}>Freight{{}}}}</td>
            <td>{{"{{"}}>ShipCountry{{}}}}</td>           
        </tr>  
    </script>

{% endhighlight %}

Result of the above code example is illustrated as follows.

![](Paging_images/Paging_img6.png) 

## Range

The `range` query is used to get some particular range of records from the data source of the **DataManager**.

{% highlight html %}

    <div class="datatable">
        <table id="table1" class="table table-striped table-bordered" style="width:700px">
            <thead>
                <tr>
                    <th>Order ID</th>
                    <th>Customer ID</th>
                    <th>Employee ID</th>
                    <th>Freight</th>
                    <th>Ship Country</th>
                </tr>
            </thead>
            <tbody></tbody>
        </table>
    </div>
    <script type="text/javascript">
        $(function () {// Document is ready.
            //oData Adaptor with DataManager
            var dataManager = ej.DataManager({
                url: "http://mvc.syncfusion.com/Services/Northwnd.svc/"            
            });
            var query = ej.Query()            
                .from("Orders")
                .select("OrderID", "CustomerID", " EmployeeID", "Freight", "ShipCountry")
                .range(25,30)            
            var execute = dataManager.executeQuery(query) // executing query
                    .done(function (e) {
                        $("#table1 tbody").html($("#tableTemplate").render(e.result));
                    });
        });
    </script>
    <script id="tableTemplate" type="text/x-jsrender">
        <tr>
            <td>{{"{{"}}>OrderID{{}}}}</td>
            <td>{{"{{"}}>CustomerID{{}}}}</td>
            <td>{{"{{"}}>EmployeeID{{}}}}</td>
            <td>{{"{{"}}>Freight{{}}}}</td>
            <td>{{"{{"}}>ShipCountry{{}}}}</td>          
        </tr>
    </script>

{% endhighlight %}

Result of the above code example is illustrated as follows.

![](Paging_images/Paging_img7.png) 

