---
title: Kotlin
name: kotlin
---
Hace unos mese, en la Droidcon 2015 en Madrid, en varias charlas, y en especial una de Antonio Leiva [Antonio Leiva](http://antonioleiva.com/), se habló de un lenguaje de programación que me llamó mucho la atención, Kotlin. Ya había oído hablar de él pero no tan en profundidad, así que me puse a investigar y hacer alguna que otra prueba, y tras juguetar un poco con el me ha llamado la atención por su curva de aprendizaje, muy rápida y amena, y su orientación funcional. Como siempre me gustaría avisar que soy primerizo con Kotlin así que cualquier aclaración será bienvenida, por ahora solo he realizado algunas pruebas basadas en sus koans de introducción que podéis encontrar en el enlace mas abajo, ¡espero que os sea de utilidad!.
- Kotlin [Koans](http://kotlinlang.org/docs/tutorials/koans.html).
- Primer bloque de introducción resulto en [github](https://github.com/Jachu5/Koans).

Kotlin es creado por Jetbrain, la compañía detrás de IntelliJ, y corre sobre la máquina virtual de Java de lo que luego hablaremos más en profundidad, es un lenguaje orientado a objetos y como he mencionado antes tiene algunas ideas que vienen de la programación funcional.

**Por que Kotlin me gusta**
- Su curva de aprendizaje es muy rápida, todo el mundo compara Kotlin con Scala, y pese a ser primerizo con ambos, encuentro la Kotlin mas sencilla, eso si, creo que Kotlin es más limitado que Scala, pero también dependerá un poco de lo que busquemos.
- Es ligero, la librería de Kotlin para Android ocupa 1073KB.
- Ofrece muy buena interoperabilidad con Java.
- Se esta posicionando como una alternativa real para Java en Android dentro de la comunidad, pero no debemos olvidar de que Kotlin aún es una versión beta (por lo menos cunado empecé a escribir este post).
- Seguramente Kotlin tenga un gran soporte por parte de Jetbrains ya que tienen un gran interés en su éxito, cuanto mas lejos llegue y dado su sencillez de integración con IntelliJ, más licencias de este último venderán, por lo tanto no me parece que vayan a abandonar el proyecto.
- Otro factor importante a mi entender es que no hay un claro sucesor para Java, han aparecido muchos lenguajes que ofrecen características como closures, modularidad, características funcionales pero ninguno se ha posicionado aún. Kotlin además de todo eso ofrece soporte por parte de Jetbrains y [reification](https://en.wikipedia.org/wiki/Reification_(computer_science), para saber sobre esto último recomiendo este [post](http://gafter.blogspot.com.es/2006/11/reified-generics-for-java.html).

##Instalación
Es muy sencillo, la gente de Jetbrain lo ha hecho muy bien.
Requerimientos:
1. Intellij 14.1 o Android Studio: [IntelliJ IDEA Minimal Survival Guide](http://hadihariri.com/2014/01/06/intellij-idea-minimal-survival-guide/).
	Puedes hacerlo desde la página de [descargas](https://confluence.jetbrains.com/display/IDEADEV/IDEA+14.1+EAP) de Jetbrains
2. JDK 1.6 o superior: Puedes hacerlo desde la página de [Oracle](http://www.oracle.com/technetwork/java/javase/downloads/index.html) o si estas muy perdido puedes recurrir al tutorial [JVM Minimal Survive Guide](http://hadihariri.com/2013/12/29/jvm-minimal-survival-guide-for-the-dotnet-developer/)
3. Plugin de Kotlin: Se puede hacer desde el propio IDE, abre IntelliJ: File -> Plugins, y busca ==Kotlin==, listo :).

##Compilador
Cuando investigué sobre Kotlin me llamó la atención su compilador, hasta ese entonces no sabía nada de como funcionaban los compilador de los lenguajes que funcionan sobre Java, especificamente en el caso de Kotlin, requiere que Kotlin entienda los ficheros fuente de Java y sus binarios, y viciversa, es decir que Java entienda los ficheros fuente de Kotlin y sus binarios. La idea de que el compilador de Kotlin entienda los ficheros fuente de Java es fácil de imaginar, pero hacer que javac, el compilador de Java, entienda los ficheros fuente de Kotlin es claramente imposible.

Actualmente el estado de los compiladores es el siguiente:
- *Groovy*:
Groovy genera stubs a partir del código, esto significa que los archivos fuente de Java contienen solo las declaraciones de las clases de Groovy, de sus métodos y de sus campos. A continuación ejecuta javac sobre los stubs y los archivos fuente Java.
Como resultado todo compila, pero los métodos de Groovy no tienen cuerpo, para solucionar esto a continuación se ejecuta el compilador de Groovy y reemplaza las clases de los stubs.
Esto tiene una gran pega, el tiempo y la complejidad que requiere.

- *Scala and Kotlin*:
Ambos lenguajes enseñan a sus compiladores a entender los archivos fuente de Java, así que ambos pueden generar los *.class y ejecutar javac sobre ellos.

## Características:
###### Java compatible
Según la gente de IntelliJ Kotlin fue diseñado con la interoperabilidad en mente, y lo poco que he probado a través de los koans me ha resultado bastante sencilla de entender e implementar, tanto Kotlin puede usar Java como en sentido contrario de un manera bastante cómoda.

Aquí la documentación es muy extensa y hacen de la experiencia algo muy agradable, recomiendo echar un vistazo directamente a la web ya que me sorprendió mucho como interactúan ambos lenguajes.

Más información en la [Documentación oficial](http://kotlinlang.org/docs/reference/java-interop.html) y en Koan resuelto en mi [Github](https://github.com/Jachu5/Koans/tree/master/src/i_introduction/_5_Nullable_Types)

###### Null Safety
Una de mis características favoritas y que soluciona uno de los problemas que más molestos me parecen, las referencias a null.
Null es lo que se llama un "first-class citizen" en el sistema de tipos de Kotlin, es decir los tipos son conscientes de que pueden ser null, tanto en el flujo de la aplicación así como en su referencia. Esto es bastante útil ya que en mi opinión la posibilidad de acceder en un nuestro código a referencias que son null (NullPointerException en Java) es una fuente de problemas inmensa que conlleva mucho boilerplate code y programación defensiva.

Kotlin puede hacer distinción entre aquellos tipos que pueden hacer referencia a null y aquellos que no.

```
var a: String = "abc"
a = null // compilation error"
val l = a.lenght() // esto nunca generará un NullPointerException y el compilador no dará problemas
```
Pero igualmente nos permite hacer un tipo "nullable"
```
var b: String? = "abc"
b = null // ok
val l = a.length() // esto puede generar un NullPointerException y el compilador no nos permitirá hacer esta llamada
```
En los casos en los que null es inevitable, Kotlin nos ofrece maneras bastante útiles de checkear las posibles referencias a null:

- Mediante checkedo explícito:
	El compilador detecta que ha habido un checkeo de null y permite la llamada a la función lenght.
```
if ( b!= null){
	b.lenght()
}
```
- Safe Calls
	Haciendo uso del operador ?, esto nos dará el valor devuelto por la función length() en caso de que b no sea null o null en caso contrario:
    ```
    b?.length()
    ```
    Y además se puede encadenar de la forma:
    ```
    inbox?.email?.message
    ```
- Operador Elvis "?:"
	Similar al de Groovy, estas dos expresiones serían equivalentes:
     ```
     val l: Int = if (b != null) b.length() else -1
     val l = b?.length() ?: -1
     ```
     Si la expresión a la izquierda del operador Elvis no es null devuelve el valor y en caso contrario **evalua** y devuelve la expresión de la derecha.

Más información en la [Documentación oficial](http://kotlinlang.org/docs/reference/null-safety.html) y en Koan resuelto en mi [Github](https://github.com/Jachu5/Koans/tree/master/src/i_introduction/_5_Nullable_Types)

###### Soporte para funciones de alto nivel y Lambdas
Otra cosa que me encanta.
Básicamente un función de alto nivel es una función que acepta otras funciones como parámetros o incluso que devuelve otra función.
Pongo un ejemplo:
 ```
list.filter {it % 2 == 1}
 ```
En este ejemplo se filtra una lista eliminando todos los elementos pares, es un ejercicio muy básico que usa una función predefinida `filter` al que se le pasa otra función como argumento `it % 2 == 1` y que se aplica toda la colección.

Probablemente la mejor manera de entenderlo sea en la [Documentación oficial](http://kotlinlang.org/docs/reference/lambdas.html) o en el koan resuelto en mi [Github](https://github.com/Jachu5/Koans/blob/master/src/i_introduction/_3_Lambdas/Lambdas.kt)


###### Data Classes
Muy útiles para clases que solo almacenan información (DTO), las Data clases nos generan de manera automática ciertas funcionalidad como la función equals(), hashCode(), toString() o una función copy() que copia los valores en una instancia nueva del objeto permitiéndonos modificar los valores deseados, actualmente tenemos alternativas en Java como la librería [AutoValue](https://github.com/google/auto/tree/master/value) de Google.

```
data class Money(val currency: String, val amount: Int)
val money = Money("USD", 100)
val moreMoney = money.copy(amount = 200)

```

Y nos permite dar valores por defecto a los parámetros de la construcción, así nos podemos olvidar de definir diferentes constructores.

```
data class Money(val currency: String = "Euro", val amount: Int = 0)
```

Y otra cosa que me gustó mucho son las Multi-declaraciones, que nos permiten hacer cosas del tipo:
```
val jane = User("Jane", 35) 
val (name, age) = jane
println("$name, $age years of age") // Imprime "Jane, 35 years of age"

```

Más información en la [Documentación oficial](http://kotlinlang.org/docs/reference/data-classes.html) y en Koan resuelto en mi [Github](https://github.com/Jachu5/Koans/tree/master/src/i_introduction/_7_Data_Classes)

###### Traits
Me encantan los Traits no puedo decir más, los Traits se pueden entender como interfaces en las que se pueden implementar funciones.
Aquí no tengo ningún ejemplo, los conozco por Scala, pero puedes encontrar mas información sobre ellos en este [post](http://blog.jetbrains.com/kotlin/2011/08/multiple-inheritance-part-2-possible-directions/).

###### Extension Fuctions######
Kotlin permite ampliar las funcionalidades de la clases ( tanto propias de Kotlin como de Java) sin necesidad de heredarlas usando la declaración "extension", estos miembros se introducen de manera estática, de esta manera nos podemos olvidar de las clases "Utils" repletas de llamadas a funciones estáticas y obtener un código mucho mas limpio
````
fun String.last() : Char {
  return this[length - 1]
}
val x = "Hey!"
println(x.last()) // Imprime "!".

```
A partir de mis escarceos con Kotlin descubrí que otros lenguajes también implementa esta funcionalidad como puede ser C#

Mas información en la [Documentación oficial](http://kotlinlang.org/docs/reference/extensions.html) y en Koan resuelto en mi [Github](https://github.com/Jachu5/Koans/tree/master/src/i_introduction/_8_Extension_Functions)

## Conclusión
Para ser honestos mi aventura con Kotlin ha sido breve por ahora, y apenas he hecho algún desarrollo que vaya mas allá de la resolución de los Koans, pero me esta gustando mucho ya que aporta mucha flexibilidad y aire fresco a Java.
Espero que este post os haya sido de utilidad!


