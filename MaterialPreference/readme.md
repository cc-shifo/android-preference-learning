Material Preference
==================
[![Android Arsenal](https://img.shields.io/badge/Android%20Arsenal-MaterialPreference-green.svg?style=true)](https://android-arsenal.com/details/1/3705)
[![CircleCI](https://circleci.com/gh/codevscolor/MaterialPreference.svg?style=svg)](https://circleci.com/gh/codevscolor/MaterialPreference)

[Report an issue][1]


This library can be used to implement Material Designed Settings/Preference Screen on Pre-Lollipop devices.
(Currently supporting devices upto api 9 )

- Material Preference Library uses `com.android.support:preference-v7:x.x.x` support library widgets.
- Also it includes a color chooser dialog widget, that can be used to select accent color .
- Header is tinted with selected secondary color.

Demo
--
On Lollipop :

![Demo](https://s33.postimg.org/cmumlk7in/lollipop.gif)

On KitKat :

![Demo](https://s33.postimg.org/vhqtvfoj3/KITKAT.gif)

Light Theme :

![Demo](https://s33.postimg.org/qcgfm4erj/lollipop_light.gif)

Download
==

```
dependencies {
compile 'com.codevscolor.materialpreference:mp:0.2.1'
}
```

How do I use this library ?
-------------------

1. Create one preference xml file inside ``res/xml`` folder
2. Add `android.support.v7.preference` widgets.
3. For Preference category, use `com.codevscolor.materialpreference.widget.MaterialPreferenceCategory` with a title , like : 
```xml
<com.codevscolor.materialpreference.widget.MaterialPreferenceCategory android:title="Category one">
.........
.........
</com.codevscolor.materialpreference.widget.MaterialPreferenceCategory>
```

4. If you want to use color chooser widget,use it with a `key`,`summary` and `title` like 
```xml
<com.codevscolor.materialpreference.widget.ColorChooserPreference
            android:key="secondary_color_position"
            android:summary="select accent color"
            android:title="secondary color" />
```

5. Now create your Preference Activity like 
```java
import com.codevscolor.materialpreference.util.MaterialPrefUtil;
import com.codevscolor.materialpreference.activity.MaterialPreferenceActivity;
import com.codevscolor.materialpreference.callback.MaterialPreferenceCallback;

public class SettingsActivity extends MaterialPreferenceActivity implements MaterialPreferenceCallback {

    //initialization of the sdk should be done here
    @Override
    public void init(@Nullable Bundle savedInstanceState) {
        //register this class as listener for preference change
        setPreferenceChangedListener(this);

        //use dark theme or not . Default is light theme
        useDarkTheme(true);

        //set toolbar title
        setToolbarTitle("My Toolbar");

        //set primary color
        setPrimaryColor(MaterialPrefUtil.COLOR_BLUE_GREY);

        //default secondary color for tinting widgets, if no secondary color is used yet
        setDefaultSecondaryColor(this, MaterialPrefUtil.COLOR_BLUE);

        //set application package name and xml resource name of preference
        setAppPackageName("com.exampletest.sampleapplicationsettings");
        //set xml resource name
        setXmlResourceName("settingspreference");

        //optional
        //if you are using color picker, set the key used for color picker in the xml preference
        setColorPickerKey("secondary_color_position");

    }


    /**
     * callback for preference changes
     *
     * @param sharedPreferences
     * @param name
     */
    @Override
    public void onPreferenceSettingsChanged(SharedPreferences sharedPreferences, String name) {
        Toast.makeText(this, "preference with key " + name + " changed", Toast.LENGTH_LONG).show();
    }
}

```

Compatibility
-------------

API level 8 and above

Author
------
Nandan Kaushik Dutta - @codevscolor on GitHub, personal blog : [codevscolor][2]

License
-------
Apache 2.0

[1]: https://github.com/codevscolor/MaterialPreference/issues
[2]: http://codevscolor.com
