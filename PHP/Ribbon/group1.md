---
title: Group
description: Overview of Group ribbon control.
platform: php
control: ribbon
documentation: ug
keywords: ribbon features, key features, ribbon overview 
---

# Group

Group is a collection of logical content groups that are combined under related Tab. Each group can be defined using content groups or custom content.

## Adding Tab Groups

Group items can be added to Tabs by specifying text and corresponding content to be displayed. The content of group can be specified as either with content collection, contentID or customContent. You can add tab group dynamically in the ribbon control with given tab index, tab group object and group index position by using [`addTabGroup`](https://help.syncfusion.com/api/js/ejribbon#methods:addtabgroup) method.

### Adding Content

Add content to Group item which is based on type of content specified. The available types are button, splitButton, toggleButton,gallery, and dropDownList.

Groups and defaults settings can be added with the content. You can add group content dynamically in the ribbon control with given tab index, group index, content, content index and sub group index position by using [`addTabGroupContent`](https://help.syncfusion.com/api/js/ejribbon#methods:addtabgroupcontent).

## Defaults

The [`tabs.groups.content.defaults.height`](https://help.syncfusion.com/api/js/ejribbon#members:tabs-groups-content-defaults-height), [`tabs.groups.content.defaults.width`](https://help.syncfusion.com/api/js/ejribbon#members:tabs-groups-content-defaults-width), 
[`tabs.groups.content.defaults.type`](https://help.syncfusion.com/api/js/ejribbon#members:tabs-groups-content-defaults-type), [`tabs.groups.content.defaults.isBig`](https://help.syncfusion.com/api/js/ejribbon#members:tabs-groups-content-defaults-isbig) property to the controls in the [`group`](https://help.syncfusion.com/api/js/ejribbon#members:tabs-groups-content-groups) can be specified commonly.

The height & width applicable to button, split button, dropdown list ,Toggle button controls and isBig applicable to only button controls ( button, split , toggle)

## Adding Content Groups

Controls such as button, split button, dropdown list, toggle button, gallery in the subgroup of the Ribbon tab can be rendered. All of these can be customized using its corresponding settings property such as buttonSettings, dropdownSettings, etc.

Custom controls or items (such as table, div etc.) can be added when the type set as custom. defaults control settings of group can be specified for an individual group instead of specifying them to groups collection commonly.

Tooltip and Custom Tooltip can be specified for each group controls.

{% highlight html %}

        <div id="Ribbon"></div>
	     <ul id="ribbonMenu">
		    <li><a>FILE</a>
		     <ul>
		        <li><a>Open</a></li>
		     </ul>
		    </li>
	     </ul>
	     <ul id="pasteSplit">
		    <li>Paste</li>
		    <li>Paste Special</li>
	     </ul>
        <?php
		require_once 'EJ\AutoLoad.php';
        $ribbon = new  \EJ\Ribbon('defaultRibbon');
        $aTab = new \EJ\Ribbon\ApplicationTab();           
        $aTab->type('menu')->menuItemID('ribbonMenu');  
        $homeTab  = new \EJ\Ribbon\Tab();
        $clipboard  = new \EJ\Ribbon\Group();
        $grpContent = new \EJ\Ribbon\Content();
        $contentGroup=new \EJ\Ribbon\ContentGroup();
        $splitButtonSettings = array('contentType'=>'imageonly','targetID'=>'pasteSplit','imagePosition'=>'imagetop','prefixIcon'=>'e-icon e-ribbon e-ribbonpaste'); 
        $contentGroup->id('paste')->text('Paste')->toolTip('Paste')->splitButtonSettings($splitButtonSettings);   
        $default= new \EJ\Ribbon\Defaults();
        $default->width(60)->height(40)->type("splitbutton");
        $grpContent->groups(array($contentGroup))->defaults($default);
        $clipboard->text('ClipBoard')->content(array($grpContent));
        $clipboard1  = new \EJ\Ribbon\Group();
        $grpContent1 = new \EJ\Ribbon\Content();
        $contentGroup1=new \EJ\Ribbon\ContentGroup();
        $contentGroup2=new \EJ\Ribbon\ContentGroup();
        $togglebutton =  array('defaultText'=>'Cut','targetID'=>'pasteSplit','activeText'=>'Cut Over'); 
        $togglebutton1 =  array('defaultText'=>'Copy','targetID'=>'pasteSplit','activeText'=>'Copy Over'); 
        $contentGroup1->id('cut')->toggleButtonSettings($togglebutton);
        $contentGroup2->id('copy')->toggleButtonSettings($togglebutton1);
        $default1= new \EJ\Ribbon\Defaults();
        $default1->width(75)->height(30)->type("togglebutton");
        $grpContent1->groups(array($contentGroup1,$contentGroup2))->defaults($default1);
        $clipboard1->text('Font')->alignType("columns")->content(array($grpContent1));
        $homeTab->id('home')->text('HOME')->groups(array($clipboard,$clipboard1));
        echo $ribbon ->width('500px')->applicationTab($aTab)->tabs(array($homeTab))->render();
        ?>

{% endhighlight %}

![](Group/group_img1.png)

## Enable Separator

Separates the control from the next control in the group when group alignType is row. Set �true� to enableSeparator.

{% highlight html %}

        <div id="Ribbon"></div>
	     <ul id="ribbonMenu">
		    <li><a>FILE</a>
		     <ul>
			    <li><a>New</a></li>
                <li><a>Open</a></li>
		     </ul>
		    </li>
	     </ul>
        <?php
		require_once 'EJ\AutoLoad.php';
        $ribbon = new  \EJ\Ribbon('defaultRibbon');
        $aTab = new \EJ\Ribbon\ApplicationTab();           
        $aTab->type('menu')->menuItemID('ribbonMenu');  
        $homeTab  = new \EJ\Ribbon\Tab();
        $clipboard  = new \EJ\Ribbon\Group();
        $grpContent = new \EJ\Ribbon\Content();
        $contentGroup=new \EJ\Ribbon\ContentGroup();
        $contentGroup1=new \EJ\Ribbon\ContentGroup();
        $buttonSettings = array('width'=> 100); 
        $contentGroup->id('new')->text('New')->toolTip('New')->enableSeparator('true')->buttonSettings($buttonSettings);   
        $buttonSettings1 = array('width'=> 150);
        $contentGroup1->id('font')->text('Font')->toolTip('Font')->buttonSettings($buttonSettings1);  
        $default= new \EJ\Ribbon\Defaults();
        $default->width(70)->type('button');
        $grpContent->groups(array($contentGroup,$contentGroup1))->defaults($default);
        $clipboard->text('New')->alignType('rows')->content(array($grpContent));
        $homeTab->id('home')->text('HOME')->groups(array($clipboard));
        echo $ribbon ->width('500px')->applicationTab($aTab)->tabs(array($homeTab))->render();
        ?>

{% endhighlight %}

![](Group/group_img2.png)

## Adding Custom Content

Set group type as custom to add custom items such as div, table and custom controls. With type as custom, content can be added in two ways as specified below.

* HTML contents can be directly added into the groups as string content using customContent property
* Custom template id can be specified to render those specific custom template using contentID property

{% highlight html %}

        <div id="Ribbon"></div>
	     <ul id="ribbonMenu">
		    <li><a>FILE</a>    
		     <ul>
			    <li><a>New</a></li>
		     </ul>
		    </li>
	     </ul>
         <button id='button'>Using Content ID</button>
        <?php
		require_once 'EJ\AutoLoad.php';
        $ribbon = new  \EJ\Ribbon('defaultRibbon');
        $aTab = new \EJ\Ribbon\ApplicationTab();           
        $aTab->type('menu')->menuItemID('ribbonMenu');  
        $homeTab  = new \EJ\Ribbon\Tab();
        $clipboard  = new \EJ\Ribbon\Group();
        $clipboard1  = new \EJ\Ribbon\Group();
        $grpContent = new \EJ\Ribbon\Content();
        $grpContent1 = new \EJ\Ribbon\Content();
        $contentGroup=new \EJ\Ribbon\ContentGroup();
        $contentGroup1=new \EJ\Ribbon\ContentGroup(); 
        $clipboard->text('New')->type('custom')->customContent("<button id='customContent'>Using Custom Content</button>");   
        $clipboard1->text('Data')->type('custom')->contentID('button');  
        $homeTab->id('home')->text('HOME')->groups(array($clipboard,$clipboard1));
        echo $ribbon ->width('500px')->applicationTab($aTab)->tabs(array($homeTab))->render();
        ?>  
              
{% endhighlight %}

![](Group/group_img3.png)

## Group Expander

Set enableGroupExpander as true to show Group Expander for each group in Tab. These expanders can be customized using groupExpand event, such as to show popup dialog. To specify tooltip for the group expander of the group [`tabs.groups.groupExpanderSettings`](https://help.syncfusion.com/api/js/ejribbon#members:tabs-groups-groupexpandersettings) and 
[`tabs.groups.groupExpanderSettings.toolTip`](https://help.syncfusion.com/api/js/ejribbon#members:tabs-groups-groupexpandersettings-tooltip) can be used.

{% highlight html %}

        <div id="Ribbon"></div>
	     <ul id="ribbonMenu">
		    <li><a>FILE</a>    
		     <ul>
			    <li><a>New</a></li>
		     </ul>
		    </li>
	     </ul>
         <button id='button'>Home button</button>
        <?php
		require_once 'EJ\AutoLoad.php';
        $ribbon = new  \EJ\Ribbon('defaultRibbon');
        $aTab = new \EJ\Ribbon\ApplicationTab();           
        $aTab->type('menu')->menuItemID('ribbonMenu');  
        $homeTab  = new \EJ\Ribbon\Tab();
        $clipboard  = new \EJ\Ribbon\Group();
        $clipboard->text('New')->alignType("rows")->type('custom')->enableGroupExpander(true)->contentID('button');    
        $homeTab->id('home')->text('HOME')->groups(array($clipboard));
        echo $ribbon ->width('500px')->applicationTab($aTab)->tabs(array($homeTab))->render();
        ?>
        <script>
             groupExpand: function (args) {
                 alert("Group expander click triggered");
             }
        </script>
              
{% endhighlight %}

![](Group/group_img4.png)
