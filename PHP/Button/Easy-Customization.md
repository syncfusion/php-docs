---
layout: post
title: Easy-Customization
description: getting started
platform: PHP
control: Button
documentation: ug
---

# Easy Customization

Button is used in all applications. Button size, content type, and image position is varied according to each application. Here you can see some customizable option for button that can perform easily.


## Button Size

You can render the button in different sizes. Here, you have some predefined size options for rendering a button with different sizes in easiest way. Each size option has different height and width. Mainly it avoids the complexity in rendering button with complex **CSS** class. 

List of predefined button size

<table>
    <tr>
        <th>
            Button Types</th>
        <th>
            Description</th>
    </tr>
    <tr>
        <td>
           Normal
        </td>
        <td>
            Creates button with content size.
        </td>
    </tr>
    <tr>
        <td>
            Mini
        </td>
        <td>
            Creates button with Built-in mini size height, width specified.
        </td>
    </tr>
    <tr>
        <td>
            Small
        </td>
        <td>
            Creates button with Built-in small size height, width specified.
        </td>
    </tr>
    <tr>
        <td>
            Medium
        </td>
        <td>
            Creates button with Built-in medium size height, width specified.
        </td>
    </tr>
    <tr>
        <td>
            Large
        </td>
        <td>
            Creates button with Built-in large size height, width specified.
        </td>
    </tr>
</table>


Apart from the above mentioned predefined size option, you can set your own width and height for button using **height** and **width** property.

The following steps explains you the details about rendering the button with different size options.

In the **PHP** page, add the following button elements to configure button widget.

{% highlight html %}
    <table>
            <tr>
                <td>Normal</td>
                <td>
                    <?php
                    $button =  new EJ\Button("normal");
                    echo $button ->size("normal")->contentType("textandimage")->prefixIcon("e-icon e-handup")->render(); // default size is normal. so no need to define specifically. Button size will be set based on the content size
                    ?>
                </td>
            </tr>
            <tr>
                <td>Mini</td>
                <td>
                    <?php
                    $button =  new EJ\Button("mini");
                    echo $button ->text("MINI")->size("mini")->render();
                    ?>
                </td>
            </tr>
            <tr>
                <td>Small</td>
                <td>
                    <?php
                    $button =  new EJ\Button("small");
                    echo $button ->text("SMALL")->size("small")->render();
                    ?>
                </td>
            </tr>
            <tr>
                <td>Medium</td>
                <td>
                    <?php
                    $button =  new EJ\Button("medium");
                    echo $button ->text("MEDIUM")->size("medium")->render();
                    ?>
                </td>
            </tr>
            <tr>
                <td>Large</td>
                <td>
                    <?php
                    $button =  new EJ\Button("large");
                    echo $button ->text("LARGE")->size("large")->render();
                    ?>
                </td>
            </tr>
        </table>
{% endhighlight %}


Execute the above code to render the following output.

![](/php/Button/Easy-Customization_images/Easy-Customization_img1.JPG) 

## Content Type

The content of the **Button** is mainly text and images. Instead of using complex **CSS** classes to render **Button** with different content types, you can use some predefined content type options provided for button control. Using this content types you can easily add different types of content for button. **Button** supports the following content types.

List of content types for button

<table>
    <tr>
        <th>
            Content Types</th>
        <th>
            Description</th>
    </tr>
    <tr>
        <td>
            TextOnly
        </td>
        <td>
            Supports only for text content only.
        </td>
    </tr>
    <tr>
        <td>
            ImageOnly
        </td>
        <td>
            Supports only for image content only
        </td>
    </tr>
    <tr>
        <td>
            ImageBoth
        </td>
        <td>
            Supports image for both ends of the button.
        </td>
    </tr>
    <tr>
        <td>
            TextAndImage
        </td>
        <td>
            Supports image with the text content.
        </td>
    </tr>
    <tr>
        <td>
            ImageTextImage
        </td>
        <td>
            Supports image with both ends and middle in text.
        </td>
    </tr>
</table>

## Prefix and Suffix icons

Icons inside the **Button** is added easily using **prefixIcon and suffixIcon** property. Location of the icon in button is a necessary thing and you can easily customize it using the following mentioned options.

**Button** control also supports the Built-in icon libraries. The **ej.widgets.core.min.css** contains definitions for important icons that can be used in buttons. Simply you can use these Built-in icons by mentioning the icon class name as value in **prefixIcon** and **suffixIcon** property. You can use any font icons that are defined in **ej.widgets.core.min.css**. It avoids the complexity in specifying icon using sprite image and **CSS**.

For example the following mentioned Built-in **CSS** class are used to show the font icons that is used by media player.

* e-mediaback
* e-mediaforward
* e-medianext
* e-mediaprev
* e-mediaeject
* e-mediaclose
* e-mediapause
* e-mediaplay

### Prefix Icon

It inserts the icon at the starting position of button. After this prefix icon, you can use text or suffix icon. This is the primary icon of the button and it is applicable for the content types image only, image text image, text and image and image both.

### Suffix Icon

It inserts the icon at the ending position of button. Before this suffix icon, you can use text or prefix icon. This is the secondary icon of the button and it is applicable for the content types imagetextimage and imageboth.

The following steps explains you the details about rendering the **Button** with above mentioned **content type**, **prefix** and **suffix icon** options

In the **PHP** page, add the following button elements to configure **Button** widget.

{% highlight html %}
        <table>
            <tr>
                <td>Image Only</td>
                <td>
                    <?php
                    $button =  new EJ\Button("imageonly");
                    echo $button ->contentType("imageonly")->prefixIcon("e-icon e-handup")->render();
                    ?>
                </td>
            </tr>
			<tr>
                <td>Image Both</td>
                <td>
                    <?php
                    $button =  new EJ\Button("imageboth");
                    echo $button ->contentType("imageboth")->prefixIcon("e-icon e-handup")->suffixIcon("e-icon e-palette")->render();
                    ?>
                </td>
            </tr>
            <tr>
                <td>Text Only</td>
                <td>
                    <?php
                    $button =  new EJ\Button("textonly");
                    echo $button ->contentType("textonly")->text("login")->render();
                    ?>
                </td>
            </tr>            
            <tr>
                <td>Text and Image</td>
                <td>
                    <?php
                    $button =  new EJ\Button("textandimage");
                    echo $button ->text("login")->contentType("textandimage")->prefixIcon("e-icon e-handup")->render();
                    ?>
                </td>
            </tr>
            <tr>
                <td>Image Text Image</td>
                <td>
                    <?php
                    $button =  new EJ\Button("imagetextimage");
                    echo $button ->text("login")->contentType("imagetextimage")->prefixIcon("e-icon e-handup")->suffixIcon("e-icon e-file-html")->render();
                    ?>
                </td>
            </tr>
        </table>
{% endhighlight %}

Execute the above code to render the following output.

![](/php/Button/Easy-Customization_images/Easy-Customization_img2.JPG)

## Image Position

To provide the best look and feel for **Button**, position of button images is an important customizable option. With **imagePosition** property you can easily customize the position of images inside button without using any complex **CSS**. **imagePosition** property is applicable only with the **textandimage** of **contentType** property. This property supports the following values.

List of values supported by ImagePosition property

<table>
    <tr>
        <th>
            ImagePosition</th>
        <th>
            Description</th>
    </tr>
    <tr>
        <td>
            ImageLeft
        </td>
        <td>
            Support for aligning text in right and image in left.
        </td>
    </tr>
    <tr>
        <td>
            ImageRight
        </td>
        <td>
            Support for aligning text in left and image in right.
        </td>
    </tr>
    <tr>
        <td>
            ImageTop
        </td>
        <td>
            Support for aligning text in bottom and image in top.
        </td>
    </tr>
    <tr>
        <td>
            ImageBottom
        </td>
        <td>
            Support for aligning text in top and image in bottom.
        </td>
    </tr>
</table>


The following steps explains you the details about rendering the **Button** with the above mentioned image Position options.

In the **PHP** page, add the following button elements to configure **Button** widget.

{% highlight html %}
        <table>
            <tr>
                <td>Image Right</td>
                <td>
                    <?php
                    $button =  new EJ\Button("imageright");
                    echo $button ->text("login")->contentType("textandimage")->prefixIcon("e-icon e-handup")->imagePosition("imageright")->render();
                    ?>
                </td>
            </tr>
			<tr>
                <td>Image Left</td>
                <td>
                    <?php
                    $button =  new EJ\Button("imageleft");
                    echo $button ->text("login")->contentType("textandimage")->prefixIcon("e-icon e-handup")->imagePosition("imageleft")->render();
                    ?>
                </td>
            </tr>          
            <tr>
                <td>Image Top</td>
                <td>
                    <?php
                    $button =  new EJ\Button("imagetop");
                    echo $button ->text("login")->contentType("textandimage")->prefixIcon("e-icon e-handup")->imagePosition("imagetop")->width(60)->height(45)->render();
                    ?>
                </td>
            </tr>
            <tr>
                <td>Image Bottom</td>
                <td>
                    <?php
                    $button =  new EJ\Button("imagebottom");
                    echo $button ->text("login")->contentType("textandimage")->prefixIcon("e-icon e-handup")->imagePosition("imagebottom")->width(60)->height(45)->render();
                    ?>
                </td>
            </tr>
        </table>
{% endhighlight %}

Execute the above code to render the following output.

![](/php/Button/Easy-Customization_images/Easy-Customization_img3.JPG)

## Theme support

You can control the style and appearance of **Button** control based on **CSS** classes. In order to apply styles to the **Button** control, you can refer two files namely, **ej.widgets.core.min.css** and **ej.theme.min.css**. When you refer the **ej.widgets.all.min.css** file, then it is not necessary to include the files **ej.widgets.core.min.css** and **ej.theme.min.css** in your project**,** as **ej.widgets.all.min.css** is the combination of these two. 

By default, there are 12 themes support available for **Button** control.

* default-theme
* flat-azure-dark
* fat-lime
* flat-lime-dark
* flat-saffron
* flat-saffron-dark
* gradient-azure
* gradient-azure-dark
* gradient-lime
* gradient-lime-dark
* gradient-saffron
* gradient-saffron-dark

## Custom CSS

You can customize the appearance of **Button** control using **CSS** class. Define a **CSS** class as per requirement and assign the class name to **cssClass** property.

The following steps explains you the details about rendering the **Button** with custom **CSS.**

In the **PHP** page, add the following button elements to configure **Button** widget.

{% highlight html %}
        <table>
            <tr>
                <td>Custom CSS 1</td>
                <td>
                    <?php
                    $button =  new EJ\Button("customCss1");
                    echo $button ->text("login")->contentType("textandimage")->prefixIcon("e-icon e-handup")->cssClass("customCss1")->render();
                    ?>
                </td>
            </tr>
			<tr>
                <td>Custom CSS 2</td>
                <td>
                    <?php
                    $button =  new EJ\Button("customCss2");
                    echo $button ->text("login")->contentType("textandimage")->prefixIcon("e-icon e-handup")->cssClass("customCss2")->render();
                    ?>
                </td>
            </tr>
            <tr>
                <td>Custom CSS 3</td>
                <td>
                    <?php
                    $button =  new EJ\Button("customCss3");
                    echo $button ->text("login")->contentType("textandimage")->prefixIcon("e-icon e-handup")->cssClass("customCss3")->render();
                    ?>
                </td>
            </tr>            
            <tr>
                <td>Custom CSS 4</td>
                <td>
                    <?php
                    $button =  new EJ\Button("customCss4");
                    echo $button ->text("login")->contentType("textandimage")->prefixIcon("e-icon e-handup")->cssClass("customCss4")->render();
                    ?>
                </td>
            </tr>
            <tr>
                <td>Custom CSS 5</td>
                <td>
                    <?php
                    $button =  new EJ\Button("customCss5");
                    echo $button ->text("login")->contentType("textandimage")->prefixIcon("e-icon e-handup")->cssClass("customCss5")->render();
                    ?>
                </td>
            </tr>
        </table>
{% endhighlight %}

Configure the **CSS** styles to apply on buttons.

{% highlight css %}

<style type="text/css" class="cssStyles">
    /* Customize the button background */
    .e-button.customCss1 {
        background-color: #121111;
    }
    .e-button.customCss2 {
        background-color: #94bbd5;
    }
    .e-button.customCss3 {
        background-color: #f3533c;
    }
    .e-button.customCss4 {
        background-color: #d1eeed;
    }
    .e-button.customCss5 {
        background-color: #deb66e;
    }
    /* Customize the button image & text color */
    .e-button.customCss1.e-btn.e-select .e-icon, .e-button.customCss1.e-btn.e-select .e-btntxt {
        color: #94bbd5;
    }
    .e-button.customCss2.e-btn.e-select .e-icon, .e-button.customCss2.e-btn.e-select .e-btntxt {
        color: #121111;
    }
    .e-button.customCss3.e-btn.e-select .e-icon, .e-button.customCss3.e-btn.e-select .e-btntxt {
        color: #cef6f7;
    }
    .e-button.customCss5.e-btn.e-select .e-icon, .e-button.customCss5.e-btn.e-select .e-btntxt {
        color: #534f4f;
    }
</style>


{% endhighlight %}


Execute the above code to render the following output.

![](/php/Button/Easy-Customization_images/Easy-Customization_img4.JPG)

