## Flutter Tutorial Part 2

![Flutter Image](https://miro.medium.com/v2/resize:fit:720/format:webp/1*BYsAMRy4iZF8vj1yB2D9xA.png)

> In this tutorial, you will learn about the Dart programming language and how it can be used to build web, mobile, and desktop applications. You will learn about the key concepts and features of Dart, including variables, functions, classes, control structures, and asynchronous programming.

> By the end of this tutorial, you should have a basic understanding of the Dart language and be able to write simple programs using various features of the language. You should also have a good foundation to build upon as you continue learning and exploring the capabilities of Dart.

> Dart is a programming language developed by Google that is used to build web, mobile, and desktop applications. It is designed to be easy to learn, with a syntax that is familiar to anyone who has worked with Java or C#.

> One of the key features of Dart is its support for both object-oriented and functional programming styles. This allows developers to use the approach that best fits their needs, whether that be writing classes and objects or using functions and immutable data.

> One of the main advantages of using Dart is that it can be compiled to run on both the server and the client side. This means that you can use it to build web applications that run in the browser, as well as mobile and desktop apps that run natively on various platforms.


### Installation

To install Dart on your local machine, you can follow these steps:Here are some key concepts in Dart:

1. Go to the official Dart website at [Dart](https://dart.dev/)
2. Click on the “Get Dart” button in the top right corner of the page.
3. On the next page, click on the “Download” button under the “Dart SDK” section.
4. Select the appropriate version of Dart for your operating system and download the installer.
5. Run the installer and follow the prompts to complete the installation process.

Alternatively, you can use an online Dart editor such as DartPad to try out Dart without installing it on your local machine. To use DartPad, simply go to [dartpad](https://dartpad.dartlang.org/) and start writing and running code in the browser.

### Dart Basic Concepts

Once you have installed Dart or are using an online editor, you can start writing and running Dart programs by following the instructions in the documentation or other tutorials.

**Variables** : Variables are used to store data in a program. Dart has support for various data types, including numbers, strings, and booleans. Here is an example of declaring and initializing variables in Dart:

```
int age = 30;
double temperature = 72.5;
bool isRainy = true;
String name = 'John';
```

**Functions**: Functions are blocks of code that perform a specific task and can be called from other parts of the program.


Here is an example of a function in Dart:

```
void printHello() {
  print('Hello, World!');
}

```

**Classes and objects**: Dart supports object-oriented programming through the use of classes and objects. A class is a blueprint for creating objects, and an object is an instance of a class.


*Here is an example of a class in Dart*:

```
class Person {
  String name;
  int age;

  Person(this.name, this.age);

  void printInfo() {
    print('Name: $name, Age: $age');
  }
}

```

**Control structures**: Dart has various control structures for controlling the flow of a program, including if statements, for loops, and while loops.


Here is an example of an if statement in Dart:

```

if (age < 18) {
  print('You are not old enough to vote.');
} else {
  print('You are old enough to vote.');
}

```

**Exceptions**: Dart has support for exception handling, which allows you to handle errors and exceptions that may occur during the execution of a program.


*Here is an example of try-catch block in Dart*:

```
try {
  int result = 12 ~/ 0;
  print(result);
} catch (e) {
  print('Caught exception: $e');
}

```


**Async programming**: Dart has support for asynchronous programming through the use of the async and await keywords. Async programming allows you to perform long-running tasks in the background without blocking the main thread of execution. Here is an example of an async function in Dart:

```
Future<int> fetchData() async {
  await Future.delayed(Duration(seconds: 3));
  return 42;
}

```

These are just a few examples of the concepts and features available in Dart. It is a versatile language with a wide range of tools and libraries for building a variety of applications.



### More Examples

Here is a simple example of a Dart program that defines a function and calls it:


```
void main() {
  printHello();
}

void printHello() {
  print('Hello, World!');
}

```

In this example, the main function is the entry point of the program. It calls the printHello function, which simply prints the string "Hello, World!" to the console.

*Here is an example of using variables*:

```
void main() {
  int age = 30;
  double temperature = 72.5;
  bool isRainy = true;
  String name = 'John';

  print('Age: $age');
  print('Temperature: $temperature');
  print('Is it rainy? $isRainy');
  print('Name: $name');
}

```

In this example, we declare and initialize variables for an integer, a double, a boolean, and a string. We then print these values to the console using string interpolation.

*Here is an example of a simple class in Dart*:

```

class Person {
  String name;
  int age;

  Person(this.name, this.age);

  void printInfo() {
    print('Name: $name, Age: $age');
  }
}

void main() {
  Person person = Person('John', 30);
  person.printInfo();
}

```

In this example, we define a Person class with a name and age field, and a printInfo method that prints the name and age of the person. We then create an instance of the Person class and call the printInfo method on it.

Dart also has a rich standard library that provides a wide range of functionality, including support for asynchronous programming, file I/O, and working with HTTP.

Overall, Dart is a powerful and versatile programming language that is well-suited for building a wide range of applications. Whether you are building a web, mobile, or desktop app, Dart provides the tools and features you need to get the job done.



1. **A Calculator App**

```

import 'dart:io';

void main() {
  print('Welcome to the calculator app!');
  print('Enter an operator (+, -, *, /) followed by two numbers:');

  var input = stdin.readLineSync();
  var parts = input.split(' ');
  var operator = parts[0];
  var num1 = int.parse(parts[1]);
  var num2 = int.parse(parts[2]);
  var result;

  switch (operator) {
    case '+':
      result = num1 + num2;
      break;
    case '-':
      result = num1 - num2;
      break;
    case '*':
      result = num1 * num2;
      break;
    case '/':
      result = num1 / num2;
      break;
    default:
      print('Invalid operator');
      return;
  }

  print('Result: $result');
}

```


In this example, we use the stdin.readLineSync function to read input from the user. We then split the input string into individual parts using the split function, and parse the operator and operands as variables.

Next, we use a switch statement to evaluate the operator and perform the appropriate calculation. Finally, we print the result to the console.

This is a very basic example of a calculator app, but it demonstrates how you can use Dart to build a simple command-line application that takes input from the user and performs calculations.


2. **Bookstore Inventory Manager**

Here is an example of a program in Dart that uses a variety of concepts and features:

```

import 'dart:async';
import 'dart:io';

class Book {
  String title;
  String author;
  int pages;
  double price;
  bool isHardcover;

  Book(this.title, this.author, this.pages, this.price, this.isHardcover);
}

class BookStore {
  String name;
  List<Book> books;

  BookStore(this.name, this.books);

  Future<void> printInventory() async {
    print('Inventory for $name:');
    for (var book in books) {
      print('${book.title} by ${book.author}');
    }
  }

  void addBook(Book book) {
    books.add(book);
  }

  void removeBook(Book book) {
    books.remove(book);
  }
}

void main() {
  var book1 = Book('The Great Gatsby', 'F. Scott Fitzgerald', 180, 9.99, true);
  var book2 = Book('To Kill a Mockingbird', 'Harper Lee', 280, 12.99, false);
  var book3 = Book('Pride and Prejudice', 'Jane Austen', 250, 11.99, true);

  var books = [book1, book2, book3];
  var bookstore = BookStore('My Bookstore', books);

  bookstore.printInventory().then((_) {
    bookstore.addBook(Book('Moby-Dick', 'Herman Melville', 752, 19.99, false));
    bookstore.printInventory().then((_) {
      bookstore.removeBook(book2);
      bookstore.printInventory();
    });
  });
}

```


In this example, we define a Book class with fields for the title, author, number of pages, price, and whether or not it is a hardcover book. We also define a BookStore class with a name and a list of books. The BookStore class has methods for printing the inventory, adding a book, and removing a book.


In the main function, we create instances of the Book class and add them to a list. We then create an instance of the BookStore class and pass it the list of books.


We call the printInventory method of the BookStore class and use the then function to chain multiple calls to the method. In between each call, we use the addBook and removeBook methods to modify the inventory of the bookstore.


This example demonstrates how you can use classes, objects, lists, and asynchronous programming in Dart to build a program that handles complex data.
In this tutorial, we learned about the Dart programming language and how it can be used to build web, mobile, and desktop applications. We learned about the key concepts and features of Dart, including variables, functions, classes, control structures, and asynchronous programming.


We also saw examples of how these concepts and features can be used in Dart programs. We learned how to declare and initialize variables, define and call functions, create and use classes and objects, use control structures, and perform asynchronous tasks.


In future tutorials, we will explore how to use the Flutter framework to build user interfaces for mobile apps using Dart. Flutter is a popular mobile development framework developed by Google that allows you to build cross-platform apps for iOS and Android with a single codebase. We will see how to use Flutter’s customizable widgets and tools to build beautiful and functional UIs for your apps.


<script src="https://utteranc.es/client.js"
        repo="https://github.com/Santigio/Santigio.github.io"
        issue-term="url"
        label="Comment"
        theme="github-light"
        crossorigin="anonymous"
        async>
</script>
