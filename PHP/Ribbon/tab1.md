---
title: Tab	
description: Overview of tab ribbon control.
platform: php
control: ribbon
documentation: ug
keywords: ribbon features, key features, ribbon overview 
---

# Tab

Tab is a collection of control groups which enables you to organize related commands into single view. Tabs can be added to Ribbon using tabs property. id & text properties are used to set unique ID and header text to Tab. The manipulation of given text tab in the ribbon control can be done by using  [`addTab`](https://help.syncfusion.com/api/js/ejribbon#methods:addtab), [`removeTab`](https://help.syncfusion.com/api/js/ejribbon#methods:removetab), [`hideTab`](https://help.syncfusion.com/api/js/ejribbon#methods:hidetab),
[`showTab`](https://help.syncfusion.com/api/js/ejribbon#methods:showtab) methods and [`tabAdd`](https://help.syncfusion.com/api/js/ejribbon#events:tabadd), [`tabCreate`](https://help.syncfusion.com/api/js/ejribbon#events:tabcreate), [`tabRemove`](https://help.syncfusion.com/api/js/ejribbon#events:tabremove), [`tabClick`](https://help.syncfusion.com/api/js/ejribbon#events:tabclick) and [`tabSelect`](https://help.syncfusion.com/api/js/ejribbon#events:tabselect) events.

{% highlight html %}

            <div id="Ribbon"></div>
             <ul id="ribbonMenu">
                 <li><a>FILE</a>
                  <ul>
                     <li><a>Open</a></li>
                  </ul>
                 </li>
             </ul>
             <div id="sendReceive">
                Send/Receive All Folders
             </div>
            <?php 
            require_once 'EJ\AutoLoad.php';
            $ribbon = new  \EJ\Ribbon('defaultRibbon');
            $aTab = new \EJ\Ribbon\ApplicationTab();
            $aTab->type('menu')->menuItemID('ribbonMenu'); 
            $homeTab  = new \EJ\Ribbon\Tab();
            $sendRect = new \EJ\Ribbon\Tab();
            $clipboard1  = new \EJ\Ribbon\Group();
            $grpcontent1 = new \EJ\Ribbon\Content();
            $contentgroup1 = new \EJ\Ribbon\ContentGroup();
            $btnsettings1 = array('contentType'=>'imageonly','imagePosition'=>'imagetop','prefixIcon'=>'e-icon e-ribbon e-ribbonsave');
            $contentgroup1->id("save")->text("Save")->toolTip("Save")->buttonSettings($btnsettings1);     
            $grpcontent1->groups(array($contentgroup1));
            $clipboard1->text('Save')->content(array($grpcontent1));
            $homeTab->id('home')->text('HOME')->groups(array($clipboard1));
            $clipboard2  = new \EJ\Ribbon\Group();
            $grpcontent2 = new \EJ\Ribbon\Content();
            $contentgroup2 = new \EJ\Ribbon\ContentGroup();
            $btnsettings2 = array('contentType'=>'imageonly','imagePosition'=>'imagetop','prefixIcon'=>'e-icon e-ribbon e-ribbonprint');
            $contentgroup2->id("print")->text("Print")->toolTip("Print")->buttonSettings($btnsettings2);   
            $grpcontent2->groups(array($contentgroup1,$contentgroup2));
            $clipboard1->text('Save')->content(array($grpcontent1,$grpcontent2));
            $homeTab->id('home')->text('HOME')->groups(array($clipboard1));
            $sendRect->id('sendRec')->text('Send/Receive')->groups(array('type'=>'custom','contentID'=>'sendReceive'));
            echo $ribbon ->width('500px')->applicationTab($aTab)->tabs(array($homeTab,$sendRect))->render();
            ?>

{% endhighlight %}

![](Tab/tab_img1.png)