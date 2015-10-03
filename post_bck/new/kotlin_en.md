---
title: Kotlin
name: kotlin
---
Some weeks ago, at the Droidcon 2015 in Madrid, several lecturers like Antonio Leiva [Antonio Leiva](http://antonioleiva.com/), talked about a programming language that called my attention, Kotlin. I had already heard about Kotlin but not in detail, so I started a research and I did some demos, the result was good, I really liked it, its learning curve is surprisingly easy and fast and its functional components are really interesting.

Kotlin is created and maintained by Jetbrains, the company behind IntelliJ, and it runs on the JVM (Java Virtual Machine). It is an object oriented language and as I mentioned before, it has some functional aspects which make it a very interesting Java alternative.


**Why I like Kotlin**
- Its learning curve is fast, everybody compares Kotlin with Scala, I am a beginner with both so make a comparison is hard but I find Kotlin easier and maybe also more limited than Scala.
- It is lightweight; the Kotlin library is only 1073KB.
- It offers a good Java interoperability.
- It is becoming a real Java alternative to the Android community, I have not tried yet the Android version, but programmers are really excited with it.
- Probably Kotlin will have a great support by Jetbrains, if Kotlin is successful they will sell more licenses of their IDE given their easy integration.
- To this day, there is not a real Java successor, a lot of JVM based languages have emerged which offers different interesting characteristics such closures, modularity, functional components, but no one has reached the throne yet. Kotlin offers all those aspects but also Jetbrains supports and [reification](https://en.wikipedia.org/wiki/Reification_(computer_science), to know more about reification visit this [post](http://gafter.blogspot.com.es/2006/11/reified-generics-for-java.html).

##Installation
Very simple, Jetbrain people have done really nice.
Requirements:
1. IntelliJ 14.1 or newer, it also works with Andorid Studio:  [IntelliJ IDEA Minimal Survival Guide](http://hadihariri.com/2014/01/06/intellij-idea-minimal-survival-guide/).
	You can download it from [downloads](https://confluence.jetbrains.com/display/IDEADEV/IDEA+14.1+EAP) from Jetbrains.
2. JDK 1.6 or superior: You can download it from the official web page  [Oracle](http://www.oracle.com/technetwork/java/javase/downloads/index.html), or maybe you prefer to use this fantastic tutorial  [JVM Minimal Survive Guide](http://hadihariri.com/2013/12/29/jvm-minimal-survival-guide-for-the-dotnet-developer/)
3. Kotlin plugin: You can download it from the IDE, just open IntelliJ and go: File -> Plugins and search ==Kotlin==.
4. Done :).

**Compiler**
Kotlin called my attention for its compiler, so far I didn't know anything about JVM based programming languages so it was very interesting what I found .
To compile mixed projects, in our case Kotlin, requires it to understand the Java source files and its binaries, it also requires Java to understand the Kotlin source files and it binaries. The idea of Kotlin compiler to understand Java source files is easy to imagine, but the opposite thing, to make the javac (Java compiler) to understand Kotlin files is hard.

So far the state of the art is the following.
- *Groovy*:
Groovy generates stubs from the code, this means the Java source files contains only Groovy classes, methods and fields declarations, later on it executes javac over the stubs and the Java source files. As a result everything compiles, but the Groovy methods has no body yet, to solve this issue it executes the Groovy compiler and replace the classes contained inside the stubs.
This process has some drawbacks, time and complexity.

- *Scala and Kotlin*:
Both languages teach their compilers to understand the Java source files, so both can generate the *.class files and execute javac over them.


## Characteristics:
###### Java interoperabilty
Kotlin was designed with interoperability in mind, and they achieved it! I didn’t try it too much, just some test code doing the koans and seems really easy to understand and to implement in both sides, from Kotlin and from Java.

Here the documentation is very clear so I recommend taking a look to it.

More information on the [Official page](http://kotlinlang.org/docs/reference/java-interop.html) or you can check the resolved koan in [Github](https://github.com/Jachu5/Koans/tree/master/src/i_introduction/_5_Nullable_Types)


###### Null Safety
This is one of my favorite characteristics that solves one of the most disgusting problem when programming, the null reference.
Null in Kotlin is a "first-class citizen" in its type system, in other words, types are aware that they can be null. In my opinion this is very useful since the NullPointerException in Java is something really nasty and evolves into a lot of boilerplate code and defensive programming.

Kotlin can make distinction between those types that can make a reference to null and those that cannot.

```
var a: String = "abc"
a = null // compilation error
val l = a.lenght() // this will no generate a NullPointerException
```
We can make a type "nullable"
```
var b: String? = "abc"
b = null // ok
val l = b.length() // Now this can generate a NullPointerException so it will no compile.
```

But if you really want to deal with null, Kotlin gives us different ways to check any possible null reference:

- Using explicit check:
	The compiler detects that has been a null check and you can saftly call the `lenght()` function.
```
if ( b!= null){
	b.lenght()
}
```
- Safe Calls
    Using the operator `?`, this will return the value of the function `lenght()`, and null otherwise.
    ```
    b?.length()
    ```
   And you can make chains like this:
    ```
    inbox?.email?.message
    ```
- Operador Elvis "?:"
	Similar to the Groovy's one, both expresion are the same:
     ```
     val l: Int = if (b != null) b.length() else -1
     val l = b?.length() ?: -1
     ```
     If the exression to the left of `?:` is null it returns the value, otherwise it **evaluaes** and returns the right-hand expression.

More information on the [Official page](http://kotlinlang.org/docs/reference/java-interop.html) or you can check the resolved koan in my [Github](https://github.com/Jachu5/Koans/tree/master/src/i_introduction/_5_Nullable_Types)

###### High order function and Lambdas support
I love it.
Basically a high order function is a function that can take other functions as parameters o it can return another function, here you got and example
 ```
list.filter {it % 2 == 1}
 ```
In the example a list is filtered removing all the even elements, it uses a predefined function `filter` which you can pass any other function as an argument `it % 2 == 1` and will be applied to the whole collection.

Probably the easiest way to understand it reading the [Official documentation](http://kotlinlang.org/docs/reference/lambdas.html)and checking the resolved koan [Github](https://github.com/Jachu5/Koans/blob/master/src/i_introduction/_3_Lambdas/Lambdas.kt)

###### Data Classes
Very useful, data classes are those which only exist to store information, Data Classes will generate certain functionalities such as equals(), hasCode(), toString or copy function, Currently Google offers the AutoValue library wich do the same [AutoValue](https://github.com/google/auto/tree/master/value).

```
data class Money(val currency: String, val amount: Int)
val money = Money("USD", 100)
val moreMoney = money.copy(amount = 200)

```
We can declare default values, so we don't need to declare different constructors.
```
data class Money(val currency: String = "Euro", val amount: Int = 0)
```
And we have Multi-declarations:
```
val jane = User("Jane", 35) 
val (name, age) = jane
println("$name, $age years of age") // Imprime "Jane, 35 years of age"

```
More information on the [Official page](http://kotlinlang.org/docs/reference/data-classes.html) or you can check the resolved koan in [Github](https://github.com/Jachu5/Koans/tree/master/src/i_introduction/_7_Data_Classes)


###### Traits
You can understand Traits as interfaces where you can implement functions, I have no example since I only know them from Scala and since then I really miss them in my daily work, you have got more info in this [post](http://blog.jetbrains.com/kotlin/2011/08/multiple-inheritance-part-2-possible-directions/).

###### Extension Fuctions######
Kotlin allows to extend the functionalities of any class (Kotlin or Java) with no heritage, just using the "extension" declaration, this members are introduced in a static way and make us to forget the "Utils" classes full of static functions, this way we obtain a cleaner code.

````
fun String.last() : Char {
  return this[length - 1]
}
val x = "Hey!"
println(x.last()) // Prints "!".

```
Reading about this I discovered that other languages like C# also implements this functionality.

More information on the [Official page](http://kotlinlang.org/docs/reference/extensions.html) or you can check the resolved koan in [Github](https://github.com/Jachu5/Koans/tree/master/src/i_introduction/_8_Extension_Functions)

## Conclusion
To be honest, as I mentioned before, my adventure with Kotlin has been short, I only made some programming doing the koans but I a really like it and I think it gives new opportunities to Java.
I hope you like the post and thank for reading it!


