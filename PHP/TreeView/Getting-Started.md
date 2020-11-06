---
title: Getting Started with TreeView | TreeView | PHP | Syncfusion
description: To get start with TreeView by adding references
platform: php
control: TreeView
documentation: UG
keywords: 
---
# Getting started

This section explains briefly about how to create a **TreeView** in your application with **PHP** wrapper classes of EJ controls.	

## Create your first TreeView in PHP

Create a PHP Project and add necessary scripts and styles with the help of the given PHP Getting Started Documentation.

## TreeView using “TreeViewItem” Property

You can create a tree using “TreeViewItem” property of TreeView control. Here there is no necessary to use a data source for rendering TreeView.

You can render the PHP TreeView with specified items.

    
    {% highlight php %}

    <?php
        $tree = new EJ\TreeView('treeView');

        $tree1 = new EJ\TreeView\TreeViewItem();
        $tree1->id('1')->text('Item 1');
        $tree2 = new EJ\TreeView\TreeViewItem();
        $tree2->id('2')->text('Item 2');
        $tree3 = new EJ\TreeView\TreeViewItem();
        $tree3->id('3')->text('Item 3');

        $tree11 = new EJ\TreeView\TreeViewItem();
        $tree11->id('11')->text('Item 1.1');    

        $tree111 = new EJ\TreeView\TreeViewItem();
        $tree111->id('121')->text('Item 1.1.1');    

        $tree21 = new EJ\TreeView\TreeViewItem();
        $tree21->id('21')->text('Item 2.1');
        $tree22 = new EJ\TreeView\TreeViewItem();
        $tree22->id('21')->text('Item 2.2');

        $tree31 = new EJ\TreeView\TreeViewItem();
        $tree31->id('31')->text('Item 3.1');   

        $tree11->addItem($tree111);    
        $tree1->addItem($tree11);
        $tree2->addItem($tree21,$tree22);    
        $tree3->addItem($tree31);
        $tree->addItem($tree1,$tree2,$tree3);
        echo $tree->render();
    ?>

    {% endhighlight %}
    

## Tree View using Data Binding

Another way of creating TreeView is binding with the data source, you can bind local data source to create a TreeView.

The [beforeLoad](https://help.syncfusion.com/api/js/ejtreeview#events:beforeload) event will be triggered before loading nodes into TreeView.

**Render TreeView with local data source.**

First specify the tree data source in array format then map the data source items with tree view fields as shown below.


    {% highlight php %}

    <?php
        $localData = array(
                        array('id'=>1, 'name'=>'Item 1', 'hasChild'=>true, 'expanded'=>true ),
                        array('id'=>2, 'parent'=>1, 'name'=>'Item 1.1' ),
                        array('id'=>3, 'parent'=>1, 'name'=>'Item 1.2' ),                    
                        array('id'=>4, 'name'=>'Item 2', 'hasChild'=>false, 'isChecked'=>true ),
                        array('id'=>4, 'name'=>'Item 3', 'hasChild'=>false ),                    
                        );
        $treeview = new \EJ\TreeView('localData');
        $fields = new EJ\TreeView\Field();
        $fields->id('id')->text('name')->parentId('parent')->hasChild('hasChild')->dataSource($localData)
            ->expanded('expanded')->isChecked('isChecked');
        echo $treeview->showCheckbox(true)->fields($fields)->render();
        ?>

    {% endhighlight %}



**Render TreeView using JSON file data**

You can get and decode the JSON file content using "**file_get_contents**" and "**json_decode**" methods respectively and then assign the decoded data to the “**datasource**” field of TreeView control. Please refer the below code example.

    {% highlight php %}

    <?php
        $Json = json_decode(file_get_contents("Data.json"), true);
        $treeview = new \EJ\TreeView("localData");
        $fields = new EJ\TreeView\Field();
        $fields->id("id")->text("name")->parentId("parent")->hasChild("hasChild")->dataSource($Json)->expanded("expanded")->isChecked("isChecked");
        echo $treeview->fields($fields)->render();
    ?>

    {% endhighlight %}

JSON file content
 
    {% highlight json %}
        
        [
        { "id": 1, "name": "Discover Music", "hasChild": true, "expanded": true },
        { "id": 2, "parent": 1, "name": "Hot Singles" },
        { "id": 3, "parent": 1, "name": "Rising Artists" },
        { "id": 4, "parent": 1, "name": "Live Music" },
        { "id": 6, "parent": 1, "name": "Best of 2013 So Far" },
        { "id": 7, "name": "Sales and Events", "hasChild": true, "expanded": true },
        { "id": 8, "parent": 7, "name": "100 Albums - $5 Each" },
        { "id": 9, "parent": 7, "name": "Hip-Hop and R&B Sale" },
        { "id": 10, "parent": 7, "name": "CD Deals" }
        ]


    {% endhighlight %}

## Create Instance for TreeView

You can create an instance for existing TreeView in following ways. Once a reference has been established, you can use the [API’s](http://help.syncfusion.com/js/api/ejtreeview#) of TreeView to control its behavior.


    {% highlight php %}

    <script type="text/javascript">
    $(function () {
            //Specify this after your TreeView creation
            //create instance for TreeView
            debugger
            var treeObj = $("#treeView").ejTreeView('instance');
            //or
            var treeObj1 = $("#treeView").data("ejTreeView");
    });
    </script>

    {% endhighlight %}

N>To configure the API settings after TreeView creation, please refer [API configuration](http://help.syncfusion.com/js/api-configuration#), [Invoking Methods](http://help.syncfusion.com/js/invoking-methods#).

## TreeView events

EJ PHP TreeView supports all the client side [events](http://help.syncfusion.com/js/api/ejtreeview#events) which is available in EJ TreeView. Refer following code example to specify an event using EJ PHP TreeView element.


    {% highlight php %}

    <?php
        $localData = array(
                        array("id"=>1, "name"=>"Item 1", "hasChild"=>true, "expanded"=>true ),
                        array("id"=>2, "parent"=>1, "name"=>"Item 1.1" ),
                        array("id"=>3, "parent"=>1, "name"=>"Item 1.2" ),                    
                        array("id"=>4, "name"=>"Item 2", "hasChild"=>false, "isChecked"=>true ),
                        array("id"=>4, "name"=>"Item 3", "hasChild"=>false ),                    
                        );
        $treeview = new \EJ\TreeView("localData");
        $fields = new EJ\TreeView\Field();
        $fields->id("id")->text("name")->parentId("parent")->hasChild("hasChild")->dataSource($localData)
            ->expanded("expanded")->isChecked("isChecked");
        echo $treeview->showCheckbox(true)->fields($fields)->nodeExpand("onExpand")->nodeCollapse("onCollapse")->nodeSelect("onSelect")->render();
    ?>

        <script type="text/javascript">
            function onCollapse(args) {
                //Handle the node collapse event
            }
        
            function onExpand(args) {
                //Handle the node expand event
            }
        
            function onSelect(args) {
                //Handle the node select event
            }
        </script>

    {% endhighlight %}

