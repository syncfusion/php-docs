---
layout: post
title: Getting-Started
description: getting started
platform: php
control: Tile
documentation: ug
---

# Getting Started

This section helps to get started of the Tile control for PHP. 

## Create Tile Control 

1)	Refer the common PHP Getting Started Documentation to create a PHP application and add necessary scripts and styles for rendering Essential PHP controls.

2)	Create the Tile control object by creating an object for the Tile referring the below code, here the class EJ\Tile object is created by using ‘new’ keyword. Define its properties and use render() method for rendering the control. We need to call the rendering element in echo statement.

{% highlight html %}

   <div class="e-tile-column">
           <?php
			 $captiontexts=array(array("text"=>"Map"));
             $tile7=new EJ\Tile("tile7");
             echo $tile7->tileSize("medium")->imageUrl("http://js.syncfusion.com/ug/web/content/tile/map.png")->caption($captiontexts[0])->render();
            ?>
   </div>  

{% endhighlight %}

N> It is mandatory to define the render() method at last as given in the above syntax, to display the Tile control on the browser.

Get the following output from the above mentioned code

![](Getting-Started_images\Getting-Started_img1.png)

You can easily design a home page using tile control for easy navigation. Therefore, you require many different sizes of tiles aligned in a grid-like manner. The tiles will be aligned automatically to define the necessary tile elements inside the wrapper element, that contains a “e-tile-column” class. You can define all columns elements under the wrapper element with the tile “e-tile-group” class to make ‘n’ number of tiles as a grouped tile. Add the below mentioned code to the corresponding view page.

{% highlight html %}
    
    <div class="e-tile-group">
        <div class="e-tile-column">
            <?php
            $tile1=new EJ\Tile("tile1");
            $captiontexts=array(array("text"=>"People"), array("text"=>"Play"), array("text"=>"Maps"), array("text"=>"Sports"), array("text"=>"Photo"), array("text"=>"Weather"), array("text"=>"Music"), array("text"=>"Favorites"));
            echo $tile1->imagePosition("fill")->tileSize("medium")->imageUrl("http://js.syncfusion.com/ug/web/content/tile/people_1.png")->caption($captiontexts[0])->render();
            ?>
            <div class="e-tile-small-col-2">
                 <?php
                 $tile2=new EJ\Tile("tile2");
                 echo $tile2->imagePosition("center")->tileSize("small")->imageUrl("http://js.syncfusion.com/ug/web/content/tile/alerts.png")->render();
                 $tile3=new EJ\Tile("tile3");
                 echo $tile3->imagePosition("center")->tileSize("small")->imageUrl("http://js.syncfusion.com/ug/web/content/tile/bing.png")->render();
                 $tile4=new EJ\Tile("tile4");
                 echo $tile4->imagePosition("center")->tileSize("small")->imageUrl("http://js.syncfusion.com/ug/web/content/tile/camera.png")->render();
                 $tile5=new EJ\Tile("tile5");
                 echo $tile5->imagePosition("center")->tileSize("small")->imageUrl("http://js.syncfusion.com/ug/web/content/tile/messages.png")->render();
                 ?>
            </div>
             <?php
             $tile6=new EJ\Tile("tile6");
             echo $tile6->imagePosition("center")->tileSize("medium")->imageUrl("http://js.syncfusion.com/ug/web/content/tile/games.png")->caption($captiontexts[1])->render();
             $tile7=new EJ\Tile("tile7");
             echo $tile7->tileSize("medium")->imageUrl("http://js.syncfusion.com/ug/web/content/tile/map.png")->caption($captiontexts[2])->render();
             $tile8=new EJ\Tile("tile8");
             echo $tile8->imagePosition("fill")->tileSize("wide")->imageUrl("http://js.syncfusion.com/ug/web/content/tile/sports.png")->caption($captiontexts[3])->render();
             ?>
        </div>
        <div class="e-tile-column">
             <?php
             $tile9=new EJ\Tile("tile9");
             echo $tile9->imagePosition("fill")->tileSize("medium")->imageUrl("http://js.syncfusion.com/ug/web/content/tile/people_2.png")->caption($captiontexts[0])->render();
             $tile10=new EJ\Tile("tile10");
             echo $tile10->imagePosition("center")->tileSize("medium")->imageUrl("http://js.syncfusion.com/ug/web/content/tile/pictures.png")->caption($captiontexts[4])->render();
             $tile11=new EJ\Tile("tile11");
             echo $tile11->imagePosition("center")->tileSize("wide")->imageUrl("http://js.syncfusion.com/ug/web/content/tile/weather.png")->caption($captiontexts[5])->render();
             $tile12=new EJ\Tile("tile12");
             echo $tile12->imagePosition("center")->tileSize("medium")->imageUrl("http://js.syncfusion.com/ug/web/content/tile/music.png")->caption($captiontexts[6])->render();
             $tile13=new EJ\Tile("tile13");
             echo $tile13->imagePosition("center")->tileSize("medium")->imageUrl("http://js.syncfusion.com/ug/web/content/tile/favs.png")->caption($captiontexts[7])->render();
             ?>
        </div>
    </div>
    
{% endhighlight %}

Run the above code to get the following output.

![](Getting-Started_images\Getting-Started_img2.png)

## Template support with Tile control  

To customize the Tile images with template feature by using imageTemplateId property of Tile control. Add the below mentioned code to the corresponding view page.

{% highlight html %}

  <div>
       <div class="e-tile-column">
           <?php
           $tile1=new EJ\Tile("tile1");
           $captiontexts=array(array("text"=>"Windows Store"));
           echo $tile1->imagePosition("fill")->tileSize("wide")->imageUrl("http://js.syncfusion.com/ug/web/content/tile/people_1.png")->caption($captiontexts[0])->imageTemplateId("imageTemplate")->render();
           ?>
       </div>
       <div id="imageTemplate">
           <div id="appimage">
           </div>
           <div class="tileMargin">
               <span class="caption">Google Search</span><br />
               <span class="description">The world’s information</span><br />
               <span class="sub">Free</span>
           </div>
       </div>
   </div>
   
{% endhighlight %}

Add the following styles to customize the tile images with template support.

{% highlight html %}

 <style>
        #appimage {
            background-image: url("http://js.syncfusion.com/UG/mobile/content/google.png");
            background-position: center center;
            background-repeat: no-repeat;
            background-size: 50% auto;
            display: table-cell;
            width: 45%;
        }

        .tileMargin {
            display: table-cell;
            padding-top: 25px;
        }

        .e-tile-template {
            display: table;
            height: 100%;
            width: 100%;
        }
    </style>
   
{% endhighlight %}

Run the above code to get the following output.

![](Getting-Started_images\Getting-Started_img3.png)

N> You can find the complete API list for all Syncfusion controls from the [API reference](https://help.syncfusion.com/api/js/ejtile)

