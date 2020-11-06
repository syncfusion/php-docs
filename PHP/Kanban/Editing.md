---
layout: post
title:  Essential EJ1 Syncfusion PHP Kanban Editing
description: This section explains how to enable different editing mode and its functionalities using the Syncfusion PHP Kanban component.
documentation: ug
platform: php
keywords: editing,kanban editing
---

# Editing

The Kanban control has support for dynamic insertion, updating and deletion of cards. 

Set `allowEditing` and `allowAdding` property as true to enable editing/inserting respectively. The primary key for the data source should be defined in `primaryKey`, for editing to work properly. 

You can start the edit action by double clicking the particular card. Similarly, you can add new card to Kanban either by double clicking the particular cell or on an external button which is bound to call `addCard` method of Kanban. 

Deletion of the card is possible by using `deleteCard` by passing primary key as attribute.

N> In Kanban, the `primary key` column will be automatically set to `read only` while editing the card which is to avoid duplicate entry in the cards.

## Configuring Edit Items

You need to configure the list of data source fields that are allowable in editing state using `editItems` property. The `field` property of `editItems` needs to be mapped with data source fields.

You can map the data source field as title to edit form using `title` property of `fields`. By default, it’s mapped with `primaryKey`.

The following code example describes the above behavior.

{% highlight html %}

    <?php
    require_once "../EJ/AutoLoad.php";
    ?>
    <div class="cols-sample-area">
    <?php
    $Json = '[{"Id": 1, "Status": "Open", "Summary": "Analyze the new requirements gathered from the customer.", "Type": "Story", "Priority": "Low", "Tags": "Analyze,Customer", "Estimate": 3.5, "Assignee": "Nancy Davloio", "ImgUrl": "Content/images/kanban/1.png", "RankId":1 }, { "Id": 2, "Status": "InProgress", "Summary": "Improve application performance", "Type": "Improvement", "Priority": "Normal", "Tags": "Improvement", "Estimate": 6, "Assignee": "Andrew Fuller", "ImgUrl": "Content/images/kanban/2.png", "RankId":1 }, { "Id": 3, "Status": "Open", "Summary": "Arrange a web meeting with the customer to get new requirements.", "Type": "Others", "Priority": "Critical", "Tags": "Meeting", "Estimate": 5.5, "Assignee": "Janet Leverling", "ImgUrl": "Content/images/kanban/3.png", "RankId":2 }, { "Id": 4, "Status": "InProgress", "Summary": "Fix the issues reported in the IE browser.", "Type": "Bug", "Priority": "Release Breaker", "Tags": "IE", "Estimate": 2.5, "Assignee": "Janet Leverling", "ImgUrl": "Content/images/kanban/3.png", "RankId":2 }, { "Id": 5, "Status": "Close", "Summary": "Fix the issues reported by the customer.", "Type": "Bug", "Priority": "Low", "Tags": "Customer", "Estimate": "3.5", "Assignee": "Steven walker", "ImgUrl": "Content/images/kanban/5.png", "RankId":1 }]';
    $Json = json_decode($Json,true);
    $colorMap = '{"#ee4e75": "Bug,Story","#57b94c": "Improvement","#edba3c": "Epic","#5187c6": "Others"}';
    $colorMap = json_decode($colorMap,true);
    $kanban = new EJ\Kanban("dialogEdit");
    $column = new EJ\Kanban\Column();
    $column ->key("Open")->headerText("Backlog");
    $column1 = new EJ\Kanban\Column();    
    $column1 ->key("InProgress")->headerText("In Progress");
    $column2 = new EJ\Kanban\Column();
    $column2 ->key("Close")->headerText("Done");
    $cardSettings = new EJ\Kanban\CardSetting();
    $cardSettings ->colorMapping($colorMap);
    $editItem = new EJ\Kanban\EditItem();
    $editItem->field("Id");
    $editItem1 = new EJ\Kanban\EditItem();
    $editItem1->field("Status")->editType("dropDownEdit");
    $editItem2 = new EJ\Kanban\EditItem();
    $editItem2->field("Assignee")->editType("dropDownEdit");
    $editItem3 = new EJ\Kanban\EditItem();
    $editItem3->field("Summary")->editType("textarea");
    $editSetting = new EJ\Kanban\EditSetting();
    $editSetting->allowEditing(true)->allowAdding(true)->editItems(array($editItem,$editItem1,$editItem2,$editItem3));
    $fields = new EJ\Kanban\Field();    
    $fields ->content("Summary")->primaryKey("Id");
    $columns = array($column,$column1,$column2);    
    echo $kanban->keyField("Status")->columns($columns)->cardSettings($cardSettings)->fields($fields)->editSettings($editSetting)->dataSource($Json)->render();
    ?>
    </div>
    
{% endhighlight %}

The following output is displayed as a result of the above code example.

![Configuring Edit Items](Editing_images/editing_img1.png)

## Edit modes

### Dialog

Set `editMode` as `dialog` to edit data using a dialog box, which displays the fields associated with the data card being edited. Default value is `dialog`.

N> For `editMode` property you can assign either `string` value (“dialog”) or `enum` value (`ej.Kanban.EditMode.Dialog`).

The following code example describes the above behavior.

{% highlight html %}

    <?php
    require_once "../EJ/AutoLoad.php";
    ?>
    <div class="cols-sample-area">
    <?php
    $Json = '[{"Id": 1, "Status": "Open", "Summary": "Analyze the new requirements gathered from the customer.", "Type": "Story", "Priority": "Low", "Tags": "Analyze,Customer", "Estimate": 3.5, "Assignee": "Nancy Davloio", "ImgUrl": "Content/images/kanban/1.png", "RankId":1 }, { "Id": 2, "Status": "InProgress", "Summary": "Improve application performance", "Type": "Improvement", "Priority": "Normal", "Tags": "Improvement", "Estimate": 6, "Assignee": "Andrew Fuller", "ImgUrl": "Content/images/kanban/2.png", "RankId":1 }, { "Id": 3, "Status": "Open", "Summary": "Arrange a web meeting with the customer to get new requirements.", "Type": "Others", "Priority": "Critical", "Tags": "Meeting", "Estimate": 5.5, "Assignee": "Janet Leverling", "ImgUrl": "Content/images/kanban/3.png", "RankId":2 }, { "Id": 4, "Status": "InProgress", "Summary": "Fix the issues reported in the IE browser.", "Type": "Bug", "Priority": "Release Breaker", "Tags": "IE", "Estimate": 2.5, "Assignee": "Janet Leverling", "ImgUrl": "Content/images/kanban/3.png", "RankId":2 }, { "Id": 5, "Status": "Close", "Summary": "Fix the issues reported by the customer.", "Type": "Bug", "Priority": "Low", "Tags": "Customer", "Estimate": "3.5", "Assignee": "Steven walker", "ImgUrl": "Content/images/kanban/5.png", "RankId":1 }]';
    $Json = json_decode($Json,true);
    $colorMap = '{"#ee4e75": "Bug,Story","#57b94c": "Improvement","#edba3c": "Epic","#5187c6": "Others"}';
    $colorMap = json_decode($colorMap,true);
    $kanban = new EJ\Kanban("dialogEdit");
    $column = new EJ\Kanban\Column();
    $column ->key("Open")->headerText("Backlog");
    $column1 = new EJ\Kanban\Column();    
    $column1 ->key("InProgress")->headerText("In Progress");
    $column2 = new EJ\Kanban\Column();
    $column2 ->key("Close")->headerText("Done");
    $cardSettings = new EJ\Kanban\CardSetting();
    $cardSettings ->colorMapping($colorMap);
    $editItem = new EJ\Kanban\EditItem();
    $editItem->field("Id");
    $editItem1 = new EJ\Kanban\EditItem();
    $editItem1->field("Status")->editType("dropDownEdit");
    $editItem2 = new EJ\Kanban\EditItem();
    $editItem2->field("Assignee")->editType("dropDownEdit");
    $editItem3 = new EJ\Kanban\EditItem();
    $editItem3->field("Summary")->editType("textarea");
    $editSetting = new EJ\Kanban\EditSetting();
    $editSetting->allowEditing(true)->allowAdding(true)->editItems(array($editItem,$editItem1,$editItem2,$editItem3));
    $fields = new EJ\Kanban\Field();    
    $fields ->content("Summary")->primaryKey("Id");
    $columns = array($column,$column1,$column2);    
    echo $kanban->keyField("Status")->columns($columns)->cardSettings($cardSettings)->fields($fields)->editSettings($editSetting)->dataSource($Json)->render();
    ?>
    </div>
    
{% endhighlight %}

The following output is displayed as a result of the above code example.

![Edit Mode as dialog](Editing_images/editing_img2.png)

### Dialog Template Form

You can edit any of the fields pertaining to a single card of data and apply it to a template so that the same format is applied to all the other cards that you may edit later. 

Using this template support, you can edit the fields that are not bound to `editItems`.

To edit the cards using Dialog template form, set `editMode` as `dialogTemplate` and specify the template id to `dialogTemplate` property of `editSettings`.

N> 1. `value` attribute is used to bind the corresponding field value while editing.
N> 2. `name` attribute is used to get the changed field values while save the edited card.
N> 3.  For `editMode` property you can assign either `string` value (“dialogTemplate”) or `enum` value (`ej.Kanban.EditMode.DialogTemplate`).

The following code example describes the above behavior.


{% highlight html %}

    <?php
    require_once "../EJ/AutoLoad.php";
    ?>
    <div class="cols-sample-area">
    <script id="template" type="text/template">
        <table cellspacing="10">
            <tr>
                <td style="text-align: right;">
                    Id
                </td>
                <td style="text-align: left">
                    <input id="Id" name="Id" value="{{: Id}}" class="e-field e-ejinputtext valid e-disable" style="text-align: right; width: 175px; height: 28px" disabled="disabled" />
                </td>
                <td style="text-align: right;">
                    Status
                </td>
                <td style="text-align: left">
                    <select id="Status" name="Status">
                        <option value="Close">Close</option>
                        <option value="InProgress">InProgress</option>
                        <option value="Open">Open</option>
                    </select>
                </td>
            </tr>
            <tr>
                <td style="text-align: right;">
                    Estimate
                </td>
                <td style="text-align: left">
                    <input type="text" id="Estimate" name="Estimate" value="{{:Estimate}}" />
                </td>
                <td style="text-align: right;">
                    Assignee
                </td>
                <td style="text-align: left">
                    <select id="Assignee" name="Assignee">
                        <option value="Nancy">Nancy</option>
                        <option value="Andrew">Andrew</option>
                        <option value="Janet">Janet</option>
                        <option value="Margaret">Margaret</option>
                        <option value="Steven">Steven</option>
                        <option value="Michael">Michael</option>
                        <option value="Robert">Robert</option>
                        <option value="Laura">Laura</option>
                    </select>
                </td>
            </tr>
        </table>
    </script>
    <script>
        function complete(args) {
            if ((args.requestType == "beginedit" || args.requestType == "add") && args.model.editSettings.editMode == ej.Kanban.EditMode.DialogTemplate) {
                $("#Estimate").ejNumericTextbox({ value: parseFloat($("#Estimate").val()), width: "175px", height: "34px", decimalPlaces: 2 });
                $("#Assignee").ejDropDownList({ width: '175px' });
                $("#Status").ejDropDownList({ width: '175px' });
                if (args.requestType == "beginedit" || args.requestType == "add") {
                    $("#Assignee").ejDropDownList("setSelectedValue", args.data['Assignee']);
                    $("#Status").ejDropDownList("setSelectedValue", args.data['Status']);
                }
            }
        }
    </script>
    <?php
    $Json = '[{"Id": 1, "Status": "Open", "Summary": "Analyze the new requirements gathered from the customer.", "Type": "Story", "Priority": "Low", "Tags": "Analyze,Customer", "Estimate": 3.5, "Assignee": "Nancy Davloio", "ImgUrl": "Content/images/kanban/1.png", "RankId":1 }, { "Id": 2, "Status": "InProgress", "Summary": "Improve application performance", "Type": "Improvement", "Priority": "Normal", "Tags": "Improvement", "Estimate": 6, "Assignee": "Andrew Fuller", "ImgUrl": "Content/images/kanban/2.png", "RankId":1 }, { "Id": 3, "Status": "Open", "Summary": "Arrange a web meeting with the customer to get new requirements.", "Type": "Others", "Priority": "Critical", "Tags": "Meeting", "Estimate": 5.5, "Assignee": "Janet Leverling", "ImgUrl": "Content/images/kanban/3.png", "RankId":2 }, { "Id": 4, "Status": "InProgress", "Summary": "Fix the issues reported in the IE browser.", "Type": "Bug", "Priority": "Release Breaker", "Tags": "IE", "Estimate": 2.5, "Assignee": "Janet Leverling", "ImgUrl": "Content/images/kanban/3.png", "RankId":2 }, { "Id": 5, "Status": "Close", "Summary": "Fix the issues reported by the customer.", "Type": "Bug", "Priority": "Low", "Tags": "Customer", "Estimate": "3.5", "Assignee": "Steven walker", "ImgUrl": "Content/images/kanban/5.png", "RankId":1 }]';
    $Json = json_decode($Json,true);
    $kanban = new EJ\Kanban("dialogEdit");
    $column = new EJ\Kanban\Column();
    $column ->key("Open")->headerText("Backlog");
    $column1 = new EJ\Kanban\Column();
    $column1 ->key("InProgress")->headerText("In Progress");
    $column2 = new EJ\Kanban\Column();
    $column2 ->key("Close")->headerText("Done");
    $editSetting = new EJ\Kanban\EditSetting();
    $editSetting->allowEditing(true)->allowAdding(true)->dialogTemplate("#template")->editMode("DialogTemplate");
    $fields = new EJ\Kanban\Field();
    $fields ->content("Summary")->primaryKey("Id");
    $columns = array($column,$column1,$column2);
    echo $kanban->keyField("Status")->actionComplete("complete")->allowTitle(true)->columns($columns)->fields($fields)->editSettings($editSetting)->dataSource($Json)->render();
    ?>
    </div>

{% endhighlight %}

The following output is displayed as a result of the above code example.

![Dialog Template form](Editing_images/editing_img3.png)

### External Form

Set the `editMode` as externalForm to open the edit form in outside kanban content.

The following code example describes the above behavior.

{% highlight html %}

    <?php
    require_once "../EJ/AutoLoad.php";
    ?>
    <div class="cols-sample-area">
    <?php
    $Json = '[{"Id": 1, "Status": "Open", "Summary": "Analyze the new requirements gathered from the customer.", "Type": "Story", "Priority": "Low", "Tags": "Analyze,Customer", "Estimate": 3.5, "Assignee": "Nancy Davloio", "ImgUrl": "Content/images/kanban/1.png", "RankId":1 }, { "Id": 2, "Status": "InProgress", "Summary": "Improve application performance", "Type": "Improvement", "Priority": "Normal", "Tags": "Improvement", "Estimate": 6, "Assignee": "Andrew Fuller", "ImgUrl": "Content/images/kanban/2.png", "RankId":1 }, { "Id": 3, "Status": "Open", "Summary": "Arrange a web meeting with the customer to get new requirements.", "Type": "Others", "Priority": "Critical", "Tags": "Meeting", "Estimate": 5.5, "Assignee": "Janet Leverling", "ImgUrl": "Content/images/kanban/3.png", "RankId":2 }, { "Id": 4, "Status": "InProgress", "Summary": "Fix the issues reported in the IE browser.", "Type": "Bug", "Priority": "Release Breaker", "Tags": "IE", "Estimate": 2.5, "Assignee": "Janet Leverling", "ImgUrl": "Content/images/kanban/3.png", "RankId":2 }, { "Id": 5, "Status": "Close", "Summary": "Fix the issues reported by the customer.", "Type": "Bug", "Priority": "Low", "Tags": "Customer", "Estimate": "3.5", "Assignee": "Steven walker", "ImgUrl": "Content/images/kanban/5.png", "RankId":1 }]';
    $Json = json_decode($Json,true);
    $kanban = new EJ\Kanban("dialogEdit");
    $column = new EJ\Kanban\Column();
    $column ->key("Open")->headerText("Backlog");
    $column1 = new EJ\Kanban\Column();    
    $column1 ->key("InProgress")->headerText("In Progress");
    $column2 = new EJ\Kanban\Column();
    $column2 ->key("Close")->headerText("Done");
    $editItem = new EJ\Kanban\EditItem();
    $editItem->field("Id");
    $editItem1 = new EJ\Kanban\EditItem();
    $editItem1->field("Status")->editType("dropDownEdit");
    $editItem2 = new EJ\Kanban\EditItem();
    $editItem2->field("Assignee")->editType("dropDownEdit");
    $editItem3 = new EJ\Kanban\EditItem();
    $editItem3->field("Summary")->editType("textarea");
    $editSetting = new EJ\Kanban\EditSetting();
    $editSetting->allowEditing(true)->allowAdding(true)->editMode("ExternalForm")->editItems(array($editItem,$editItem1,$editItem2,$editItem3));
    $fields = new EJ\Kanban\Field();    
    $fields ->content("Summary")->primaryKey("Id");
    $columns = array($column,$column1,$column2);    
    echo $kanban->keyField("Status")->allowTitle(true)->columns($columns)->fields($fields)->editSettings($editSetting)->dataSource($Json)->render();
    ?>
    </div>

{% endhighlight %}

The following output is displayed as a result of the above code example.

![External Form](Editing_images/editing_img11.png)

Form Position:

Form Position can be customized by setting the `formPosition` property of `editSettings' as "right" or "bottom".

The following code example describes the above behavior.

{% highlight html %}

    <?php
    require_once "../EJ/AutoLoad.php";
    ?>
    <div class="cols-sample-area">
    <?php
    $Json = '[{"Id": 1, "Status": "Open", "Summary": "Analyze the new requirements gathered from the customer.", "Type": "Story", "Priority": "Low", "Tags": "Analyze,Customer", "Estimate": 3.5, "Assignee": "Nancy Davloio", "ImgUrl": "Content/images/kanban/1.png", "RankId":1 }, { "Id": 2, "Status": "InProgress", "Summary": "Improve application performance", "Type": "Improvement", "Priority": "Normal", "Tags": "Improvement", "Estimate": 6, "Assignee": "Andrew Fuller", "ImgUrl": "Content/images/kanban/2.png", "RankId":1 }, { "Id": 3, "Status": "Open", "Summary": "Arrange a web meeting with the customer to get new requirements.", "Type": "Others", "Priority": "Critical", "Tags": "Meeting", "Estimate": 5.5, "Assignee": "Janet Leverling", "ImgUrl": "Content/images/kanban/3.png", "RankId":2 }, { "Id": 4, "Status": "InProgress", "Summary": "Fix the issues reported in the IE browser.", "Type": "Bug", "Priority": "Release Breaker", "Tags": "IE", "Estimate": 2.5, "Assignee": "Janet Leverling", "ImgUrl": "Content/images/kanban/3.png", "RankId":2 }, { "Id": 5, "Status": "Close", "Summary": "Fix the issues reported by the customer.", "Type": "Bug", "Priority": "Low", "Tags": "Customer", "Estimate": "3.5", "Assignee": "Steven walker", "ImgUrl": "Content/images/kanban/5.png", "RankId":1 }]';
    $Json = json_decode($Json,true);
    $kanban = new EJ\Kanban("dialogEdit");
    $column = new EJ\Kanban\Column();
    $column ->key("Open")->headerText("Backlog");
    $column1 = new EJ\Kanban\Column();    
    $column1 ->key("InProgress")->headerText("In Progress");
    $column2 = new EJ\Kanban\Column();
    $column2 ->key("Close")->headerText("Done");
    $editItem = new EJ\Kanban\EditItem();
    $editItem->field("Id");
    $editItem1 = new EJ\Kanban\EditItem();
    $editItem1->field("Status")->editType("dropDownEdit");
    $editItem2 = new EJ\Kanban\EditItem();
    $editItem2->field("Assignee")->editType("dropDownEdit");
    $editItem3 = new EJ\Kanban\EditItem();
    $editItem3->field("Summary")->editType("textarea");
    $editSetting = new EJ\Kanban\EditSetting();
    $editSetting->allowEditing(true)->allowAdding(true)->formPosition("Bottom")->editMode("ExternalForm")->editItems(array($editItem,$editItem1,$editItem2,$editItem3));
    $fields = new EJ\Kanban\Field();    
    $fields ->content("Summary")->primaryKey("Id");
    $columns = array($column,$column1,$column2);    
    echo $kanban->keyField("Status")->allowTitle(true)->columns($columns)->fields($fields)->editSettings($editSetting)->dataSource($Json)->render();
    ?>
    </div>
        
{% endhighlight %}

The following output is displayed as a result of the above code example.

![Form Position](Editing_images/editing_img12.png)

### External Template Form

You can edit any of the fields pertaining to a single card of data and apply it to a template so that the same format is applied to all the other cards that you may edit later. 

Using this template support, you can edit the fields that are not bound to Kanban Edit Items.

To edit the cards using External template form, set `editMode` as `externalFormTemplate` and specify the template id to `externalFormTemplate` property of `editSettings`.

While using template, you can change the elements that are defined in the template, to appropriate Syncfusion JS controls based on the column type. This can be achieved by using `actionComplete` event of Kanban.

N> 1. `value` attribute is used to bind the corresponding field value while editing. 
N> 2. `name` attribute is used to get the changed field values while save the edited card. 
N> 3. For `editMode` property you can assign either `string` value ("externalFormTemplate") or `enum` value (`ej.Kanban.EditMode.ExternalFormTemplate`).

The following code example describes the above behavior.

{% highlight html %}

    <?php
    require_once "../EJ/AutoLoad.php";
    ?>
    <div class="cols-sample-area">
    <script id="template" type="text/template">
        <table cellspacing="10">
            <tr>
                <td style="text-align:left;">
                    Id
                </td>
                <td style="text-align: left">
                    <input id="Id" name="Id" value="{{: Id}}" class="e-field e-ejinputtext valid e-disable" style="text-align: right; width: 175px; height: 28px" disabled="disabled" />
                </td>
            </tr>
            <tr>
                <td style="text-align: left;">
                    Status
                </td>
                <td style="text-align: left">
                    <select id="Status" name="Status">
                        <option value="Close">Close</option>
                        <option value="InProgress">InProgress</option>
                        <option value="Open">Open</option>
                        <option value="Testing">Testing</option>
                        <option value="Validate">Validate</option>
                    </select>
                </td>
            </tr>
            <tr>
                <td style="text-align: left;">
                    Assignee
                </td>
                <td style="text-align: left">
                    <select id="Assignee" name="Assignee">
                        <option value="Nancy">Nancy</option>
                        <option value="Andrew Fuller">Andrew Fuller</option>
                        <option value="Janet Leverling">Janet Leverling</option>
                        <option value="Margaret">Margaret</option>
                        <option value="Steven walker">Steven walker</option>
                        <option value="Michael Suyama">Michael Suyama</option>
                        <option value="Robert King">Robert King</option>
                        <option value="Laura Callahan">Laura Callahan</option>
                    </select>
                </td>
            </tr>
            <tr>
                <td style="text-align: left;">
                    Priority
                </td>
                <td style="text-align: left">
                    <input id="Priority" name="Priority" value="{{: Priority}}" class="e-field e-ejinputtext valid" style="width: 175px; height: 28px" />
                </td>
            </tr>
            <tr>
                <td style="text-align: left;">
                    Summary
                </td>
                <td style="text-align: left">
                    <textarea id="Summary" name="Summary" class="e-ejinputtext" value="{{: Summary}}" style="width: 270px; height: 95px">{{: Summary}}</textarea>
                </td>
            </tr>
        </table>
    </script>
    <script>
        function complete(args) {
            if ((args.requestType == "beginedit" || args.requestType == "add") && args.model.editSettings.editMode == ej.Kanban.EditMode.ExternalFormTemplate) {
                $("#Assignee").ejDropDownList({ width: '175px' });
                $("#Status").ejDropDownList({ width: '175px' });
                if (args.requestType == "beginedit" || args.requestType == "add") {
                    $("#Assignee").ejDropDownList("setSelectedValue", args.data['Assignee']);
                    $("#Status").ejDropDownList("setSelectedValue", args.data['Status']);
                }
            }
        }
    </script>
    <?php
    $Json = '[{"Id": 1, "Status": "Open", "Summary": "Analyze the new requirements gathered from the customer.", "Type": "Story", "Priority": "Low", "Tags": "Analyze,Customer", "Estimate": 3.5, "Assignee": "Nancy Davloio", "ImgUrl": "Content/images/kanban/1.png", "RankId":1 }, { "Id": 2, "Status": "InProgress", "Summary": "Improve application performance", "Type": "Improvement", "Priority": "Normal", "Tags": "Improvement", "Estimate": 6, "Assignee": "Andrew Fuller", "ImgUrl": "Content/images/kanban/2.png", "RankId":1 }, { "Id": 3, "Status": "Open", "Summary": "Arrange a web meeting with the customer to get new requirements.", "Type": "Others", "Priority": "Critical", "Tags": "Meeting", "Estimate": 5.5, "Assignee": "Janet Leverling", "ImgUrl": "Content/images/kanban/3.png", "RankId":2 }, { "Id": 4, "Status": "InProgress", "Summary": "Fix the issues reported in the IE browser.", "Type": "Bug", "Priority": "Release Breaker", "Tags": "IE", "Estimate": 2.5, "Assignee": "Janet Leverling", "ImgUrl": "Content/images/kanban/3.png", "RankId":2 }, { "Id": 5, "Status": "Close", "Summary": "Fix the issues reported by the customer.", "Type": "Bug", "Priority": "Low", "Tags": "Customer", "Estimate": "3.5", "Assignee": "Steven walker", "ImgUrl": "Content/images/kanban/5.png", "RankId":1 }]';
    $Json = json_decode($Json,true);
    $kanban = new EJ\Kanban("dialogEdit");
    $column = new EJ\Kanban\Column();
    $column ->key("Open")->headerText("Backlog");
    $column1 = new EJ\Kanban\Column();
    $column1 ->key("InProgress")->headerText("In Progress");
    $column2 = new EJ\Kanban\Column();
    $column2 ->key("Close")->headerText("Done");
    $editSetting = new EJ\Kanban\EditSetting();
    $editSetting->allowEditing(true)->allowAdding(true)->externalFormTemplate("#template")->editMode("ExternalFormTemplate");
    $fields = new EJ\Kanban\Field();
    $fields ->content("Summary")->primaryKey("Id");
    $columns = array($column,$column1,$column2);
    echo $kanban->keyField("Status")->actionComplete("complete")->allowTitle(true)->columns($columns)->fields($fields)->editSettings($editSetting)->dataSource($Json)->render();
    ?>
    </div>

{% endhighlight %}

The following output is displayed as a result of the above code example.

![External Template Form](Editing_images/editing_img13.png)

