---
layout: post
title:  Essential EJ1 Syncfusion PHP Kanban Filtering
description: This section explains how to enable filtering and its functionalities using the Syncfusion PHP Kanban component.
documentation: ug
platform: php
keywords: filtering,kanban filtering
---

# Filtering

Filtering allows to filter the collection of cards from `dataSource` which meets the predefined `query` in the quick filters collection. To enable filtering, define `filterSettings` collection with display `text` and `ej.Query`. 

You can also define display tip to describe filter definition to user using property `description`. If the `description` property is not defined, given `text` will act as display tip.

We can also customize filter option through external button or `customToolbarItems` by using `filterCards()` method.

The following code example describes the above behavior.

{% highlight html %}

    <?php
    require_once '../EJ/AutoLoad.php';
    ?>
    <div class="cols-sample-area">
    <?php    
    $Json = '[{"Id": 1, "Status": "Open", "Summary": "Analyze the new requirements gathered from the customer.", "Type": "Story", "Priority": "Low", "Tags": "Analyze,Customer", "Estimate": 3.5, "Assignee": "Nancy Davloio", "ImgUrl": "Content/images/kanban/1.png", "RankId":1 }, { "Id": 2, "Status": "InProgress", "Summary": "Improve application performance", "Type": "Improvement", "Priority": "Normal", "Tags": "Improvement", "Estimate": 6, "Assignee": "Andrew Fuller", "ImgUrl": "Content/images/kanban/2.png", "RankId":1 }, { "Id": 3, "Status": "Open", "Summary": "Arrange a web meeting with the customer to get new requirements.", "Type": "Others", "Priority": "Critical", "Tags": "Meeting", "Estimate": 5.5, "Assignee": "Janet Leverling", "ImgUrl": "Content/images/kanban/3.png", "RankId":2 }, { "Id": 4, "Status": "InProgress", "Summary": "Fix the issues reported in the IE browser.", "Type": "Bug", "Priority": "Release Breaker", "Tags": "IE", "Estimate": 2.5, "Assignee": "Janet Leverling", "ImgUrl": "Content/images/kanban/3.png", "RankId":2 }, { "Id": 5, "Status": "Close", "Summary": "Fix the issues reported by the customer.", "Type": "Bug", "Priority": "Low", "Tags": "Customer", "Estimate": "3.5", "Assignee": "Steven walker", "ImgUrl": "Content/images/kanban/5.png", "RankId":1 }]';
    $Json = json_decode($Json,true);
    $kanban = new EJ\Kanban("default");    
    $column = new EJ\Kanban\Column();
    $column ->key("Open")->headerText("Backlog");    
    $column1 = new EJ\Kanban\Column();
    $column1 ->key("InProgress")->headerText("In Progress");    
    $column2 = new EJ\Kanban\Column();
    $column2 ->key("Close")->headerText("Done");  
    $filterQuery = new EJ\Query();
    $filterQuery->where("'Assignee','equal','Janet Leverling'");
    $filterQuery1 = new EJ\Query();
    $filterQuery1->where("'Status','equal','Close'");
    $filter = new EJ\Kanban\FilterSetting();
    $filter->text("Janet Issues")->query($filterQuery)->description("Displays issues which matches the assignee as Janet Leverling");
    $filter1 = new EJ\Kanban\FilterSetting();
    $filter1->text("Closed Issues")->query($filterQuery1)->description("Display the issues of 'Closed Issues'");			
    $fields = new EJ\Kanban\Field();
    $fields ->content("Summary")->primaryKey("Id")->tag("Tags");
    $filterSettings = array( 
    $filterSetting,$filterSetting1);    
    $columns = array( 
    $column,$column1,$column2);    
    echo $kanban ->columns($columns)->filterSettings(array($filter,$filter1))->dataSource($Json)->fields($fields)->keyField("Status")->render();
    ?>
    </div>

{% endhighlight %}

The following output is displayed as a result of the above code example.

![Filtering in PHP kanban control](Filtering_images/filter_img1.png)