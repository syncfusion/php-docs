---
title: Searching
description: searching
platform: php
control: DataManager
documentation: ug
---

# Searching

Searching is a basic query technique in data manager. It is used to filter the records from the entire data source based on the `search` key parameter.

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
       //oData Adaptor with DataManager
       dataSource = [{ OrderID: 10248, CustomerID: "VINET", EmployeeID: 5 },
   { OrderID: 10249, CustomerID: "AANAR", EmployeeID: 4 },
   { OrderID: 10250, CustomerID: "VICTE", EmployeeID: 7 },
   { OrderID: 10251, CustomerID: "TOMSP", EmployeeID: 4 },
   { OrderID: 10252, CustomerID: "SUPRD", EmployeeID: 4 }];
   
       var dataManager = ej.DataManager(dataSource);
   
       var query = ej.Query()
           .from("Orders")                
           .search(4, "EmployeeID");
   
       var records = dataManager.executeLocal(query) // executing query
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

![](/js/DataManager/Searching_images/Searching_img1.png) 

