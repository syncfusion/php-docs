---
layout: post
title:  Responsive | Kanban | PHP | Syncfusion
description: This section explains the responsive behavior of the Syncfusion PHP Kanban component based on the client browser width and height.
documentation: ug
platform: php
keywords: responsive,kanban responsive
---

# Responsive

The Kanban control has support for responsive behavior based on client browser’s width and height. To enable responsive, `isResponsive` property should be true.There are two modes of responsive layout is available in Kanban based on client width. They are.

* Mobile(<480px)
* Desktop(>480px)

You can check the image representation of touch actions from the below image.

![Responsive](Responsive_images/KanbanOverlayImage.png)

## Mobile Layout

If client width is less than 480px, the Kanban will render in mobile mode. In which, you can see that kanban user interface is customized and redesigned for best view in small screens.To enable responsive, `isResponsive` property should be true.

{% highlight html %}

    <?php
    require_once "../EJ/AutoLoad.php";
    ?>
    <div class="cols-sample-area">
    <?php
    $Json = '[{"Id": 1, "Status": "Open", "Summary": "Analyze the new requirements gathered from the customer.", "Type": "Story", "Priority": "Low", "Tags": "Analyze,Customer", "Estimate": 3.5, "Assignee": "Nancy Davloio", "ImageUrl": "Content/images/kanban/1.png", "RankId":1 }, { "Id": 2, "Status": "InProgress", "Summary": "Improve application performance", "Type": "Improvement", "Priority": "Normal", "Tags": "Improvement", "Estimate": 6, "Assignee": "Andrew Fuller", "ImageUrl": "Content/images/kanban/2.png", "RankId":1 }, { "Id": 3, "Status": "Open", "Summary": "Arrange a web meeting with the customer to get new requirements.", "Type": "Others", "Priority": "Critical", "Tags": "Meeting", "Estimate": 5.5, "Assignee": "Janet Leverling", "ImageUrl": "Content/images/kanban/3.png", "RankId":2 }, { "Id": 4, "Status": "InProgress", "Summary": "Fix the issues reported in the IE browser.", "Type": "Bug", "Priority": "Release Breaker", "Tags": "IE", "Estimate": 2.5, "Assignee": "Janet Leverling", "ImageUrl": "Content/images/kanban/3.png", "RankId":2 }, { "Id": 5, "Status": "Testing", "Summary": "Fix the issues reported by the customer.", "Type": "Bug", "Priority": "Low", "Tags": "Customer", "Estimate": "3.5", "Assignee": "Steven walker", "ImageUrl": "Content/images/kanban/5.png", "RankId":1 }, { "Id": 6, "Status": "Close", "Summary": "Arrange a web meeting with the customer to get the login page requirements.", "Type": "Others", "Priority": "Low", "Tags": "Meeting", "Estimate": 2, "Assignee": "Michael Suyama", "ImageUrl": "Content/images/kanban/6.png", "RankId":1 }, { "Id": 7, "Status": "Close", "Summary": "Validate new requirements", "Type": "Improvement", "Priority": "Low", "Tags": "Validation", "Estimate": 1.5, "Assignee": "Robert King", "ImageUrl": "Content/images/kanban/7.png", "RankId":1 }, { "Id": 8, "Status": "Close", "Summary": "Login page validation", "Type": "Story", "Priority": "Release Breaker", "Tags": "Validation,Fix", "Estimate": 2.5, "Assignee": "Laura Callahan", "ImageUrl": "Content/images/kanban/8.png", "RankId":2 }, { "Id": 9, "Status": "Testing", "Summary": "Fix the issues reported in Safari browser.", "Type": "Bug", "Priority": "Release Breaker", "Tags": "Fix,Safari", "Estimate": 1.5, "Assignee": "Nancy Davloio", "ImageUrl": "Content/images/kanban/1.png", "RankId":2 }]';
    $Json = json_decode($Json,true);
    $colorMap = '{"#ee4e75": "Bug,Story","#57b94c": "Improvement","#edba3c": "Epic","#5187c6": "Others"}';
    $colorMap = json_decode($colorMap,true);
    $kanban = new EJ\Kanban("dialogEdit");
    $column = new EJ\Kanban\Column();
    $column ->key("Open")->headerText("Backlog")->showAddButton(true);
    $column1 = new EJ\Kanban\Column();    
    $column1 ->key("InProgress")->headerText("In Progress");
    $column2  = new EJ\Kanban\Column();
    $column2 ->key("Testing")->headerText("Testing");
    $column3 = new EJ\Kanban\Column();
    $column3 ->key("Close")->headerText("Done");
    $cardSetting = new EJ\Kanban\CardSetting();
    $cardSetting ->colorMapping($colorMap);
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
    $fields ->content("Summary")->primaryKey("Id")->swimlaneKey('Assignee')->imageUrl("ImageUrl");
	$filterQuery = new EJ\Query();
    $filterQuery->where("'Assignee','equal','Janet Leverling'");
    $filterQuery1 = new EJ\Query();
    $filterQuery1->where("'Status','equal','Close'");
    $filter = new EJ\Kanban\FilterSetting();
    $filter->text("Janet Issues")->query($filterQuery)->description("Displays issues which matches the assignee as Janet Leverling");
    $filter1 = new EJ\Kanban\FilterSetting();
    $filter1->text("Closed Issues")->query($filterQuery1)->description("Display the issues of 'Closed Issues'");	
    $columns = array($column,$column1,$column2,$column3);    
    echo $kanban->keyField("Status")->allowFiltering(true)->allowSearching(true)->allowKeyboardNavigation(true)->filterSettings(array($filter,$filter1))->allowTitle(true)->isResponsive(true)->columns($columns)->cardSettings($cardSetting)->fields($fields)->editSettings($editSetting)->dataSource($Json)->render();
    ?>
    </div>

{% endhighlight %}
   
![Mobild Layout](Responsive_images/Responsive_img2.png)


W> IE8 and IE9 does not support responsive kanban. `ej.responsive.css` should be referred to display Responsive Kanban.

![Responsive](Responsive_images/Responsive_img3.png)
{:caption}
CRUD in mobile layout

![CRUD in mobile layout](Responsive_images/Responsive_img4.png)
{:caption}
Filtering in mobile layout

![Filtering in mobile layout](Responsive_images/Responsive_img5.png)
{:caption}
Searching in mobile layout

![Searching](Responsive_images/Responsive_img6.png)

![Searching in mobile layout](Responsive_images/Responsive_img7.png)
{:caption}
Kanban with Swim-lane

## Width

By default, the Kanban is adaptable to its parent container. It can adjust its width of columns based on parent container width. You can also assign width of `columns` in percentage. 

The following code example describes the above behavior.


{% highlight html %}

    <?php
    require_once '../EJ/AutoLoad.php';
    ?>
    <div class="cols-sample-area">
    <?php    
    $Json = '[{"Id": 1, "Status": "Open", "Summary": "Analyze the new requirements gathered from the customer.", "Type": "Story", "Priority": "Low", "Tags": "Analyze,Customer", "Estimate": 3.5, "Assignee": "Nancy Davloio", "ImageUrl": "Content/images/kanban/1.png", "RankId":1 }, { "Id": 2, "Status": "InProgress", "Summary": "Improve application performance", "Type": "Improvement", "Priority": "Normal", "Tags": "Improvement", "Estimate": 6, "Assignee": "Andrew Fuller", "ImageUrl": "Content/images/kanban/2.png", "RankId":1 }, { "Id": 3, "Status": "Open", "Summary": "Arrange a web meeting with the customer to get new requirements.", "Type": "Others", "Priority": "Critical", "Tags": "Meeting", "Estimate": 5.5, "Assignee": "Janet Leverling", "ImageUrl": "Content/images/kanban/3.png", "RankId":2 }, { "Id": 4, "Status": "InProgress", "Summary": "Fix the issues reported in the IE browser.", "Type": "Bug", "Priority": "Release Breaker", "Tags": "IE", "Estimate": 2.5, "Assignee": "Janet Leverling", "ImageUrl": "Content/images/kanban/3.png", "RankId":2 }, { "Id": 5, "Status": "Close", "Summary": "Fix the issues reported by the customer.", "Type": "Bug", "Priority": "Low", "Tags": "Customer", "Estimate": "3.5", "Assignee": "Steven walker", "ImageUrl": "Content/images/kanban/5.png", "RankId":1 }]';
    $Json = json_decode($Json,true);
    $kanban = new EJ\Kanban("default");    
    $column = new EJ\Kanban\Column();
    $column ->key("Open")->headerText("Backlog")->width("10%") ;    
    $column1 = new EJ\Kanban\Column();
    $column1 ->key("InProgress")->headerText("In Progress")->width("10%");      
    $column2 = new EJ\Kanban\Column();
    $column2 ->key("Close")->headerText("Done")->width("10%");    
    $fields = new EJ\Kanban\Field();
    $fields ->content("Summary")->primaryKey("Id")->tag('Tags');
    $columns = array( 
        $column,$column1,$column2
        );    
    echo $kanban ->columns($columns)->dataSource($Json)->isResponsive(true)->fields($fields)->keyField("Status")->render();
    ?>
    </div>

{% endhighlight %}

N> `allowScrolling` should be false while defining width in percentage.

## Min Width

Min Width is used to maintain minimum width for the Kanban. If the Kanban width is less than `minWidth` then the scrollbar will be displayed to maintain minimum width.

The following code example describes the above behavior.

{% highlight html %}

    <?php
    require_once '../EJ/AutoLoad.php';
    ?>
    <div class="cols-sample-area">
    <?php    
    $Json = '[{"Id": 1, "Status": "Open", "Summary": "Analyze the new requirements gathered from the customer.", "Type": "Story", "Priority": "Low", "Tags": "Analyze,Customer", "Estimate": 3.5, "Assignee": "Nancy Davloio", "ImageUrl": "Content/images/kanban/1.png", "RankId":1 }, { "Id": 2, "Status": "Open", "Summary": "Improve application performance", "Type": "Improvement", "Priority": "Normal", "Tags": "Improvement", "Estimate": 6, "Assignee": "Andrew Fuller", "ImageUrl": "Content/images/kanban/2.png", "RankId":1 }, { "Id": 3, "Status": "Open", "Summary": "Arrange a web meeting with the customer to get new requirements.", "Type": "Others", "Priority": "Critical", "Tags": "Meeting", "Estimate": 5.5, "Assignee": "Janet Leverling", "ImageUrl": "Content/images/kanban/3.png", "RankId":2 }, { "Id": 4, "Status": "InProgress", "Summary": "Fix the issues reported in the IE browser.", "Type": "Bug", "Priority": "Release Breaker", "Tags": "IE", "Estimate": 2.5, "Assignee": "Janet Leverling", "ImageUrl": "Content/images/kanban/3.png", "RankId":2 }, { "Id": 5, "Status": "Open", "Summary": "Fix the issues reported by the customer.", "Type": "Bug", "Priority": "Low", "Tags": "Customer", "Estimate": "3.5", "Assignee": "Steven walker", "ImageUrl": "Content/images/kanban/5.png", "RankId":1 }]';
    $Json = json_decode($Json,true);
    $kanban = new EJ\Kanban("default");    
    $column = new EJ\Kanban\Column();
    $column ->key("Open")->headerText("Backlog")->width(120) ;    
    $column1 = new EJ\Kanban\Column();
    $column1 ->key("InProgress")->headerText("In Progress")->width(110);      
    $column2 = new EJ\Kanban\Column();
    $column2 ->key("Close")->headerText("Done")->width(110);    
    $fields = new EJ\Kanban\Field();
    $fields ->content("Summary")->primaryKey("Id")->tag('Tags');
    $columns = array( 
        $column,$column1,$column2
        );    
    echo $kanban ->columns($columns)->dataSource($Json)->minWidth(700)->isResponsive(true)->fields($fields)->keyField("Status")->render();
    ?>
    </div>

{% endhighlight %}

The following output is displayed as a result of the above code example.

![Minimum Width](Responsive_images/responsive_img1.png)
