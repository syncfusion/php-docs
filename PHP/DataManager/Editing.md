---
title: Editing
description: editing
platform: php
control: DataManager
documentation: ug
keywords: DataManager editing
---

# Editing

Editing is a key feature in **DataManager** and it provides support to add a new record, edit an existing record and remove a record from the table. Here, you can learn in detail how these operations are performed using **DataManager**.

##Batch Edit

Batch Editing is a unique feature, where requests to add, remove and change are handled altogether at a time rather than passing the request separately for each operation.

{% highlight html %}

<div class="datatable">
   <table id="table1" class=" table table-striped table-bordered" style="width:700px">
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
<script id="template" type="text/x-jsrender">
   <tr>
       <td >{{:EmployeeID}}</td>
       <td>{{:FirstName}}</td>
       <td>{{:LastName}}</td>
   </tr>
</script>
<script type="text/javascript">
   $(function () {
       window.gridData = [
       { FirstName: "John", EmployeeID: 1, LastName: "Paul"},
       { FirstName: "Ben", EmployeeID: 2, LastName: "Parker"},
       { FirstName: "Andrew", EmployeeID:3, LastName: "Becket"}];
       window.change = function (args) {
           if (args.value) {
               data = window.DataManager.executeLocal(ej.Query().where("EmployeeID", ej.FilterOperators.equal, parseInt(args.value, 10)));
               if (data.length) {
                   $("#EmployeeID")[0].value = data[0]["EmployeeID"];
                   $("#FirstName").val(data[0]["FirstName"]);
                   $("#LastName").val(data[0]["LastName"]);
               }
           }
       }
       $(".e-ejinputtext").val("");
       window.DataManager = ej.DataManager(window.gridData);
       window.changes = { changed: [], added: [], deleted: [] };
       $("#table1").find("tbody").html($("#template").render(window.gridData));
       $("input:button").ejButton({
           click: function (args) {
               if (document.activeElement.value == "Change") {
                   data = window.DataManager.executeLocal(ej.Query().where("EmployeeID", ej.FilterOperators.equal, parseInt($("#EmployeeID").val(), 10)));
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
                   data = window.DataManager.executeLocal(ej.Query().where("EmployeeID", ej.FilterOperators.equal, parseInt($("#EmployeeID").val(), 10)));
                   if (data.length)
                       window.changes.deleted.push(data[0]);
               }
               else {
                   window.DataManager.saveChanges(window.changes, "EmployeeID");    $("#table1").find("tbody").empty().html($("#template").render(window.DataManager.dataSource.json));
               }
           }
       });
       });
       
</script>

{% endhighlight %}



Result of the above code example is illustrated as follows.



![](/js/DataManager/Editing_images/Editing_img1.png) 

##Insert

The `insert` method of the data manager is used to add a new record to the table. The **JSON** data passed as a parameter to the insert method that is inserted to the data source of the data manager.



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
   $(function () {// Document is ready.
       //oData Adaptor with DataManager
       var data = [{ OrderID: 10248, CustomerID: "VINET", EmployeeID: 5 },
       { OrderID: 10249, CustomerID: "AANAR", EmployeeID: 9 },
       { OrderID: 10250, CustomerID: "VICTE", EmployeeID: 2 },
       { OrderID: 10251, CustomerID: "TOMSP", EmployeeID: 7 },
       { OrderID: 10252, CustomerID: "SUPRD", EmployeeID: 6 }];
       var dataManager = ej.DataManager(data);
       var query = ej.Query()
           .from("Orders") 
           .sortBy("OrderID", "descending", false)
       var record = { OrderID: 10253, CustomerID: "STRPQ", EmployeeID: 4};
       dataManager.insert(record)
       var dataSource = dataManager.executeLocal(query) // executing query
                  $("#table1 tbody").html($("#tableTemplate").render(dataSource));
   });
</script>
<script id="tableTemplate" type="text/x-jsrender">
   <tr>
       <td>{{>OrderID}}</td>
       <td>{{>CustomerID}}</td>
       <td>{{>EmployeeID}}</td>
   </tr>
</script>

{% endhighlight %}



Result of the above code example is illustrated as follows.

![](/js/DataManager/Editing_images/Editing_img2.png) 

##Update

The `update` method is used to update the modified changes made to a record in the data source of the **DataManager**.

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
   var query = ej.Query().sortByDesc("EmployeeID");
   var data = [{ OrderID: 10248, CustomerID: "VINET", EmployeeID: 5 },
       { OrderID: 10249, CustomerID: "AANAR", EmployeeID: 9 },
       { OrderID: 10250, CustomerID: "VICTE", EmployeeID: 2 },
       { OrderID: 10251, CustomerID: "TOMSP", EmployeeID: 7 },
       { OrderID: 10252, CustomerID: "SUPRD", EmployeeID: 6 }];
   var updateData = { OrderID: 10252, CustomerID: "STRQP", EmployeeID: 4 };
   var dataManger = ej.DataManager(data);
   dataManger.update("OrderID", updateData, data);
   $(function () {
       // executing query
       var result = dataManger.executeLocal(query);
       $("#table1 tbody").html($("#tableTemplate").render(result));
   });
</script>
<script id="tableTemplate" type="text/x-jsrender">
   <tr>
       <td>{{>OrderID}}</td>
       <td>{{>CustomerID}}</td>
       <td>{{>EmployeeID}}</td>            
   </tr>
</script>

{% endhighlight %}



Result of the above code example is illustrated as follows.



![](/js/DataManager/Editing_images/Editing_img3.png) 

##Remove

The `remove` method is used to delete a record from the data source of the **DataManager**.

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
   var query = ej.Query().sortByDesc("EmployeeID");
   var data = [{ OrderID: 10248, CustomerID: "VINET", EmployeeID: 5 },
       { OrderID: 10249, CustomerID: "AANAR", EmployeeID: 9 },
       { OrderID: 10250, CustomerID: "VICTE", EmployeeID: 2 },
       { OrderID: 10251, CustomerID: "TOMSP", EmployeeID: 7 },
       { OrderID: 10252, CustomerID: "SUPRD", EmployeeID: 6 }];
   var dataManger = ej.DataManager(data);
   dataManger.remove("OrderID", 10252, data);
   $(function () {
       // executing query
       var result = dataManger.executeLocal(query);
       $("#table1 tbody").html($("#tableTemplate").render(result));
   });
</script>
<script id="tableTemplate" type="text/x-jsrender">
   <tr>
       <td>{{>OrderID}}</td>
       <td>{{>CustomerID}}</td>
       <td>{{>EmployeeID}}</td>            
   </tr>
</script>

{% endhighlight %}



Result of the above code example is illustrated as follows.

![](/js/DataManager/Editing_images/Editing_img4.png) 

