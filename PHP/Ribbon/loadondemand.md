---
title: Load on Demand
description: Overview of Load on Demand ribbon control.
platform: php
control: ribbon
documentation: ug
keywords: ribbon features, key features, ribbon overview 
---

# Load on Demand

Set enableOnDemand as true to enable load tab and backstage contents dynamically. Loading content on demand improves the initial rendering time of the ribbon by rendering tab and backstage content when tabs and backstage items are clicked.

{% highlight html %}

       <?php
       require_once 'EJ/AutoLoad.php';
       ?>
       <div id="defaultRibbon"></div>
        <div id="newCon" style='display:none'>
          <table>
            <tr>
              <td>
                <button id="btn1" class="e-bsnewbtnstyle">Blank WorkBook</button>
              </td>
            </tr>
          </table>
        </div>
       <div id="accountCon" style='display:none'>
        <div class="e-userDiv">
           <span>User Information</span>
           <div>
             <div class="e-accuser e-newpageicon"></div>
             <div class="e-userCon">
                  <div>user</div>
                  <div>xyz@syncfusion.com</div>
               </div>
             </div>
           </div>
           <a href="#">Sign out</a>
       </div>
       <?php
       $ribbon = new  \EJ\Ribbon('defaultRibbon');
       $aTab = new \EJ\Ribbon\ApplicationTab();      
       $backstage = new \EJ\Ribbon\BackstageSetting();
       $backstagepages1=new EJ\Ribbon\Page();
       $backstagepages1->id("new")->text("New")->contentID("newCon");
       $backstagepages2=new EJ\Ribbon\Page();
       $backstagepages2->id("close")->text("Close")->enableSeparator("true")->itemType("button");
       $backstagepages3=new EJ\Ribbon\Page();
       $backstagepages3->id("account")->text("Office Account")->contentID("accountCon");
       $backstage->text("FILE")->height("360")->width("600")->headerWidth("125")->pages(array($backstagepages1,$backstagepages2,$backstagepages3));
       $aTab->type("backstage")->backstageSettings($backstage);
       $hometab = new \EJ\Ribbon\Tab();
       $clipboard = new \EJ\Ribbon\Group();
       $grpcontent = new \EJ\Ribbon\Content();
       $contentgroup=new \EJ\Ribbon\ContentGroup();
       $btnsettings=array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-ribbon e-ribbonpaste');
       $contentgroup->id('paste')->text('paste')->toolTip('Paste')->buttonSettings($btnsettings);
       $default= new \EJ\Ribbon\Defaults();
       $default->width(50)->height(70)->type("button")->isBig('true'); 
       $grpcontent->groups(array($contentgroup))->defaults($default);     
       $group = array('toolTip'=>'Clipboard');
       $clipboard->text('Clipboard')->alignType('columns')->groupExpanderSettings($group)->content(array($grpcontent));
       $clipboard1 = new \EJ\Ribbon\Group();
       $grpcontent1 = new \EJ\Ribbon\Content();
       $contentgroup1=new \EJ\Ribbon\ContentGroup();
       $btnsettings1=array('contentType'=>'imageonly','imagePosition'=>'imagetop','prefixIcon'=>'e-icon e-ribbon e-new');
       $contentgroup1->id('new')->text('New')->toolTip('New')->buttonSettings($btnsettings1);
       $default1= new \EJ\Ribbon\Defaults();
       $default1->width(60)->height(70)->type("button"); 
       $grpcontent1->groups(array($contentgroup1))->defaults($default1);
       $clipboard1->text('New')->alignType('rows')->content(array($grpcontent1));
       $layoutab  = new \EJ\Ribbon\Tab();
       $clipboard2  = new \EJ\Ribbon\Group();
       $grpcontent2 = new \EJ\Ribbon\Content();
       $contentgroup2 = new \EJ\Ribbon\ContentGroup();
       $btnsettings2=array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-ribbon e-bullet');
       $contentgroup2->id('bullet')->text('Bullet Format')->toolTip('Bullets')->buttonSettings($btnsettings2);
       $default2= new \EJ\Ribbon\Defaults();
       $default2->type("button")->isBig('false'); 
       $grpcontent2->groups(array($contentgroup2))->defaults($default2);     
       $clipboard2->text('Alignment')->alignType('rows')->content(array($grpcontent2));
       $clipboard3  = new \EJ\Ribbon\Group();
	   $contentgroup3 = new \EJ\Ribbon\ContentGroup();
       $grpcontent3 = new \EJ\Ribbon\Content();
       $btnsettings3=array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-ribbon e-numbericon');
       $contentgroup3->id('number')->text('Number Format')->toolTip('Numbering')->buttonSettings($btnsettings3);
       $grpcontent3->groups(array($contentgroup3))->defaults($default2); 
       $clipboard3->content(array($grpcontent3));
	   $hometab->id('home')->text('HOME')->groups(array($clipboard,$clipboard1));
       $layoutab->id('layout')->text('LAYOUT')->groups(array($clipboard2,$clipboard3));
       echo $ribbon ->enableOnDemand('true')->width('50%')->applicationTab($aTab)->tabs(array($hometab,$layoutab))->render();
       ?>
       <script>
          $(function () {
	            $('#btn1').ejButton({
                size: 'large',
                height: 200,
                width: 225,
                contentType: 'textandimage',
                imagePosition: 'imagetop',
                prefixIcon: 'e-icon e-blank e-infopageicon'
                });
          });
       </script>
       <link href='Content/ejthemes/ribbon-css/ej.icons.css' rel='stylesheet' />
       <style class="cssStyles">
                .e-accuser {
                        background-image: url("../content/ejthemes/common-images/ribbon/User.jpg"),url("content/ejthemes/common-images/ribbon/User.jpg");
                }
                .e-blank {
                        background-image: url("../content/ejthemes/common-images/ribbon/blank.png"),url("content/ejthemes/common-images/ribbon/blank.png");
                }
                .e-infopageicon {
                        background-repeat: no-repeat;
                        height: 150px;
                        width: 198px;
                }
                .e-newpageicon {
                        background-repeat: no-repeat;
                        height: 42px;
                        width: 42px;
                }
                .e-bspagestyle {
                        line-height: 0;
                        font-size: 30px;
                }
                .e-ribbon .e-ribbonbackstagepage .e-bsnewbtnstyle {
                        color: #212121;
                        background: #fdfdfd;
                        margin: 20px;
                }
       </style>

{% endhighlight %}

![](Ondemand/ondemand_img1.png)

## Initially Collapsible

Set collapsible'](https://help.syncfusion.com/api/js/ejribbon#members:collapsible) as true to render ribbon control in collapsed state, which results ribbon tabs to render without any content initially. While using initially collapsible ribbon with [enableOnDemand` feature improves the performance by reducing initial loading time of ribbon.

{% highlight html %}

        <?php
        require_once 'EJ/AutoLoad.php';
        ?>
        <div id="defaultRibbon"></div>
          <div id="newCon" style='display:none'>
             <table>
                 <tr>
                    <td>
                       <button id="btn1" class="e-bsnewbtnstyle">Blank WorkBook</button>
                    </td>
                  </tr>
             </table>
           </div>
        <div id="accountCon" style='display:none'>
           <div class="e-userDiv">
               <span>User Information</span>
               <div>
                   <div class="e-accuser e-newpageicon"></div>
                   <div class="e-userCon">
                        <div>user</div>
                        <div>xyz@syncfusion.com</div>
                   </div>
               </div>
            </div>
            <a href="#">Sign out</a>
        </div>
        <?php
        $ribbon = new  \EJ\Ribbon('defaultRibbon');
        $aTab = new \EJ\Ribbon\ApplicationTab();      
        $backstage = new \EJ\Ribbon\BackstageSetting();
        $backstagepages1=new EJ\Ribbon\Page();
        $backstagepages1->id("new")->text("New")->contentID("newCon");
        $backstagepages2=new EJ\Ribbon\Page();
        $backstagepages2->id("close")->text("Close")->enableSeparator("true")->itemType("button");
        $backstagepages3=new EJ\Ribbon\Page();
        $backstagepages3->id("account")->text("Office Account")->contentID("accountCon");
        $backstage->text("FILE")->height("360")->width("600")->headerWidth("125")->pages(array($backstagepages1,$backstagepages2,$backstagepages3));
        $aTab->type("backstage")->backstageSettings($backstage);
        $hometab = new \EJ\Ribbon\Tab();
        $clipboard = new \EJ\Ribbon\Group();
        $grpcontent = new \EJ\Ribbon\Content();
        $contentgroup=new \EJ\Ribbon\ContentGroup();
        $btnsettings=array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-ribbon e-ribbonpaste');
        $contentgroup->id('paste')->text('paste')->toolTip('Paste')->buttonSettings($btnsettings);
        $default= new \EJ\Ribbon\Defaults();
        $default->width(50)->height(70)->type("button")->isBig('true'); 
        $grpcontent->groups(array($contentgroup))->defaults($default);     
        $group = array('toolTip'=>'Clipboard');
        $clipboard->text('Clipboard')->alignType('columns')->groupExpanderSettings($group)->content(array($grpcontent));
        $clipboard1 = new \EJ\Ribbon\Group();
        $grpcontent1 = new \EJ\Ribbon\Content();
        $contentgroup1=new \EJ\Ribbon\ContentGroup();
        $btnsettings1=array('contentType'=>'imageonly','imagePosition'=>'imagetop','prefixIcon'=>'e-icon e-ribbon e-new');
        $contentgroup1->id('new')->text('New')->toolTip('New')->buttonSettings($btnsettings1);
        $default1= new \EJ\Ribbon\Defaults();
        $default1->width(60)->height(70)->type("button"); 
        $grpcontent1->groups(array($contentgroup1))->defaults($default1);
        $clipboard1->text('New')->alignType('rows')->content(array($grpcontent1));
        $layoutab = new \EJ\Ribbon\Tab();
        $clipboard2 = new \EJ\Ribbon\Group();
        $grpcontent2 = new \EJ\Ribbon\Content();
        $contentgroup2 = new \EJ\Ribbon\ContentGroup();
        $btnsettings2=array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-ribbon e-bullet');
        $contentgroup2->id('bullet')->text('Bullet Format')->toolTip('Bullets')->buttonSettings($btnsettings2);
        $default2= new \EJ\Ribbon\Defaults();
        $default2->type("button")->isBig('false'); 
        $grpcontent2->groups(array($contentgroup2))->defaults($default2);     
        $clipboard2->text('Alignment')->alignType('rows')->content(array($grpcontent2));
        $clipboard3 = new \EJ\Ribbon\Group();
		$contentgroup3 = new \EJ\Ribbon\ContentGroup();
        $grpcontent3 = new \EJ\Ribbon\Content();
        $btnsettings3=array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-ribbon e-numbericon');
        $contentgroup3->id('number')->text('Number Format')->toolTip('Numbering')->buttonSettings($btnsettings3);
        $grpcontent3->groups(array($contentgroup3))->defaults($default2); 
        $clipboard3->content(array($grpcontent3));
		$hometab->id('home')->text('HOME')->groups(array($clipboard,$clipboard1));
        $layoutab->id('layout')->text('LAYOUT')->groups(array($clipboard2,$clipboard3));
        echo $ribbon ->collapsible('true')->width('50%')->applicationTab($aTab)->tabs(array($hometab,$layoutab))->render();
        ?>
        <script>
           $(function () {
	            $('#btn1').ejButton({
                size: 'large',
                height: 200,
                width: 225,
                contentType: 'textandimage',
                imagePosition: 'imagetop',
                prefixIcon: 'e-icon e-blank e-infopageicon'
                });
           });
        </script>
        <link href='Content/ejthemes/ribbon-css/ej.icons.css' rel='stylesheet' />
        <style class="cssStyles">
             .e-accuser {
                     background-image: url("../content/ejthemes/common-images/ribbon/User.jpg"),url("content/ejthemes/common-images/ribbon/User.jpg");
             }
             .e-blank {
                     background-image: url("../content/ejthemes/common-images/ribbon/blank.png"),url("content/ejthemes/common-images/ribbon/blank.png");
             }
             .e-infopageicon {
                     background-repeat: no-repeat;
                     height: 150px;
                     width: 198px;
             }
             .e-newpageicon {
                     background-repeat: no-repeat;
                     height: 42px;
                     width: 42px;
             }
             .e-bspagestyle {
                     line-height: 0;
                     font-size: 30px;
             }
             .e-ribbon .e-ribbonbackstagepage .e-bsnewbtnstyle {
                     color: #212121;
                     background: #fdfdfd;
                     margin: 20px;
             }
        </style>

{% endhighlight %}

![](Ondemand/ondemand_img2.png)