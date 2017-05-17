# Andriod

Just begin to learn develop andriod.

## Lecture 1 

Creat the first andriod project. File -> project strcture to see the version.  

- Linux Kernal
- C/C++ Libs / Android runtime
- Application framework
- Application layer

Amdroid project --> Buils(Gradle) --> APK(byte code/ Resources/ Manifest)(Gradele) --> Jar Signer(Sign) --> Install on device(ADB)  

**Gradle** is the build system of choice for Android Studio.


Four conponents:  
1. Activity: Responsible for creating the window that the application uses to draw and receive events from the system  
2. Service   
3. Content Provider  
4. Broadcast Receiver

### Android Layout

An **activity** is a single focused thing that the user can do. An activity creates **views** to show the user information, and to let the user interact with the activity. Views are a class in the Android UI framework. An activity determines what views to create (and where to put them), by reading an **XML** layout file.  

**There are two major categories of views**. The first type are **UI components** that are often interactive. 

```
TextView		Creates text on the screen; generally non interactive text.
EditText		Creates a text input on the screen
ImageView		Creates an image on the screen
Button			Creates a button on the screen
Chronometer	    Create a simple timer on screen
```

The second are views called "**Layout**" or "**Container**" views. They extend from a class called **ViewGroup**. They are primarily responsible for containing a group of views and determining where they are on screen.

```
LinearLayout		Displays views in a single column or row.
RelativeLayout		Displays views positioned relative to each other and this view.
FrameLayout	    	A ViewGroup meant to contain a single child view.
ScrollView			A FrameLayout that is designed to let the user scroll through the content in the view.
ConstraintLayout	This is a newer viewgroup; it positions views in a flexible way. We’ll be exploring constraint layout later in the lesson.
```

### Width and Height

Some of the most important properties are the **width** property and **height** property - those must be defined for every view. Remember that all views occupy a rectangular area on the screen - the width and height are the width and height of that area. You can define this in pixels, or better yet **dp** (stands for density-independent pixels)

For the sake of having a layout be responsive and adjust to different devices, two common values are not numbers at all, but wrap_content and match_parent used as shown here:

```
android:layout_width="wrap_content"
android:layout_height="match_parent"
```

**wrap_content** will shrink the view to wrap whatever is displayed **inside** the view. For example, if the view is filled with the text “Hello world” then wrap_content for the width will set the width of the view to be the exact width that the text “Hello world” takes up on the screen.

**match_parent** will expand the size of the view to be as large as the parent view which it is nested inside of.

### Padding and Margin

padding and layout_margin are two very similar attributes. Both determine the space around a View. The difference is that **padding** determines space **within** the boundaries of the view, and **layout_margin** determines the space **outside** the boundaries of the view**.

<center>
![](https://github.com/bikegcy/MK_Pic/blob/master/padding-margin.png?raw=true)
</center>

### How do the XML Layouts relate to the Java Activites?

After you create your XML Layout you need to associate it with your activity. This is done in the **onCreate** method of the Activity using the method **setContentView**. You pass a reference to the layout file as R.layout.name_of_layout. For example, if your layout were named activity_main.xml this would look like:

```java
public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
       super.onCreate(savedInstanceState);
       setContentView(R.layout.activity_main);
       // other code to setup the activity
    }
    // other code
}
```
**SetContentView**:  It **inflates the layout**. Essentially what happens is that Android reads your XML file and generates Java objects for each of the tags in your layout file. You can then edit these objects in the Java code by calling methods on the Java objects. We’ll go over what these methods look like and how to access view in your layout files later in the course.











