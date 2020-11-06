---
layout: post
title: Getting-Started
description: getting started
platform: php
control: RadioButton
documentation: ug
---

# Getting Started

This section explains briefly about the necessary steps required to render and configure EJ RadioButton control using PHP wrapper classes.

Create a PHP Project and add necessary scripts and styles with the help of the given PHP [Getting Started](https://help.syncfusion.com/php/getting-started) Documentation.


## Create RadioButton

Create a RadioButton control by instantiating the PHP wrapper class available in EJ namespace as shown below.

{% highlight html %}
    <div class='frame'>
            <div class='radioalign'>
                <br />
                Category
              <br />
                <br />
                <table>
                    <tr>
                        <td class='chkrad'>
                            <?php
                            $radio=new EJ\RadioButton('Radio1');
                            echo  $radio->render()
                            ?>
                            <label for='Radio1' class='clslab'>Fresher</label>
                        </td>
                        <td class='chkrad' colspan='2'>
                            <?php
                            $radio=new EJ\RadioButton('Radio3');
                            echo $radio->checked(true)->render()
                            ?>
                            <label for='Radio3' class='clslab'>Experienced</label>
                        </td>
                    </tr>
                </table>
                <br />
                <br />
                Experienced
              <br />
                <br />
                <table>
                    <tr>
                        <td class='chkrad'>
                            <?php
                            $radio=new EJ\RadioButton('Radio2');
                            echo  $radio->checked(true)->render();
                            ?>
                            <label for='Radio2' class='clslab'>1+ years</label>
                        </td>
                        <td class='chkrad'>
                            <?php
                            $radio=new EJ\RadioButton('Radio4');
                            echo   $radio->size('medium')->render()
                            ?>
                            <label for='Radio4' class='clslab'>2.5+years</label>
                        </td>
                        <td class='chkrad'>
                            <?php
                            $radio=new EJ\RadioButton('Radio5');
                            echo $radio->size('medium')->render()
                            ?>
                            <label for='Radio5' class='clslab'>5+years</label>
                        </td>
                    </tr>
                </table>
                <br />
            </div>

{% endhighlight %}

Add the following styles to show the **RadioButton** control in an order.

{% highlight css %}

    <style>
        table {
            margin: auto;
            width: 300px;
        }

        td {
            padding: 11px;
        }
    </style>

{% endhighlight %}

The following screenshot illustrates the output of above code.

![](/php/RadioButton/Getting-Started_images/Getting-Started_img1.JPG) 