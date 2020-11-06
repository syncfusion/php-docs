---
layout: post
title:  Essential EJ1 Syncfusion PHP Kanban Print
description: This section explains how to perform printing feature and its functionalities using the Syncfusion PHP Kanban component.
documentation: ug
platform: php
---

# Print

 Set `allowPrinting` as true, to enable Print icon in the Kanban toolbar.  You can use ‘print()’ method from Kanban instance to print the Kanban.

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
    $fields = new EJ\Kanban\Field();
    $fields ->content("Summary")->primaryKey("Id");
    $columns = array( 
        $column,$column1,$column2
        );    
    echo $kanban ->columns($columns)->dataSource($Json)->allowTitle(true)->allowPrinting(true)->fields($fields)->keyField("Status")->render();
    ?>
    </div>

{% endhighlight %}

The following output is displayed as a result of the above code example.

![Print in PHP kanban control](Printing_images/print_img1.png)


