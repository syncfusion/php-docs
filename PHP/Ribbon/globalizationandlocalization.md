---
title: Globalization And Localization
description: Overview of Globalization And Localization ribbon control.
platform: php
control: ribbon
documentation: ug
keywords: ribbon features, key features, ribbon overview 
---

# Localization

The localization support allows to customize the display of text within the Ribbon in a user-specific culture and locale. The Ribbon control can be localized in specific culture using the common API locale along with the collection of localized words defined for that culture using the ej.Ribbon.Locale [culture-code].Please find the table with list of properties and its value in locale object.

<table>
   <tr>
      <th>
         <b>Locale key words </b>
      </th>
      <th>
         <b>Text </b>
      </th>
	</tr>
	<tr>
      <td>
         CustomizeQuickAccess
      </td>
      <td>
         Customize Quick Access Toolbar
      </td>
    </tr>
	<tr>
      <td>
         RemoveFromQuickAccessToolbar
      </td>
      <td>
         Remove from Quick Access Toolbar
      </td>
    </tr>
	<tr>
      <td>
         AddToQuickAccessToolbar
      </td>
      <td>
         Add to Quick Access Toolbar
      </td>
    </tr>
	<tr>
      <td>
         ShowAboveTheRibbon
      </td>
      <td>
         Show Above the Ribbon
      </td>
    </tr>
	<tr>
      <td>
         ShowBelowTheRibbon
      </td>
      <td>
         Show Below the Ribbon
      </td>
    </tr>
	<tr>
      <td>
         MoreCommands
      </td>
      <td>
         More Commands..
      </td>
    </tr>
</table>

N> By default, the Ribbon control is localized in en-US culture.

For further information on � how to refer the required culture scripts into your application, refer here.

{% highlight html %}

          <div id="Ribbon"></div>
	       <ul id="ribbonmenu">
		      <li><a>FILE</a>    
	           <ul>
			      <li><a>New</a></li>
		       </ul>
		      </li>
	      </ul>
         <?php
         require_once 'EJ\AutoLoad.php';
         $rte =new EJ\RTE('texteditor');
         $ribbon = new  \EJ\Ribbon('defaultRibbon');
         $aTab = new \EJ\Ribbon\ApplicationTab();           
         $aTab->type('menu')->menuItemID('ribbonmenu');  
         $hometab  = new \EJ\Ribbon\Tab();
         $clipboard  = new \EJ\Ribbon\Group();
         $grpcontent = new \EJ\Ribbon\Content();
         $contentgroup=new \EJ\Ribbon\ContentGroup();
         $splitbutton=array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-ribbon e-ribbonpaste','targetID'=>'pasteSplit','buttonMode'=>'dropdown','arrowPosition'=>'Bottom','click'=>'executeAction');
         $contentgroup->id('paste')->text('paste')->toolTip('Paste')->quickAccessMode('toolbar')->splitButtonSettings($splitbutton);
         $default = new \EJ\Ribbon\Defaults();
         $default->width(50)->height(70)->type('splitbutton');
         $grpcontent->groups(array($contentgroup))->defaults($default);
         $clipboard->text('Clipboard')->alignType('columns')->content(array($grpcontent));     
         $hometab->id('home')->text('HOME')->groups(array($clipboard));
         echo $ribbon ->locale('es-ES')->showQAT('true')->width('500px')->applicationTab($aTab)->tabs(array($hometab))->render();
         ?>
         <script>
	         ej.Ribbon.Locale["es-ES"] = {
		     CustomizeQuickAccess: "Agordu Rapida Aliro",
	 	     RemovefromQuickAccessToolbar: "Forigu de Rapida Aliro Ilobreto",
		     AddtoQuickAccessToolbar: "Aldoni al Rapida Aliro Ilobreto",
		     ShowAbovetheRibbon: "Montru Super la Ribbona",
		     ShowBelowtheRibbon: "Montru Sube la Ribbon",
		     MoreCommands: "pli Komando"
	         };
         </script>                                 

{% endhighlight %}

![](Globalization/globalization_img1.png)

## Right to Left - RTL

By default, Ribbon render its content and layout from left to right. To customize Ribbon direction, you can change direction from LTR to RTL by using enableRTL as true.

{% highlight html %}

        <div id="defaultRibbon"></div>
         <ul id="ribbonmenu">
            <li><a>FILE</a>
             <ul>
                <li><a>New</a></li>
                <li><a>Open</a></li>
                <li><a>Save</a></li>
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
        $menu = array('openOnClick'=>false);
        $aTab->type('menu')->menuItemID('ribbonmenu')->menuSettings($menu);        
        $hometab  = new \EJ\Ribbon\Tab();
        $clipboard  = new \EJ\Ribbon\Group();
        $grpcontent = new \EJ\Ribbon\Content();
        $contentgroup=new \EJ\Ribbon\ContentGroup();
        $btn = array('contentType'=>'imageonly','imagePosition'=>'imagetop','prefixIcon'=>'e-icon e-ribbon e-new','click'=>'executeAction'); 
        $contentgroup->id('new')->text('New')->toolTip('New')->buttonSettings($btn);   
        $default= new \EJ\Ribbon\Defaults();
        $default->width(60)->height(70)->type('button');
        $grpcontent->groups(array($contentgroup))->defaults($default);
        $clipboard->text('New')->alignType('rows')->content(array($grpcontent));
        $clipboard1  = new \EJ\Ribbon\Group();
        $grpcontent1 = new \EJ\Ribbon\Content();
        $contentgroup1=new \EJ\Ribbon\ContentGroup();
        $splitbutton = array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-ribbon e-ribbonpaste','targetID'=>'pasteSplit','buttonMode'=>'dropdown','arrowPosition'=>'bottom','click'=>'executeAction'); 
        $contentgroup1->id('paste')->text('Paste')->toolTip('Paste')->splitButtonSettings($splitbutton);   
        $default1= new \EJ\Ribbon\Defaults();
        $default1->width(50)->height(70)->type('splitbutton');
        $grpcontent1->groups(array($contentgroup1))->defaults($default1);
        $clipboard1->text('Clipboard')->alignType('columns')->content(array($grpcontent1));
        $hometab->id('home')->text('HOME')->groups(array($clipboard,$clipboard1));
        echo $ribbon ->width('40%')->enableRTL(true)->applicationTab($aTab)->tabs(array($hometab))->render();
        ?>   

{% endhighlight %}

![](Globalization/globalization_img2.png)