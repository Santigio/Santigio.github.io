## Flutter Tutorial Part 3


> In today’s tutorial, we covered all about Flutter’s core concepts. We discussed widgets, state management, routing, networking, asynchronous programming, gesture detection, animation, theming, internationalization, and dependency injection. We also provided code examples to help illustrate each concept. If you haven’t installed the Flutter SDK yet, you can use FlutLab, an online Flutter development environment, to test your app and experiment with the concepts covered in this tutorial.

**Widgets: These are the basic building blocks of a Flutter app. They are responsible for creating the visual elements of an app, such as buttons, text, and images.


```
// Example of a simple button widget
class MyButton extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return RaisedButton(
      onPressed: () {
        print('Button pressed!');
      },
      child: Text('Press Me'),
    );
  }
}

```

> This code is an example of creating a simple button widget in Flutter. It is a StatelessWidget which means it will not store any mutable state and it will only depend on the configuration passed to it.

> The MyButton class extends the StatelessWidget class and overrides the build method. The build method returns a RaisedButton widget which is a built-in widget in Flutter.

> The RaisedButton widget takes two arguments, the onPressed callback and the child widget, the child is the Text widget that will be displayed inside the button. The onPressed callback is a function that is called when the button is pressed and it is responsible for handling the button press event.


**State Management: This refers to how an app maintains and updates its state. In Flutter, the recommended way of managing state is to use the setState method, which allows you to update the state of a widget and rebuild it as needed.


```
// Example of managing state with setState
class MyCounter extends StatefulWidget {
  @override
  _MyCounterState createState() => _MyCounterState();
}

class _MyCounterState extends State<MyCounter> {
  int _count = 0;

  void _incrementCounter() {
    setState(() {
      _count++;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Column(
      children: [
        Text('Count: $_count'),
        RaisedButton(
          onPressed: _incrementCounter,
          child: Text('Increment'),
        ),
      ],
    );
  }
}

```

> In this example, we have a MyCounter widget that displays a count and a button to increment the count. The MyCounter widget is a StatefulWidget which means that it stores mutable state. To manage the state, we create a separate _MyCounterState class which extends State <MyCounter> and stores the count as an instance variable.

> The _incrementCounter method is called when the button is pressed and it uses the setState method to update the count and rebuild the widget. The setState method takes a callback function that modifies the state and schedules a rebuild of the widget.

> The build method is responsible for creating the visual elements of the widget and it uses the current count to display the text.

**Routing: This refers to how an app navigates between its different pages or screens. In Flutter, the recommended way of managing routing is to use the Navigator widget, which allows you to push and pop pages from a stack.

``` 
// Example of managing routing with Navigator
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      initialRoute: '/',
      routes: {
        '/': (context) => FirstPage(),
        '/second': (context) => SecondPage(),
      },
    );
  }
}

class FirstPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('First Page')),
      body: Center(
        child: RaisedButton(
          onPressed: () {
            Navigator.pushNamed(context, '/second');
          },
          child: Text('Go to Second Page'),
        ),
      ),
    );
  }
}

class SecondPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Second Page')),
      body: Center(
        child: RaisedButton(
          onPressed: () {
            Navigator.pop(context);
          },
          child: Text('Go Back'),
        ),
      ),
    );
  }
}

```

> In this example, we use the MaterialApp widget to configure the routing in our app. We specify the initialRoute and the routes map. The initialRoute is the first screen that will be shown when the app starts, and the routes map defines the mapping between the route names and the corresponding widgets.

> In the MyHomePage widget, we use the Navigator.pushNamed method to navigate to the /settings route, which corresponds to the MySettingsPage widget.

> In the MySettingsPage widget, we use the Navigator.pop method to navigate back to the previous screen.

> The Navigator widget uses a stack-based navigation model, where each new screen is pushed onto the top of the stack, and the back button pops the top screen from the stack. Also, you can use Navigator.push and Navigator.pushReplacement to navigate between pages, this way you can use the MaterialPageRoute class instead of using the routes map.


**Networking: This refers to how an app retrieves data from a remote server. In Flutter, you can use the http package to make HTTP requests and receive responses.

```
// Example of making a GET request
import 'package:http/http.dart' as http;

class MyAPI {
  static Future<http.Response> getData() async {
    final response = await http.get('https://example.com/data');
    return response;
  }
}

```

> This code is an example of how you can use the http package to make a GET request to a server. In this example, we create a MyAPI class that has a getData method which uses the http.get method to make a GET request to the specified URL. It returns a Future<String> which will contain the response body if the request was successful or an exception if there was an error.

> In the MyHomePage widget, we use the FutureBuilder widget to handle the response from the API. The FutureBuilder widget takes a Future and a builder function as arguments. The builder function is called with the current state of the future and it can return different widgets based on the state.

> If the future has data, it will return a Text widget with the data, if the future has an error it will return a Text widget with the error message. If the future is still waiting for the response it will return a CircularProgressIndicator widget.

**Asynchronous Programming: This refers to how an app can perform multiple tasks at the same time and handle their results. In Flutter, you can use the async and await keywords to write asynchronous code.


```
// Example of using async/await
class MyAsyncTask extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return RaisedButton(
      onPressed: () async {
        final response = await MyAPI.getData();
        print(response.body);
      },
      child: Text('Fetch Data'),
    );
  }
}

```

> In this example, we have a _getData method that is marked as async which means that it can return a Future. Inside the method, we use the await keyword to wait for the Future.delayed method to complete, this simulates a delay of 2 seconds.

> In the build method of the MyHomePage widget, we use the FutureBuilder widget to handle the response from the _getData method, it works the same way as the previous example.

> The async and await keywords make it easy to write asynchronous code that is easy to read and understand. They allow you to write asynchronous code in a way that looks and behaves like synchronous code.

> It’s worth mentioning that there are other ways of handling async code in Flutter like using Streams or Futures, but async/await is the recommended and most widely used way.


**Gesture Detection: This refers to how an app can detect and respond to user gestures such as taps and swipes. In Flutter, you can use the GestureDetector widget to detect gestures and call callbacks.

``` 
// Example of gesture detection
class MyGestureDetector extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return GestureDetector(
      onDoubleTap: () {
        print('Double tap detected!');
      },
      child: Container(
        width: 100,
        height: 100,
        color: Colors.green,
      ),
    );
  }
}

```

> In this example, we use the GestureDetector widget to detect a tap gesture on a blue container. The GestureDetector widget takes a child and an onTap callback function as arguments. The child is the widget that will be rendered inside the GestureDetector widget, in this case, it's a blue container with a text "Tap me" in the center. The onTap callback is a function that will be called when the container is tapped, in this example it's a simple print statement, but you can handle the tap gesture in a more complex way.

> The GestureDetector widget can handle many other types of gestures like onDoubleTap, onLongPress, onScaleEnd and onScaleStart, etc.

**Animation: This refers to how an app can create visual effects and animations. In Flutter, you can use the Animation and Animated widgets to create animations, as well as the AnimationController to control the animation's behavior.


```

// Example of a simple animation
class MyAnimatedContainer extends StatefulWidget {
  @override
  _MyAnimatedContainerState createState() => _MyAnimatedContainerState();
}

class _MyAnimatedContainerState extends State<MyAnimatedContainer>
    with SingleTickerProviderStateMixin {
  AnimationController _controller;
  Animation _animation;

  @override
  void initState() {
    super.initState();
    _controller = AnimationController(
      vsync: this,
      duration: Duration(seconds: 1),
    );
    _animation = Tween<double>(begin: 0, end: 1).animate(_controller);
  }

  @override
  Widget build(BuildContext context) {
    _controller.forward();
    return AnimatedBuilder(
      animation: _animation,
      builder: (context, child) {
        return Container(
          width: _animation.value * 100,
          height: _animation.value * 100,
          color: Colors.green,
        );
      },
    );
  }
}

```

> The code above is an example of how to create and control a simple animation in Flutter using the Animation and AnimatedBuilder classes.

> In the _MyHomePageState class, an AnimationController object _controller is created and a Tween animation object _animation is created and linked to the controller. The Tween animation object is used to define the range of the animation, in this case, it's from 0 to 1.

> In the initState method, the AnimationController is initialized with a duration of 2 seconds and the Tween animation is linked to the controller.

> In the build method, an AnimatedBuilder widget is used to build the animation. The AnimatedBuilder widget takes an animation and a builder function as arguments. The animation is the animation that is being controlled, in this case, it's _animation and the builder function is called with the current value of the animation and it returns a widget that is affected by the animation.

> In this example, we’re using Transform.scale widget and we're scaling it by the animation value, this will result in the Flutter logo scaling up from 0 to 1 over the course of 2 seconds.

> A FloatingActionButton is added to the screen, the button will be used to start the animation when pressed.

**Theming: This refers to how an app can change its appearance based on a set of predefined styles. In Flutter, you can use the Theme widget to define and apply a theme to your app.


```
// Example of a theme
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      theme: ThemeData(
        primarySwatch: Colors.green,
        textTheme: TextTheme(
          headline1: TextStyle(
            color: Colors.white,
            fontSize: 24,
            fontWeight: FontWeight.bold,
          ),
        ),
      ),
      home: MyHomePage(),
    );
  }
}

```

> In this example, we create a ThemeData object and set its properties to define the visual style of the app.

> The primarySwatch property is set to Colors.blue, which will be the primary color used throughout the app. The visualDensity property is set to VisualDensity.adaptivePlatformDensity, this adjusts the layout of widgets to match the platform density.

> The textTheme property is set to a TextTheme object, which allows you to define the styles of different text elements in the app. In this example, we're setting the styles for headline1, headline6 and bodyText2 text elements.
Once the theme is created, it is passed to the MaterialApp widget as the theme property. This will apply the theme to the entire app, so that all the widgets in the app will use the styles defined in the theme.
It’s worth mentioning that you can also use the Theme.of(context) method to access the current theme from anywhere in the app. This allows you to change the theme dynamically at runtime.
Overall, Theming in Flutter allows you to easily define the visual style of your app, and apply it consistently throughout the app. It’s an essential feature for creating polished and professional-looking apps.

**Internationalization: This refers to how an app can support multiple languages and cultures. In Flutter, you can use the intl package to handle translations and localization.

```
// Example of internationalization
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      localizationsDelegates: [
        GlobalMaterialLocalizations.delegate,
        GlobalWidgetsLocalizations.delegate,
      ],
      supportedLocales: [
        Locale('en', 'US'),
        Locale('fr', 'FR'),
      ],
      home: MyHomePage(),
    );
  }
}

```

> In this example, the localizationsDelegates property of the MaterialApp widget is set to a list of localization delegates. These delegates provide the localized resources for the app. The supportedLocales property is set to a list of supported locales for the app, in this case, US English and French.

> You can also use the Intl.message function to translate messages:

```
String greeting(String name) => Intl.message(
  'Hello, $name!',
  name: 'greeting',
  args: [name],
  desc: 'A greeting for the user',
);

```

**Dependency Injection: This refers to how an app can manage its dependencies and make them easily testable. In Flutter, you can use a dependency injection library like flutter_injector to handle the instantiation and management of dependencies.

```
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    // Register our dependencies
    getIt.registerSingleton<MyDependency>(MyDependency());

    return MaterialApp(
      home: MyHomePage(),
    );
  }
}

class MyHomePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    // Retrieve our dependency
    final myDependency = getIt<MyDependency>();

    return Scaffold(
      appBar: AppBar(title: Text('Home Page')),
      body: Center(
        child: Text(myDependency.greeting),
      ),
    );
  }
}

class MyDependency {
  String get greeting => 'Hello from MyDependency';
}

```

> In this example, the Injector widget is used to define the dependencies that are available to the app. The inject property is set to a list of Inject objects, each of which defines a dependency and the function to create it. The MyService is registered as a dependency and will be created with MyService() constructor.

> The MyHomePage class is dependent on MyService, so it's passed as a required parameter in the constructor. This way, the MyService object is injected into the MyHomePage class, so it can use it to get data.
By using dependency injection, you can ensure that your code is more modular, testable and maintainable. It also allows you to easily swap out dependencies for testing or other purposes.

> In conclusion, this article covered a variety of concepts in Flutter development, including widgets, animations, themes, internationalization, and dependency injection. These concepts are essential for building professional and polished apps in Flutter.

> I hope that this article was helpful in providing you with a deeper understanding of these concepts and how they can be used in a Flutter app. Remember that as you continue to develop apps with Flutter, you don’t need to know everything from the start. It’s normal to have questions and to keep learning as you go. The most important thing is to keep practicing and building apps.

> In the next article, we will start building apps with the knowledge we have gained. It’s important to remember that the more you practice and build, the better you will get. So, don’t be afraid to dive in and start building your own apps. Remember that it’s always okay to ask for help and to seek out resources to learn more. Happy coding!

