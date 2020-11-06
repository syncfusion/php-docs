---
title: Query
description: query
platform: php
control: DataManager
documentation: ug
keywords: select, clone, expand, from
---

# Query

**DataManager** provides support for multiple queries in order to perform various operations like filtering, sorting, cloning, expanding, searching, grouping etc., in the data source. Here, you can learn the query options in detail.

## Select

The `select` query of the data manager is used to select only some particular fields or columns from the data source. The following code example illustrates on how to select only particular fields using the select query.

{% highlight html %}

    <div class="datatable">
        <table id="table1" class=" table table-striped table-bordered" style="width:700px">
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
            var dataManager = ej.DataManager({//oData Adaptor with DataManager
                url: "http://mvc.syncfusion.com/Services/Northwnd.svc/Orders"
            });
        
            var query = ej.Query()            
                .select("OrderID", "CustomerID", "EmployeeID", "Freight", "ShipCountry").take(5)
        
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

![](Query_images/Query_img1.png)

## From

The `from` query of the data manager is used to select the table from where the data is retrieved and bound to the table. The following code example illustrates on how to use the `from` query.

{% highlight html %}

    <div class="datatable">
        <table id="table1" class=" table table-striped table-bordered" style="width:700px">
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
                .select("OrderID", "CustomerID", "EmployeeID", "Freight", "ShipCountry").take(5)
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

![](Query_images/Query_img2.png)

## Clone

The `clone` query of the data manager is used to duplicate the query. The following code example illustrates on how to `clone` a query.

{% highlight html %}

    <div class="datatable">
        <table id="table1" class=" table table-striped table-bordered" style="width:700px">
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
                .from("Orders").select("OrderID", "CustomerID", "EmployeeID", "Freight", "ShipCountry").take(5)
            var query1 = query.clone();
        
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

![](Query_images/Query_img3.png)

## Expand

The `expand` query of the data manager is used to perform complex data binding.


{% highlight html %}

    <div class="datatable">
        <table id="table1" class=" table table-striped table-bordered" style="width:700px">
            <thead>
                <tr>
                    <th>Order ID</th>
                    <th>Customer ID</th>
                    <th>Employee Name</th>
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
                .from("Orders").select("OrderID", "CustomerID", " Employee.FirstName", "Freight", "ShipCountry").take(5).expand("Employee")
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

![](Query_images/Query_img4.png)
