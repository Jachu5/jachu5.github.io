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

**Compilador**
Cunado investigué sobre Kotlin me llamó la atención su compiladore, hasta ese entonces no sabía nada de como funcionaban los compilador de los lenguajes que funcionan sobre Java. Compilar proyectos mixtos, y en le caso de Kotlin, requiere que que Kotlin deba entender los ficheros fuentes de Java y sus binarios, y Java los ficheros fuentes de Kotlin y sus binarios. La idea de que el compilador de Kotlin entienda los ficheros fuente de Java es facil de imaginar, pero hacer que javac, el compilador de java, entienda los los ficheros fuentes de Kotlin es claramente imposible.

Actualmente el estado de los compiladores es el siguiente:
- *Groovy*:
Groovy genra stubs a partir del código, esto significa que los archivos fuente de Java contienen solo las declaraciones de las clases de Groovy, métodos y campos. A continuación ejecuta javac en los stubs y los archivos fuentes Java.
Como resultado todo compila, pero los métodos de Groovy no tienen cuerpo, para solucionar esto a continuación se ejecuta el compilador de Groovy y reemplaza las clases de los stubs.
Esto tiene una gran pega, el tiempo y la complejidad.

- *Scala and Kotlin*:
Ambos lenguajes enseñan a sus compiladores a enteder los archivos fuente de Java, así que ambos pueden generar los *.class y ejecutar javac sobre ellos.

**Compiler**
During my Kotlin research it called my attention its compiler, so far I didn't know anything about JVM based programming languages.
To compile mixed projects, in our case Kotlin, requires it to understand source Java files and its binaries, it also requires Java to understand Kotlin source files and it binaries. The idea of Kotlin compiler to understand Java source files is easy to imagine, but the opposite thing, to make the javac, the Java compiler, to understand Kotlin files is hard.

So far the start of the art if the following.
- *Groovy*:
Groovy genereates stubs from the code, this means the Java source files contains only Groovy classes, methods and fileds declarations, later on it executes javac over the stubs and the Java source files. As a result everything compiles, but the Groovy methods has no body yet, to solve this issue it execute the Groovy compiler and replace the classes contained on the stubs.
This process have a drawback, time and complexity.

- *Scala and Kotlin*:
Both languajes teach their compilers to understand Java source files, so both can generate the *.class files and execute javac over them.

## Caracterisiticas:
*Tipado Estático*
*Null Safety*
*Nombre y argumentos opcionales*
*Soporte para Lambdas*
*Data Objects*
*Singletons usando object notation*
*Traits*
*Extension Fuctions*


## PASAO 1

### PASO 1.1:

#### **Paso 1.1.1**


```
$ CODE
```

##### Paso 1.1.1.1:



#### **Paso 1.1.2**

#### **Paso 1.1.3**


## PASO 2

## Referencias:

* Nanme Ref: [http://url.com/](http://url.com/ "Url").
