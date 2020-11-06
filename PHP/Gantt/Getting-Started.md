---
layout: post
title: Getting-Started
description: getting started
platform: php
control: Gantt
documentation: ug
---

# Getting Started

This section explains briefly about how to create a Gantt chart in your application with PHP.

## Create your first Gantt in PHP

In this tutorial, you can learn how to create a simple Gantt chart, add tasks or subtasks, and set relationship between tasks during the design phase of a software project. The following screenshot displays the desired output after completing this tutorial,

![](/PHP/Gantt/Getting-Started_images/Getting-Started_img4.png)

## Adding script references
Create an HTML file and add the following necessary script and CSS files to the HTML file.

{% highlight html %}

    <!DOCTYPE html>

    <html xmlns="http://www.w3.org/1999/xhtml">

    <head>

        <title>Getting Started with Gantt Control for PHP</title>

        <!-- style sheet for default theme(flat azure) -->
        <link href="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/flat-azure/ej.web.all.min.css" rel="stylesheet" />

        <!--scripts-->
        <script src="http://cdn.syncfusion.com/js/assets/external/jquery-1.10.2.min.js"></script>

        <script src="http://cdn.syncfusion.com/js/assets/external/jsrender.min.js"></script>

        <script src="http://cdn.syncfusion.com/js/assets/external/jquery.globalize.min.js"></script>

        <script src="http://cdn.syncfusion.com/js/assets/external/jquery.easing.1.3.min.js"></script>

        <script src="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/ej.web.all.min.js "></script>

    </head>

    <body>
        <!--Add  Gantt control here-->
    </body>

    </html>

{% endhighlight %}

## Initialize Gantt with local data

{% highlight html %}

<body style="width:100%;height:100%;position:static;">
      <?php
    $gantt=new EJ\Gantt("GanttDefault");
    $Json = [{
        taskID: 1,
        taskName: "Design",
        startDate: "02/10/2014",
        endDate: "02/14/2014",
        duration: 6,          
        subtasks: [
            {
                taskID: 2,
                taskName: "Software Specification",
                startDate: "02/10/2014",
                endDate: "02/12/2014",
                duration: 4,
                progress: "60",
                resourceId: [2]
            },
            {
                taskID: 3,
                taskName: "Develop prototype",
                startDate: "02/10/2014",
                endDate: "02/12/2014",
                duration: 4,
                progress: "70",
                resourceId: [3]
            },
        ]
    }];
    echo $gantt -> taskIdMapping("taskID")
    ->taskNameMapping("taskName")
    ->startDateMapping("startDate")
    ->endDateMapping("endDate")
    ->durationMapping("duration")
    ->isResponsive(true)
    ->progressMapping("progress")
    ->childMapping("subtasks")
    ->treeColumnIndex(1)
    ->dataSource($Json)->render();
    ?>
</body>

{% endhighlight %}

## Initialize the Gantt with JSON data from external file.

{% highlight html %}

<body style="width:100%;height:100%;position:static;">
    <?php
    $gantt=new EJ\Gantt("GanttDefault");
    $Json = json_decode(file_get_contents("Data.json"), true);
    $size=new EJ\Gantt\SizeSetting();
    echo $gantt -> taskIdMapping("taskID")
    ->taskNameMapping("taskName")
    ->startDateMapping("startDate")
    ->endDateMapping("endDate")
    ->durationMapping("duration")
    ->isResponsive(true)
    ->progressMapping("progress")
    ->childMapping("subtasks")
    ->treeColumnIndex(1)
    ->dataSource($Json)->render();
    ?>
</body>

{% endhighlight %}

A Gantt chart is created as shown in the following screen shot.

![](/PHP/Gantt/Getting-Started_images/Getting-Started_img5.png)

## Enable Toolbar

Gantt control contains toolbar options to edit, search, expand or collapse all records, indent, outdent, delete, and add a task. You can enable toolbar using the [`toolbarSettings`](http://help.syncfusion.com/js/api/ejgantt#members:toolbarsettings "toolbarSettings") property.

{% highlight javascript %}

<body style="width:100%;height:100%;position:static;">
    <?php
    $gantt=new EJ\Gantt("GanttDefault");
    $Json = json_decode(file_get_contents("Data.json"), true);
    $toolbar=new EJ\Gantt\ToolbarSetting();
    $toolbarItems = array("add","edit","delete","update","cancel","indent","outdent","expandAll","collapseAll","search");
    $toolbar->showToolbar(true)->toolbarItems($toolbarItems);    
    echo $gantt 
    ->toolbarSettings($toolbar)
    //... 
    ->dataSource($Json)->render();
    ?>
</body>

{% endhighlight %}

The following screen shot displays a Tool bar in Gantt chart control:

![](/PHP/Gantt/Getting-Started_images/Getting-Started_img6.png)

N>  Add, edit, delete, indent and outdent options are enabled when enabling the allowEditing, allowAdding, allowDelete, allowIndent and allowOutdent properties in the edit Options.

## Enable Sorting

The Gantt control has sorting functionality to arrange the tasks in ascending or descending order based on a particular column.

### Multicolumn Sorting

Enable the multicolumn sorting in Gantt by setting [`allowMultiSorting`](http://help.syncfusion.com/js/api/ejgantt#members:allowmultisorting "allowMultiSorting") as `true`. You can sort multiple columns in Gantt, by selecting the desired column header while holding the `CTRL` key.

{% highlight javascript %}

   <body style="width:100%;height:100%;position:static;">
    <?php
    $gantt=new EJ\Gantt("GanttDefault");
    $Json = json_decode(file_get_contents("Data.json"), true);
   
    echo $gantt 
    ->allowSorting(true)
    ->allowMultiSorting(true)
    //... 
    ->dataSource($Json)->render();
    ?>
</body>
{% endhighlight %}

## Enable Editing

You can enable editing using [`editSettings`](http://help.syncfusion.com/js/api/ejgantt#members:editsettings "editSettings") and [`allowGanttChartEditing`](http://help.syncfusion.com/js/api/ejgantt#allowganttchartediting "allowGanttChartEditing") options.

### Cell Editing

Modify the task details through the grid cell editing by setting the [`editMode`](http://help.syncfusion.com/js/api/ejgantt#members:editsettings-editmode "editSettings.editMode") as [`cellEditing`](http://help.syncfusion.com/js/api/ejgantt#members:editsettings-editmode "cellEditing").

### Normal Editing

Modify the task details through the edit dialog by setting the [`editMode`](http://help.syncfusion.com/js/api/ejgantt#members:editsettings-editmode "editSettings.editMode") as [`normal`](http://help.syncfusion.com/js/api/ejgantt#members:editsettings-editmode "normal").

### Taskbar Editing

Modify the task details through user interaction such as resizing and dragging the taskbar.

### Predecessor Editing

Modify the predecessor details of a task using mouse interactions by setting [`allowGanttChartEditing`](http://help.syncfusion.com/js/api/ejgantt#members:allowganttchartediting "allowGanttChartEditing") as `true` and setting the value for `predecessorMapping` property.

{% highlight javascript %}

<body style="width:100%;height:100%;position:static;">
    <?php
    $gantt=new EJ\Gantt("GanttDefault");
    $Json = json_decode(file_get_contents("Data.json"), true);
    $edit=new EJ\Gantt\EditSetting();
    $edit->allowAdding(true)->allowDeleting(true)->allowEditing(true)->allowIndent(true);
    echo $gantt 
    ->allowGanttChartEditing(true)
    ->predecessorMapping("predecessor")
    ->editSettings($edit)
    //... 
    ->dataSource($Json)->render();
    ?>
</body>

{% endhighlight %}

The following screen shot displays a Gantt chart control with Enable Editing options.

![](/PHP/Gantt/Getting-Started_images/Getting-Started_img7.png)

N>  Both cellEditing and  normal  editing operations are performed through double-click action.

## Enable Context Menu

You can enable the context menu in Gantt, by setting the [`enableContextMenu`](http://help.syncfusion.com/js/api/ejgantt#members:enablecontextmenu "enableContextMenu") as `true`.

{% highlight javascript %}

<body style="width:100%;height:100%;position:static;">
    <?php
    $gantt=new EJ\Gantt("GanttDefault");
    $Json = json_decode(file_get_contents("Data.json"), true);   
    echo $gantt 
    ->enableContextMenu(true)
    //... 
    ->dataSource($Json)->render();
    ?>
</body>

{% endhighlight %}

The following screen shot displays Gantt chart in which Context menu option is enabled:

![](/PHP/Gantt/Getting-Started_images/Getting-Started_img8.png)

## Enable Column Menu

You can enable the column menu in Gantt, by setting the [`showColumnChooser`](http://help.syncfusion.com/js/api/ejgantt#members:showcolumnchooser "showColumnChooser") as `true`.

{% highlight javascript %}

<body style="width:100%;height:100%;position:static;">
    <?php
    $gantt=new EJ\Gantt("GanttDefault");
    $Json = json_decode(file_get_contents("Data.json"), true);   
    echo $gantt 
    ->showColumnChooser(true)
    //... 
    ->dataSource($Json)->render();
    ?>
</body>

{% endhighlight %}

The following screen shot displays Gantt chart in which column chooser option is enabled:

![](/PHP/Gantt/Getting-Started_images/Getting-Started_img11.png)

## Provide tasks relationship

In Gantt, you have the predecessor support to show the relationship between two different tasks.

* **Start to Start (SS)** - You cannot start a task until the other task also starts.
* **Start to Finish (SF)** - You cannot finish a task until the other task finishes.
* **Finish to Start (FS)** - You cannot start a task until the other task completes.
* **Finish to Finish (FF)** - You cannot finish a task until the other task completes.

You can show the relationship in tasks, by using the [`predecessorsMapping`](http://help.syncfusion.com/js/api/ejgantt#members:predecessormapping "predecessorsMapping")

, as shown in the following code example.

{% highlight javascript %}

<body style="width:100%;height:100%;position:static;">
    <?php
    $gantt=new EJ\Gantt("GanttDefault");
    $Json = json_decode(file_get_contents("Data.json"), true);   
    echo $gantt 
    ->predecessorMapping("predecessor")
    //... 
    ->dataSource($Json)->render();
    ?>
</body>

{% endhighlight %}

The following screenshot displays the relationship between tasks.

![](/PHP/Gantt/Getting-Started_images/Getting-Started_img9.png)

## Provide Resources

In Gantt control, you can display and assign the resource for each task. Create a collection of `JSON` object, which contains id and name of the resource and assign it to [`resources`](http://help.syncfusion.com/js/api/ejgantt#members:resources "resources") property. Then, specify the field name for id and name of the resource in the resource collection to [`resourceIdMapping`](http://help.syncfusion.com/js/api/ejgantt#members:resourceidmapping "resourceIdMapping") and [`resourceNameMapping`](http://help.syncfusion.com/js/api/ejgantt#members:resourcenamemapping "resourceNameMapping") options. The name of the field, which contains the actual resources assigned for a particular task in the `dataSource` is specified using [`resourceInfoMapping`](http://help.syncfusion.com/js/api/ejgantt#members:resourceinfomapping "resourceInfoMapping").

1.Initialize the Gantt with resources

{% highlight javascript %}

<body style="width:100%;height:100%;position:static;">
      <?php
    $gantt=new EJ\Gantt("GanttDefault");
    $resource=[{
        resourceId: 1,
        resourceName: "Project Manager"
    },{
        resourceId: 2,
        resourceName: "Software Analyst"
    },{
        resourceId: 3,
        resourceName: "Developer"
    },{
        resourceId: 4,
        resourceName: "Testing Engineer"
    }];
    echo $gantt
    ->resourceInfoMapping("resourceId") //Field name which contains resource details for the task
    ->resourceNameMapping("resourceName") //resource Name mapping
    ->resourceIdMapping("resourceId") //resource Id Mapping
    ->resources($resource) //resource collection dataSource
    ->render();
    ?>
</body>

{% endhighlight %}

The following screenshot displays resource allocation for tasks in Gantt chart.

![](/PHP/Gantt/Getting-Started_images/Getting-Started_img10.png)

By following these steps, you have learned how to provide data source to Gantt chart, how to configure Gantt to set task relationships, assign resources for each task, and add toolbar with necessary buttons.

## Highlight Weekend

In Gantt, you can on or off weekends high lighting by setting the [`highlightWeekEnds`](http://help.syncfusion.com/js/api/ejgantt#members:highlightweekends "highlightWeekEnds")

 as `true` or `false`.

{% highlight javascript %}

<body style="width:100%;height:100%;position:static;">
    <?php
    $gantt=new EJ\Gantt("GanttDefault");
    $Json = json_decode(file_get_contents("Data.json"), true);   
    echo $gantt 
    ->highlightWeekEnds(false)
    //... 
    ->dataSource($Json)->render();
    ?>
</body>

{% endhighlight %}

The following screen shot displays Gantt chart in which highlight weekends is disabled:

![](/PHP/Gantt/Getting-Started_images/Getting-Started_img12.png)
