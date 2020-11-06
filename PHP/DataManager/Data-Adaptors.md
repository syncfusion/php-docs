---
title: Data-Adaptors
description: data adaptors
platform: php
control: DataManager
documentation: ug
keywords: JSON Adaptor, URL Adaptor, OData Adaptor, Odata4 Adaptor, WebApi Adaptor, Cache Adaptor, Custom Adaptor, RemoteSave Adaptor
---

# Data Adaptors

**DataManger** uses adaptors to process data. There are three types of adaptors in **DataManger**. They are

* JSON Adaptor

* URL Adaptor

* OData Adaptor

Here, you can learn when and how each adaptor is used.

## JSON Adaptor

**JSONAdaptor** is used to process **JSON** data. It contains methods to process the given **JSON** data based on the queries. 

**JSONAdaptor** has the following unique in-built methods, 

<table>
    <tr>
        <th> Properties<br/> </th>
        <th> Parameters<br/> </th>
        <th> Description <br/> </th>
    </tr>
     <tr>
        <td> processQuery(dataObj, query) </td>
        <td> 
            <table>
                <tr>  <td> dataObj </td> <td> Object </td> <td> ej.DataManager object </td> </tr>
                <tr>  <td> query </td> <td> ej.Query </td> <td>  Sets the default query for the data source </td> </tr>
            </table>
        </td>
        <td> Used to prepare query string for the request data </td>
    </tr>
    <tr>
        <td> processResponse(data, dataManagerObj, query, xhr) </td>
         <td> 
            <table>
                <tr>  <td> data </td> <td> Object </td> <td>  JSON data or JSON array </td> </tr>
                <tr>  <td> dataManagerObj </td> <td> Object </td> <td> ej.DataManager object </td> </tr>
                <tr>  <td> query </td> <td> ej.Query </td> <td>  Sets the default query for the data source </td> </tr>
                <tr>  <td> xhr </td> <td> Object </td> <td> XMLHTTPRequest object </td> </tr>
            </table>
        </td>
        <td> Used to precess the response which is return from the Data Source </td>
    </tr>
    <tr>
        <td> insert(dataObj, data) </td>
        <td> 
            <table>
                <tr>  <td> data </td> <td> Object </td> <td>  JSON data or JSON array </td> </tr>
                <tr>  <td> dataObj </td> <td> Object </td> <td> ej.DataManager object </td> </tr>
            </table>
        </td>
        <td> Inserts a data item in the data table. </td>
    </tr>
    <tr>
        <td> remove(dataObj, keyField, value, tableName) </td>
        <td> 
            <table>
                <tr>  <td> dataObj </td> <td> Object </td> <td>  ej.DataManager object </td> </tr>
                <tr>  <td> keyField </td> <td> String </td> <td> KeyColumn to find the data </td> </tr>
                <tr>  <td> String </td> <td> Object </td> <td> Specified value for the keyField</td> </tr>
                <tr>  <td> tableName </td> <td> String </td> <td> Name of the source table </td> </tr>
            </table>
        </td>
        <td> It is used to remove the data from the dataSource </td>
    </tr>
    <tr>
        <td> update(dataObj, keyField, value, tableName) </td>
        <td> 
            <table>
                <tr>  <td> dataObj </td> <td> Object </td> <td>  ej.DataManager object </td> </tr>
                <tr>  <td> keyField </td> <td> String </td> <td> KeyColumn to find the data </td> </tr>
                <tr>  <td> String </td> <td> Object </td> <td> Specified value for the keyField</td> </tr>
                <tr>  <td> tableName </td> <td> String </td> <td> Name of the source table </td> </tr>
            </table>
        </td>
        <td> Updates existing record and saves the changes to the table.. </td>
    </tr>
</table>

The following code example illustrates on how to use **JSONAdaptor**.

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
            $("#table1 tbody").html($("#tableTemplate")
                        .render(dataManager.executeLocal(new ej.Query().take(3))));
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

The result of above code example is illustrated as follows.

![](Data-Adaptors_images/Data-Adaptors_img1.png) 

## URL Adaptor

URL Adaptor of **DataManager** can be used when you are required to use remote service to retrieve data. It interacts with server-side for all **DataManager** Queries and **CRUD** operations. 

**UrlAdaptor** has the following unique in-built methods, 

<table>
    <tr>
        <th> Properties<br/> </th>
        <th> Parameters<br/> </th>
        <th> Description <br/> </th>
    </tr>
     <tr>
        <td> processQuery(dataObj, query, hierarchyFilters) </td>
        <td> 
            <table>
                <tr>  <td> dataObj </td> <td> Object </td> <td> ej.DataManager object </td> </tr>
                <tr>  <td> query </td> <td> ej.Query </td> <td>  Sets the default query for the data source </td> </tr>
                <tr>  <td> hierarchyFilters </td> <td> ej.Query </td> <td> The hierarchical query can be provided by using the hierarchical function.  </td> </tr>
            </table>
        </td>
        <td> Used to prepare query string for the request data </td>
    </tr>
    <tr>
        <td> processResponse(data, dataManagerObj, query, xhr, request, changes) </td>
         <td> 
            <table>
                <tr>  <td> data </td> <td> Object </td> <td>  JSON data or JSON array of Result</td> </tr>
                <tr>  <td> dataManagerObj </td> <td> Object </td> <td> ej.DataManager object </td> </tr>
                <tr>  <td> query </td> <td> ej.Query </td> <td>  Sets the default query for the data source </td> </tr>
                <tr>  <td> xhr </td> <td> Object </td> <td> XMLHTTPRequest object </td> </tr>
                <tr>  <td> request </td> <td> Object </td> <td>  request object to the Data Source </td> </tr>
                <tr>  <td> changes </td> <td> Object </td> <td> Specified changes to the Data Source </td> </tr>
            </table>
        </td>
        <td> Used to precess the response which is return from the Data Source </td>
    </tr>
    <tr>
        <td> insert(dataObj, data, tableName, query) </td>
        <td> 
            <table>
                <tr>  <td> data </td> <td> Object </td> <td>  JSON data or JSON array </td> </tr>
                <tr>  <td> dataObj </td> <td> Object </td> <td> ej.DataManager object </td> </tr>
                <tr>  <td> tableName </td> <td> String </td> <td> Name of the source table </td> </tr>
                <tr>  <td> query </td> <td> ej.Query </td> <td>  Sets the default query for the data source </td> </tr>
            </table>
        </td>
        <td> Inserts a data item in the data table. </td>
    </tr>
    <tr>
        <td> remove(dataObj, keyField, value, tableName, query) </td>
        <td> 
            <table>
                <tr>  <td> dataObj </td> <td> Object </td> <td>  ej.DataManager object </td> </tr>
                <tr>  <td> keyField </td> <td> String </td> <td> KeyColumn to find the data </td> </tr>
                <tr>  <td> String </td> <td> Object </td> <td> Specified value for the keyField</td> </tr>
                <tr>  <td> tableName </td> <td> String </td> <td> Name of the source table </td> </tr>
                <tr>  <td> query </td> <td> ej.Query </td> <td>  Sets the default query for the data source </td> </tr>
            </table>
        </td>
        <td> It is used to remove the data from the dataSource </td>
    </tr>
    <tr>
        <td> update(dataObj, keyField, value, tableName, query) </td>
        <td> 
            <table>
                <tr>  <td> dataObj </td> <td> Object </td> <td>  ej.DataManager object </td> </tr>
                <tr>  <td> keyField </td> <td> String </td> <td> KeyColumn to find the data </td> </tr>
                <tr>  <td> String </td> <td> Object </td> <td> Specified value for the keyField</td> </tr>
                <tr>  <td> tableName </td> <td> String </td> <td> Name of the source table </td> </tr>
                <tr>  <td> query </td> <td> ej.Query </td> <td>  Sets the default query for the data source </td> </tr>
            </table>
        </td>
        <td> Updates existing record and saves the changes to the table.. </td>
    </tr>
</table>

Now, in the following code example the data is retrieved from **MVC** **Controller**. 

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
            var dataManager = ej.DataManager({ url: "Home/Data", adaptor: new ej.UrlAdaptor() });
            var query = ej.Query().take(3);
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
        </tr>
    </script>


{% endhighlight %}

{% highlight c# %}

    public class HomeController : Controller
    {
        public JsonResult Data(DataManager dataObj)
        {
            List<Object> data = new List<object>();
            for (int i = 1; i <= 10; i++)
            {
                data.Add(new { OrderID = 10240 + i, CustomerID = "Customer" + i, EmployeeID = i });
            }
            var records = data.Take(dataObj.Take); // take query of Data Manager

            return Json(records, JsonRequestBehavior.AllowGet);
        }
    }

{% endhighlight %}


The result of the above code example is illustrated as follows.


![](Data-Adaptors_images/Data-Adaptors_img2.png) 

## OData Adaptor

**OData** Adaptor that is extended from **UrlAdaptor**, is used for consuming data through OData Service. You can use the following code example to use **OData** adaptor.

**ODataAdaptor** has the following unique in-built methods, 

<table>
    <tr>
        <th> Properties<br/> </th>
        <th> Parameters<br/> </th>
        <th> Description <br/> </th>
    </tr>
    <tr>
        <td> processResponse(data, dataManagerObj, query, xhr, request, changes) </td>
         <td> 
            <table>
                <tr>  <td> data </td> <td> Object </td> <td>  JSON data or JSON array </td> </tr>
                <tr>  <td> dataManagerObj </td> <td> Object </td> <td> ej.DataManager object </td> </tr>
                <tr>  <td> query </td> <td> ej.Query </td> <td>  Sets the default query for the data source </td> </tr>
                <tr>  <td> xhr </td> <td> Object </td> <td> XMLHTTPRequest object </td> </tr>
                <tr>  <td> request </td> <td> Object </td> <td>  request object to the Data Source </td> </tr>
                <tr>  <td> changes </td> <td> Object </td> <td> Specified changes to the Data Source </td> </tr>
            </table>
        </td>
        <td> Used to precess the response which is return from the Data Source </td>
    </tr>
     <tr>
        <td> insert(dataObj, data, tableName) </td>
        <td> 
            <table>
                <tr>  <td> data </td> <td> Object </td> <td>  JSON data or JSON array </td> </tr>
                <tr>  <td> dataObj </td> <td> Object </td> <td> ej.DataManager object </td> </tr>
                <tr>  <td> tableName </td> <td> String </td> <td> Name of the source table </td> </tr>
            </table>
        </td>
        <td> Inserts a data item in the data table. </td>
    </tr>
    <tr>
        <td> remove(dataObj, keyField, value, tableName) </td>
        <td> 
            <table>
                <tr>  <td> dataObj </td> <td> Object </td> <td>  ej.DataManager object </td> </tr>
                <tr>  <td> keyField </td> <td> String </td> <td> KeyColumn to find the data </td> </tr>
                <tr>  <td> String </td> <td> Object </td> <td> Specified value for the keyField</td> </tr>
                <tr>  <td> tableName </td> <td> String </td> <td> Name of the source table </td> </tr>
            </table>
        </td>
        <td> It is used to remove the data from the dataSource </td>
    </tr>
    <tr>
        <td> update(dataObj, keyField, value, tableName) </td>
        <td> 
            <table>
                <tr>  <td> dataObj </td> <td> Object </td> <td>  ej.DataManager object </td> </tr>
                <tr>  <td> keyField </td> <td> String </td> <td> KeyColumn to find the data </td> </tr>
                <tr>  <td> String </td> <td> Object </td> <td> Specified value for the keyField</td> </tr>
                <tr>  <td> tableName </td> <td> String </td> <td> Name of the source table </td> </tr>
            </table>
        </td>
        <td> Updates existing record and saves the changes to the table.. </td>
    </tr>
</table>

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
                url: "http://mvc.syncfusion.com/Services/Northwnd.svc/Orders",
                crossDomain: true,
                offline: true
            });
            var query = ej.Query()
                .select("OrderID", "CustomerID", "EmployeeID", "Freight", "ShipCountry").take(10)
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


The result of the above code example is illustrated as follows.

![](Data-Adaptors_images/Data-Adaptors_img3.png) 

## WebAPI Adaptor

**WebApi** Adaptor, extended from **ODataAdaptor**, of **DataManager** is used for retrieving data from WebApi service. 

**WebApiAdaptor** has the following unique in-built methods, 

<table>
    <tr>
        <th> Properties<br/> </th>
        <th> Parameters<br/> </th>
        <th> Description <br/> </th>
    </tr>
    <tr>
        <td> processResponse(data, dataManagerObj, query, xhr, request, changes) </td>
         <td> 
            <table>
                <tr>  <td> data </td> <td> Object </td> <td>  JSON data or JSON array </td> </tr>
                <tr>  <td> dataManagerObj </td> <td> Object </td> <td> ej.DataManager object </td> </tr>
                <tr>  <td> query </td> <td> ej.Query </td> <td>  Sets the default query for the data source </td> </tr>
                <tr>  <td> xhr </td> <td> Object </td> <td> XMLHTTPRequest object </td> </tr>
                <tr>  <td> request </td> <td> Object </td> <td>  request object to the Data Source </td> </tr>
                <tr>  <td> changes </td> <td> Object </td> <td> Specified changes to the Data Source </td> </tr>
            </table>
        </td>
        <td> Used to precess the response which is return from the Data Source </td>
    </tr>
     <tr>
        <td> insert(dataObj, data, tableName) </td>
        <td> 
            <table>
                <tr>  <td> data </td> <td> Object </td> <td>  JSON data or JSON array </td> </tr>
                <tr>  <td> dataObj </td> <td> Object </td> <td> ej.DataManager object </td> </tr>
                <tr>  <td> tableName </td> <td> String </td> <td> Name of the source table </td> </tr>
            </table>
        </td>
        <td> Inserts a data item in the data table. </td>
    </tr>
    <tr>
        <td> remove(dataObj, keyField, value, tableName) </td>
        <td> 
            <table>
                <tr>  <td> dataObj </td> <td> Object </td> <td>  ej.DataManager object </td> </tr>
                <tr>  <td> keyField </td> <td> String </td> <td> KeyColumn to find the data </td> </tr>
                <tr>  <td> String </td> <td> Object </td> <td> Specified value for the keyField</td> </tr>
                <tr>  <td> tableName </td> <td> String </td> <td> Name of the source table </td> </tr>
            </table>
        </td>
        <td> It is used to remove the data from the dataSource </td>
    </tr>
    <tr>
        <td> update(dataObj, keyField, value, tableName) </td>
        <td> 
            <table>
                <tr>  <td> dataObj </td> <td> Object </td> <td>  ej.DataManager object </td> </tr>
                <tr>  <td> keyField </td> <td> String </td> <td> KeyColumn to find the data </td> </tr>
                <tr>  <td> String </td> <td> Object </td> <td> Specified value for the keyField</td> </tr>
                <tr>  <td> tableName </td> <td> String </td> <td> Name of the source table </td> </tr>
            </table>
        </td>
        <td> Updates existing record and saves the changes to the table.. </td>
    </tr>
</table>

Refer to the following code example.

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
            var dataManager = ej.DataManager({ 
                url: "http://mvc.syncfusion.com/UGService/api/Orders", 
                crossDomain: true, 
                adaptor: new ej.WebApiAdaptor() });
            var query = ej.Query()
                .select("OrderID", "CustomerID", "EmployeeID").take(5)
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
        </tr>
    </script>

{% endhighlight %}

Result of the above code example is illustrated as follows.

![](Data-Adaptors_images/Data-Adaptors_img4.png) 

## RemoteSave Adaptor

**RemoteSaveAdaptor**, extended from **JsonAdaptor** of **DataManager**, is used for binding local data and performs all **DataManager** queries in client-side. It interacts with server-side only for **CRUD** operations to pass the modified records. 

**JSONAdaptor** has the following unique in-built methods, 

<table>
    <tr>
        <th> Properties<br/> </th>
        <th> Parameters<br/> </th>
        <th> Description <br/> </th>
    </tr>
    <tr>
        <td> insert(dataObj, data, tableName, query) </td>
        <td> 
            <table>
                <tr>  <td> data </td> <td> Object </td> <td>  JSON data or JSON array </td> </tr>
                <tr>  <td> dataObj </td> <td> Object </td> <td> ej.DataManager object </td> </tr>
                <tr>  <td> tableName </td> <td> String </td> <td> Name of the source table </td> </tr>
                <tr>  <td> query </td> <td> ej.Query </td> <td>  Sets the default query for the data source </td> </tr>
            </table>
        </td>
        <td> Inserts a data item in the data table. </td>
    </tr>
    <tr>
        <td> remove(dataObj, keyField, value, tableName, query) </td>
        <td> 
            <table>
                <tr>  <td> dataObj </td> <td> Object </td> <td>  ej.DataManager object </td> </tr>
                <tr>  <td> keyField </td> <td> String </td> <td> KeyColumn to find the data </td> </tr>
                <tr>  <td> String </td> <td> Object </td> <td> Specified value for the keyField</td> </tr>
                <tr>  <td> tableName </td> <td> String </td> <td> Name of the source table </td> </tr>
                <tr>  <td> query </td> <td> ej.Query </td> <td>  Sets the default query for the data source </td> </tr>
            </table>
        </td>
        <td> It is used to remove the data from the dataSource </td>
    </tr>
    <tr>
        <td> update(dataObj, keyField, value, tableName, query) </td>
        <td> 
            <table>
                <tr>  <td> dataObj </td> <td> Object </td> <td>  ej.DataManager object </td> </tr>
                <tr>  <td> keyField </td> <td> String </td> <td> KeyColumn to find the data </td> </tr>
                <tr>  <td> String </td> <td> Object </td> <td> Specified value for the keyField</td> </tr>
                <tr>  <td> tableName </td> <td> String </td> <td> Name of the source table </td> </tr>
                <tr>  <td> query </td> <td> ej.Query </td> <td>  Sets the default query for the data source </td> </tr>
            </table>
        </td>
        <td> Updates existing record and saves the changes to the table.. </td>
    </tr>
</table>

Refer to the following code example.

{% highlight html %}

    <div>
        <div class="row">
            <div class="col-md-3">
            OrderID
            </div>
            <div class="col-md-3">
            <input id="OrderID" class="e-ejinputtext" type="text" value="" />
            </div>
        </div>
        <div class="row">
            <div class="col-md-3">
            Customer ID
            </div>
            <div class="col-md-3">
            <input id="CustomerID" class="e-ejinputtext" type="text" value="" />
            </div>
        </div>
        <div class="row">
            <div class="col-md-3">
            Employee ID
            </div>
            <div class="col-md-3">
            <input id="EmployeeID" class="e-ejinputtext" type="text" value="" />
            </div>
        </div>
        <div class="row">
            <div class="col-md-3">
            <input type="button" value="Change" />
            <input type="button" value="Add" />
            <input type="button" value="Remove" />
            </div>
        </div>
    </div>
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
            var records = [{ OrderID: 10248, CustomerID: "Customer1", EmployeeID: 1 },
                    { OrderID: 10249, CustomerID: "Customer2", EmployeeID: 2 },
                    { OrderID: 10250, CustomerID: "Customer3", EmployeeID: 3 },
                    { OrderID: 10251, CustomerID: "Customer4", EmployeeID: 4 },
                    { OrderID: 10252, CustomerID: "Customer5", EmployeeID: 5 }];
            window.DataManager = ej.DataManager({ json: records, adaptor: new ej.remoteSaveAdaptor(), updateUrl: "Home/Update",insertUrl:"Home/Insert",removeUrl: "Home/Remove", offline:false });
        
            $("#table1 tbody").html($("#tableTemplate").render(window.DataManager.dataSource.json));
        
            $("input:button").ejButton({
                click: function (args) {
                    if (document.activeElement.value == "Change") {
                        var data = window.DataManager.executeLocal(new ej.Query().where("OrderID", ej.FilterOperators.equal, $("#OrderID").val(), 10));
                        if (data.length) {
                            data[0].OrderID = $("#OrderID").val();
                            data[0].CustomerID = $("#CustomerID").val();
                            data[0].EmployeeID = $("#EmployeeID").val();
                            window.DataManager.update("OrderID", data[0]).done(function (e) {
                                $("#table1").find("tbody").empty().html($("#tableTemplate").render(e));
                                window.DataManager.dataSource.json = e;
                                window.changes = null;
                                $(".e-ejinputtext").val("");
                            })
                        }
                    }
                    if (document.activeElement.value == "Add") {
                        var data = {OrderID: $("#OrderID").val(), CustomerID:$("#CustomerID").val(), EmployeeID: $("#EmployeeID").val()};
                            window.DataManager.insert(data).done(function (e) {
                                $("#table1").find("tbody").empty().html($("#tableTemplate").render(e.record));
                                window.DataManager.dataSource.json = e.record;
                                window.changes = null;
                                $(".e-ejinputtext").val("");
                            })
                    }
                    if (document.activeElement.value == "Remove") {
                        var data = $("#OrderID").val();
                        if (data.length) {
                            window.DataManager.remove("OrderID", data).done(function (e) {
                                $("#table1").find("tbody").empty().html($("#tableTemplate").render(e));
                                window.DataManager.dataSource.json = e;
                                window.changes = null;
                                $(".e-ejinputtext").val("");
                            })
                        }       
                    }
                }
            });
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

{% highlight c# %}

    public class HomeController : Controller
    {
        public static IList<EditableOrder> Data()
        {
            IList<EditableOrder> records = (IList<EditableOrder>)System.Web.HttpContext.Current.Session["Orders"];

            if (records == null)
            {
                List<EditableOrder> temp = new List<EditableOrder>();
                for (int i = 1; i <= 5; i++)
                {
                    var order = new EditableOrder() { OrderID = 10247 + i, CustomerID = "Customer" + i, EmployeeID = i };
                    temp.Add(order);
                }
                System.Web.HttpContext.Current.Session["Orders"] = records = temp;
            }
            return records;
        }
        public JsonResult Update(EditableOrder value)
        {

            var record = Data().Where(o => o.OrderID == value.OrderID).FirstOrDefault();
            if (record != null)
            {
                record.OrderID = value.OrderID;
                record.CustomerID = value.CustomerID;
                record.EmployeeID = value.EmployeeID;
            }
            return Json(Data(), JsonRequestBehavior.AllowGet);
        }
        public JsonResult Insert(EditableOrder value)
        {
            Data().Insert(0, value);
            return Json(Data(), JsonRequestBehavior.AllowGet);
        }
        public JsonResult Remove(int key)
        {
            var record = Data().Where(o => o.OrderID == key).FirstOrDefault();
            Data().Remove(record);
            return Json(Data(), JsonRequestBehavior.AllowGet);
        }
    }


{% endhighlight %}

Result of the above code example is illustrated as follows.

![](Data-Adaptors_images/Data-Adaptors_img5.png) 

## Custom Adaptor

Custom adaptor is a key technique to customize adaptors in **DataManager**. It is useful to write own adaptor. Normally **ej.Adaptor** is base class for all adaptors. Therefore you first inherit **ej.Adaptor** to develop customized one and then you override functionality in custom adaptor with base class. 

The following code example illustrates you on how to create custom adaptor.

{% highlight html %}

    <div class="datatable">
        <table id="table1" class="table table-striped table-bordered" style="width:700px">
            <thead>
            <tr>
                <th>FirstName</th>
                <th>LastName</th>
                <th>Email</th>
            </tr>
            </thead>
            <tbody></tbody>
        </table>
    </div>
    <script type="text/javascript">
        $(function () {// Document is ready.
        
            //new custom adaptor implementation
            //able to implement more option in custom adaptor other than insert
            var customAdaptor = new ej.Adaptor().extend({
                insert: function (dataObj, data) {
                    return dataObj.dataSource.json.push(data);
                },
                processQuery: ej.JsonAdaptor.prototype.processQuery // reused process query from json adaptor
            });
            window.gridData = [
        
                { FirstName: "John", LastName: "Beckett", Email: "john@syncfusion.com" },
                { FirstName: "Ben", LastName: "Beckett", Email: "ben@syncfusion.com" },
                { FirstName: "Andrew", LastName: "Beckett", Email: "andrew@syncfusion.com" }
            ];
        
            var dataManager = new ej.DataManager(window.gridData);
            // assigning custom adaptor to datamanager
            dataManager.adaptor = new customAdaptor();
            // insert from custom adaptor usage
            dataManager.insert({ FirstName: "Joel", LastName: "Beckett", Email: "joel@syncfusion.com" });
            
            $("#table1 tbody").html($("#tableTemplate")
                .render(dataManager.executeLocal(new ej.Query())));
        });
        
    </script>

    <script id="tableTemplate" type="text/x-jsrender">
        <tr>
            <td>{{"{{"}}>FirstName{{}}}}</td>
            <td>{{"{{"}}>LastName{{}}}}</td>
            <td>{{"{{"}}>Email{{}}}}</td>
        </tr>
    </script>

{% endhighlight %}

Result of above code example is as follows.

![](Data-Adaptors_images/Data-Adaptors_img6.png) 

Using Custom Adaptor, you can override the existing method of Extended Adaptor, 

<table>
    <tr>
        <th> Properties<br/> </th>
        <th> Description <br/> </th>
    </tr>
    <tr>
        <td> beforeSend </td>
        <td> Custom headers can be set using pre-request callback beforeSend, by using the setRequestHeader method can be used to modify the XMLHTTPRequest </td>
    </tr>
     <tr>
        <td> processQuery </td>
        <td> Used to prepare query string for the request data </td>
    </tr>
    <tr>
        <td> processResponse </td>
        <td> Used to precess the response which is return from the Data Source </td>
    </tr>
    <tr>
        <td> insert </td>
        <td> The insert method of the data manager is used to add a new record to the table </td>
    </tr>
    <tr>
        <td> remove </td>
        <td> The remove action submits the data items that should be deleted </td>
    </tr>
    <tr>
        <td> update </td>
        <td> The update method is used to update the modified changes made to a record in the data source of the DataManager. </td>
    </tr>
</table>

## Cache Adaptor

Cache Adaptor is used to cache the data of the visited pages. It prevents new requests for the previously visited pages. It can be enabled by using the `enableCaching` property. You can configure cache page size and duration of caching by using `cachingPageSize` and `timeTillExpiration` properties of the [`ej.DataManager`](https://help.syncfusion.com/api/js/ejdatamanager# "DataManager"). 

**CacheAdaptor** has the following unique in-built methods, 

<table>
    <tr>
        <th> Properties<br/> </th>
        <th> Parameters<br/> </th>
        <th> Description <br/> </th>
    </tr>
     <tr>
        <td> processQuery(dataObj, query, hierarchyFilters) </td>
        <td> 
            <table>
                <tr>  <td> dataObj </td> <td> Object </td> <td> ej.DataManager object </td> </tr>
                <tr>  <td> query </td> <td> ej.Query </td> <td>  Sets the default query for the data source </td> </tr>
                <tr>  <td> hierarchyFilters </td> <td> ej.Query </td> <td> The hierarchical query can be provided by using the hierarchical function.  </td> </tr>
            </table>
        </td>
        <td> Used to prepare query string for the request data </td>
    </tr>
    <tr>
        <td> processResponse(data, dataManagerObj, query, xhr, request, changes) </td>
         <td> 
            <table>
                <tr>  <td> data </td> <td> Object </td> <td>  JSON data or JSON array </td> </tr>
                <tr>  <td> dataManagerObj </td> <td> Object </td> <td> ej.DataManager object </td> </tr>
                <tr>  <td> query </td> <td> ej.Query </td> <td>  Sets the default query for the data source </td> </tr>
                <tr>  <td> xhr </td> <td> Object </td> <td> XMLHTTPRequest object </td> </tr>
                <tr>  <td> request </td> <td> Object </td> <td>  Sets the default query for the data source </td> </tr>
                <tr>  <td> changes </td> <td> Object </td> <td> XMLHTTPRequest object </td> </tr>
            </table>
        </td>
        <td> Used to precess the response which is return from the Data Source </td>
    </tr>
    <tr>
        <td> insert(dataObj, data, tableName) </td>
        <td> 
            <table>
                <tr>  <td> data </td> <td> Object </td> <td>  JSON data or JSON array </td> </tr>
                <tr>  <td> dataObj </td> <td> Object </td> <td> ej.DataManager object </td> </tr>
                <tr>  <td> tableName </td> <td> String </td> <td> Name of the source table </td> </tr>
            </table>
        </td>
        <td> Inserts a data item in the data table. </td>
    </tr>
    <tr>
        <td> remove(dataObj, keyField, value, tableName) </td>
        <td> 
            <table>
                <tr>  <td> dataObj </td> <td> Object </td> <td>  ej.DataManager object </td> </tr>
                <tr>  <td> keyField </td> <td> String </td> <td> KeyColumn to find the data </td> </tr>
                <tr>  <td> String </td> <td> Object </td> <td> Specified value for the keyField</td> </tr>
                <tr>  <td> tableName </td> <td> String </td> <td> Name of the source table </td> </tr>
            </table>
        </td>
        <td> It is used to remove the data from the dataSource </td>
    </tr>
    <tr>
        <td> update(dataObj, keyField, value, tableName) </td>
        <td> 
            <table>
                <tr>  <td> dataObj </td> <td> Object </td> <td>  ej.DataManager object </td> </tr>
                <tr>  <td> keyField </td> <td> String </td> <td> KeyColumn to find the data </td> </tr>
                <tr>  <td> String </td> <td> Object </td> <td> Specified value for the keyField</td> </tr>
                <tr>  <td> tableName </td> <td> String </td> <td> Name of the source table </td> </tr>
            </table>
        </td>
        <td> Updates existing record and saves the changes to the table.. </td>
    </tr>
</table>

{% highlight html %}

    <div id="CacheGrid"></div>

{% endhighlight %}

{% highlight javascript %}

    $(function() {

        var dataManger = ej.DataManager({ 
            url: "http://mvc.syncfusion.com/Services/Northwnd.svc/Orders/",
            enableCaching: true, 
            cachingPageSize: 10, 
            timeTillExpiration: 120000 }); 

        $("#CacheGrid").ejGrid({
            dataSource: dataManger, 
            allowPaging: true, 
            columns: ["OrderID", "CustomerID", "EmployeeID", "Freight", "ShipCity"] 
        }); 
    });

{% endhighlight %}

![](Data-Adaptors_images/Data-Adaptors_img7.png)

Cache Adaptor has the following unique properties, 

<table>
    <tr>
        <th> Properties<br/> </th>
        <th> Description <br/> </th>
    </tr>
    <tr>
        <td> TimeTillExpiration </td>
        <td> Specifies the duration of cached pages in milliseconds </td>
    </tr>
    <tr>
        <td> CachingPageSize </td>
        <td> A number of pages to be cached </td>
    </tr>
</table>