---
title: Filtering in DataManager | Syncfusion
description: Describes about Filtering in DataManager control.
platform: php
control: DataManager
documentation: ug
keywords: filter Operators, lessThan, lessThanOrEqual, less, contains
---

# Filtering

Filtering is a basic technique in **DataManager** query. The “where” query is used to filter some particular or related records from the data source to review details of records. 

## Filter Operators

Filter operators are generally used to specify the filter type. The various filter operators corresponding to the type of the column is listed in the following table.

<table>
<tr>
<th>
Column type</th><th>
Filter operators</th></tr>
<tr>
<td>
Number</td><td>
ej.FilterOperators.greaterThan<br/>ej.FilterOperators.greaterThanOrEqual<br/>ej.FilterOperators.lessThan<br/>ej.FilterOperators.lessThanOrEqual<br/>ej.FilterOperators.equal</td></tr>
<tr>
<td>
String</td><td>
ej.FilterOperators.startsWith<br/>ej.FilterOperators.endsWith<br/>ej.FilterOperators.contains<br/>ej.FilterOperators.equal<br/>ej.FilterOperators.notEqual</td></tr>
<tr>
<td>
Boolean</td><td>
ej.FilterOperators.equal<br/>ej.FilterOperators.notEqual</td></tr>
<tr>
<td>
Date</td><td>
ej.FilterOperators.greaterThan<br/>ej.FilterOperators.greaterThanOrEqual<br/>ej.FilterOperators.lessThan<br/>ej.FilterOperators.lessThanOrEqual<br/>ej.FilterOperators.equal</td></tr>
</table>


## lessThan

This operator is used to get the records with values less than that of the filter value.

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
                .from("Orders").select("OrderID", "CustomerID", " EmployeeID", "Freight", "ShipCountry")
                .page(1,10).where("OrderID", "lessThan", 10252, false);
        
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

![lessThan](Filtering_images/Filtering_img1.png) 

## greaterThan

This operator is used to get the records with values greater than that of the filter value.

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
                .from("Orders").select("OrderID", "CustomerID", " EmployeeID", "Freight", "ShipCountry")
                .page(1,5)
                .where("OrderID", "greaterThan", 10263, false);
        
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

![greaterThan](Filtering_images/Filtering_img2.png) 

## lessThanOrEqual

This operator is used to get the records with values less than or equal to the filter value.

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
                .select("OrderID", "CustomerID", " EmployeeID", "Freight", "ShipCountry")
                .page(1,10)
                .where("OrderID", "lessThanOrEqual", 10251, false);
        
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

![less Than Or Equal](Filtering_images/Filtering_img3.png) 

## greaterThanOrEqual

This operator is used to get the records with values greater than or equal to the filter value.

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
                .from("Orders").select("OrderID", "CustomerID", " EmployeeID", "Freight", "ShipCountry")
                .page(1,5)
                .where("OrderID", "greaterThanOrEqual", 10256, false);
        
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

![greater](Filtering_images/Filtering_img4.png) 

## equal

This operator is used to get the records with values equal to that of the filter value.

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
                .from("Orders").select("OrderID", "CustomerID", " EmployeeID", "Freight", "ShipCountry")
                .page(1,5).where("EmployeeID", "equal", 6, false);
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

![equal](Filtering_images/Filtering_img5.png) 

## notEqual

This operator is used to get the records with values not equal to that of the filter value specified.

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
                url: "http://mvc.syncfusion.com/Services/Northwnd.svc/"
            });
        
            var query = ej.Query()            
                .from("Orders")
                .select("OrderID", "CustomerID", " EmployeeID", "Freight", "ShipCountry")
                .page(1,5)
                .where("ShipCountry", "notEqual", "Rio de Janeiro", false);
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

![notEqual](Filtering_images/Filtering_img6.png) 

## contains

This operator is used to get the records that contains the filter value.

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
                .select("OrderID", "CustomerID", " EmployeeID", "Freight", "ShipCountry")
                .page(1,5)
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

Result of the above code example is illustrated as follows.

![contains](Filtering_images/Filtering_img7.png) 

## starts with

This operator is used to get the records that starts with the filter value specified.

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
                .from("Orders").select("OrderID", "CustomerID", " EmployeeID", "Freight", "ShipCountry")
                .page(1,5).where("CustomerID", "startswith", "V", false);
        
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

![starts with](Filtering_images/Filtering_img8.png) 

## ends with

This operator is used to get the records that ends with the filter value specified.


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
                .from("Orders").select("OrderID", "CustomerID", " EmployeeID", "Freight", "ShipCountry")
                .page(1,5).where("CustomerID", "endswith", "E", false);
        
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

![ends with](Filtering_images/Filtering_img9.png) 

## and predicate

The `and` predicate is used to add n-number of predicates with “and” condition and filter the data.

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
                .select("OrderID", "CustomerID", " EmployeeID", "Freight", "ShipCountry")
                .page(1,5)
                .where(ej.Predicate("OrderID", ej.FilterOperators.greaterThan, 10399, true).and("CustomerID", ej.FilterOperators.startsWith, "V", true));
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

![and predicate](Filtering_images/Filtering_img10.png) 

## or predicate

Using this method you can add n-number of predicates with `or` condition and filter the data.

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
                .select("OrderID", "CustomerID", " EmployeeID", "Freight", "ShipCountry")
                .page(1,5)
                .where(ej.Predicate("EmployeeID", ej.FilterOperators.greaterThan, 6, true)**.or**("CustomerID", ej.FilterOperators.startsWith, "S", true));
        
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

![or predicate](Filtering_images/Filtering_img11.png) 

## Containment Operators

### not contains

This operator is used to get the records that not contains the filter value.

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
            var dataManager = ej.DataManager({
                url: "http://mvc.syncfusion.com/Services/Northwnd.svc/"
            });

            var query = ej.Query()
                .from("Orders").select("OrderID", "CustomerID", " EmployeeID", "Freight", "ShipCountry")
                .page(1,5).where("ShipCountry", "notcontains", "CAN", false);

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

![not contains](Filtering_images/Filtering_image111.png) 

### contains

This operator is used to get the records that contains the filter value.

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
            var dataManager = ej.DataManager({
                url: "http://mvc.syncfusion.com/Services/Northwnd.svc/"
            });

            var query = ej.Query()
                .from("Orders").select("OrderID", "CustomerID", " EmployeeID", "Freight", "ShipCountry")
                .page(1, 5).where("ShipCountry", "contains", "CAN", false);

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

![contains](Filtering_images/Filtering_image12.png) 

### in

This operator used to fetch the records with value match with the given filter value. 

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
            var dataManager = ej.DataManager({
            url: "http://mvc.syncfusion.com/Services/Northwnd.svc/"
        });

        var query = ej.Query()
            .from("Orders").select("OrderID", "CustomerID", " EmployeeID", "Freight", "ShipCountry")
            .page(1, 5).where("ShipCountry", "IN", ['INDIA'], false);

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

![in](Filtering_images/Filtering_image13.png) 

### not in

This operator used to fetch the records with value not match with the given filter value. 

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
            var dataManager = ej.DataManager({
            url: "http://mvc.syncfusion.com/Services/Northwnd.svc/"
        });

        var query = ej.Query()
            .from("Orders").select("OrderID", "CustomerID", " EmployeeID", "Freight", "ShipCountry")
            .page(1, 5).where("ShipCountry", "notin", ['INDIA'], false);

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

![not](Filtering_images/Filtering_image14.png) 

![not in](Filtering_images/Filtering_image15.png) 

## Lambda Operators

### aLL

The ALL operator returns TRUE if all the sub query values meet the condition. This operator used to fetch the records of the fields match with the given value’s fields.

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
        var gridData=[{OrderID:10248,CustomerID:"VINET",EmployeeID:5,OrderDate:new Date(8364186e5),ShipName:"Vins et alcools Chevalier",ShipCity:"Reims",ShipAddress:"59 rue de l'Abbaye",ShipRegion:null,ShipPostalCode:"51100",ShipCountry:"France",Freight:32.38,Verified:!0}];
        var Data= [{OrderID:10248,CustomerID:"VINET",EmployeeID:5,OrderDate:new Date(8364186e5),ShipName:"Vins et alcools Chevalier",ShipCity:"Reims",ShipAddress:"59 rue de l'Abbaye",ShipRegion:null,ShipPostalCode:"51100",ShipCountry:"France",Freight:32.38,Verified:!0}];
        var dataManager = ej.DataManager(gridData);
        var source = ej.DataManager(Data);
        var result = ej.Query().select("ShipCountry")
        var ShipCountry = source.executeLocal(result);
        var query = ej.Query()            
            .where("ShipCountry", "equal all",ShipCountry , false).select("OrderID", "CustomerID", "EmployeeID","Freight","ShipCountry");
            var execute = dataManager.executeLocal(query); // executing query
        $("#table1 tbody").html($("#tableTemplate").render(execute));        });

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

![all](Filtering_images/Filtering_image16.png) 

### any

The ANY operator returns TRUE if any of the sub query values meet the condition. The returned data match with any one of the field in existing table.

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
            var gridData = window.gridData;
            var data = [{ OrderID: 10343, CustomerID: "LEHMS", EmployeeID: 4, OrderDate: new Date(8467002e5), ShipName: "Lehmanns Marktstand", ShipCity: "Frankfurt a.M.", ShipAddress: "Magazinweg 7", ShipRegion: null, ShipPostalCode: "60528", ShipCountry: "Germany", Freight: 110.37, Verified: !0 }, { OrderID: 10344, CustomerID: "WHITC", EmployeeID: 4, OrderDate: new Date(8467866e5), ShipName: "White Clover Markets", ShipCity: "Seattle", ShipAddress: "1029 - 12th Ave. S.", ShipRegion: "WA", ShipPostalCode: "98124", ShipCountry: "USA", Freight: 23.29, Verified: !1 }];

            var dataManager = ej.DataManager(data);
            var source = ej.DataManager(gridData1);
            var result = ej.Query().select("ShipCountry")
            var ShipCountry = source.executeLocal(result);
            var query = ej.Query()
			   .where("ShipCountry", "equal any", ShipCountry, false).select("OrderID", "CustomerID", "EmployeeID", "Freight", "ShipCountry");
            var execute = dataManager.executeLocal(query); // executing query
            $("#table1 tbody").html($("#tableTemplate").render(execute));  
          }
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

![any](Filtering_images/Filtering_image17.png) 