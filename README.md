# flutter-tutorial-notes
Notes on all the tutorials I followed to learn Flutter.

Flutter is the framework to build apps from a single codebase. It will be used to build web-apps as well. Google is developing "Hummingbird" which will allow to develop web apps using flutter.  

Advantages:  
1. Increases Productivity - HMR, Same codebase for iOS and Android.  
2. Speed - JIT & AOT. Uses "Skia" for rendering, which is used by Chrome.  
3. OSS  
4. Pixel perfect UI. Cupertino (iOS) and Material (Android)  

Disadvantages:  
1. Bigger size  
2. Young  

Examples:  
1. Alibaba  
2. Google Ads  

Flutter SDK: [Click Here](https://flutter.dev/docs/get-started/install/windows)  

# WIDGETS

A widget is the basic build block of the UI in a flutter app. It is an immutable declaration of part of UI.  

A text, button, image, font, color scheme, padding, margins, theme, cols-rows, tables, material-app - everything is a widget.  

[Material design](https://material.io/design/introduction/) is the Design Language that Google developed.  

The library that Flutter uses for material design is **Material.dart**.  

While developing widgets, the question you need to ask is - will it be a static or a dynamic widget.  

In other words, there are 2 types:  
1. Stateful Widgets: The state changes during the widget's lifetime. Ex. Input field. What really changes, is not the widget itself (as it is immutable), it is the STATE that changes during the lifetime.  

2. Stateless Widgtes: Only configuration information. Ex - Title of app or Image of app logo - It will not change during the app's lifetime.  Therefore we define a stateless widget when the part of the UI that we are describing does not depend on anything other than the configuration information of the object.  


CUSTOM WIDGETS: Created by composing smaller widgets.  

[Create flutter apps (Flutter playground).](https://flutterstudio.app/)

# STATE

State is information (attached to widget) that might change during lifetime of the widget. Flutter has a **UNIFIED OBJECT MODEL**, unlike other frameworks where the business logic is separated from the view. THis UOM is called a WIDGET and you write business logic in this UOB (aka Widget).  

There are no layout files in flutter.  

Checkout widget tree in the android studio.

# BUILDING LAYOUTS  
There are many kinds of widgets like Layout, Gestures (Interaction Models), Animations - [More](https://flutter.dev/docs/development/ui/widgets)  

## LAYOUT WIDGETS
The widgets here will have their own child widgets.  

Row: Will have Columns as child widgets.  
Column: Will have row as child widgets.  
List View: When you need to show info more than the height of the device  

Gesture Detector: A widgets which detects gestures.  

### ANIMATIONS
In flutter, you can develop 2 kinds of animations:  
1. Tweens: In-between animations. Define begin-end points, timeline and curve. Flutter will apply the transition.  

2. Physics based: Real world behaviour. For example: Flip of a coin or dropping of an object whose speed will depend on the weight of the object and distance from the ground.  Governed by the physics laws and forces.  

## STREAMS and THE BLoC PATTERN - alternate for setState()
We use `setState()` to set the state of the widget. But this has a drawback as the logic is in the same class as the layout which can be an issue as the app grows and can also result in [spaghetti code](https://en.wikipedia.org/wiki/Spaghetti_code).  

May complicate code reuse.  

Risk of code duplication.  

BLoC stands for **Business Logic Components**. It is officially supported by Google.  

 BLoC's are based on streams. It is like a one-way pipe where you insert the data at one end and the data flows out from the other.  

 **Stream Controllers:** The streams are managed by stream controllers. The two main properties of the **StreamController** are:  
 1. **.sink** --> The way-in the stream (insterting data into the stream).  
 2. **.stream** --> The way-out of the stream (data exiting from the stream).  

 `.sink` and `.stream` are the two properties to control the stream.  

 In order to use the stream and be notified when something gets out of it, you listen to the stream. Therefore, you define a **listener** with a `StreamSubscription` object.  

 The `StreamSubscription` is notified everytime a event related to the stream occurs. For example, when there is an ERROR or when the data flows out of the stream.  

 You can also TRANSFORM the data in the stream using a `StreamTransformer` object. For example if you want to FILTER or MODIFY the data inside the stream.  

![image](https://user-images.githubusercontent.com/18363595/78969991-eab5a280-7b25-11ea-9bc2-0f4dd59e93bb.png)  

**BLoC Pattern**
The business logic of the apps should be moved to BLoCs and therefore should be removed from the UI.  

It should rely on the use of STREAMS for input (.sink) and output (.stream).  

It should remain platform and environment independent.  

BLoCs are components that contain the business logic of your app. Use `.sinks` to take events from widgets and `.stream` to output the result to widgets.  

What happens inside the BLoC is independent from the UI.  

![image](https://user-images.githubusercontent.com/18363595/78970377-cad2ae80-7b26-11ea-8c3f-66371f175867.png)


# FLUTTER TOOLS

In Android Studio, you can inspect a element in the UI like in Web Dev using the Flutter Inspector. It is is `View -> Tool Windows -> Flutter Inspector`. Here you can see the entire widget tree with its properties.

In VSCODE -   
type `stles` to create a StateLess widget.  
type `stful` to create StateFull widget.  
type `stanim` to create Animation widget.  

Quick Fixes and Others - `Ctrl + .`
Problems - `Ctrl + Shift + M`  

## PACKAGES
[Flutter Packages](https://pub.dev/flutter/packages)  
[Dart Packages](https://pub.dev/dart/packages)  

## LOCALIZATIONS
[flutter_localizations](https://api.flutter.dev/flutter/flutter_localizations/flutter_localizations-library.html)  - A library used to make flutter app multi-lingual.  

[Docs](https://flutter.dev/docs/development/accessibility-and-localization/internationalization)  

## TESTING
1. Unit Test (Functions, etc.)
2. Widget Test  (like testing components in Angular)
3. Integration Test (Tests the whole app or a large part of the app. Try to run it on a real device)  

`test.dart` package is used to write test cases.  

## FLARE + 2DIMENSIONS.COM = RIVE
Make animations and use directly into your flutter app.
Vector design and animation tool that exports directly to Flutter. [Rive](https://rive.app/) is used as vector design and animation tool.  

[Register here](https://rive.app/register)  

[Tutorial](https://medium.com/rive/building-a-water-tracking-app-with-flare-flutter-f03de436dba3)

[Add flutter to exisiting apps (iOS and Android)](https://flutter.dev/docs/development/add-to-app)  

## Designing for iOS and Android with the same codebase
`Platform` is the class which contains information on the envrionment in which the current app is running.  
You can distinguish code for different platforms like:  

`if(Platform.isIOS){}`  

`if(Platform.isAndroid){}`  

**But this will almost double the amount of code to produce the UI.**  

### Flutter Platform Widgets
There are better patterns to follow and there is also a dedicated library for the same - [flutter_platform_widgets](https://pub.dev/packages/flutter_platform_widgets)  

**flutter_platform_widgets** helps to create platform specific UI without having to duplicate the code.  
You'll be using classes like: `PlatformScaffold`, `PlatformAppBar`, `PlatformText` instead of `Scaffold`, `AppBar`, etc.  

***
# Flutter (Tutorial #2)
Even though flutter lies in the HYBRID APP DEVELOPMENT category, it is a better alternative than react native, Cordova/Ionic and Xamarin.  

The main issues with them is that they need a BRIDGE between your code and the mobile OS and thus that hampers the performance of the app which is well below the performance of the native app.  

Using 3rd party libraries and components with apps developed using these can be very problematic.  

## WHY FLUTTER?
Flutter compiles to native. Therefore it provides excellent perforamance. Types of compilation - JIT, AOT  
Fast Development framework  
Single code-base for iOS and Android  
No bridges between your code base and the OS of the mobile  

Flutter is developed using a strongly typed language called "Dart".

















