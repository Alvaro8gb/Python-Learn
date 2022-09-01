# Guia de Estilo para Python
## Max long lineas
Limita todas las líneas a un máximo de 80 caracteres.
---
## Lineas en blanco

Separa funciones de alto nivel y definiciones de clase con dos líneas
en blanco.
Definiciones de métodos dentro de una clase son separadas por una
línea en blanco.
Líneas en blanco adicionales pueden ser utilizadas (escasamente)
para separar grupos de funciones relacionadas. Se pueden omitir
entre un grupo (de funciones) de una línea relacionadas (por ejemplo,
un conjunto de implementaciones ficticias).

---
## Importaciones
Las importaciones deben estar en líneas separadas, por ejemplo:
	Sí: import os
	    import sys
	No: import sys, os

Sin embargo, es correcto decir:
	from subprocess import Popen, PIPE

Las importaciones siempre se colocan al comienzo del archivo,simplemente luego de cualquier comentario o documentación del
módulo, y antes de globales y constantes.

Las importaciones deben estar agrupadas en el siguiente orden:
 1. importaciones de la librería estándar
 2. importaciones terceras relacionadas
 3. importaciones locales de la aplicación / librería

Deberías poner una línea en blanco entre cada grupo.
Coloca cualquier especificación __all__ luego de las
importaciones.

Al importar una clase desde un módulo que contiene una clase,
generalmente está bien realizar esto:
	from myclass import MyClass
	from foo.bar.yourclass import YourClass

Si esto causa coincidencias con nombres locales, realiza:
	import myclass
	import foo.bar.yourclass
y usa “myclass.MyClass” y “foo.bar.yourclass.YourClass”.

---
## Espacios en blanco en Expresiones y Sentencias

Evita usar espacios en blanco extraños en las siguientes situaciones:
### Inmediatamente dentro de paréntesis, corchetes o llaves:
	Sí: spam(ham[1], {eggs: 2})
	No: spam( ham[ 1 ], { eggs: 2 } )

### Inmediatamente antes de una coma, un punto y coma o dos puntos:
	Sí: if x == 4: print x, y; x, y = y, x
	No: if x == 4 : print x , y ; x , y = y , x

### Inmediatamente antes del paréntesis que comienza la lista de argumentos en la llamada a una función:
	Sí: spam(1)
	No: spam (1)

### Inmediatamente antes de un corchete que empieza una indexación :
	Sí: dict['key'] = list[index]
	No: dict ['key'] = list [index]

### Más de un espacio alrededor de un operador de asignación (u otro) para alinearlo con otro:
	Sí:
		x = 1
		y = 2
		long_variable = 3
	No:
		x   = 1
		y   = 2		
		long_variable   = 3


####  Otras recomendaciones
Siempre rodea estos operadores binarios con un espacio en
cada lado: asignación (=), asignación de aumentación (+=, -=,
etc.), comparaciones (==, <, >, !=, <>, <=, >=, in, not in, is,
is not), “Booleans” (and, or, not).

Si se utilizan operadores con prioridad diferente, considera
agregar espacios alrededor del operador con la menor prioridad.
Usa tu propio criterio, de todas menaras, nunca uses más de un
espacio, y siempre mantén la misma cantidad en ambos lados.

	Sí:
		i = i + 1
		submitted += 1
		x = x*2 - 1
		hypot2 = x*x + y*y
		c = (a+b) * (a-b)
	No:
		i=i+1
		submitted +=1
		x = x * 2 - 1
		hypot2 = x * x + y * y
		c = (a + b) * (a - b)

No uses espacios alrededor del = (igual) cuando es utilizado
para indicar un argumento en una función (“keyword
argument”) o un parámetro con un valor por defecto.

	Sí:	
		def complex(real, imag=0.0):
			return magic(r=real, i=imag)
	No:
		def complex(real, imag = 0.0):
			return magic(r = real, i = imag)

### Las sentencias compuestas (múltiples sentencias en la misma línea) son generalmente desalentadas.
	Sí:
		if foo == 'blah':
		do_blah_thing()
		do_one()
		do_two()
		do_three()
	Más bien no:
		if foo == 'blah': do_blah_thing()
		do_one(); do_two(); do_three()


---
## Comentarios
`¡Nunca cambies las mayúsculas/minúsculas de los identificadores! (Nombres de clases, objetos, funciones, etc.).`
`¡Siempre realiza una prioridad de mantener los comentarios al día cuando el código cambie!`

1. Comentarios que contradigan el código es peor que no colocar comentarios. 
2. Los comentarios deben ser oraciones completas. 
3. Si un comentario es una frase u oración, su primera palabra debe comenzar con
mayúscula, a menos que sea un identificador que comienza con minúscula. 
4. Si un comentario es corto, el punto al final puede omitirse.

Comentarios en bloque generalmente consisten en uno o máspárrafos compuestos por oraciones completas, por lo que cada una de ellas debe finalizar en un punto.

Deberías usar dos espacios luego de una oración que termine con un punto.

Al escribir en Inglés, se aplica “Strunk and White”.

Para los programadores de Python de países de habla no Inglesa: por favor escribe tus comentarios en Inglés, a menos que estés 120% seguro que tu código jamás serA leído por gente que no hable tu idioma.

### Comentarios en bloque

- Los comentarios en bloque generalmente se aplican a algunos (o
todos) códigos que los siguen, y están indentados al mismo nivel que
ese código. Cada línea de un comentario en bloque comienza con un # (numeral) y un espacio (a menos que esté indentado dentro del mismo comentario).

- Los párrafos dentro de un comentario en bloque están separados por una línea que contiene únicamente un # (numeral).

### Comentarios en línea (comentarios en la misma línea)

- Usa comentarios en línea escasamente.
- Un comentario en línea es aquel que se encuentra en la misma línea que una sentencia. Los comentarios en línea deberían estar
separados por al menos dos espacios de la sentencia. Deberían empezar con un # (numeral) seguido de un espacio.
- Los comentarios en línea son innecesarios y de hecho molestos si su acción es obvia. 
	No hagas esto:
		x = x + 1 # Incrementar x
	Pero algunas veces es útil:
		x = x + 1 # Compensar el borde


### Cadenas de documentación

Las convenciones para escribir buenas cadenas de documentación
(alias “docstrings”). Escribe “docstrings” para todos los módulos, funciones, clases
y métodos públicos. Los “docstrings” no son necesarios para
los métodos no públicos, pero deberían tener un comentario
que describa su función. Este comentario debe aparecer luego
de la línea “def”.

Ejemplo:
"""Return a foobang
Optional plotz says to frobnicate the bizbaz first.
"""
Para “docstrings” de una línea, está bien terminar el """ en la
misma línea.

---
## Convenciones de nombramiento

### Nombres para evitar
Nunca uses los caracteres ‘l’ (letra ele en minúscula), ‘O’ (letra o
mayúscula), o ‘I’ (letra i mayúscula) como simples caracteres para
nombres de variables. En algunas fuentes, estos caracteres son indistinguibles de los
números uno y cero. Cuando se quiera usar ‘l’, en lugar usa ‘L’.

### Nombres de paquetes y módulos
Los módulos deben tener un nombre corto y en minúscula. Guiones bajos pueden utilizarse si mejora la legiblidad.

Los paquetes en Python también deberían tener un nombre corto y en minúscula, aunque el uso de guiones bajos es desalentado (poco recomendado). Ya que los nombres de módulos están ligados a los de los archivos, y algunos sistemas operativos distinguen caracteres entre minúsculas
y mayúsculas y truncan nombres largos, es importante que sean
bastante cortos – esto no será un problema en Unix, pero podrá ser
un problema cuando el código es portado a una antigua versión de
Mac, Windows o DOS.

Cuando un módulo escrito en C o C++ provee una interfaz de alto
nivel escrita en Python, debe llevar un guión bajo como prefijo (por
ejemplo, _socket).

### Nombres de clases
Casi sin excepción, los nombres de clases deben utilizar la
convención “CapWords” (palabras que comienzan con mayúsculas).
Clases para uso interno tienen un guión bajo como prefijo.

### Nombres de excepciones
Debido a que las excepciones deben ser clases, se aplica la
convención anterior. De todas maneras, deberías usar un sufijo
“Error” en los nombres de excepciones (en caso que corresponda a
un error).


#### Nombres de variables globales
(Esperemos que esas variables sean únicamente para uso dentro del
módulo). Las convenciones son las mismas que se aplican para las
funciones.
Los módulos que estén diseñados para usarse vía from M import
* deben usar el mecanismo __all__ para prevenir la exportación de
las variables globales, o usar la antigua convención especificando un
guión bajo como prefijo (lo que tratarás de hacer es indicar esas
globales como “no públicas”).

### Nombres de funciones
Las funciones deben ser en minúscula, con las palabras separadas
por un guión bajo, aplicándose éstos tanto como sea necesario para
mejorar la legibilidad.


### Argumentos de funciones y métodos
- Siempre usa self para el primer argumento de los métodos de
instancia.

- Siempre usa cls para el primer argumento de los métodos de clase.
- Si los argumentos de una función coincide con una palabra reservada
del lenguaje, generalmente es mejor agregar un guión bajo como sufijo antes 
de usar una abreviación u ortografía incorrecta. class_ es mejor que clss. (Tal vez es mejor evitar las coincidencias usando un sinónimo.)

### Nombres de métodos y variables de instancia

Usa las mismas reglas que para el nombramiento de funciones: en minúscula con palabras separadas con guiones bajos, tantos como sea necesario para mejorar la legibilidad.
Usa un solo guión bajo como prefijo para métodos no públicos y variables de instancia.

Para evitar coincidencias con subclases, usa dos guiones bajos como prefijo para invocar las reglas del “name mangling” de Python.
Python cambia (“mangles”, en el texto original) estos nombres con el
nombre de la clase: si la clase Foo tiene un atributo llamado __a, no
puede ser accedido por Foo.__a. (Un usuario insistente aún puede acceder llamando a Foo._Foo_a.) 

Generalmente, el doble guión bajo como prefijo debería ser únicamente utilizado para evitar conflicto con los nombres en atributos y clases diseñados para ser parte de una subclase.

### Constantes
Las constantes son generalmente definidas a nivel módulo, escritas
con todas las letras en mayúscula y con guiones bajos separando
palabras. Por ejemplo, MAX_OVERFLOW y TOTAL.
