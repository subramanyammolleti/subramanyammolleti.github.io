---
layout: post
title: "A quick Glimpse of Android Toolbar"
comments: true
permalink: "android-toolbar-tutorial"
---

## A Small Introduction
Toolbar is the extended version of `ActionBar`, A ToolBar has got a rich user Experience and has been introduced from the API Level 21(Lollipop).
The User Experience of Lollipop has been increased with the introduction of the [Material Design](http://www.google.com/design/spec/material-design/introduction.html) which is a combination of rich UI elements 
and Components. As Toolbar is introduced in `Android Lollipop` to support the devices below this API level Andorid has introduced a AppCompact
Support Library with which we can backport this Toolbar to the lower versions of Android.

<img src="/assets/toolbar.png" style="padding:10px;align:middle;"/>


## So, How to include a Toolbar ?
Firstly define some colors in `colors.xml` under <strong>res</strong>-><strong>values</strong>-><strong>colors.xml</strong>

Sample `colors.xml` file

{% highlight xml %}

<?xml version="1.0" encoding="utf-8"?>
<resources>
    <color name="bar_color">#FF1493</color>
    <color name="primary_dark">#FF1493</color>
    <color name="accent">#FF1493</color>
</resources>

{% endhighlight %}

Toolbar can be created in five simple steps 

* Disable the ActionBar and add color for the different attributes, you can find them in the below image.

<img src="/assets/attributes.png" style="padding:10px;align:middle;width:350;height:400;"/>

In styles.xml disable ActionBar by setting the parent  to NoActionBar using `Theme.AppCompat.Light.NoActionBar`.

{% highlight xml %} 
 
<resources>

    <!-- Base application theme. -->
    <style name="AppTheme" parent="Theme.AppCompat.Light.NoActionBar">
        <!-- Main theme colors -->
        <!--   your app branding color for the app bar -->
        <item name="android:colorPrimary">@color/primary</item>
        <!--   darker variant for the status bar and contextual app bars -->
        <item name="android:colorPrimaryDark">@color/primary_dark</item>
        <!--   theme UI controls like checkboxes and text fields -->
        <item name="android:colorAccent">@color/accent</item>
    </style>

</resources>
 
{% endhighlight %}

* Add the Dependencies i.e AppCompact Support Library in dependencies inside build.gradle file

{% highlight Java %}

dependencies {
    compile fileTree(dir: 'libs', include: ['*.jar'])
	// this line adds the AppCompact Support Library to the project
    compile 'com.android.support:appcompat-v7:22.1.1' 
}

{% endhighlight %}

* Create a layout file for the Toolbar

{% highlight xml %} 

<?xml version="1.0" encoding="utf-8"?>
<android.support.v7.widget.Toolbar xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:background="@color/bar_color"
    android:theme="@style/ThemeOverlay.AppCompat.Dark.ActionBar">

</android.support.v7.widget.Toolbar>

{% endhighlight %} 

* Include the Toolbar XML file in Activity's layout file with this code

{% highlight xml %} 

<include
    android:id="@+id/tool_bar"
    layout="@layout/tool_bar">
</include>

{% endhighlight %} 

* Replace the `extends Activity` with `extends AppCompatActivity` and create a reference for it and set it using  `setSupportActionBar(Toolbar)`.

{% highlight java %} 

Toolbar toolBar = (Toolbar) findViewById(R.id.tool_bar);
setSupportActionBar(toolBar);

{% endhighlight %} 

If your stuck anywhere please post it here.

Thanks for reading


{% include twitter_plug.html %}
