---
title: Kotlin
name: kotlin
---
Hace no unas semanas, en la Droidcon 2015 en Madrid, en varias charlas, como la de de Antonio Leiva [Antonio Leiva](http://antonioleiva.com/) se habló de un lenguaje de programación que me llamó mucho la atención, Kotlin. Y a había oido hablar de él pero no tan en profundidad, así que me puse a investigar y hacer alguna que otra prueba, lo cierto es que me llamó mucho la atención por su curva de aprendizaje, muy rápida y amena, y sus orientación funcional. Como siempre me gustaría avisar que soy un primerizo con Kotlin así que cualquier aclaración será bienvenida, ¡espero que os sea de utilidad!.

Kotlin es creado por Jetbrain, la compañia detrás de IntelliJ, y corre sobre la máquina virtual de Java, luego hablaremos más en profundidad sobre esto, es un lenguaje orientado a objetos y como hemos mencionado tiene algunas ideas que vienen de la programación funcional.

A weeks ago, at Droidcon 2015 in Madrid, severeal specheers like Antonio Leiva [Antonio Leiva](http://antonioleiva.com/), talked about a programming wich call my attention, Kotlin. I have already heard about Kotlin but not in detail, so I start a research I did some demos, and the result was good, I really liked it, its learning curve is surprisingly easy and fast and its functional componentes are really interesting.

Kotlin is created and maintained by Jetbrains, the compnay behind IntelliJ, and it runs on the JVM (Java Virtual Machine), but will talk about it later. It is a object oriented language and as I mentioned before it has some functional aspects wich make it a very interesting Java alternative.

**Por que Kotlin me gusta**
- Su curva de aprendizaje es muy ráìda, todo el mundo compara Kotlin con Scala, y pese a ser primerizo con mabos, encuentro la Kotlin mas sencilla, eso si, encutro Kotlin mas limitado que Scala.
- Es ligero, la librería de Kotlin para Android ocupa 1073KB.
- Ofrece muy buena interoperabilidad con Java.
- Se esta posicionando como una alternativa real para Java en Android en la comunidad, pero no debemos olvidar de que Kotlin aún es una versión beta.
- Seguramente Kotlin tenga un gran soporte por parte de Jetbrains ya que tienen un gran interes en su éxito, cunato mas lejos llegue y dado su sencillez de integración con IntelliJ, más licencias de este último venderan, por lo tanto no me parece que vayan a abandonar el proyecto.
- Otro factor importante a mi entender es que no hay un claro sucesor para Java, han aparecido muchos lenguajes que ofecen características como closures, modularidad, características funcionales pero ninguno se ha posicionado aún. Kotlin además de todo eso ofrece soporte por parte de Jetbrains y [reification](https://en.wikipedia.org/wiki/Reification_(computer_science), para saber sobre esto último recomiendo este [post](http://gafter.blogspot.com.es/2006/11/reified-generics-for-java.html).

**Why I like Kotlin**
- Its learning curve is fast, everybody compares Kotlin with Scala, I am a begginer in btoh, but I find Kotlin easier but more limited than Scala.
- It is light, the Kotlin library is only 1073KB.
- It offer a good Java interoperability.
- It is becoming a real Java alternative to the Android comunity, I have not tried yet the Android version, but programmers are really exicited.
- Probably Kotlin will have a great support by Jetbrains, if Kotlin is successful they will sell more licenses of their IDE given their easy integration.
- To this day, there is not a real Java sucesor, a lot of JVM based languages have emereged which offers diferents interesting characteristics such closures, modularity, fuctional componentes, but no one has reached the throne yet. Kotlin offers all those aspects but also Jetbrains supports and [reification](https://en.wikipedia.org/wiki/Reification_(computer_science), to know more abot reification visit this [post](http://gafter.blogspot.com.es/2006/11/reified-generics-for-java.html).

##Instalación
Es muy sencillo, la gente de Jetbrain lo ha hecho muy bien.
Requerimientos:
1. Intellij 14.1 o Android Studio: [IntelliJ IDEA Minimal Survival Guide](http://hadihariri.com/2014/01/06/intellij-idea-minimal-survival-guide/).
	Puedes hacerlo desde la página de [descargas](https://confluence.jetbrains.com/display/IDEADEV/IDEA+14.1+EAP) de Jetbrains
2. JDK 1.6 o superior: Puedes hacerlo desde la página de [Oracle](http://www.oracle.com/technetwork/java/javase/downloads/index.html) o si estas muy perdido puedes recurrir al tutorial [JVM Minimal Survive Guide](http://hadihariri.com/2013/12/29/jvm-minimal-survival-guide-for-the-dotnet-developer/)
3. Plugin de Kotlin: Se puede hacer desde el propio IDE, abre IntelliJ: File -> Plugins, y busca ==Kotlin==, listo :).

##Installation
Very simple, Jetbrain people has done really nice.
Requirements:
1. IntelliJ 14.1 or newer, it also works with Andorid Studion:  [IntelliJ IDEA Minimal Survival Guide](http://hadihariri.com/2014/01/06/intellij-idea-minimal-survival-guide/).
	You can dowload it from [dowloads](https://confluence.jetbrains.com/display/IDEADEV/IDEA+14.1+EAP) from Jetbrains.
2. JDK 1.6 or superior: You can dowload it from the official web page  [Oracle](http://www.oracle.com/technetwork/java/javase/downloads/index.html), or maybe you prefer to use this fantastic tutorial  [JVM Minimal Survive Guide](http://hadihariri.com/2013/12/29/jvm-minimal-survival-guide-for-the-dotnet-developer/)
3. Kotlin plugin: Ypu can download it from the IDE, just open IntelliJ and go: File -> PLugins and search ==Kotlin==.
4. Done :).

**Compiler**
During my Kotlin research it called my attention its compiler, so far I didn't know anything about JVM based programming languages.
To compile mixed projects, in our case Kotlin, requires it to understand source Java files and its binaries, it also requires Java to understand Kotlin source files and it binaries. The idea of Kotlin compiler to understand Java source files is easy to imagine, but the opposite thing, to make the javac, the Java compiler, to understand Kotlin files is hard.

So far the start of the art if the following.
- *Groovy*:
Groovy genereates stubs from the code, this means the Java source files contains only Groovy classes, methods and fileds declarations, later on it executes javac over the stubs and the Java source files. As a result everything compiles, but the Groovy methods has no body yet, to solve this issue it execute the Groovy compiler and replace the classes contained on the stubs.
This process have a drawback, time and complexity.

- *Scala and Kotlin*:
Both languajes teach their compilers to understand Java source files, so both can generate the *.class files and execute javac over them.

## Characteristics:
###### Java interoperabilty
Kotlin was design with interoperability in mind, and they achived it! I dind't try it too much, just some test code doing the koans and seems really easy to understand and to implemend in btohs sides, from Kotlin and from Java.

Here the documentation is very clear so I recommend to take a look to the offical documentation.

More information on the [Official page](http://kotlinlang.org/docs/reference/java-interop.html) or you can check the resolved koan in my [Github](https://github.com/Jachu5/Koans/tree/master/src/i_introduction/_5_Nullable_Types)

###### Null Safety
Una de mis características favoritas y que soluciona uno de los problemas que más molestos me parecen, las referencias a null.

One of my favourity characteristics that solves one of the most disgusting problem when programming, the null reference.
Null in Kotlin is a "first-class citizen" in its type system, in other words, types are aware that they can be null. In my opinion this is very usefull since the NullPointerException in Java is somenthing really nasty and evolves into a lot of boilerplate code and defensice programming.

Kotlin can make distinction between those types that can make a reference to null a those which cannot.

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
	The compiler detects that has been a null check and you can saftly call the `lenght()`.
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
I love it,
Basiccally a high orer function is a function that can take other functions as paremeters o it can return another fucntion, here you got and example
 ```
list.filter {it % 2 == 1}
 ```
In the example a list is filtered removing all the even elements, it uses a predefined function `filter` which you cna pass any other function as an argument `it % 2 == 1` and will be applyed to the whole collection.

Probably the easiest way to understand it reading the [Official documentation](http://kotlinlang.org/docs/reference/lambdas.html)and checking the resolved koan [Github](https://github.com/Jachu5/Koans/blob/master/src/i_introduction/_3_Lambdas/Lambdas.kt)

###### Data Classes
Very usefull to classes those wich only exits to store information, Data Classes will generate certain functionallities such as equals(), hasCode(), toString or copy function, Currently Google offers the AutoValue library wich do the same [AutoValue](https://github.com/google/auto/tree/master/value).

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

Kotlin allows to extend the functionallities of any class (Kotlin or Java) with no heritage, just using the "extension" declaration, this members are introduced in a static way and make us to forget the "Utils" classes full of static functions, this way we obtaine a cleaner code.

````
fun String.last() : Char {
  return this[length - 1]
}
val x = "Hey!"
println(x.last()) // Prints "!".

```
Reading about this I discovered that other langueges like C# also implements this functionalliy.

More information on the [Official page](http://kotlinlang.org/docs/reference/extensions.html) or you can check the resolved koan in [Github](https://github.com/Jachu5/Koans/tree/master/src/i_introduction/_8_Extension_Functions)

## Conclusion
To be honest, as I mentioned before, my adventure with Kotlin has been short, a just made some programming doing the koans, I a really like it and I think it gives new opportunities if you compare it with Java.
I hope you like the post and thank for reaidng it!.



