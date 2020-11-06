---
layout: post
title:  Essential EJ1 Syncfusion PHP Kanban Workflows
description: This section explains the flow of cards between the Kanban columns in the Syncfusion PHP Kanban component.
documentation: ug
platform: php
keywords: Workflows,kanban Workflows
---

# Workflows 

Workflows can be defined to set the flow of card moving between the Kanban column statuses and it is applicable to drag and drop and context menu features.

You can set `workflows` as array of Objects which consists of `key` and `allowedTransitions` properties. The `allowedTransitions` accepts more than one transition of the specific column key mentioned in `key` property.

If a card is to be dragged to not allowed transition columns , then not supported warning symbol will be displayed for denoting the error.
        
The following code example describes the above Workflow functionality.

{% highlight html %}

    <?php
    require_once '../EJ/AutoLoad.php';
    ?>
    <div class="cols-sample-area">  
    <?php    
    $Json = '[{"Id": 1, "Status": "Open", "Summary": "Analyze the new requirements gathered from the customer.", "Type": "Story", "Priority": "Low", "Tags": "Analyze,Customer", "Estimate": 3.5, "Assignee": "Nancy Davloio", "ImgUrl": "Content/images/kanban/1.png", "RankId":1 }, { "Id": 2, "Status": "Testing", "Summary": "Improve application performance", "Type": "Improvement", "Priority": "Normal", "Tags": "Improvement", "Estimate": 6, "Assignee": "Andrew Fuller", "ImgUrl": "Content/images/kanban/2.png", "RankId":1 }, { "Id": 3, "Status": "InProgress", "Summary": "Arrange a web meeting with the customer to get new requirements.", "Type": "Others", "Priority": "Critical", "Tags": "Meeting", "Estimate": 5.5, "Assignee": "Janet Leverling", "ImgUrl": "Content/images/kanban/3.png", "RankId":2 }, { "Id": 4, "Status": "Close", "Summary": "Fix the issues reported in the IE browser.", "Type": "Bug", "Priority": "Release Breaker", "Tags": "IE", "Estimate": 2.5, "Assignee": "Janet Leverling", "ImgUrl": "Content/images/kanban/3.png", "RankId":2 }, { "Id": 5, "Status": "Validate", "Summary": "Fix the issues reported by the customer.", "Type": "Bug", "Priority": "Low", "Tags": "Customer", "Estimate": "3.5", "Assignee": "Steven walker", "ImgUrl": "Content/images/kanban/5.png", "RankId":1 }]';
    $Json = json_decode($Json,true);
    $kanban = new EJ\Kanban("default");    
	 $constraint = new EJ\Kanban\Constraint();
    $constraint ->max(2);
    $Workflow = new EJ\Kanban\Workflow();
    $Workflow->key('Open')->allowedTransitions('InProgress');
    $Workflow1 = new EJ\Kanban\Workflow();
    $Workflow1->key('InProgress')->allowedTransitions('Testing,Close');
    $column = new EJ\Kanban\Column();
    $column->key('Open')->headerText('Backlog');
    $column1 = new EJ\Kanban\Column();
    $column1->key('InProgress,Validate')->headerText('In Progress or Validate');
	$column2  = new EJ\Kanban\Column();
    $column2->key('Testing')->headerText('Testing');
    $column3 = new EJ\Kanban\Column();
    $column3->key('Close')->headerText('Done');
    $fields = new EJ\Kanban\Field();
    $fields ->content("Summary")->primaryKey("Id");
	$Workflows = array( 
        $Workflow,$Workflow1
        );    
    $columns = array( 
        $column,$column1,$column2,$column3
        );    
    echo $kanban ->columns($columns)->Workflows($Workflows)->dataSource($Json)->fields($fields)->keyField("Status")->render();
    ?>
    </div>

{% endhighlight %}

The following output is displayed as a result of the above code example.

![Workflows in PHP kanban control](WorkFlows_images/workflows1.png)