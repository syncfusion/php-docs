---
title: Grouping
description: grouping
platform: php
control: DataManager
documentation: ug
---

# Grouping

Grouping technique is also supported in **DataManager**. When you want to analyze any particular record based on its category simply you can group that column and analyze the records based on category. The following code example illustrates the grouping behavior in table.


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
           .page(1,5).group("CustomerID");
   
       var execute = dataManager.executeQuery(query) // executing query
              .done(function (e) {
                  $("#table1 tbody").html($("#groupTemplate").render(e.result));
              });
   });
</script>
<script id="groupTemplate" type="text/x-jsrender">
   <tr class='caption'>
       <th>Key: {{>key}}</th>
       <th colspan='3'>
           Count: {{>count}}</th>
   </tr>
   {{if items.GROUPGUID}}
   {{for items tmpl="#groupTemplate"/}}
   {{else}}
   {{for items tmpl="#tableTemplate"/}}
   {{/if}}
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

![](/js/DataManager/Grouping_images/Grouping_img1.png) 



