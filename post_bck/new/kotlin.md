---
title: Kotlin
name: kotlin
---
Hace unos mese, en la Droidcon 2015 en Madrid, en varias charlas de Antonio Leiva [Antonio Leiva](http://antonioleiva.com/) se habló de un lenguaje de programación que me llamó mucho la atención, Kotlin. Ya había oido hablar de él pero no tan en profundidad, así que me puse a investigar y hacer alguna que otra prueba, lo cierto es que me llamó mucho la atención por su curva de aprendizaje, muy rápida y amena, y sus orientación funcional. Como siempre me gustaría avisar que soy un primerizo con Kotlin así que cualquier aclaración será bienvenida, por ahora solo he realizado alguna pruebas basadas en sus koans de introducción que podéis encontrar en el enlace mas abajo, ¡espero que os sea de utilidad!.
- Kotlin [Koans](http://kotlinlang.org/docs/tutorials/koans.html).
- Primer bloque de introducción resulto en [github](https://github.com/Jachu5/Koans).

Kotlin es creado por Jetbrain, la compañia detrás de IntelliJ, y corre sobre la máquina virtual de Java, luego hablaremos más en profundidad sobre esto, es un lenguaje orientado a objetos y como hemos mencionado tiene algunas ideas que vienen de la programación funcional.

**Por que Kotlin me gusta**
- Su curva de aprendizaje es muy ráìda, todo el mundo compara Kotlin con Scala, y pese a ser primerizo con mabos, encuentro la Kotlin mas sencilla, eso si, encutro Kotlin mas limitado que Scala.
- Es ligero, la librería de Kotlin para Android ocupa 1073KB.
- Ofrece muy buena interoperabilidad con Java.
- Se esta posicionando como una alternativa real para Java en Android en la comunidad, pero no debemos olvidar de que Kotlin aún es una versión beta.
- Seguramente Kotlin tenga un gran soporte por parte de Jetbrains ya que tienen un gran interes en su éxito, cunato mas lejos llegue y dado su sencillez de integración con IntelliJ, más licencias de este último venderan, por lo tanto no me parece que vayan a abandonar el proyecto.
- Otro factor importante a mi entender es que no hay un claro sucesor para Java, han aparecido muchos lenguajes que ofecen características como closures, modularidad, características funcionales pero ninguno se ha posicionado aún. Kotlin además de todo eso ofrece soporte por parte de Jetbrains y [reification](https://en.wikipedia.org/wiki/Reification_(computer_science), para saber sobre esto último recomiendo este [post](http://gafter.blogspot.com.es/2006/11/reified-generics-for-java.html).

**Compilador**
Cunado investigué sobre Kotlin me llamó la atención su compiladore, hasta ese entonces no sabía nada de como funcionaban los compilador de los lenguajes que funcionan sobre Java. Compilar proyectos mixtos, y en le caso de Kotlin, requiere que que Kotlin deba entender los ficheros fuentes de Java y sus binarios, y Java los ficheros fuentes de Kotlin y sus binarios. La idea de que el compilador de Kotlin entienda los ficheros fuente de Java es facil de imaginar, pero hacer que javac, el compilador de java, entienda los los ficheros fuentes de Kotlin es claramente imposible.

Actualmente el estado de los compiladores es el siguiente:
- *Groovy*:
Groovy genra stubs a partir del código, esto significa que los archivos fuente de Java contienen solo las declaraciones de las clases de Groovy, métodos y campos. A continuación ejecuta javac en los stubs y los archivos fuentes Java.
Como resultado todo compila, pero los métodos de Groovy no tienen cuerpo, para solucionar esto a continuación se ejecuta el compilador de Groovy y reemplaza las clases de los stubs.
Esto tiene una gran pega, el tiempo y la complejidad.

- *Scala and Kotlin*:
Ambos lenguajes enseñan a sus compiladores a enteder los archivos fuente de Java, así que ambos pueden generar los *.class y ejecutar javac sobre ellos.

## Caracterisiticas:
*Tipado Estático*
*Java compatible*
*Null Safety*
*Nombre y argumentos opcionales*
*Soporte para funciones de alto nivel*
*Extension de funciones*
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
