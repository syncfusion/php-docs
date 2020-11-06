---
title: Contextual Tabs
description: Overview of Contextual tabs ribbon control.
platform: php
control: ribbon
documentation: ug
keywords: ribbon features, key features, ribbon overview 
---

# Contextual Tabs

Contextual Tabs are collection of Tabs that extended styling and can be shown based on some criteria. Contextual Tabs can be added like tabs including groups and content section. You can set backgroundColor and borderColor to highlight them as Tab set. Contextual tabs can be added or set dynamically in ribbon control using [`addContextualTabs`](https://help.syncfusion.com/api/js/ejribbon#methods:addcontextualtabs) with it's object and index position.

{% highlight html %}

          <div id="Ribbon"></div>
	       <ul id="ribbonMenu">
		      <li><a>FILE</a>    
		       <ul>
		          <li><a>New</a></li>
		       </ul>
		      </li>
	       </ul>
          <div id="Contents">Custom Control</div>
          <div id="headings" class="e-headings">
           <div>
              <p>ABCD</p>
              <p>No Spacing</p>
           </div>
           <div>
              <p class="e-strong">ABCD</p>
              <p>Strong</p>
           </div>
           <div>
              <p class="e-emphasis">ABCD</p>
              <p>Emphasis</p>
           </div>
          </div>
          <table id="design" class="e-designtTablestyle">
            <tr>
               <td>
                 <input type="checkbox" id="Check2" />
                 <label for="Check2">First Column</label>
               </td>
               <td>
                 <input type="checkbox" id="check4" checked="checked" />
                 <label for="check4">Total Row</label>
               </td>
            </tr>
          </table>
          <?php
		  require_once 'EJ\AutoLoad.php';
          $ribbon = new  \EJ\Ribbon('defaultRibbon');
          $aTab = new \EJ\Ribbon\ApplicationTab();           
          $aTab->type('menu')->menuItemID('ribbonMenu');  
          $homeTab  = new \EJ\Ribbon\Tab();
          $clipboard  = new \EJ\Ribbon\Group();
          $clipboard->text('CustomControls')->type('custom')->contentID('Contents');     
          $homeTab->id('home')->text('HOME')->groups(array($clipboard));
          $contextTab  = new \EJ\Ribbon\ContextualTab();
          $contextTab1  = new \EJ\Ribbon\ContextualTab();
          $designTab = new \EJ\Ribbon\Tab();
          $clipboard1  = new \EJ\Ribbon\Group();
          $clipboard1->text('Table Style Options')->type('custom')->contentID('design');
          $designTab->id('Design')->text('DESIGN')->groups(array($clipboard1));
          $contextTab->backgroundColor('#FCFBEB')->borderColor('#F2CC1C')->tabs(array($designTab));
          $tabset1 = new \EJ\Ribbon\Tab();
          $clipboard2  = new \EJ\Ribbon\Group();
          $clipboard2->text('Tabset1 Style')->type('custom')->contentID('headings');
          $tabset1->id('tabset1')->text('Tabset1')->groups(array($clipboard2));
          $tabset2 = new \EJ\Ribbon\Tab();
          $clipboard3  = new \EJ\Ribbon\Group();
          $grpContent = new \EJ\Ribbon\Content();
          $contentGroup=new \EJ\Ribbon\ContentGroup();
          $contentGroup1=new \EJ\Ribbon\ContentGroup();
          $buttonSettings=array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-ribbon e-uppercase');
          $contentGroup->id('uppercase')->text('Upper Case')->buttonSettings($buttonSettings);
          $buttonSettings1=array('contentType'=>'imageonly','prefixIcon'=>'e-icon e-ribbon e-lowercase');
          $contentGroup1->id('lowercase')->text('Lower Case')->buttonSettings($buttonSettings1);
          $default = new \EJ\Ribbon\Defaults();
          $default->isBig('true');
          $grpContent->groups(array($contentGroup,$contentGroup1))->defaults($default);
          $clipboard3->text('TabSet2 Style')->content(array($grpContent));
          $tabset2->id('tabset2')->text('Tabset2')->groups(array($clipboard3));
          $contextTab1->backgroundColor('blue')->borderColor('red')->tabs(array($tabset1,$tabset2));
          echo $ribbon ->width('500px')->applicationTab($aTab)->tabs(array($homeTab))->contextualTabs(array($contextTab,$contextTab1))->render();
          ?>

{% endhighlight %}

![](Context/context_img1.png)