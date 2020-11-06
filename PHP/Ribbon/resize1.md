---
title: Resize
description: Overview of Resize ribbon control.
platform: php
control: ribbon
documentation: ug
keywords: ribbon features, key features, ribbon overview 
---

# Resize

Ribbon control dynamically resizes to display possible number of controls in the optimal layout as the application window size changes.

As the window is narrowed, controls in the Ribbon will be combined as group button with dropdown arrow, in which controls can be expanded with dropdown arrow.

## Tablet Layout

Set isResponsive as true to enable responsive layout in Ribbon.If client width is above 420px or control content exceeds the page then, the ribbon will render in Tablet mode.

{% highlight html %}

         <?php
         require_once 'EJ/AutoLoad.php';
         ?>
         <div id="Ribbon"></div>
	      <ul id="ribbonmenu">
		      <li><a>FILE</a>    
	            <ul>
				    <li><a>New</a></li>
                    <li><a>Open</a></li>
			    </ul>
		      </li>
	      </ul>
         </div>
         <?php
         $ribbon = new  \EJ\Ribbon('defaultRibbon');
         $aTab = new \EJ\Ribbon\ApplicationTab();           
         $aTab->type('menu')->menuItemID('ribbonmenu');  
         $hometab  = new \EJ\Ribbon\Tab();
         $clipboard  = new \EJ\Ribbon\Group();
         $clipboard1  = new \EJ\Ribbon\Group();
         $clipboard2  = new \EJ\Ribbon\Group();
         $grpcontent = new \EJ\Ribbon\Content();
         $grpcontent1 = new \EJ\Ribbon\Content();
         $grpcontent2 = new \EJ\Ribbon\Content();
         $contentgroup = new \EJ\Ribbon\ContentGroup();
         $contentgroup1 = new \EJ\Ribbon\ContentGroup();
         $contentgroup2 = new \EJ\Ribbon\ContentGroup();
         $contentgroup3 = new \EJ\Ribbon\ContentGroup();
         $contentgroup4 = new \EJ\Ribbon\ContentGroup();
         $contentgroup5 = new \EJ\Ribbon\ContentGroup();
         $default= new \EJ\Ribbon\Defaults();
         $default->width(40)->height(70)->type('button'); 
         $contentgroup->id('cut')->text('Cut');
         $contentgroup1->id('copy')->text('Copy');                 
         $grpcontent->groups(array($contentgroup,$contentgroup1))->defaults($default);
         $clipboard->text('Clipboard')->content(array($grpcontent));
         $contentgroup2->id('bold')->text('Bold');
         $contentgroup3->id('italic')->text('Italic');                 
         $grpcontent1->groups(array($contentgroup2,$contentgroup3))->defaults($default);
         $clipboard1->text('Font')->content(array($grpcontent1));
         $contentgroup4->id('left')->text('Left');
         $contentgroup5->id('right')->text('Right');                 
         $grpcontent2->groups(array($contentgroup4,$contentgroup5))->defaults($default);
         $clipboard2->text('Align')->content(array($grpcontent2));
         $hometab->id('home')->text('HOME')->groups(array($clipboard,$clipboard1,$clipboard2));
         echo $ribbon ->isResponsive('true')->width('20%')->applicationTab($aTab)->tabs(array($hometab))->render();
         ?>             

{% endhighlight %}

![](Resize/resize_img1.png)

# Mobile Layout

If client width is less than 420px, the ribbon will render in mobile mode. In which, you can see that ribbon user interface is customized and redesigned for best view in small screens.
The customized features includes responsive tab & group rendering, backstage, gallery and button controls.

## Responsive Tab and group

Set isResponsive as true to enable responsive mode in Ribbon.

{% highlight html %}

         <?php
         require_once 'EJ/AutoLoad.php';
         ?>
         <div id="Ribbon"></div>
         <?php
         $ribbon = new  \EJ\Ribbon('defaultRibbon');
         $aTab = new \EJ\Ribbon\ApplicationTab();             
         $hometab  = new \EJ\Ribbon\Tab();
         $clipboard  = new \EJ\Ribbon\Group();
         $grpcontent = new \EJ\Ribbon\Content();
         $contentgroup = new \EJ\Ribbon\ContentGroup();
         $contentgroup1 = new \EJ\Ribbon\ContentGroup();
         $contentgroup2 = new \EJ\Ribbon\ContentGroup();
         $contentgroup3 = new \EJ\Ribbon\ContentGroup();
         $contentgroup4 = new \EJ\Ribbon\ContentGroup();
         $default= new \EJ\Ribbon\Defaults();
         $default->isBig('false'); 
         $togglebtn = array('contentType'=>'imageonly','defaultText'=>'Bold','activeText'=>'Bold','defaultPrefixIcon'=>'e-icon e-ribbon e-resbold','activePrefixIcon'=>'e-icon e-ribbon e-resbold');
         $contentgroup->id('bold')->isMobileOnly('true')->type('togglebutton')->toggleButtonSettings($togglebtn);
		 $togglebtn1 = array('contentType'=>'imageonly','defaultText'=>'Italic','activeText'=>'Italic','defaultPrefixIcon'=>'e-icon e-ribbon e-resitalic','activePrefixIcon'=>'e-icon e-ribbon e-resitalic');
         $contentgroup1->id('italic')->isMobileOnly('true')->type('togglebutton')->toggleButtonSettings($togglebtn1);         
         $togglebtn2 = array('contentType'=>'imageonly','defaultText'=>'Underline','activeText'=>'Underline','defaultPrefixIcon'=>'e-icon e-ribbon e-resunderline','activePrefixIcon'=>'e-icon e-ribbon e-resunderline');
         $contentgroup2->id('underline')->text('Underline')->isMobileOnly('true')->type('togglebutton')->toggleButtonSettings($togglebtn2);
         $togglebtn3 = array('contentType'=>'imageonly','defaultText'=>'Strikethrough','activeText'=>'Strikethrough','defaultPrefixIcon'=>'e-icon e-ribbon e-strikethrough','activePrefixIcon'=>'e-icon e-ribbon e-strikethrough');
         $contentgroup3->id('strikethrough')->text('Strikethrough')->isMobileOnly('true')->type('togglebutton')->toggleButtonSettings($togglebtn3);
         $btn = array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-ribbon e-superscription');
         $contentgroup4->id('superscript')->text('Superscript')->isMobileOnly('true')->type('button')->buttonSettings($btn);
         $grpcontent->groups(array($contentgroup,$contentgroup1,$contentgroup2,$contentgroup3,$contentgroup4))->defaults($default);
         $clipboard->text('Font')->alignType('rows')->content(array($grpcontent));
         $hometab->id('home')->text('HOME')->groups(array($clipboard));
         echo $ribbon ->isResponsive('true')->width('20%')->applicationTab($aTab)->tabs(array($hometab))->render();
         ?>             

{% endhighlight %}

![](Resize/resize_img2.png)

Ribbon Responsive with tab content

N> To make the Ribbon control to react as responsive in mobile devices, it is necessary to refer the additional ej.responsive.css file in the application.

## Mobile Toolbar Customization

Set isMobileOnly as true to group control to show the controls 
in the Mobile Toolbar of the ribbon. For each tab , first row of mobile ribbon will pick and display the controls which is set as isMobileOnly with look adapt to mobile mode.If isMobileOnly property is not defined to any of the control within tab, then by default first group content will be displayed in first row toolbar.

To adapt to proper display of controls , following layout will be customized with constants display.

* First ribbon toolbar and Button controls with min-height.
* Drop down control will adapt to full screen width.
* All button controls icon will be displayed commonly as Top position.
 
 {% highlight html %}

         <?php
         require_once 'EJ/AutoLoad.php';
         ?>
         <div id="Ribbon"></div>
         <?php
         $ribbon = new  \EJ\Ribbon('defaultRibbon');
         $aTab = new \EJ\Ribbon\ApplicationTab();             
         $hometab  = new \EJ\Ribbon\Tab();
         $clipboard  = new \EJ\Ribbon\Group();
         $grpcontent = new \EJ\Ribbon\Content();
         $contentgroup = new \EJ\Ribbon\ContentGroup();
         $contentgroup1 = new \EJ\Ribbon\ContentGroup();
         $contentgroup2 = new \EJ\Ribbon\ContentGroup();
         $contentgroup3 = new \EJ\Ribbon\ContentGroup();
         $contentgroup4 = new \EJ\Ribbon\ContentGroup();
         $default= new \EJ\Ribbon\Defaults();
         $default->isBig('false'); 
         $togglebtn = array('contentType'=>'imageonly','defaultText'=>'Bold','activeText'=>'Bold','defaultPrefixIcon'=>'e-icon e-ribbon e-resbold','activePrefixIcon'=>'e-icon e-ribbon e-resbold');
         $contentgroup->id('bold')->isMobileOnly('true')->type('togglebutton')->toggleButtonSettings($togglebtn);
		 $togglebtn1 = array('contentType'=>'imageonly','defaultText'=>'Italic','activeText'=>'Italic','defaultPrefixIcon'=>'e-icon e-ribbon e-resitalic','activePrefixIcon'=>'e-icon e-ribbon e-resitalic');
         $contentgroup1->id('italic')->isMobileOnly('true')->type('togglebutton')->toggleButtonSettings($togglebtn1);              
         $togglebtn2 = array('contentType'=>'imageonly','defaultText'=>'Underline','activeText'=>'Underline','defaultPrefixIcon'=>'e-icon e-ribbon e-resunderline','activePrefixIcon'=>'e-icon e-ribbon e-resunderline');
         $contentgroup2->id('underline')->text('Underline')->isMobileOnly('true')->type('togglebutton')->toggleButtonSettings($togglebtn2);
         $togglebtn3 = array('contentType'=>'imageonly','defaultText'=>'Strikethrough','activeText'=>'Strikethrough','defaultPrefixIcon'=>'e-icon e-ribbon e-strikethrough','activePrefixIcon'=>'e-icon e-ribbon e-strikethrough');
         $contentgroup3->id('strikethrough')->text('Strikethrough')->isMobileOnly('true')->type('togglebutton')->toggleButtonSettings($togglebtn3);
         $btn = array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-ribbon e-superscription');
         $contentgroup4->id('superscript')->text('Superscript')->isMobileOnly('true')->type('button')->buttonSettings($btn);
         $grpcontent->groups(array($contentgroup,$contentgroup1,$contentgroup2,$contentgroup3,$contentgroup4))->defaults($default);
         $clipboard->text('Font')->alignType('rows')->content(array($grpcontent));
         $hometab->id('home')->text('HOME')->groups(array($clipboard));
         echo $ribbon ->isResponsive('true')->width('20%')->applicationTab($aTab)->tabs(array($hometab))->render();
         ?>             

{% endhighlight %}

![](Resize/resize_img3.png)

Ribbon Responsive with MobileToolbar

## Customized Features

The customized layout for Quick Access Toolbar, backstage, gallery can be seen following screen shots.

![](Resize/resize_img4.png)

Ribbon Responsive with Quick Access Toolbar

![](Resize/resize_img5.png)

![](Resize/resize_img6.png)

Ribbon Responsive with backstage

![](Resize/resize_img7.png)

Ribbon Responsive with gallery

## Group Button Customization

Based on window size, detailed group is shrined into single button and you can expand group items with group button click.

For each group shirked for resizing, Custom Class will be added based on group text.For example, e-action whereas action is group text. Using this custom class, group button can be customized such as to set icons etc.

{% highlight html %}

         <?php
         require_once 'EJ/AutoLoad.php';
         ?>
         <div id="Ribbon"></div>
	       <ul id="ribbonmenu">
		       <li><a>FILE</a>    
			    <ul>
				    <li><a>New</a></li>
                    <li><a>Open</a></li>
			    </ul>
		       </li>
	       </ul>
         <?php
         $fontfamily = ["Segoe UI", "Arial", "Times New Roman", "Tahoma", "Helvetica"];
         $fontsize = ["1pt", "2pt", "3pt", "4pt", "5pt"];
         $ribbon = new  \EJ\Ribbon('defaultRibbon');
         $aTab = new \EJ\Ribbon\ApplicationTab();             
         $aTab->type('menu')->menuItemID('ribbonmenu');  
         $hometab  = new \EJ\Ribbon\Tab();
         $layoutab  = new \EJ\Ribbon\Tab();
         $clipboard  = new \EJ\Ribbon\Group();
         $clipboard1  = new \EJ\Ribbon\Group();
         $clipboard2  = new \EJ\Ribbon\Group();
         $clipboard3  = new \EJ\Ribbon\Group();
         $clipboard4  = new \EJ\Ribbon\Group();
         $grpcontent = new \EJ\Ribbon\Content();
         $grpcontent1 = new \EJ\Ribbon\Content();
         $grpcontent2 = new \EJ\Ribbon\Content();
         $grpcontent3 = new \EJ\Ribbon\Content();
         $grpcontent4 = new \EJ\Ribbon\Content();
         $grpcontent5 = new \EJ\Ribbon\Content();
         $contentgroup = new \EJ\Ribbon\ContentGroup();
         $contentgroup1 = new \EJ\Ribbon\ContentGroup();
         $contentgroup2 = new \EJ\Ribbon\ContentGroup();
         $contentgroup3 = new \EJ\Ribbon\ContentGroup();
         $contentgroup4 = new \EJ\Ribbon\ContentGroup();
         $contentgroup5 = new \EJ\Ribbon\ContentGroup();
         $contentgroup6 = new \EJ\Ribbon\ContentGroup();
         $contentgroup7 = new \EJ\Ribbon\ContentGroup();
         $contentgroup8 = new \EJ\Ribbon\ContentGroup();
         $default= new \EJ\Ribbon\Defaults();
         $default->width(50)->height(70)->isBig('true'); 
         $btn = array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-ribbon e-ribbonpaste');
         $contentgroup->id('paste')->text('Paste')->toolTip('Paste')->type('button')->buttonSettings($btn);
         $grpcontent->groups(array($contentgroup))->defaults($default);
         $default1= new \EJ\Ribbon\Defaults();
         $default1->width(60)->height(40)->isBig('false');
         $btn1 = array('contentType'=>'textandimage','prefixIcon'=>'e-icon e-ribbon e-ribboncut');
         $contentgroup1->id('cut')->text('Cut')->toolTip('Cut')->type('button')->buttonSettings($btn1);
         $btn2 = array('contentType'=>'textandimage','prefixIcon'=>'e-icon e-ribbon e-ribboncopy');
         $contentgroup2->id('copy')->text('Copy')->toolTip('Copy')->type('button')->buttonSettings($btn2);
         $grpcontent1->groups(array($contentgroup1,$contentgroup2))->defaults($default1);
         $clipboard->text('Clipboard')->alignType('columns')->enableGroupExpander('true')->content(array($grpcontent,$grpcontent1));
         $default2= new \EJ\Ribbon\Defaults();
         $default2->type('dropdownlist')->height(28)->isBig('false');
         $dropdown=array('dataSource'=>$fontfamily,'text'=>'Segeo UI','width'=>150);
         $contentgroup3->id('fontfamily')->toolTip('Font')->dropdownSettings($dropdown);
         $dropdown1=array('dataSource'=>$fontsize,'text'=>'1pt','width'=>65);
         $contentgroup4->id('fontsize')->toolTip('FontSize')->dropdownSettings($dropdown1); 
         $grpcontent2->groups(array($contentgroup3,$contentgroup4))->defaults($default2);
         $clipboard1->text('Font')->alignType('rows')->content(array($grpcontent2));
         $default3= new \EJ\Ribbon\Defaults();
         $default3->width(60)->height(40); 
         $btn3 = array('contentType'=>'imageonly','imagePosition'=>'imagetop','prefixIcon'=>'e-icon e-ribbon e-new');
         $contentgroup5->id('new')->text('New')->toolTip('New')->type('button')->buttonSettings($btn3);
         $grpcontent3->groups(array($contentgroup5))->defaults($default3);
         $clipboard2->text('New')->alignType('rows')->content(array($grpcontent3));
         $default4= new \EJ\Ribbon\Defaults();
         $default4->width(40)->height(70); 
         $btn4 = array('contentType'=>'textandimage','imagePosition'=>'imagetop','prefixIcon'=>'e-icon e-ribbon e-undo');
         $contentgroup6->id('undo')->text('Undo')->toolTip('Undo')->type('button')->buttonSettings($btn4);
         $btn5 = array('contentType'=>'textandimage','imagePosition'=>'imagetop','prefixIcon'=>'e-icon e-ribbon e-redo');
         $contentgroup7->id('redo')->text('Redo')->toolTip('Redo')->type('button')->buttonSettings($btn5);
         $grpcontent4->groups(array($contentgroup6,$contentgroup7))->defaults($default4);
         $clipboard3->text('Actions')->alignType('rows')->content(array($grpcontent4));
         $default5= new \EJ\Ribbon\Defaults();
         $default5->width(80)->height(70);
         $btn6 = array('contentType'=>'textandimage','imagePosition'=>'imagetop','prefixIcon'=>'e-icon e-ribbon e-printlayout');
         $contentgroup8->id('printlayout')->text('Print Layout')->toolTip('Print Layout')->type('button')->buttonSettings($btn6);
         $grpcontent5->groups(array($contentgroup8))->defaults($default5);
         $clipboard4->text('Print Layout')->alignType('rows')->content(array($grpcontent5));
         $hometab->id('home')->text('HOME')->groups(array($clipboard,$clipboard1,$clipboard2,$clipboard3));
         $layoutab->id('layout')->text('Layout')->groups(array($clipboard4));
         echo $ribbon ->allowResizing('true')->width('36%')->applicationTab($aTab)->tabs(array($hometab,$layoutab))->render();
         ?>
         <style type="text/css">
                .e-ribbon .e-New:before, .e-ribbon .e-Actions:before {
                       font-family: "ej-ribbonfont";
                       font-size: 28px;
                       line-height: 35px;
                }
                .e-ribbon .e-New:before {
                       content: "\e167";            
                       text-indent: -1.5px;
                }
                .e-ribbon .e-Actions:before {
                       content: "\e184;
                       text-indent: 7px;
                }
         </style>

{% endhighlight %}

![](Resize/resize_img8.png)