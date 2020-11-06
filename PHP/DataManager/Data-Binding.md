---
title: Data-Binding
description: data binding
platform: php
control: DataManager
documentation: ug
keywords: DataManager data binding
---

# Data Binding

## JSON

A data source can be bound to a table through **JavaScript**. The **DataManager** supports **JSON** array binding. It is useful to bind records in client side using **JSON** data that is very helpful in Single Page Application (SPA) and in feature rich web application. To achieve this, you can refer the following code example.

{% highlight html %}
<body>
   <div class="datatable" style="padding:10px">
      <table id="table1" class="table table-striped table-bordered" style="width:700px">
         <thead>
            <tr>
               <th>Order ID</th>
               <th>Customer ID</th>
               <th>Employee ID</th>
               <th>Freight</th>
            </tr>
         </thead>
         <tbody></tbody>
      </table>
   </div>
   <script type="text/javascript">
      $(function () {
          window.data = [{ OrderID: 10248, CustomerID: "VINET", EmployeeID: 2, Freight: 32.38 },
                          { OrderID: 10249, CustomerID: "AANAR", EmployeeID: 9, Freight: 11.61 },
                          { OrderID: 10250, CustomerID: "VICTE", EmployeeID: 2, Freight: 65.83 },
                          { OrderID: 10251, CustomerID: "TOMSP", EmployeeID: 7, Freight: 70.63 },
                          { OrderID: 10252, CustomerID: "SUPRD", EmployeeID: 9, Freight: 45.45 },
                          ];
          var dataManager = ej.DataManager(data);
          var query = ej.Query();
          var promise = dataManager.executeLocal(query);
          $("#table1 tbody").html($("#tableTemplate").render(promise));
      });
   </script>
   <script id="tableTemplate" type="text/x-jsrender">
      <tr>
        <td>{{"{{"}}>OrderID{{}}}}</td>
        <td>{{"{{"}}>CustomerID{{}}}}</td>
        <td>{{"{{"}}>EmployeeID{{}}}}</td>
        <td>{{"{{"}}>Freight{{}}}}</td>
      </tr>       
   </script>
</body>

{% endhighlight %}



The result of the above code example is illustrated as follows.



![](/js/DataManager/Data-Binding_images/Data-Binding_img1.png) 

## REST Services

###OData binding

**OData** is standardized protocol for creating and consuming data. You can retrieve data from OData service using **DataManager.** You can refer to the following code example of remote Data binding using OData service.



{% highlight html %}

<body>
   <div class="datatable">
      <table id="table1">
         <thead>
            <tr>
               <th>Item ID</th>
               <th>Item Name</th>
               <th>Item Type</th>
               <th>Price</th>
               <th>Stock</th>
            </tr>
         </thead>
         <tbody></tbody>
      </table>
   </div>
   <script type="text/javascript">
      var dataManger = ej.DataManager(
                           "http://mvc.syncfusion.com/Services/Northwnd.svc"
                       );
      
      // Query creation
      var query = ej.Query()
          .from("Foods")
          .select("ItemID", "ItemName", "ItemType", "Price", "Stock").take(7)
      var execute = dataManger.executeQuery(query) // executing query
             .done(function (e) {
                 $("#table1 tbody").html($("#tableTemplate").render(e.result));
             });
      
   </script>
   <script id="tableTemplate" type="text/x-jsrender">
      <tr>
        <td>{{"{{"}}>ItemID{{}}}}</td>
        <td>{{"{{"}}>ItemName{{}}}}</td>
        <td>{{"{{"}}>ItemType{{}}}}</td>
        <td>{{"{{"}}>Price{{}}}}</td>
        <td>{{"{{"}}>Stock{{}}}}</td>
      </tr>
   </script>
</body>

{% endhighlight %}



The result of the above code example is illustrated as follows.

![](/js/DataManager/Data-Binding_images/Data-Binding_img2.png) 

## OData V4

The OData v4 is an improved version of OData protocols and the **DataManager** can also retrieve and consume OData v4 services.  For more details on OData v4 Services, refer the [odata documentation](http://www.odata.org/documentation/).

You can refer to the following code example for consuming OData v4 services and bind the result to the simple **HTML** table. In the the following code, `crossDomain` is enabled to make cross domain request.

{% highlight html %}

<body>
   <div class="datatable" style="padding:10px">
      <table id="table1" class="table table-striped table-bordered" style="width:700px" >
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
          var dataManager = ej.DataManager({ url: "http://services.odata.org/V4/Northwind/Northwind.svc/", crossDomain: true });
          var query = new ej.Query().from("Orders").select("OrderID", "CustomerID", "EmployeeID").take(5);
          var promise = dataManager.executeQuery(query);
          promise.done(function (e) {
              $("#table1 tbody").html($("#tableTemplate").render(e.result.value));
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
</body>

{% endhighlight %}



The request and response to the service from the **DataManager** is illustrated as follows.



![](/js/DataManager/Data-Binding_images/Data-Binding_img3.png) 

 _OData v4 request and response_

The result of the above code example is illustrated as follows.



![](/js/DataManager/Data-Binding_images/Data-Binding_img4.png) 

 _OData v4 binding_

## WebAPI binding

The Web API is a programmatic interface to define the request and response messages system that is mostly exposed in **JSON** or **XML**. The **DataManager** contains default adaptor to handle the Web API request and responses. The **WebApiAdaptor** is discussed briefly in the Adaptor section.

Refer to the following code example for consuming Web API data using ej.DataManager.



{% highlight html %}

<body>
   <div class="datatable" style="padding:10px">
      <table id="table1" class="table table-striped table-bordered" style="width:700px" >
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
          var dataManager = ej.DataManager({ url: "http://mvc.syncfusion.com/UGService/api/Orders", crossDomain: true, adaptor:new ej.WebApiAdaptor() });
          var query = new ej.Query().take(5);
          var promise = dataManager.executeQuery(query);
          promise.done(function (e) {
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
</body>
{% endhighlight %}



The request to the Web API and response is illustrated as follows.

![](/js/DataManager/Data-Binding_images/Data-Binding_img5.png) 

_Web API adaptor request and response_

The result for the above code example is illustrated as follows.



![](/js/DataManager/Data-Binding_images/Data-Binding_img6.png) 

_Web API data binding_

## Other Web Services binding

The ejDataManager can also retrieve data from **ASP.Net Web** methods and **ASP.Net MVC** Controller`s action. You can achieve this by using the UrlAdaptor of ej.DataManager. The UrlAdaptor is discussed briefly in the adaptor section.  By default, the UrlAdaptor is used when accessing remote data. 

Refer to the following code example to know how the **DataManager** can be used to consume data from the web method.



{% highlight html %}

<asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">
   <div class="datatable" style="padding:10px">
      <table id="table1" class="table table-striped table-bordered" style="width:700px" >
         <thead>
            <tr>
               <th>University Code</th>
               <th>Title</th>
               <th>Course Fees</th>
            </tr>
         </thead>
         <tbody></tbody>
      </table>
   </div>
</asp:Content>

<asp:Content runat="server" ID="ScriptContent" ContentPlaceHolderID="ScriptContent">
   <script type="text/javascript">
      $(function () {
          var dataManager = ej.DataManager({ url: "WebService1.asmx/getData" });
          var promise = dataManager.executeQuery(new ej.Query());
          promise.done(function (e) {
              $("#table1 tbody").append($("#tableTemplate").render(e.result));
          });
      });
   </script>
   <script id="tableTemplate" type="text/x-jsrender">
      <tr>
        <td>{{"{{"}}>UniversityCode{{}}}}</td>
        <td>{{"{{"}}>Title{{}}}}</td>
        <td>{{"{{"}}>CourseFees{{}}}}</td>
      </tr>
   </script>
</asp:Content>

{% endhighlight %}


![](/js/DataManager/Data-Binding_images/Data-Binding_img7.png) 

Consuming data from the MVC controller`s action is as follows. Now the data from the action is handled by the UrlAdaptor.



{% highlight html %}

<body>
   <div class=”datatable”>
      <table id=”table1” class=”table table-striped table-bordered” style=”width:700px”>
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
   <script type=”text/javascript”>
      $(function () {
          var dataManager = ej.DataManager({ url: “Home/Data”, adaptor: new ej.UrlAdaptor() });
          var query = ej.Query().take(3);
          var execute = dataManager.executeQuery(query) // executing query
                 .done(function I {
                     $(“#table1 tbody”).html($(“#tableTemplate”).render(e.result));
                 });
      });
   </script>
   <script id=”tableTemplate” type=”text/x-jsrender”>
      <tr>
        <td>{{"{{"}}>OrderID{{}}}}</td>
        <td>{{"{{"}}>CustomerIDTitle{{}}}}</td>
        <td>{{"{{"}}>EmployeeID{{}}}}</td>
      </tr>
   </script>
</body>

{% endhighlight %}



{% highlight c# %}


    public class HomeController : Controller
    {
       public JsonResult Data(DataManager dataObj)
        {
            List<Object> data = new List<object>();
            for (int i = 1; i <= 10; i++)
            {
                data.Add(new { OrderID = 10240 + i, CustomerID = “Customer” + i, EmployeeID = i });
            }
            var records = data.Take(dataObj.Take); // take query of Data Manager
            return Json(records, JsonRequestBehavior.AllowGet);
        }
    }
{% endhighlight %}



The result and the request-response to the controller is illustrated as follows.

![](/js/DataManager/Data-Binding_images/Data-Binding_img8.png) 
