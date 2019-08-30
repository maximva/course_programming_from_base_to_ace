---
description: This chapter introduces a hello world application in C#. As a reader you will get acquainted with the basic syntax of the C# programming language and you will develop your first small application.
title: 03 - Starting in C#
---

# Chapter 03 - Starting in C#

<!-- TODO
Maybe some general things about C#? -->

## Hello World

A "Hello World!" program is a computer program that outputs or displays "Hello World!" to the user. Being a **very simple program** in most programming languages, it is often used to **illustrate the basic syntax of a programming language** for a working program. It is often the very first program people write when they are new to the language.

![Hello World](./img/hello_world.jpg)

A "Hello world!" program is often used to **introduce novice programmers to a programming language**. In general, it is simple enough to be understood easily, especially with the guidance of a teacher or a written guide.

In addition, "Hello world!" can be a **useful sanity test** to make sure that a language's compiler, development environment, and run-time environment are correctly installed. Configuring a complete programming toolchain from scratch to the point where even trivial programs can be compiled and run can involve substantial amounts of work. For this reason, a simple program is used first when testing a new toolchain.

"Hello world!" is also used by computer hackers as a **proof of concept** that arbitrary code can be executed through an exploit where the system designers did not intend code to be executed - for example, on Sony's PlayStation Portable. This is the first step in using homemade content ("home brew") on such a device.

![Hello World on PSP](./img/psp_hello_world.jpeg)

## Hello World in C#

Let's jump right in and create a "Hello World" application in C#.

::: warning Naming Things
Naming things correctly is one of the main responsibilities of a programmer. By giving things (applications, variables, methods, ...) decent names, you will make your own life and that of fellow programmers a lot easier.
:::

Open Visual Studio and create a new project of the type `Console Application (.NET Core)`. Give it a sensible name such as `HelloWorld`.

![Creating a Console Application in .NET Core](./img/console_app_project_vs.png)

::: tip Console Applications
When developing applications a choice must be made between a GUI and a console application. As discussed earlier, a console application has no real graphical user interface and interacts with the user via the terminal (console). The default options for input and output are essentially text. This course will first focus on console applications after which it will introduce WPF allowing the creation of graphical applications.
:::

Once the wizard is finished it will automatically generate a basic "Hello World" application with the code shown below.

```csharp
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

Starting the application can be achieved by navigating to `Debug => Start Debugging` or by pressing `F5`. This will open a terminal windows and output the text `Hello World!` as shown below.

```text
Hello World!

C:\Program Files\dotnet\dotnet.exe (process 12088) exited with code 0.
To automatically close the console when debugging stops,
enable Tools->Options->Debugging->Automatically close the console when debugging stops.
Press any key to close this window . . .
```

Notice that the application terminates after outputting the text to the terminal. The window of the terminal stays open for our convenience, so the developer can see what was outputted to the terminal. The terminal can be closed by pressing a key on your keyboard.

## Dissecting Hello World

While not diving into many details here, there are however a couple of things which can be clarified about the code above.

### The Main Method

The most important part of this small C# application is the `Main()` method.

```csharp{7-8,10}
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

This piece of code needs to be in every C# application and is the start-point of your program. Without it, your program would not be able to be executed. It is often called the **entry-point of the application**.

The piece of code shown above is also more general known as a **method**. A method consists of some code that can be executed by **calling** it somewhere else in your application using the name of the method. Here the name of the method is `Main()`. Most of the applications that are used as examples in this chapter will contain code that needs to be placed inside this main method, between the curly braces `{}`, which is called the **body** of the method.

Do not worry to much about the keywords such as `static` and `void`. This course will explain these later.

Sometimes the code outside of the `Main()` method might not be shown in examples in this course. This because it will mostly stay the same (apart from the actual name of the application which will change if you create a new project).

### Output to Terminal

Applications often require information from the user (input) and return back some information to the user (output). This basic hello world application does not require input, but is does output some text to the console.

In code this is achieved by using the methods `Console.Write()` and `Console.WriteLine()`. Both display text to the console window. The difference between these two methods is that `Console.WriteLine()` follows the text with a line terminator, which moves the cursor to the next line.

```csharp{9}
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

Most lines of code such as `Console.WriteLine("Hello World!");` are called `statements`. A statement is an action that is performed in code, often acting on some part of data or information. In the example above, the information is a piece of text, namely "Hello World!". This piece of text is called a **String** in programming languages and they are most often specified between two quotes `"Placing some text between quotes makes it a string"`.

A statement is typically **terminated** using a semicolon `;`. By placing this at the end of a statement, the compiler knows that the line of code has ended.

The data `"Hello World!"` (in this case a piece of text) that is provided to the method `Console.WriteLine()` is called an **argument**. It is a piece of information that is passed to a method so it can be used inside the method - to be displayed, processed or handled in another way.

### Namespace

Basically a namespace is a **container that groups together resources**. What these resources are will be clarified later on. Namespace also allow developers to give resources the same name within different namespaces. There might for example be a resource `Rectangle` in the namespace `Geometry` as well as in the namespace `Graphics`. Without these namespaces these resource names would collide, leading to bad naming conventions to avoid these clashes.

```csharp{3-4,12}
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

To avoid collisions with the resources provided by .NET, the applications created in Visual Studio are automatically put into their own namespace, based on the name of the application. In this case, the `Program` class is put inside the namespace `HelloWorld`. More on namespaces later.

### Using

The `using System;` directive allows the usage of resources defined inside the `System` namespace.

```csharp{1}
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

By including the `System` namespace, the `Console.WriteLine()` method can be used as is. If one does not include the namespace, the **fully qualified name** would have to be used, which is `System.Console.WriteLine()`. If no collisions can arrise it is often a good idea to include the namespace for resources that are used a lot. It makes the code shorter.

### Class Program

A lot can be said about classes, as you'll see later on in this course. For the moment all you need to know is that this application defines a single class called `Program` with a single method called `Main()` and all the action is taking place in this method.

```csharp{5-6,11}
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

## Train Yourself

### Multiple Choice

1. How do we call a piece/line of code as shown below?

    ```csharp
    Console.Write("Sharpy says hi!");
    ```

    * A decision
    * A statement
    * A condition
    * A namespace

2. What is the entry point of a C# application ?

    * The `start()` method
    * The file `HelloWorld.cs`
    * The `Main()` method
    * The `Program` class

3. What is common use of a Hello World application ?

    * Proof of concept to show a device can run user code
    * To show that code is faster with a compiler
    * To check if your application contains bugs
    * Test if a programming language is object oriented

4. How do we call a line of code that performs a specific action and is terminated with a semicolon ?

    * A condition
    * A class
    * A method
    * A statement

5. Code in `Main()` is placed between ...

    * slashes `//`
    * curly brackets `{}`
    * parentheses `()`
    * brackets `[]`

6. The rectangle's (process step) in a flowchart will often map on ... in C#.

    * a condition
    * an escape sequence
    * a statement
    * a method

### Exercises and Challenges

Checkout the exercises and challenges which can be found at [https://github.com/BioBoost/csharp_practical](https://github.com/BioBoost/csharp_practical).