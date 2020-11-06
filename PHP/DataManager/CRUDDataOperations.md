---
title: CRUD Data Operations
description: CRUD Data Operations
platform: php
control: DataManager
documentation: ug
keywords: Insert of Records, Delete, Update, Read, Remove, Add Fields
---

# CRUD Data Operations

The DataManager fully supports the CRUD (Create, Read, Update, Destroy) data operations. However, it must be combined with some user interface or another Syncfusion UI widget such as the Grid, ListView, etc.

## Local CRUD Operations

The information in this section is applicable to scenarios, in which the data is already available on the client, or when it is you that is going to take care of its retrieval and submission. In other words, DataManager will not make any HTTP requests on its own.

### Insert

The insert method of the data manager is used to add a new record to the table. The JSON data passed as a parameter to the insert method that is inserted to the data source of the data manager.

{% highlight html %}

    <div class="datatable">
        <table id="table1" class="table table-striped table-bordered" style="width:700px">
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
            var dataManager = ej.DataManager(data);
            var query = ej.Query()
                .from("Orders")
                .sortBy("OrderID", "descending", false)
            var record = { OrderID: 10253, CustomerID: "STRPQ", EmployeeID: 4 };
            dataManager.insert(record);
            // executing query
            var dataSource = dataManager.executeLocal(query);
            renderTable(dataSource);

        });

        // This function can be better replaced with any template engine. We used this for simplicity in demo.
        function renderTable(data) {
            var tableBody = "", row;
            for (var i = 0; i < data.length; i++) {
                row = data[i];
                tableBody += String.format("<tr><td>{0}</td><td>{1}</td><td>{2}</td></tr>", row.OrderID, row.CustomerID, row.EmployeeID);
            }
            $(".table tbody").html(tableBody);
        }
    </script>

{% endhighlight %}

![](CRUD_images/insert1.png) 

### Update

The update method is used to update the modified changes made to a record in the data source of the DataManager.

{% highlight html %}

    <div class="datatable">
        <table id="table1" class="table table-striped table-bordered" style="width:700px">
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
            var query = ej.Query().sortByDesc("EmployeeID");
            var data = [{ OrderID: 10248, CustomerID: "VINET", EmployeeID: 5 },
                        { OrderID: 10249, CustomerID: "AANAR", EmployeeID: 9 },
                        { OrderID: 10250, CustomerID: "VICTE", EmployeeID: 2 },
                        { OrderID: 10251, CustomerID: "TOMSP", EmployeeID: 7 },
                        { OrderID: 10252, CustomerID: "SUPRD", EmployeeID: 6 }];
            var updateData = { OrderID: 10252, CustomerID: "ZAUDS", EmployeeID: 4 };
            var dataManger = ej.DataManager(data);
            dataManger.update("OrderID", updateData, data);
            var result = dataManger.executeLocal(query);
            renderTable(result);

        });

        function renderTable(data) {
            var tableBody = "", row;
            for (var i = 0; i < data.length; i++) {
                row = data[i];
                tableBody += String.format("<tr><td>{0}</td><td>{1}</td><td>{2}</td></tr>", row.OrderID, row.CustomerID, row.EmployeeID);
            }
            $(".table tbody").html(tableBody);
        }
    </script>

{% endhighlight %}

![](CRUD_images/update1.png) 

### Remove

The remove function receives the items to be deleted in the Data Table. The function should remove the provided items from the data source of the DataManager.

{% highlight html %}

    <div class="datatable">
        <table id="table1" class="table table-striped table-bordered" style="width:700px">
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
            var query = ej.Query().sortByDesc("EmployeeID");
            var data = [{ OrderID: 10248, CustomerID: "VINET", EmployeeID: 5 },
                            { OrderID: 10249, CustomerID: "AANAR", EmployeeID: 9 },
                            { OrderID: 10250, CustomerID: "VICTE", EmployeeID: 2 },
                            { OrderID: 10251, CustomerID: "TOMSP", EmployeeID: 7 },
                            { OrderID: 10252, CustomerID: "SUPRD", EmployeeID: 6 }];
            var dataManager = ej.DataManager(data);
            dataManager.remove("OrderID", 10252, data);
            var dataSource = dataManager.executeLocal(query);
            renderTable(dataSource);

        });

        function renderTable(data) {
            var tableBody = "", row;
            for (var i = 0; i < data.length; i++) {
                row = data[i];
                tableBody += String.format("<tr><td>{0}</td><td>{1}</td><td>{2}</td></tr>", row.OrderID, row.CustomerID, row.EmployeeID);
            }
            $(".table tbody").html(tableBody);
        }
    </script>

{% endhighlight %}

![](CRUD_images/remove1.png) 

## Remote CRUD Operations

The information in this section is applicable to scenarios, in which the data should be retrieved from and submitted to a remote data service via HTTP requests made by the DataManager.
CRUD operations with remote data rely on server code to perform the read, update, create and destroy actions. Instead of configuring client functions, the DataManager defines remote service URLs and the expected format in which data should be sent and received. Theoretically, it is possible to use remote CRUD operations with transport functions, similar to the above examples that use local data, but this is rarely required.

Each of the CRUD operation settings—read, update, create, destroy—provides some common settings that need to be set accordingly:

* The client request type can be "get" or "post".
* Additional optional headers parameters can be sent to the server if needed.
* The client request and expected server response dataType can be "json", "jsonp", "odata", etc.

### Insert

The insert method of the data manager is used to add a new record to the table. The JSON data passed as a parameter to the insert method that is inserted to the data source of the data manager.

{% highlight html %}

    <div class="datatable">
        <table id="table1" class="table table-striped table-bordered" style="width:700px">
            <thead>
                <tr>
                    <th>ItemID</th>
                    <th>ItemName</th>
                    <th>ItemType</th>
                </tr>
            </thead>
            <tbody></tbody>
        </table>
    </div>
    <script type="text/javascript">
        $(function () {

            var dataManager = ej.DataManager({
                url: "http://mvc.syncfusion.com/Services/Northwnd.svc/Foods",
                crossDomain: true
            });
            var query = ej.Query()
                .sortBy("ItemID", "descending", false)
                    .select("ItemID", "ItemName", "ItemType")
            var record = { ItemID: 15, ItemName: "Orange Pie", ItemType: "Veg" };
            dataManager.insert(record);
            // executing query
            var dataSource = dataManager.executeQuery(query).done(function (args) {
                //Once data is inserted, showing in the Table
                renderTable(args.result);
            }).fail(function (args) {
                //error handling
            });

        });

    // This function can be better replaced with any template engine. We used this for simplicity in demo.
    function renderTable(data) {
        var tableBody = "", row;
        for (var i = 0; i < data.length; i++) {
            row = data[i];
            tableBody += String.format("<tr><td>{0}</td><td>{1}</td><td>{2}</td></tr>", row.ItemID, row.ItemName, row.ItemType);
        }
        $(".table tbody").html(tableBody);
    }
    </script>

{% endhighlight %}

![](CRUD_images/insert2.png) 

### Update

The update method is used to update the modified changes made to a record in the data source of the DataManager.

{% highlight html %}

    <div class="datatable">
        <table id="table1" class="table table-striped table-bordered" style="width:700px">
            <thead>
                <tr>
                    <th>ItemID</th>
                    <th>ItemName</th>
                    <th>ItemType</th>
                </tr>
            </thead>
            <tbody></tbody>
        </table>
    </div>

    <script type="text/javascript">
        $(function () {

            var dataManager = ej.DataManager({
                url: "http://mvc.syncfusion.com/Services/Northwnd.svc/Foods",
                crossDomain: true
            });
            var query = ej.Query()
                .sortBy("ItemID", "descending", false)
                    .select("ItemID", "ItemName", "ItemType")
            var updateData = { ItemID: 14, ItemName: "Grapes Juice", ItemType: "Veg" };
            dataManager.update("ItemID", updateData);
            // executing query
            var dataSource = dataManager.executeQuery(query).done(function (args) {

                renderTable(args.result);
            }).fail(function (args) {
                // handle error 
            });
        });

        // This function can be better replaced with any template engine. We used this for simplicity in demo.
        function renderTable(data) {
            var tableBody = "", row;
            for (var i = 0; i < data.length; i++) {
                row = data[i];
                tableBody += String.format("<tr><td>{0}</td><td>{1}</td><td>{2}</td></tr>", row.ItemID, row.ItemName, row.ItemType);
            }
            $(".table tbody").html(tableBody);
        }
    </script>

{% endhighlight %}

### Remove

The remove action submits the data items that should be deleted, or just its IDs. 

{% highlight html %}

    <div class="datatable">
        <table id="table1" class="table table-striped table-bordered" style="width:700px">
            <thead>
                <tr>
                    <th>ItemID</th>
                    <th>ItemName</th>
                    <th>ItemType</th>
                </tr>
            </thead>
            <tbody></tbody>
        </table>
    </div>

    <script type="text/javascript">
        $(function () {

            var dataManager = ej.DataManager({
                url: "http://mvc.syncfusion.com/Services/Northwnd.svc/Foods",
                crossDomain: true
            });
            var query = ej.Query()
                .sortBy("ItemID", "descending", false)
                .select("ItemID", "ItemName", "ItemType")

            dataManager.remove("ItemID", 14);
            // executing query
            var dataSource = dataManager.executeQuery(query).done(function (args) {

                renderTable(args.result);
            }).fail(function (args) {
            });

        });

        // This function can be better replaced with any template engine. We used this for simplicity in demo.
        function renderTable(data) {
            var tableBody = "", row;
            for (var i = 0; i < data.length; i++) {
                row = data[i];
                tableBody += String.format("<tr><td>{0}</td><td>{1}</td><td>{2}</td></tr>", row.ItemID, row.ItemName, row.ItemType);
            }
            $(".table tbody").html(tableBody);
        }

    </script>

{% endhighlight %}

## Batch Edit

Batch Editing is a unique feature, where requests to add, remove and change are handled altogether at a time rather than passing the request separately for each operation.

{% highlight html %}

    <div class="datatable">
        <table id="table1" class="table table-striped table-bordered" style="width:700px">
            <thead>
                <tr>
                    <th>Employee ID</th>
                    <th>First Name</th>
                    <th>Last Name</th>
                </tr>
            </thead>
            <tbody></tbody>
        </table>
    </div>
    EmployeeID
    <input id="EmployeeID" class="e-ejinputtext" type="text" value="" />
    First Name
    <input id="FirstName" class="e-ejinputtext" type="text" value="" />
    Last Name
    <input id="LastName" class="e-ejinputtext" type="text" value="" />

    <input type="button" value="Add" />
    <input type="button" value="Change" />
    <input type="button" value="Delete" />
    <input type="button" value="save All" />

    <script type="text/javascript">
        $(function () {
            window.gridData = [
            { FirstName: "John", EmployeeID: 1, LastName: "Paul"},
            { FirstName: "Ben", EmployeeID: 2, LastName: "Parker"},
            { FirstName: "Andrew", EmployeeID:3, LastName: "Becket"}];
   
            window.DataManager = ej.DataManager(window.gridData);
            window.changes = { changed: [], added: [], deleted: [] };

            var dataManager = ej.DataManager(window.gridData);
            var query = ej.Query()
                .sortBy("FirstName", "descending", false)
                .select("FirstName", "EmployeeID", "LastName")

            var result = dataManager.executeLocal(query);
            renderTable(result);

            $("input:button").ejButton({
                click: function (args) {
                    if (document.activeElement.value == "Change") {
                        data = dataManager.executeLocal(ej.Query().where("EmployeeID", ej.FilterOperators.equal, parseInt($("#EmployeeID").val(), 10)));
                        if (data.length) {
                            data[0].FirstName = $("#FirstName").val();
                            window.changes.changed.push(data);
                        }
                    }
                    else if (document.activeElement.value == "Add") {
                        window.changes.added.push({
                            EmployeeID: parseInt($("#EmployeeID").val(), 10),
                            FirstName: $("#FirstName").val(),
                            LastName: $("#LastName").val(),
                        });
                    }
                    else if (document.activeElement.value == "Delete") {
                        data = dataManager.executeLocal(ej.Query().where("EmployeeID", ej.FilterOperators.equal, parseInt($("#EmployeeID").val(), 10)));
                        if (data.length)
                            window.changes.deleted.push(data[0]);
                    }
                    else {
                        var tableData = ej.DataManager(window.gridData).saveChanges(window.changes);
                        renderTable(tableData);
                    }
                }
            });
        });
        function renderTable(data) {
            var tableBody = "", row;
            for (var i = 0; i < data.length; i++) {
                row = data[i];
                tableBody += String.format("<tr><td>{0}</td><td>{1}</td><td>{2}</td></tr>", row.EmployeeID, row.FirstName, row.LastName);
            }
            $(".table tbody").html(tableBody);
        }
    </script>

{% endhighlight %}

Result of the above code example is illustrated as follows.

![](Editing_images/Editing_img1.png)