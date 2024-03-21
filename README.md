# ThemesPerFramgments

# Using Different Themes for Different Fragments in Android

This guide demonstrates how to implement different themes for different fragments in an Android app using Navigation Fragments.

## Prerequisites
- Basic understanding of Android development.
- Android Studio installed on your machine.
- A basic Android project set up with Navigation Fragments.

## Steps

1. **Define Base Theme**: 
    - In your `res/values/styles.xml` file, define your base theme for the application.

    ```xml
    <style name="AppTheme" parent="Theme.AppCompat.Light">
        <!-- Customize your base theme here -->
    </style>
    ```

2. **Create Fragment Themes**:
    - Create a separate folder for each fragment's theme under `res/values`. For example, if you have a fragment named `Fragment1`, create a folder named `fragment1_theme`.
    - Inside each fragment's theme folder, create a `styles.xml` file and define the theme for that fragment.

    ```xml
    <resources>
        <style name="Fragment1Theme" parent="Theme.AppCompat.Light">
            <!-- Customize your fragment1 theme here -->
        </style>
    </resources>
    ```

3. **Set Theme for Each Fragment**:
    - In the `AndroidManifest.xml` file, specify the theme for each fragment using metadata tags. 

    ```xml
    <activity android:name=".YourActivity">
        <intent-filter>
            ...
        </intent-filter>
        <meta-data
            android:name="android.support.PARENT_ACTIVITY"
            android:value=".ParentActivity" />
        <meta-data
            android:name="android.support.UI_OPTIONS"
            android:value="splitActionBarWhenNarrow" />
        <meta-data
            android:name="android.app.theme"
            android:resource="@style/Fragment1Theme" /> <!-- Set the theme for Fragment1 here -->
    </activity>
    ```

4. **Apply Themes to Fragments**:
    - In your code where you navigate to each fragment, set the theme for the fragment's activity.

    ```java
    // Inside your activity where you navigate to Fragment1
    Intent intent = new Intent(this, Fragment1Activity.class);
    intent.putExtra("theme", R.style.Fragment1Theme);
    startActivity(intent);
    ```

5. **Handle Theme in Fragment's Activity**:
    - In each fragment's activity, retrieve the theme passed from the calling activity and apply it to the activity.

    ```java
    // Inside Fragment1Activity's onCreate() method
    int theme = getIntent().getIntExtra("theme", R.style.AppTheme);
    setTheme(theme);
    ```

## Conclusion
By following these steps, you can implement different themes for different fragments in your Android app, providing a customized user experience.
