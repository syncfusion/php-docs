---
title: Table-Model
description: table model
platform: php
control: DataManager
documentation: ug
keywords : Table Model, getTableModel
---

# Table Model

The **DataManager** contains a default support to bind a TableModel to the element. You can make the data observable using the **getTableModel** method. The **getTableModel** method also accept extra properties or properties with computed value that can be added to the TableModel. In the view, you can create a simple view by using the bindings **getTableModel**

Then the model is bound with the element using the **bindTo.** 

{% highlight html %}

    <div class="datatable" style="padding:10px">
        <div class="row">
            <div class="col-md-7">
                <table id="table1" class="table table-striped table-bordered" style="width:700px">
                    <thead>
                        <tr>
                            <th>EmployeeID</th>
                            <th>Full Name</th>
                        </tr>
                    </thead>
                    <tbody id="tbody1">
                        <tr>
                            <td ej-observe="EmployeeID" ej-computed="EmployeeIndex"></td>
                            <td ej-computed="FullName"></td>
                        </tr>
                    </tbody>
                </table>
            </div>
            <div class="col-md-5">
                <form class="form-horizontal" role="form">
                    <div class="form-group">
                        <label class="col-sm-4 control-label">EmployeeID</label>
                        <div class="col-sm-8">
                            <input type="text" class="form-control" id="empId">
                        </div>
                    </div>
                    <div class="form-group">
                        <label class="col-sm-4 control-label">FirstName</label>
                        <div class="col-sm-8">
                            <input type="text" class="form-control" id="first">
                        </div>
                    </div>
                    <div class="form-group">
                        <label class="col-sm-4 control-label">LastName</label>
                        <div class="col-sm-8">
                            <input type="text" class="form-control" id="last">
                        </div>
                    </div>
                    <div class="form-group">
                        <div class="col-sm-offset-4 col-sm-4">
                            <button type="button" id="formSubmit" class="btn btn-default">Change</button>
                        </div>
                    </div>
                </form>
            </div>
        </div>
    </div>
    <script type="text/javascript">
        $(function () {
            window.data = [{ "EmployeeID": 1, "LastName": "Davolio", "FirstName": "Nancy" },
                { "EmployeeID": 2, "LastName": "Fuller", "FirstName": "Andrew" },
                { "EmployeeID": 3, "LastName": "Leverling", "FirstName": "Janet" },
                { "EmployeeID": 4, "LastName": "Peacock", "FirstName": "Margaret" },
                { "EmployeeID": 5, "LastName": "Buchanan", "FirstName": "Steven" },
                { "EmployeeID": 6, "LastName": "Suyama", "FirstName": "Michael" }
                            ];        
            window.employees = [];          
            var dataManager = ej.DataManager(data);
            var query = ej.Query();
            var promise = dataManager.executeQuery(query);
            promise.done(function (e) {
                employees = e.getTableModel({
                    FullName: {
                        value: function () {
                            return this.FirstName + ' ' + this.LastName;
                        },
                        deps: ["FirstName", "LastName"]
                    },
                    EmployeeIndex: {
                        value: function () {
                            return this.EmployeeID;
                        },
                        deps: ["EmployeeID"]
                    }
                });
                employees.bindTo($("#tbody1"));
            });
        
        });
        $("#formSubmit").click(function (e) {
            var empId = parseInt($("#empId").val(), 10);
            var fName = $("#first").val();
            var lName = $("#last").val();          
            employ = employees.get(empId - 1);
            employ.set("FirstName",fName);
            employ.set("LastName",lName);
        });               
    </script>

{% endhighlight %}

The result for the above code example is illustrated as follows.



![](Table-Model_images/Table-Model_img1.png) 

[Sample Link](http://jsplayground.syncfusion.com/2clbqjhr)


