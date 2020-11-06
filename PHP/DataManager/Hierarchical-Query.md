---
title: Hierarchical-Query | DataManager | PHP | Syncfusion
description: hierarchical query
platform: php
control: DataManager
documentation: ug
keywords: Hierarchical Query, Complex query processing
---

# Hierarchical Query

The **DataManager** contains support to manage the hierarchical query. The hierarchical queries are commonly required when you use foreign key binding. The hierarchical query can be provided using the **hierarchical** function. This method accepts two parameters such as the query and the selector function. 

## ForeignKey

The **Foreign key** method of **ej.Query** can be used to refer another table fields. The foreign key method accepts one parameter that is the foreign key value. 

The following code example illustrates the hierarchical query and foreign key method. 


{% highlight html %}

    <div id="grid" class="e-grid" style="width:850px" >
        <div class="e-gridheader">
            <table class="e-table">
                <colgroup>
                    <col style="width:25%" />
                    <col style="width:25%"/>
                    <col style="width:25%"/>
                    <col style="width:25%"/>
                </colgroup>
            <thead>
                <tr>
                    <th class="e-headercell"><div class="e-headercelldiv">Order ID</div></th>
                    <th class="e-headercell"><div class="e-headercelldiv">Customer ID</div></th>
                    <th class="e-headercell"><div class="e-headercelldiv">Order Date</div></th>
                    <th class="e-headercell"><div class="e-headercelldiv">Employee</div></th>
                </tr>
            </thead>
            </table>
        </div>
        <div class="e-gridcontent">
            <table class="e-table">
                <tbody class="e-body">

                </tbody>
            </table>
        </div>
    </div>
    <script type="text/javascript">
        $(function () {
            // DataManager creation
            var dataManger = ej.DataManager({
                url: "http://mvc.syncfusion.com/Services/Northwnd.svc/",
                crossDomain: true
            });

            // Query creation
            var query = ej.Query()
                .from("Orders")
                .search("TM", ["CustomerID", "Employee.FirstName"])
                .page(1, 10)
                .hierarchy(
                    ej.Query()
                        .foreignKey("OrderID")
                        .from("Order_Details")
                        .sortBy("Quantity"),
                    function () {
                        // Selective loading of child elements
                        return [10410, 10492, 10949, 10742, 10975]
                    }
                )
                .select("OrderID", "CustomerID", "OrderDate", "Employee.FirstName")
                .expand("Employee");
            // executing query
            var promise = dataManger.executeQuery(query);
            promise.done(function (e) {
                
                $("#grid .e-body").html($("#tableTemplate").render(e.result));
                $("#grid").ejWaitingPopup("hide");
            });

            $("#grid").ejWaitingPopup({ autoDisplay: true });
        });
    </script>

    <script id="hierTemplate" type="text/x-jsrender">
        <tr>
            <td class="e-rowcell">{{"{{"}}>ProductID{{}}}}</td>
            <td class="e-rowcell">{{"{{"}}>Quantity{{}}}}</td>
            <td class="e-rowcell">{{"{{"}}>UnitPrice{{}}}}</td>
        </tr>
    </script>
    <script id="tableTemplate" type="text/x-jsrender">
        <tr>
            <td class="e-rowcell">{{"{{"}}>OrderID{{}}}}{{>OrderID}}</td>
            <td class="e-rowcell">{{"{{"}}>CustomerID{{}}}}{{>CustomerID}}</td>
            <td class="e-rowcell">{{"{{"}}>OrderDate.toDateString{{}}}}</td>
            <td class="e-rowcell">{{"{{"}}>Employee.FirstName{{}}}}</td>
        </tr>
        {{if Order_Details && Order_Details.length}}
        <tr class="childgrid">
            <td colspan="4">
            <div>
            <table class="e-table">
            <tbody>  
            <tr>
            <td colspan="3">
                <b>Order Details of {{>OrderID}}</b>
                <div class="e-grid">
                    <div class="e-gridheader">
                    <table class="e-table">
                        <thead>
                                <colgroup>
                                <col style="width:33%" />
                                <col style="width:33%"/>
                                <col style="width:33%"/>
                            </colgroup>
                            <tr>
                                <th class="e-headercell"><div class="e-headercelldiv">Product ID</div></th>
                                <th class="e-headercell"><div class="e-headercelldiv">Quantity</div></th>
                                <th class="e-headercell"><div class="e-headercelldiv">Unit Price</div></th>
                            </tr>
                        </thead>
                        </table>  
                    </div>
                    <div class="e-gridcontent"> 
                        <table class="e-table">
                            <tbody>
                            {{for Order_Details tmpl="#hierTemplate"/}}
                            </tbody>
                        </table>
                        </div>
                </div>
                </tr>
                </tbody>  
                </table>
            </td>
            </div>
            </td>
        </tr>
        {{/if}}
    </script>

{% endhighlight %}

The result for the above code example is illustrated as follows.

![hierarchical](Hierarchical-Query_images/Hierarchical-Query_img1.png) 



