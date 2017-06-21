---
layout: post
title:  "Add drawable to Multiline EditText's top left corner"
date:   2017-06-22
---

EditText is a user interface element for entering and modifying text. When you define an edit text widget, you must specify the TextView_inputType attribute. For example, for plain text input set **inputType** to "text": 
{% highlight xml %}
<EditText
     android:id="@+id/plain_text_input"
     android:layout_height="wrap_content"
     android:layout_width="match_parent"
     android:inputType="text"/>
{% endhighlight %} 
We can add drawable into EditText, so the source code example like below :
{% highlight xml %}
 <EditText
     android:id="@+id/plain_text_input"
     android:layout_height="wrap_content"
     android:layout_width="match_parent"
     android:inputType="text"
     android:drawableLeft="@drawable/ic_cellphone_android"
     android:drawablePadding="8dp"/>
{% endhighlight %} 
If we want to change EditText inputType to "Multiline", we can changed **android:inputType="text"** to
**android:inputType="textMultiLine"** and add some additional property like **"android:maxLines"** or **"android:scrollbars"**.
{% highlight xml %}
<EditText
     android:id="@+id/plain_text_input"
     android:layout_height="wrap_content"
     android:layout_width="match_parent"
     android:inputType="textMultiLine"
     android:maxLines="4"
     android:scrollbars="vertical"
     android:drawableLeft="@drawable/ic_cellphone_android"
     android:drawablePadding="8dp"/>
{% endhighlight %} 
Now, you can run your this project and you got this result :

----------
![Image1](https://drive.google.com/uc?id=0Bzu9omikbG_SMVh6aHA5U3Y2WDA)

----------
As we see, that drawable icon going down to middle center of the EditText, like a picture above. To make that drawable icon stay on left top position, **create a xml drawable @drawable/custom_multiline_edittext**

**custom_multiline_edittext.xml**
{% highlight xml %}
<?xml version="1.0" encoding="utf-8"?>
<selector xmlns:android="http://schemas.android.com/apk/res/android">
    <item><layer-list>
    <item android:left="8dp" android:right="8dp" 
    android:bottom="8dp" android:top="8dp">
    <bitmap android:gravity="left|center"
     android:src="@drawable/ic_menu_share"/>
    </item>
    </layer-list></item>
</selector>
{% endhighlight %} 
then set your EditText background **android:background="@drawable/custom_multiline_edittext"**, like below :
{% highlight xml %}
<EditText
      android:id="@+id/plain_text_input"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="5dp"
        android:paddingTop="10dp"
        android:paddingBottom="10dp"
        android:paddingLeft="42dp"
        android:background="@drawable/custom_multiline_edittext"
        android:inputType="textMultiLine"
        android:maxLines="4"
        android:scrollbars="vertical"
        android:textSize="16sp"/>
{% endhighlight %} 
and then, we got result like below :

---
![Image2](https://drive.google.com/uc?id=0Bzu9omikbG_SVjlUU0dzRzlCS28)

---