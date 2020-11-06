---
layout: post
title:  Essential EJ1 Syncfusion PHP Kanban cards
description: This section explains how to define the basic structure of cards and their features of the Syncfusion PHP Kanban component.
documentation: ug
platform: php
keywords: cards,kanban cards
---

# Cards in PHP Kanban component

## Customization

Cards can be customized with appropriate mapping fields from the database.  

The following code example describes the above behavior.

{% highlight html %}
   
    <?php
    require_once "../EJ/AutoLoad.php";
    ?>
    <div class="cols-sample-area">
    <?php
    $Json = '[{"Id": 1, "Status": "Open", "Summary": "Analyze the new requirements gathered from the customer.", "Type": "Story", "Priority": "Low", "Tags": "Analyze,Customer", "Estimate": 3.5, "Assignee": "Nancy Davloio", "ImgUrl": "Content/images/kanban/1.png", "RankId":1 }, { "Id": 2, "Status": "InProgress", "Summary": "Improve application performance", "Type": "Improvement", "Priority": "Normal", "Tags": "Improvement", "Estimate": 6, "Assignee": "Andrew Fuller", "ImgUrl": "Content/images/kanban/2.png", "RankId":1 }, { "Id": 3, "Status": "Open", "Summary": "Arrange a web meeting with the customer to get new requirements.", "Type": "Others", "Priority": "Critical", "Tags": "Meeting", "Estimate": 5.5, "Assignee": "Janet Leverling", "ImgUrl": "Content/images/kanban/3.png", "RankId":2 }, { "Id": 4, "Status": "InProgress", "Summary": "Fix the issues reported in the IE browser.", "Type": "Bug", "Priority": "Release Breaker", "Tags": "IE", "Estimate": 2.5, "Assignee": "Janet Leverling", "ImgUrl": "Content/images/kanban/3.png", "RankId":2 }, { "Id": 5, "Status": "Testing", "Summary": "Fix the issues reported by the customer.", "Type": "Bug", "Priority": "Low", "Tags": "Customer", "Estimate": "3.5", "Assignee": "Steven walker", "ImgUrl": "Content/images/kanban/5.png", "RankId":1 }]';
    $Json = json_decode($Json,true);
    $colormap = '{"#ee4e75": "Bug,Story","#57b94c": "Improvement","#edba3c": "Epic","#5187c6": "Others"}';
    $colormap = json_decode($colormap,true);
    $kanban = new EJ\Kanban("customization");
    $column = new EJ\Kanban\Column();
    $column ->key("Open")->headerText("Backlog");
    $column1 = new EJ\Kanban\Column();
    $column1 ->key("InProgress")->headerText("In Progress");
    $column2 = new EJ\Kanban\Column();
    $column2 ->key("Close")->headerText("Done");
    $cardset = new EJ\Kanban\CardSetting();
    $cardset ->colorMapping($colormap);
    $fields = new EJ\Kanban\Field();
    $fields ->content("Summary")->primaryKey("Id")->imageUrl("ImgUrl")->tag("Tags")->priority("RankId")->color("Type");
    $columns = array($column,$column1,$column2);
    echo $kanban->keyField("Status")->allowTitle(true)->columns($columns)->cardSettings($cardset)->fields($fields)->dataSource($Json)->render();
    ?>
    </div>

{% endhighlight %}

The following output is displayed as a result of the above code example.

![Card customization in PHP kanban control](Cards_images/cards_img1.png)

## Template

Templates are used to create custom card layout as per the user convenient. HTML templates can be specified in the `template` property of the `cardSettings` as an ID of the template’s HTML element.

The following code example describes the above behavior.

{% highlight html %}

    <?php
    require_once "../EJ/AutoLoad.php";
    ?>
    <div class="cols-sample-area">
    <script id="cardtemplate" type="text/x-jsrender">
        <table class="e-templatetable">
            <colgroup>
                <col width="10%">
                <col width="90%">
            </colgroup>
            <tbody>
                <tr>
                    <td class="photo">
                        <img src="Content/images/kanban/{{:Priority}}.png">
                    </td>
                    <td class="details">
                        <table>
                            <colgroup>
                                <col width="10%">
                                <col width="90%">
                            </colgroup>
                            <tbody>
                                <tr>
                                    <td class="CardHeader">   Assignee: </td>
                                    <td>{{"{{"}}:Assignee{{}}}}</td>
                                </tr>
                                <tr>
                                    <td class="CardHeader">   Summary: </td>
                                    <td>{{"{{"}}:Summary{{}}}}</td>
                                </tr>
                                <tr>
                                    <td class="CardHeader">   Type: </td>
                                    <td>{{"{{"}}:Type{{}}}}</td>
                                </tr>
                            </tbody>
                        </table>
                    </td>
                </tr>
            </tbody>
        </table>
    </script>
    <style type="text/css">
        .e-templatetable {
            width: 100%;
        }
        .details > table {
            margin-left: 2px;
            border-collapse: separate;
            border-spacing: 2px;
            width: 100%;
        }
        .details td {
            vertical-align: top;
        }
        .details {
            padding: 8px 8px 10px 0;
        }
        .photo {
            padding: 8px 6px 10px 6px;
            text-align: center;
        }
        .CardHeader {
            font-weight: bolder;
            padding-right: 10px;
        }
    </style>
    <?php
    $Json = '[{"Id": 1, "Status": "Open", "Summary": "Analyze the new requirements gathered from the customer.", "Type": "Story", "Priority": "Low", "Tags": "Analyze,Customer", "Estimate": 3.5, "Assignee": "Nancy Davloio", "ImgUrl": "Content/images/kanban/1.png", "RankId":1 }, { "Id": 2, "Status": "InProgress", "Summary": "Improve application performance", "Type": "Improvement", "Priority": "Normal", "Tags": "Improvement", "Estimate": 6, "Assignee": "Andrew Fuller", "ImgUrl": "Content/images/kanban/2.png", "RankId":1 }, { "Id": 3, "Status": "Open", "Summary": "Arrange a web meeting with the customer to get new requirements.", "Type": "Others", "Priority": "Critical", "Tags": "Meeting", "Estimate": 5.5, "Assignee": "Janet Leverling", "ImgUrl": "Content/images/kanban/3.png", "RankId":2 }, { "Id": 4, "Status": "InProgress", "Summary": "Fix the issues reported in the IE browser.", "Type": "Bug", "Priority": "Release Breaker", "Tags": "IE", "Estimate": 2.5, "Assignee": "Janet Leverling", "ImgUrl": "Content/images/kanban/3.png", "RankId":2 }, { "Id": 5, "Status": "Testing", "Summary": "Fix the issues reported by the customer.", "Type": "Bug", "Priority": "Low", "Tags": "Customer", "Estimate": "3.5", "Assignee": "Steven walker", "ImgUrl": "Content/images/kanban/5.png", "RankId":1 }]';
    $Json = json_decode($Json,true);
    $colormap = '{"#ee4e75": "Bug,Story","#57b94c": "Improvement","#edba3c": "Epic","#5187c6": "Others"}';
    $colormap = json_decode($colormap,true);
    $kanban = new EJ\Kanban("template");
    $column = new EJ\Kanban\Column();
    $column->key("Open")->headerText("Backlog");
    $column1 = new EJ\Kanban\Column();
    $column1->key("InProgress")->headerText("In Progress");
    $column2  = new EJ\Kanban\Column();
    $column2->key("Testing")->headerText("Testing");
    $column3 = new EJ\Kanban\Column();
    $column3->key("Close")->headerText("Done");
    $cardset = new EJ\Kanban\CardSetting();
    $fields= new EJ\Kanban\Field();
    $fields->primaryKey("Id");
    $cardset->template("#cardtemplate");
    $columns = array($column,$column1,$column3);
    echo $kanban->keyField("Status")->allowTitle(true)->columns($columns)->enableTouch(false)->fields($fields)->cardSettings($cardset)->dataSource($Json)->render();
    ?>
    </div>

{% endhighlight %}

The following output is displayed as a result of the above code example.

![Card template in PHP kanban control](Cards_images/cards_img2.png)

## Tooltip

You can enable HTML tooltip for Kanban card elements by setting `enable` property as true in `tooltipSettings`.

The following code example describes the above behavior.

{% highlight html %}

    <?php
    require_once "../EJ/AutoLoad.php";
    ?>
    <div class="cols-sample-area">
    <?php
    $Json = '[{"Id": 1, "Status": "Open", "Summary": "Analyze the new requirements gathered from the customer.", "Type": "Story", "Priority": "Low", "Tags": "Analyze,Customer", "Estimate": 3.5, "Assignee": "Nancy Davloio", "ImgUrl": "Content/images/kanban/1.png", "RankId":1 }, { "Id": 2, "Status": "InProgress", "Summary": "Improve application performance", "Type": "Improvement", "Priority": "Normal", "Tags": "Improvement", "Estimate": 6, "Assignee": "Andrew Fuller", "ImgUrl": "Content/images/kanban/2.png", "RankId":1 }, { "Id": 3, "Status": "Open", "Summary": "Arrange a web meeting with the customer to get new requirements.", "Type": "Others", "Priority": "Critical", "Tags": "Meeting", "Estimate": 5.5, "Assignee": "Janet Leverling", "ImgUrl": "Content/images/kanban/3.png", "RankId":2 }, { "Id": 4, "Status": "InProgress", "Summary": "Fix the issues reported in the IE browser.", "Type": "Bug", "Priority": "Release Breaker", "Tags": "IE", "Estimate": 2.5, "Assignee": "Janet Leverling", "ImgUrl": "Content/images/kanban/3.png", "RankId":2 }, { "Id": 5, "Status": "Testing", "Summary": "Fix the issues reported by the customer.", "Type": "Bug", "Priority": "Low", "Tags": "Customer", "Estimate": "3.5", "Assignee": "Steven walker", "ImgUrl": "Content/images/kanban/5.png", "RankId":1 }]';
    $Json = json_decode($Json,true);
    $colormap = '{"#ee4e75": "Bug,Story","#57b94c": "Improvement","#edba3c": "Epic","#5187c6": "Others"}';
    $colormap = json_decode($colormap,true);
    $kanban = new EJ\Kanban("customization");
    $column = new EJ\Kanban\Column();
    $column ->key("Open")->headerText("Backlog");
    $column1 = new EJ\Kanban\Column();
    $column1 ->key("InProgress")->headerText("In Progress");
    $column2 = new EJ\Kanban\Column();
    $column2 ->key("Close")->headerText("Done");
    $cardset = new EJ\Kanban\CardSetting();
    $cardset ->colorMapping($colormap);
    $fields = new EJ\Kanban\Field();
    $fields ->content("Summary")->primaryKey("Id")->imageUrl("ImgUrl")->tag("Tags")->priority("RankId")->color("Type");
    $columns = array($column,$column1,$column2);
    echo $kanban->keyField("Status")->allowTitle(true)->columns($columns)->cardSettings($cardset)->fields($fields)->dataSource($Json)->render();
    ?>
    </div>

{% endhighlight %}
 
The following output is displayed as a result of the above code example.

![Card tooltip in PHP kanban control](Cards_images/cards_img3.png)

### Template

By making use of template feature with tooltip, all the field names that are mapped from the `dataSource` can be accessed to define the `template` tooltip for card. The `tooltipSettings.enable` must be enabled first.

The following code example describes the tooltip template.

{% highlight html %}

    <?php
    require_once '../EJ/AutoLoad.php';
    ?>
    <div class="cols-sample-area">
    <script id="tooltipTemp" type="text/x-jsrender">
        <div class='e-kanbantooltiptemplate'>
            <table>
                <tr>
                    <td class="photo">
                        <img src="{{:ImgUrl}}">
                    </td>
                    <td class="details">
                        <table>
                            <colgroup>
                                <col width="30%">
                                <col width="70%">
                            </colgroup>
                            <tbody>
                                <tr>
                                    <td class="CardHeader">Assignee:</td>
                                    <td>{{"{{"}}:Assignee{{}}}}</td>
                                </tr>
                                <tr>
                                    <td class="CardHeader">Type:</td>
                                    <td>{{"{{"}}:Type{{}}}}</td>
                                </tr>
                                <tr>
                                    <td class="CardHeader">Estimate:</td>
                                    <td>{{"{{"}}:Estimate{{}}}}</td>
                                </tr>
                                <tr>
                                    <td class="CardHeader">Summary:</td>
                                    <td>{{"{{"}}:Summary{{}}}}</td>
                                </tr>
                            </tbody>
                        </table>
                    </td>
                </tr>
            </table>
        </div>
    </script>
    <style>
        .details > table {
            width: 100%;
            margin-left: 2px;
            border-collapse: separate;
            border-spacing: 1px;
        }

        .e-kanbantooltiptemplate {
            width: 250px;
            padding: 3px;
        }

            .e-kanbantooltiptemplate > table {
                width: 100%;
            }

            .e-kanbantooltiptemplate td {
                vertical-align: top;
            }

        td.details {
            padding-left: 10px;
        }

        .CardHeader {
            font-weight: bolder;
        }
    </style>
    <?php
    $Json = '[{"Id": 1, "Status": "Open", "Summary": "Analyze the new requirements gathered from the customer.", "Type": "Story", "Priority": "Low", "Tags": "Analyze,Customer", "Estimate": 3.5, "Assignee": "Nancy Davloio", "ImgUrl": "Content/images/kanban/1.png", "RankId":1 }, { "Id": 2, "Status": "InProgress", "Summary": "Improve application performance", "Type": "Improvement", "Priority": "Normal", "Tags": "Improvement", "Estimate": 6, "Assignee": "Andrew Fuller", "ImgUrl": "Content/images/kanban/2.png", "RankId":1 }, { "Id": 3, "Status": "Open", "Summary": "Arrange a web meeting with the customer to get new requirements.", "Type": "Others", "Priority": "Critical", "Tags": "Meeting", "Estimate": 5.5, "Assignee": "Janet Leverling", "ImgUrl": "Content/images/kanban/3.png", "RankId":2 }, { "Id": 4, "Status": "InProgress", "Summary": "Fix the issues reported in the IE browser.", "Type": "Bug", "Priority": "Release Breaker", "Tags": "IE", "Estimate": 2.5, "Assignee": "Janet Leverling", "ImgUrl": "Content/images/kanban/3.png", "RankId":2 }, { "Id": 5, "Status": "Testing", "Summary": "Fix the issues reported by the customer.", "Type": "Bug", "Priority": "Low", "Tags": "Customer", "Estimate": "3.5", "Assignee": "Steven walker", "ImgUrl": "Content/images/kanban/5.png", "RankId":1 }]';
    $Json = json_decode($Json,true);
    $kanban = new EJ\Kanban("default");
    $column = new EJ\Kanban\Column();
    $column ->key("Open")->headerText("Backlog");
    $column1 = new EJ\Kanban\Column();
    $column1 ->key("InProgress")->headerText("In Progress");
    $column2 = new EJ\Kanban\Column();
    $column2 ->key("Testing")->headerText("Testing");
    $column3 = new EJ\Kanban\Column();
    $column3 ->key("Close")->headerText("Done");
    $tooltipSettings = new EJ\Kanban\TooltipSetting();
    $tooltipSettings ->enable(true)->template("#tooltipTemp");
    $fields = new EJ\Kanban\Field();
    $fields ->content("Summary")->primaryKey("Id")->tag('Tags');
    $columns = array(
    $column,$column1,$column2,$column3
    );
    echo $kanban ->columns($columns)->dataSource($Json)->tooltipSettings($tooltipSettings)->fields($fields)->keyField("Status")->render();
    ?>
    </div>

{% endhighlight %}

The following output is displayed as a result of the above code example.

![Card tooltip template in PHP kanban control](Cards_images/cards_img4.png)
