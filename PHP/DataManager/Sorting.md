---
title: Sorting
description: sorting
platform: php
control: DataManager
documentation: ug
keywords: sorting, multi sorting, dynamic sorting, SortBy
---

# Sorting

## Default

Sorting is basic query in **DataManager**. It enables you to view the items or records in ascending or descending order based on particular field and sorting direction specified. The query parameter of **DataManager** enables you to retrieve the data in the sorted fashion and thus utilizing the resultant data obtained.

{% highlight html %}

    <div class="datatable">
        <table id="table1" class=" table table-striped table-bordered" style="width:700px">
            <thead>
                <tr>
                    <th>Order ID</th>
                    <th>Customer ID</th>
                    <th>Employee ID</th>
                </tr>
            </thead>
            <tbody>
            </tbody>
        </table>
    </div>
    <script type="text/javascript">

        $(function () 
        {

            var data = [{ OrderID: 10248, CustomerID: "VINET", EmployeeID: 5 },	                
            { OrderID: 10249, CustomerID: "AANAR", EmployeeID: 9 },	                    
            { OrderID: 10250, CustomerID: "VICTE", EmployeeID: 2 },
            { OrderID: 10251, CustomerID: "TOMSP", EmployeeID: 7 },	                    
            { OrderID: 10252, CustomerID: "SUPRD", EmployeeID: 6 }];

            var query = ej.Query().sortBy("CustomerID", ej.sortOrder.Ascending, false);

            var dataManager = ej.DataManager(data).executeLocal(query);

            $("#table1 tbody").html($("#tableTemplate").render(dataManager));

        });

    </script>

    <script id="tableTemplate" type="text/x-jsrender">
        <tr>
            <td>{{"{{"}}>OrderID{{}}}}</td>
            <td>{{"{{"}}>CustomerID{{}}}}</td>
            <td>{{"{{"}}>EmployeeID{{}}}}</td>        
        </tr>
    </script>

{% endhighlight %}


Result of the above code example is illustrated as follows.

![](Sorting_images/Sorting_img1.png) 

## SortByDesc

The `sortByDesc` query of the data manager is used to sort the specified field in descending order by default. You can use the following code example for `sortByDesc` query.

{% highlight html %}

    <div class="datatable">
        <table id="table1" class=" table table-striped table-bordered" style="width:700px">
            <thead>
                <tr>
                    <th>Order ID</th>
                    <th>Customer ID</th>
                    <th>Employee ID</th>
                </tr>
            </thead>
            <tbody></tbody>
        </table>
    </div>
    <script type="text/javascript">
        $(function () {
        
            var data = [{ OrderID: 10248, CustomerID: "VINET", EmployeeID: 5 },
                { OrderID: 10249, CustomerID: "AANAR", EmployeeID: 9 },
                { OrderID: 10250, CustomerID: "VICTE", EmployeeID: 2 },
                { OrderID: 10251, CustomerID: "TOMSP", EmployeeID: 7 },
                { OrderID: 10252, CustomerID: "SUPRD", EmployeeID: 6 }];
        
        var query = ej.Query().sortByDesc("EmployeeID");
            var dataManager = ej.DataManager(data).executeLocal(query);
            $("#table1 tbody").html($("#tableTemplate").render(dataManager));
        });

    </script>
    <script id="tableTemplate" type="text/x-jsrender">
        <tr>
            <td>{{"{{"}}>OrderID{{}}}}</td>
            <td>{{"{{"}}>CustomerID{{}}}}</td>
            <td>{{"{{"}}>EmployeeID{{}}}}</td>    
        </tr>
    </script>

{% endhighlight %}

Result of the above code example is illustrated as follows.

![](Sorting_images/Sorting_img2.png) 

## Dynamic sorting

The table can be dynamically sorted using an external button click event. The value of the column to be sorted can be obtained the sortBy query and thus the sorted data is retrieved and bounded to the table. The following code example illustrates you to dynamically sort the data source.

{% highlight html %}

    <select id="colName">
        <option value="OrderID">Order ID</option>
        <option value="CustomerID">Customer ID</option>
        <option value="EmployeeID">Employee ID</option>
        <option value="ShipCity">Ship City</option>
    </select>
    <input type="button" value="sort" id="sort"/>
    <br/>
    <div class="datatable">
        <table id="table1" class=" table table-striped table-bordered" style="width:700px">
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
                url: "http://mvc.syncfusion.com/Services/Northwnd.svc/Orders" });
            var query = ej.Query().take(5)
            var execute = data.executeQuery(query) // executing query
                .done(function (e) {
                    $("#table1 tbody").html($("#tableTemplate").render(e.result));
                });
            $("#sort").click(function () {
                var query = ej.Query().take(5).sortBy(
                    function () {
                        if ($('#colName').val() != "")
                            return $('#colName').val();
                        else
                            return "OrderID";
                    })
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

![](Sorting_images/Sorting_img3.png) 

## Multi sorting

Multi sorting is a special technique, where you can sort multiple fields by adding multiple sorting queries to **DataManager.**

{% highlight html %}

    <div class="datatable">
        <table id="table1" class=" table table-striped table-bordered" style="width:700px">
            <thead>
                <tr>
                    <th>Order ID</th>
                    <th>Customer ID</th>
                    <th>Employee ID</th>
                </tr>
            </thead>
            <tbody></tbody>
        </table>
    </div>
    <script type="text/javascript">
        $(function () {// Document is ready.
            dataSource = [{ OrderID: 10248, CustomerID: "VINET", EmployeeID: 5 },
            { OrderID: 10249, CustomerID: "AANAR", EmployeeID: 2 },
            { OrderID: 10250, CustomerID: "VICTE", EmployeeID: 7 },
            { OrderID: 10251, CustomerID: "TOMSP", EmployeeID: 7 },
            { OrderID: 10252, CustomerID: "SUPRD", EmployeeID: 6 }];
            var data = ej.DataManager(dataSource)

            var query = ej.Query().sortBy("CustomerID", "descending").sortBy("EmployeeID", "ascending")
            var records = data.executeLocal(query) // executing query
                        $("#table1 tbody").html($("#tableTemplate").render(records));
        });
    </script>
    <script id="tableTemplate" type="text/x-jsrender">
        <tr>
            <td>{{"{{"}}>OrderID{{}}}}</td>
            <td>{{"{{"}}>CustomerID{{}}}}</td>
            <td>{{"{{"}}>EmployeeID{{}}}}</td>
        </tr>
    </script>

{% endhighlight %}

Result of above code example is illustrated as follows.

![](Sorting_images/Sorting_img4.png) 