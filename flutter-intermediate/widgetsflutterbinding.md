# WidgetsFlutterBinding

> :bulb:If you need to use Flutter's engine or Flutter's embedder (e.g., to invoke native methods) before calling `runApp`, you must ensure that the Flutter framework is connected to the Flutter Engine by calling `WidgetsFlutterBinding.ensureInitialized()`.

## What is the WidgetsFlutterBinding class?

The WidgetsFlutterBinding class is:

* the glue that binds the framework to the Flutter engine (see image below);
* a concrete binding for applications based on the Widgets framework.

<figure><img src="../.gitbook/assets/flutter-engine.png" alt=""><figcaption><p>Flutter Engine</p></figcaption></figure>

***

## What does "binding" mean?

In the context of Flutter, "binding" refers to the connection between different parts of the framework. Specifically, it refers to the connection between the Flutter framework and the underlying Flutter engine (the C++ engine that renders and runs the Flutter application on different platforms).

The Flutter framework is primarily written in the Dart programming language and provides the building blocks for creating UI elements, managing state, handling user interactions, and more. On the other hand, the Flutter engine is written in C++ and handles the rendering of UI elements, communication with native platform APIs, and performance optimizations.

> The role of the binding classes like `WidgetsFlutterBinding` is to act as an intermediary or "glue" that connects the Dart-based Flutter framework with the C++ Flutter engine. It facilitates communication and coordination between these two parts, allowing them to work together seamlessly.

When a Flutter application starts, the `WidgetsFlutterBinding` is responsible for:

* initializing the necessary components,
* setting up event handling,
* and configuring the engine to render the UI created using the Flutter framework.&#x20;

It ensures that Dart code can interact with the engine effectively, enabling a smooth user experience.

In summary, the "binding" in this context represents the vital connection between the Dart-based Flutter framework and the C++ Flutter engine, managed by classes like `WidgetsFlutterBinding`. This binding allows the framework to control the UI and logic while leveraging the engine's rendering capabilities and platform integration for a performant and cross-platform experience.

***

## WidgetsFlutterBinding.ensureInitialized()

{% hint style="info" %}
[Read about it on StackOverflow!](https://stackoverflow.com/questions/63873338/what-does-widgetsflutterbinding-ensureinitialized-do)
{% endhint %}

We already said that the `WidgetFlutterBinding` is used to interact with the **Flutter engine**.

Methods like `Firebase.initializeApp()` need to call native code (therefore, using the **Embedder layer**) to initialize Firebase (in this example), and since the plugin needs to use platform channels to call the native code, which is done asynchronously, you have to call `ensureInitialized()` to make sure that you have an instance of the `WidgetsBinding`.

You only need to call this method if you need the binding to be initialized before calling runApp.
