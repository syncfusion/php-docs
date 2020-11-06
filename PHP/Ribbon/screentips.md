---
title: Screen Tips
description: Overview of Screen Tips ribbon control.
platform: php
control: ribbon
documentation: ug
keywords: ribbon features, key features, ribbon overview 
---

# Screen Tips

ScreenTip/Tooltip is used to reduce the controls related Help that are needed to the end user to do control related actions.

## HTML Tooltip

Standard html tooltip can be set using tooltip property of each group item.

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
         $ribbon = new  \EJ\Ribbon('defaultRibbon');
         $aTab = new \EJ\Ribbon\ApplicationTab();           
         $aTab->type('menu')->menuItemID('ribbonmenu');  
         $hometab  = new \EJ\Ribbon\Tab();
         $clipboard  = new \EJ\Ribbon\Group();
         $grpcontent = new \EJ\Ribbon\Content();
         $contentgroup = new \EJ\Ribbon\ContentGroup();
         $contentgroup1 = new \EJ\Ribbon\ContentGroup();
         $default= new \EJ\Ribbon\Defaults();
         $default->width(60)->height(70)->type('button'); 
         $btnsettings=array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-ribbon e-ribboncut');
         $contentgroup->id('cut')->text('Cut')->toolTip('Remove the selection and put it on clipboard')->buttonSettings($btnsettings);
		 $btnsettings1=array('contentType'=>'textandimage','prefixIcon'=>' e-icon e-ribbon  e-ribboncopy');
         $contentgroup1->id('copy')->text('Copy')->toolTip('Put a copy of selection on clipboard')->buttonSettings($btnsettings1);                 
         $grpcontent->groups(array($contentgroup,$contentgroup1))->defaults($default);
         $clipboard->text('Clipboard')->content(array($grpcontent));
         $hometab->id('home')->text('HOME')->groups(array($clipboard));
         echo $ribbon ->allowResizing('true')->width('20%')->applicationTab($aTab)->tabs(array($hometab))->render();
         ?>

{% endhighlight %}

![](Screen/screen_img1.png)

## Custom Tooltip

Custom Tooltip is used to set detailed help to the user about the controls. You can set title, content and prefixIcon class to customize the tooltip with icons.

## For Groups

Custom tooltip for each group controls can be specified. Such as to the controls button, split button, dropdown list etc.

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
         $ribbon = new  \EJ\Ribbon('defaultRibbon');
         $aTab = new \EJ\Ribbon\ApplicationTab();           
         $aTab->type('menu')->menuItemID('ribbonmenu');  
         $hometab  = new \EJ\Ribbon\Tab();
         $clipboard  = new \EJ\Ribbon\Group();
         $grpcontent = new \EJ\Ribbon\Content();
         $contentgroup = new \EJ\Ribbon\ContentGroup();
         $contentgroup1 = new \EJ\Ribbon\ContentGroup();
         $default= new \EJ\Ribbon\Defaults();
         $default->width(60)->height(70)->type('button'); 
         $btnsettings=array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-ribbon e-ribbonpaste');
         $custom = array('title'=>'Paste','content'=>'<h6>Paste the content.<br/><br/>Add content on the Clipboard to your document.</h6>','prefixIcon'=>'e-pastetip');
         $contentgroup->id('paste')->text('Paste')->customToolTip($custom)->buttonSettings($btnsettings);
         $btnsettings1=array('contentType'=>'textandimage','prefixIcon'=>' e-icon e-ribbon  e-ribboncopy');
         $custom1 = array('title'=>'Copy','content'=>'<h6>Copy the content');
         $contentgroup1->id('copy')->text('Copy')->customToolTip($custom1)->buttonSettings($btnsettings1);                 
         $grpcontent->groups(array($contentgroup,$contentgroup1))->defaults($default);
         $clipboard->text('Clipboard')->content(array($grpcontent));
         $hometab->id('home')->text('HOME')->groups(array($clipboard));
         echo $ribbon ->width('20%')->applicationTab($aTab)->tabs(array($hometab))->render();
         ?>

{% endhighlight %}

![](Screen/screen_img2.png)

## For Gallery

Custom tooltip for each gallery and custom gallery items button control can be specified.

N> Custom gallery item menu is not supported to Custom tooltip.

{% highlight html %}

         <?php
         require_once 'EJ/AutoLoad.php';
         ?>   
         <div id="Ribbon"></div>    
          <ul id="ribbonmenu">
              <li><a>FILE</a> </li>
          </ul>
          <ul id="custommenu">
              <li><a>New Quick Step</a>
               <ul>
                   <li><a>Flag and Move</a></li>
               </ul>
              </li>
          </ul>	
         <?php
         $ribbon = new  \EJ\Ribbon("defaultRibbon");
         $aTab = new \EJ\Ribbon\ApplicationTab();      
         $aTab->type('menu')->menuItemID('ribbonmenu');
         $hometab  = new \EJ\Ribbon\Tab();
         $clipboard  = new \EJ\Ribbon\Group();
         $grpcontent = new \EJ\Ribbon\Content();
         $contentgroup=new \EJ\Ribbon\ContentGroup();
         $btnsettings=array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-gallerycontent1 e-gbtnimg','cssClass'=>'e-gbtnposition');
         $customToolTip=new \EJ\Ribbon\CustomToolTip();
         $customToolTip->title('Style 1')->content("<I>Style 1 to customize the table</I>");
         $gallery=new \EJ\Ribbon\GalleryItem();
         $gallery->text('Style 1')->customToolTip($customToolTip)->buttonSettings($btnsettings);
         $btnsettings1=array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-gallerycontent2 e-gbtnimg','cssClass'=>'e-gbtnposition');
         $customToolTip1=new \EJ\Ribbon\CustomToolTip();
         $customToolTip1->title('Style 2')->content("<I>Style 2 to customize the table</I>");
         $gallery1=new \EJ\Ribbon\GalleryItem();
         $gallery1->text('Style 2')->customToolTip($customToolTip1)->buttonSettings($btnsettings1);
         $btnsettings2=array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-gallerycontent3 e-gbtnimg','cssClass'=>'e-gbtnposition');
         $customToolTip2=new \EJ\Ribbon\CustomToolTip();
         $customToolTip2->title('Style 3')->content("<I>Style 3 to customize the table</I>");
         $gallery2=new \EJ\Ribbon\GalleryItem();
         $gallery2->text('Style 3')->customToolTip($customToolTip2)->buttonSettings($btnsettings2);
         $btnsettings3=array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-gallerycontent4 e-gbtnimg','cssClass'=>'e-gbtnposition');
         $customToolTip3=new \EJ\Ribbon\CustomToolTip();
         $customToolTip3->title('Style 4')->content("<I>Style 4 to customize the table</I>");
         $gallery3=new \EJ\Ribbon\GalleryItem();
         $gallery3->text('Style 4')->customToolTip($customToolTip3)->buttonSettings($btnsettings3);
         $customGallery=new \EJ\Ribbon\CustomGalleryItem();
         $customGallery1=new \EJ\Ribbon\CustomGalleryItem();
         $btnsettings4=array('cssClass'=>'e-extrabtnstyle');
         $customToolTip4=new \EJ\Ribbon\CustomToolTip();
         $customToolTip4->title('Clear Format')->content("<I>Clear Formatting</I>");
         $customGallery->text('Clear Formatting')->toolTip('clear Formatting')->customItemType('button')->customToolTip($customToolTip4)->buttonSettings($btnsettings4);
         $menu=array('openOnClick'=>false);
         $customGallery1->customItemType('menu')->menuId('custommenu')->menuSettings($menu);
         $contentgroup->id('Gallery')->columns(2)->itemHeight(54)->itemWidth(73)->expandedColumns(3)->type('gallery')->galleryItems(array($gallery,$gallery1,$gallery2,$gallery3))->customGalleryItems(array($customGallery,$customGallery1)); 
         $grpcontent->groups(array($contentgroup));     
         $clipboard->text('Gallery')->type('gallery')->content(array($grpcontent));
         $hometab->id('home')->text('HOME')->groups(array($clipboard));
         echo $ribbon ->width("500px")->applicationTab($aTab)->tabs(array($hometab))->render();
         ?>
         <style type="text/css">
               .e-gallerycontent1 {
                      background-position: 0 -105px;
               }
               .e-gallerycontent2 {
                      background-position: -69px -105px;
               }
               .e-gallerycontent3 {
                      background-position: -136px -105px;
               }
               .e-gallerycontent4 {
                      background-position: 0 -53px;
               }
               .e-gbtnposition {
                      margin-top: 5px;
               }
               .e-gbtnimg {
                     background-image: url("../RibbonPHP/Content/ejthemes/common-images/ribbon/homegallery.png");
                     background-repeat: no-repeat;
                     height: 64px;
                     width: 64px;
               }
               .e-extracontent .e-extrabtnstyle {
                     padding-left: 28px;
                     text-align: left;
               }
         </style>

{% endhighlight %}

![](Screen/screen_img3.png)

## For Expand Pin

Specifies the custom tooltip for expand pin in the Ribbon.

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
         $ribbon = new  \EJ\Ribbon("defaultRibbon");
         $aTab = new \EJ\Ribbon\ApplicationTab();      
         $menusettings = array('openOnClick'=>false);
         $aTab->type('menu')->menuItemID('ribbonmenu')->menuSettings($menusettings);
         $hometab  = new \EJ\Ribbon\Tab();
         $clipboard  = new \EJ\Ribbon\Group();
         $grpcontent = new \EJ\Ribbon\Content();
         $contentgroup=new \EJ\Ribbon\ContentGroup();
         $btnsettings=array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-ribbon e-new','click'=>'executeAction');
         $contentgroup->id("new")->text("New")->toolTip("New")->buttonSettings($btnsettings);  
         $default= new \EJ\Ribbon\Defaults();
         $default->width(60)->height(70)->type("button");
         $grpcontent->groups(array($contentgroup))->defaults($default);
         $clipboard->text("New")->alignType("rows")->content(array($grpcontent));
         $hometab->id("home")->text("HOME")->groups(array($clipboard));
         $custom = new \EJ\Ribbon\CustomToolTip();
         $custom->title('Collapse the Ribbon')->content("<h6>Click the icon to collapse the Ribbon.</h6>");
         $expand = new \EJ\Ribbon\ExpandPinSetting();
         $expand->customToolTip($custom);
         echo $ribbon ->expandPinSettings($expand)->width("500px")->applicationTab($aTab)->tabs(array($hometab))->render();
         ?>                 

{% endhighlight %}

![](Screen/screen_img4.png)

## For Collapse Pin

Specifies the custom tooltip for collapse pin in the Ribbon.

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
          $ribbon = new  \EJ\Ribbon("defaultRibbon");
          $aTab = new \EJ\Ribbon\ApplicationTab();      
          $menusettings = array('openOnClick'=>false);
          $aTab->type('menu')->menuItemID('ribbonmenu')->menuSettings($menusettings);
          $hometab  = new \EJ\Ribbon\Tab();
          $clipboard  = new \EJ\Ribbon\Group();
          $grpcontent = new \EJ\Ribbon\Content();
          $contentgroup=new \EJ\Ribbon\ContentGroup();
          $btnsettings=array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-ribbon e-new','click'=>'executeAction');
          $contentgroup->id("new")->text("New")->toolTip("New")->buttonSettings($btnsettings);  
          $default= new \EJ\Ribbon\Defaults();
          $default->width(60)->height(70)->type("button");
          $grpcontent->groups(array($contentgroup))->defaults($default);
          $clipboard->text("New")->alignType("rows")->content(array($grpcontent));
          $hometab->id("home")->text("HOME")->groups(array($clipboard));
          $custom = new \EJ\Ribbon\CustomToolTip();
          $custom->title('Pin the Ribbon')->content("<h6>Keep it open while you work.</h6>");
          $collapse = new \EJ\Ribbon\CollapsePinSetting();
          $collapse->customToolTip($custom);
          echo $ribbon ->collapsePinSettings($collapse)->width("500px")->applicationTab($aTab)->tabs(array($hometab))->render();
          ?>

{% endhighlight %}

![](Screen/screen_img5.png)

## For GroupExpander

Custom tooltip for each group expander can be specified.

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
          $ribbon = new  \EJ\Ribbon("defaultRibbon");
          $aTab = new \EJ\Ribbon\ApplicationTab();      
          $menusettings = array('openOnClick'=>false);
          $aTab->type('menu')->menuItemID('ribbonmenu')->menuSettings($menusettings);
          $hometab  = new \EJ\Ribbon\Tab();
          $clipboard  = new \EJ\Ribbon\Group();
          $grpcontent = new \EJ\Ribbon\Content();
          $contentgroup=new \EJ\Ribbon\ContentGroup();
          $btnsettings=array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-ribbon e-new','click'=>'executeAction');
          $contentgroup->id("new")->text("New")->toolTip("New")->buttonSettings($btnsettings);  
          $default= new \EJ\Ribbon\Defaults();
          $default->width(60)->height(70)->type("button");
          $grpcontent->groups(array($contentgroup))->defaults($default);
          $custom = new \EJ\Ribbon\CustomToolTip();
          $custom->title('Clipboard')->content("<h6>Show a popup for the clipboard group.</h6>");
          $group = new \EJ\Ribbon\GroupExpanderSetting();
          $group->customToolTip($custom);
          $clipboard->text("New")->alignType("rows")->enableGroupExpander('true')->groupExpanderSettings($group)->content(array($grpcontent));
          $hometab->id("home")->text("HOME")->groups(array($clipboard));
          echo $ribbon ->width("500px")->applicationTab($aTab)->tabs(array($hometab))->render();
          ?> 

{% endhighlight %}

![](Screen/screen_img6.png)



