---
title: Quick Access Toolbar
description: Overview of Quick Access Toolbar ribbon control.
platform: php
control: ribbon
documentation: ug
keywords: ribbon features, key features, ribbon overview 
---

# Quick Access Toolbar

Quick Access Toolbar provides the shortcuts to the most commonly used commands by placing the controls at the Quick Access Toolbar section. It can be placed at the top or bottom of the Ribbon.

Set `showQAT` as true to enable Quick Access Toolbar in Ribbon. It supports the Button, Split Button, Toggle Button controls. The quickAccessMode is used to change the controls state in Quick Access Toolbar through options as toolbar,menu and none. Default value is none and QAT toolbar is created with specified controls added in Toolbar.

The toolbar option used to set controls visibility in Quick Access Toolbar.The menu option shows the controls in Quick Access Menu and does not show controls in Quick Access Toolbar.

Once the controls are visible in Toolbar , then controls state will be set as ticked in Quick Access Menu and vice versa.

The client side event for Quick Access Toolbar menu click is qatMenuItemClick and it will be triggered with QAT menu item click.

More Commands command provides with Quick Access Menu. This can be customized using qatMenuItemClick event, such as to show popup dialog.

{% highlight html %}

       <div id="Ribbon"></div>    
        <ul id="ribbonmenu">
           <li><a>FILE</a>
            <ul>
              <li><a>New</a></li>
              <li><a>Open</a></li>                
              <li><a>Save As</a></li>                
            </ul>
           </li>
        </ul>  
       <?php
       require_once '../EJ/AutoLoad.php';
       $ribbon = new  \EJ\Ribbon("defaultRibbon");
       $aTab = new \EJ\Ribbon\ApplicationTab();           
       $aTab->type("menu")->menuItemID("ribbonmenu");
       $hometab  = new \EJ\Ribbon\Tab();
       $clipboard  = new \EJ\Ribbon\Group();
       $grpcontent1 = new \EJ\Ribbon\Content();
       $grpcontentpaste = new \EJ\Ribbon\Content();
       $contentgroup1=new \EJ\Ribbon\ContentGroup();
       $btnsettings1=array('contentType'=>'imageonly','imagePosition'=>'imagetop','prefixIcon'=>'e-icon e-ribbon e-ribbonpaste');
       $contentgroup1->id("paste")->text("Paste")->toolTip("Paste")->quickAccessMode("toolbar")->buttonSettings($btnsettings1);    
       $default2= new \EJ\Ribbon\Defaults();
       $default2->width(60)->height(70)->type("button");
       $contentgroup2=new \EJ\Ribbon\ContentGroup();
       $btnsettings2=array('contentType'=>'textandimage','prefixIcon'=>'e-icon e-ribbon e-ribboncut');
       $contentgroup2->id("cut")->text("Cut")->toolTip("Cut")->buttonSettings($btnsettings2); 
       $contentgroup3=new \EJ\Ribbon\ContentGroup();
       $btnsettings3=array('contentType'=>'textandimage','prefixIcon'=>'e-icon e-ribbon e-ribboncopy');
       $contentgroup3->id("copy")->text("Copy")->toolTip("Copy")->buttonSettings($btnsettings3); 
       $contentgroup4=new \EJ\Ribbon\ContentGroup();
       $btnsettings4=array('contentType'=>'textandimage','prefixIcon'=>'e-icon e-ribbon clearAll');
       $contentgroup4->id("clear")->text("Clear")->toolTip("Clear")->buttonSettings($btnsettings4); 
       $default3= new \EJ\Ribbon\Defaults();
       $default3->width(60)->height(25)->type("button");  
       $grpcontentpaste->groups(array($contentgroup1))->defaults($default2);
       $grpcontent1->groups(array($contentgroup2,$contentgroup3,$contentgroup4))->defaults($default3);
       $clipboard->text("Clipboard")->alignType("columns")->content(array($grpcontentpaste,$grpcontent1));
       $clipboard1  = new \EJ\Ribbon\Group();
       $grpcontent = new \EJ\Ribbon\Content();
       $contentgroup=new \EJ\Ribbon\ContentGroup();
       $btnsettings=array('contentType'=>'imageonly','imagePosition'=>'imagetop','prefixIcon'=>'e-icon e-ribbon e-new');
       $contentgroup->id("new")->text("New")->toolTip("New")->buttonSettings($btnsettings);  
       $default1= new \EJ\Ribbon\Defaults();
       $default1->width(60)->height(70)->type("button");
       $grpcontent->groups(array($contentgroup))->defaults($default1);
       $clipboard1->text("New")->alignType("rows")->content(array($grpcontent));
       $align  = new \EJ\Ribbon\Group();
       $grpcontent2 = new \EJ\Ribbon\Content();
       $aligncontentgroup1=new \EJ\Ribbon\ContentGroup();
       $alignbtnsettings1=array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-ribbon e-bullet');
       $aligncontentgroup1->id("bullet")->text("Bullet Format")->toolTip("Bullet Format")->quickAccessMode("toolbar")->buttonSettings($alignbtnsettings1);
       $aligncontentgroup2=new \EJ\Ribbon\ContentGroup();
       $alignbtnsettings2=array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-ribbon e-numbericon');
       $aligncontentgroup2->id("number")->text("Number Format")->toolTip("Number Format")->quickAccessMode("toolbar")->buttonSettings($alignbtnsettings2);
       $aligncontentgroup3=new \EJ\Ribbon\ContentGroup();
       $alignbtnsettings3=array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-ribbon e-indent');
       $aligncontentgroup3->id("textindent")->text("Text Indent")->toolTip("Text Indent")->quickAccessMode("toolbar")->buttonSettings($alignbtnsettings3);
       $aligncontentgroup4=new \EJ\Ribbon\ContentGroup();
       $alignbtnsettings4=array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-ribbon e-outdent');
       $aligncontentgroup4->id("textoudent")->text("Text Oudent")->toolTip("Text Oudent")->quickAccessMode("toolbar")->buttonSettings($alignbtnsettings4);
       $aligncontentgroup5=new \EJ\Ribbon\ContentGroup();
       $alignbtnsettings5=array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-ribbon e-sort');
       $aligncontentgroup5->id("sort")->text("Sort")->toolTip("Sort")->buttonSettings($alignbtnsettings5);
       $aligncontentgroup6=new \EJ\Ribbon\ContentGroup();
       $alignbtnsettings6=array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-ribbon e-border');
       $aligncontentgroup6->id("border")->text("Border")->toolTip("Border")->buttonSettings($alignbtnsettings6);
       $aligndefault= new \EJ\Ribbon\Defaults();
       $aligndefault->type("button");
       $grpcontent2->groups(array($aligncontentgroup1,$aligncontentgroup2,$aligncontentgroup3,$aligncontentgroup4,$aligncontentgroup5,$aligncontentgroup6))->defaults(array($aligndefault));
       $aligngrpcontent = new \EJ\Ribbon\Content();
       $aligndefault1= new \EJ\Ribbon\Defaults();
       $aligndefault1->type("button");
       $alignsubgroup1=new \EJ\Ribbon\ContentGroup();
       $leftbtnsettings=array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-ribbon alignleft');
       $alignsubgroup1->id("alignleft")->text("JustifyLeft")->toolTip("alignleft")->buttonSettings($leftbtnsettings);
       $alignsubgroup2=new \EJ\Ribbon\ContentGroup();
       $centerbtnsettings=array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-ribbon aligncenter');
       $alignsubgroup2->id("aligncenter")->text("JustifyCenter")->toolTip("alignleft")->buttonSettings($centerbtnsettings);
       $alignsubgroup2=new \EJ\Ribbon\ContentGroup();
       $justbtnsettings=array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-ribbon justify');
       $alignsubgroup2->id("aligncenter")->text("JustifyCenter")->toolTip("alignleft")->buttonSettings($justbtnsettings);
       $alignsubgroup3=new \EJ\Ribbon\ContentGroup();
       $rightbtnsettings=array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-ribbon alignright');
       $alignsubgroup3->id("alignright")->text("JustifyRight")->toolTip("alignright")->buttonSettings($rightbtnsettings);
       $alignsubgroup4=new \EJ\Ribbon\ContentGroup();
       $justifybtnsettings=array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-ribbon justify');
       $alignsubgroup4->id("justify")->text("justifyFull")->toolTip("justify")->buttonSettings($justifybtnsettings);
       $alignsubgroup5=new \EJ\Ribbon\ContentGroup();
       $upperbtnsettings=array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-ribbon e-uppercase');
       $alignsubgroup5->id("uppercase")->text("Uppercase")->toolTip("uppercase")->buttonSettings($upperbtnsettings);
       $alignsubgroup6=new \EJ\Ribbon\ContentGroup();
       $lowerbtnsettings=array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-ribbon e-lowercase');
       $alignsubgroup6->id("lowercase")->text("Lowercase")->toolTip("lowercase")->buttonSettings($lowerbtnsettings);
       $alignsubgroup6->id("lowercase")->text("Lowercase")->toolTip("lowercase")->buttonSettings($lowerbtnsettings);
       $aligngrpcontent->groups(array($alignsubgroup1,$alignsubgroup2,$alignsubgroup3,$alignsubgroup4,$alignsubgroup5,$alignsubgroup6))->defaults($aligndefault1);
       $align->text("Alignment")->alignType("rows")->content(array($grpcontent2,$aligngrpcontent));
       $action  = new \EJ\Ribbon\Group();
       $actioncontent = new \EJ\Ribbon\Content();
       $actcontentgroup=new \EJ\Ribbon\ContentGroup();
       $actcontentgroup1=new \EJ\Ribbon\ContentGroup();
       $actbtnsettings=array('contentType'=>'textandimage','imagePosition'=>'imagetop','prefixIcon'=>'e-icon e-ribbon e-undo');
       $actcontentgroup->id("undo")->text("Undo")->toolTip("Undo")->buttonSettings($actbtnsettings); 
       $actbtnsettings1=array('contentType'=>'textandimage','imagePosition'=>'imagetop','prefixIcon'=>'e-icon e-ribbon e-redo');
       $actcontentgroup1->id("redo")->text("Redo")->toolTip("Redo")->buttonSettings($actbtnsettings1); 
       $actdefault1= new \EJ\Ribbon\Defaults();
       $actdefault1->width(40)->height(70)->type("button");
       $actioncontent->groups(array($actcontentgroup,$actcontentgroup1))->defaults($actdefault1);
       $action->text("Actions")->alignType("rows")->content(array($actioncontent));
       $hometab->id("home")->text("HOME")->groups(array($clipboard1,$clipboard,$align,$action));
       echo $ribbon ->width("600px")->applicationTab($aTab)->tabs(array($hometab,$inserttab))->showQAT("true")->render();
       ?> 
       <style class="cssStyles">
          .e-ribbon .e-rbnquickaccessbar .e-ribbonpaste:before {
            font-size: 27px;
            left: -5px;
            top: -6px;
          }
          .cols-sample-area {
			height: 300px !important;
          } 
       </style>
 
{% endhighlight %}

![](Toolbar/toolbar_img1.png)