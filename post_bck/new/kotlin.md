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
###### Tipado Estático
###### Java compatible
###### Null Safety
Una de mis características favoritas, null es lo que se llama un "first-class citizen" en el sistema de tipos de kotlin, es decir los tipos son conscientes de que pueden ser null, tanto en el flujo de la aplicación asi como en su referenciación. Esto es bastante útil ya que en mi opinión la posibilidad de acceder en un nuestro codigo a referencias que son null (NullPointerException en Java) es una fuente de problemas inmensa que conlleva mucho boilerplate code y programación defensiva.

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
En los casos en los que null es invetable, Kotlin nos ofrece maneras bastante útiles de checkear las posibles referencias a null:

- Mediante checkedo explícito:
	El compilador detecta que ha habido un checkeo de null y permite la llamda a la función lenght.
```
if ( b!= null){
	b.lenght()
}
```
- Safe Calls
	Haciendo uso del operador ?, esto nos devolverá el valor devulto por la función length() en caso de que b no sea null o null en caso contrario:
    ```
    b?.length()
    ```
    Y además se puede encadenar de la forma:
    ```
    inbox?.email?.message
    ```
- Elvis operator "?:"
	Similar al de Groovy, estas dos expresiones serían equivalentes:
     ```
     val l: Int = if (b != null) b.length() else -1
     val l = b?.length() ?: -1
     ```
     Si la expresión a la izquierda del Elvis Operator no es null devuelve el valor, en caso contrario **evalua** y devuelve la expresión de la derecha.

Más información en la [Documentación oficial](http://kotlinlang.org/docs/reference/null-safety.html) y en Koan resuelto en mi [Github](https://github.com/Jachu5/Koans/tree/master/src/i_introduction/_5_Nullable_Types)


###### Nombre y argumentos opcionales
###### Soporte para funciones de alto nivel
###### Data Classes
Muy útiles para clases que solo almancenan información, de manera que nos genran de manera automática ciertas funcionalidad como la función equals(), hashCode(), toString() o una función copy() que copia los valores en una instancia nueva del objeto permitiendonos modificar los valores deseados, actualmente tenemos alternativas en Java como la librería [AutoValue](https://github.com/google/auto/tree/master/value) de Google.

```
data class Money(val currency: String, val amount: Int)
val money = Money("USD", 100)
val moreMoney = money.copy(amount = 200)

```

Y nos permite dar valores por defecto a los parámetros de la construcción, así nos podemos olvidar de definir diferentes contructores.

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

###### Singletons usando object notation
###### Traits
###### Extension Fuctions######
Kotlin permite ampliar las funcionalidades de la clases ( tanto propias de Kotlin como de Java) sin necesidad de heredarlas usando la declaración "extension", estos miembros se introducen de manera estática, de esta manera nos podemos olvidar de las clases "Utils" repltas de llamadas a funciones estáticas y obtener un código mucho mas limpio
````
fun String.last() : Char {
  return this[length - 1]
}
val x = "Hey!"
println(x.last()) // Imprime "!".

```
A partir de mis escarceos con Kotlin descubrí que otros lenguajes también implementa esta funcionalidad como puede ser C#
Mas información en la [Documentación oficial](http://kotlinlang.org/docs/reference/extensions.html) y en Koan resuelto en mi [Github](https://github.com/Jachu5/Koans/tree/master/src/i_introduction/_8_Extension_Functions)



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
