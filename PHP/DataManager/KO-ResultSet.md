---
title: KO-ResultSet | Syncfusion
description: ko resultset
platform: php
control: DataManager
documentation: ug
keywords : KO ResultSet
---

# KO ResultSet

The **DataManager** contains a default method to subscribe the view model properties as KO observable. This is done at the success of the **executeQuery** using the **getKnockoutModel.** You can also provide computed properties to the view model using the getKnockoutModel.

The following code example illustrates on how the model is made observable and updated.

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
                    <tbody data-bind="foreach: employees">
                        <tr>
                            <td data-bind="text: EmployeeID"></td>
                            <td data-bind="text: FullName"></td>
                        </tr>
                    </tbody>
                </table>
            </div>
            <div class="col-md-5">
                <form class="form-horizontal" role="form">
                    <div class="form-group">
                        <label class="col-sm-4 control-label">EmployeeID</label>
                        <div class="col-sm-8">
                            <input type="text" class="form-control" id="employee">
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
            window.data = [{ "EmployeeID": 1, "LastName": "Peacock", "FirstName": "Nancy" },
                { "EmployeeID": 2, "LastName": "Fuller", "FirstName": "Andrew" },
                { "EmployeeID": 3, "LastName": "Leverling", "FirstName": "Janet" },
                { "EmployeeID": 4, "LastName": "Peacock", "FirstName": "Margaret" },
                { "EmployeeID": 5, "LastName": "Buchanan", "FirstName": "Steven" },
                { "EmployeeID": 6, "LastName": "Suyama", "FirstName": "Michael" }
                            ];
            window.pageModel = {
                employees: []
            };
            var dataManager = ej.DataManager(data);
            var query = ej.Query();
            var promise = dataManager.executeQuery(query);
            promise.done(function (e) {
                pageModel.employees = e.getKnockoutModel({
                    FullName: function () {
                        return this.FirstName() + " " + this.LastName();
                    }
                });
                ko.applyBindings(pageModel);
            });               
            });
        $("#formSubmit").click(function (e) {
            var employee = parseInt($("#employee").val(), 10);
            var fName = $("#first").val();
            var lName = $("#last").val();
            employee = window.pageModel.employees()[employee - 1];
            employee.FirstName(fName);
            employee.LastName(lName);
        });
    </script>

{% endhighlight %}

The result of the above code example is illustrated as follows.

Before changing the model, EmployeeID 1 has FullName value as Nancy Peacock. After changing, the result is as follows.

![result](KO-ResultSet_images/KO-ResultSet_img1.png) 

