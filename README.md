
# PRUEBA 02 – 2º Trimestre

**Módulo:** Entornos de Desarrollo
**Duración:** 2 horas

---

## 1. Objetivo

Se desea desarrollar un programa en **Java** que permita gestionar la **plantilla de empleados de una empresa**.

Los empleados pueden ser de dos tipos, pero no vamos a usa ninguna clase enumerada:

* **Técnicos**
* **Comerciales**

El sueldo de cada tipo de empleado se calculará de forma distinta.

La estructura del programa está descrita en el **diagrama UML proporcionado**, el cual debes respetar.

<image src="/assets/DAM2526_ED_Prueba02_Trim2-3.jpg" alt="Diagrama de clases">

* También en PDF: [Diagrama de clases en PDF](DAM2526_ED_Prueba02_Trim2-3.pdf)

* La clase `Empleado` es **abstracta** y el método `getSueldo()` también es **abstracto**.

---

## 2. Reglas de cálculo del sueldo

### Técnicos

El sueldo se calculará como su sueldo base más la categoría multiplicada por 100.

---

### Comerciales

El sueldo se calculará como su sueldo base más el 10% de las ventas realizadas.

---

## 3. Clase Plantilla

En la clase `Plantilla`:

### Método `contratarEmpleado()`

Debe añadir el empleado recibido como parámetro a la plantilla.

---

### Método `getEmpleadosPorNombre(String filtroNombre)`

Debe devolver una lista con todos los empleados cuyo:

* **nombre**
* **o apellidos**

contenga el texto pasado como parámetro.

### Reglas

* La búsqueda debe **ignorar mayúsculas y minúsculas**.
* Si el parámetro está vacío (`""`), se devolverán **todos los empleados**.

---

## 4. Gestión mediante menú

El programa se ejecutará mediante un menú:

```
1 - Contratar empleado
2 - Listar todos los empleados
3 - Listar empleados con filtro
4 - Salir
```

El programa deberá ejecutarse en un bucle hasta seleccionar **Salir**.

---

### Opción 1 – Contratar empleado

Se preguntará el tipo de empleado:

```
1 - Técnico
2 - Comercial
```

Después se solicitarán los datos necesarios para crear el empleado.

---

### Opción 2 – Listar todos

Debe mostrar todos los empleados **ordenados por nombre**.

Formato de salida:

```
N - Nombre Apellidos: Sueldo €
```

---

### Opción 3 – Listar con filtro

Se pedirá un texto y se mostrarán los empleados cuyo nombre o apellidos contengan dicho texto.

---

## 5. Ordenación de la lista

Antes de mostrar los empleados, la lista debe estar **ordenada por nombre**.

En Java es posible ordenar listas utilizando herramientas como:

* `Collections.sort()`
* `List.sort()`
* `Comparator`

Ejemplo de ordenación de una lista de productos por código:

```java
Collections.sort(productos, Comparator.comparing(Producto::getCodigo));
```

⚠️ Importante:

La ordenación **no debería realizarse dentro del método `getEmpleadosPorNombre()`**, ya que este método solo debe encargarse de **filtrar empleados**.

La ordenación debe hacerse **en el lugar donde se muestran los datos**.

---

## 6. Comprobación del funcionamiento

Para comprobar que el programa funciona correctamente, introduce los siguientes empleados:

### Técnico

```
Nombre: Pablo
Apellidos: Bicicletas
DNI: 11111111H
Sueldo base: 1000.75
Categoría: 1
```

---

### Técnico

```
Nombre: Omar
Apellidos: Mediterraneo
DNI: 22222222J
Sueldo base: 1000,99
Categoría: 2
```

---

### Comercial

```
Nombre: Luna
Apellidos: Rota
DNI: 33333333P
Sueldo base: 800
Ventas: 6000
```

---

### Resultado esperado al listar todos

```
1 - Luna Rota: 1400 €
2 - Omar Mediterraneo: 1200,99 €
3 - Pablo Bicicletas: 1100,75 €
```

---

### Resultado esperado al filtrar por "ta"

```
1 - Luna Rota: 1400 €
2 - Pablo Bicicletas: 1100,75 €
```
---

## 7. Aclaraciones sobre algunos métodos a desarrollar

### Métodos de `GestorEmpleados`

#### ejecutar()

Ejecuta el menú principal de la aplicación. Muestra las distintas opciones disponibles y procesa la acción seleccionada por el usuario. El programa se mantiene en ejecución hasta que el usuario elige la opción de salir.

#### contratarEmpleado()

Permite crear y contratar un nuevo empleado. Solicita al usuario el tipo de empleado (técnico o comercial) y los datos necesarios para construir el objeto correspondiente. Finalmente añade el empleado a la plantilla.

#### ordenarPorNombre(List<Empleado>)

Ordena una lista de empleados alfabéticamente según su nombre.

#### listarEmpleados(List<Empleado>)

Muestra por pantalla una lista de empleados. Antes de mostrarlos, la lista se ordena por nombre. Cada empleado se muestra numerado y con el formato: N - Nombre Apellidos: Sueldo €. Usa `ordenarPorNombre`.

#### listarTodos()

Obtiene todos los empleados de la plantilla y los muestra. Usa `plantilla.getEmpleadosPorNombre` y `listarEmpleados`.

#### listarPorFiltro()

Solicita al usuario un texto de filtro, obtiene los empleados según dicho filtro y los muestra. Usa `plantilla.getEmpleadosPorNombre` y `listarEmpleados`.

---

### Métodos de `Plantilla`

#### getEmpleadosPorNombre(String filtroNombre)

Devuelve una `nueva` lista de empleados cuyo nombre o apellidos contienen el texto indicado. La búsqueda ignora mayúsculas y minúsculas. Si el filtro está vacío, se devuelven todos los empleados.

---

### Métodos de `Consola`

#### leerEntero(String mensaje)

Muestra un mensaje por pantalla solicitando al usuario un número entero y lee la entrada desde teclado. Si el valor introducido no es un entero válido, captura la excepción y muestra un mensaje de error, repitiendo la petición hasta que el usuario introduce un número correcto.

#### leerImporte(String mensaje)

Solicita al usuario un importe numérico mostrando previamente un mensaje. Lee el valor introducido por teclado y lo convierte a tipo double, permitiendo tanto coma como punto como separador decimal. Si el formato no es válido, muestra un mensaje de error y vuelve a pedir el dato hasta que el usuario introduce un importe correcto.

#### mostrarMenu()

Muestra por pantalla el menú principal de la aplicación con las diferentes opciones disponibles para el usuario, como contratar un empleado, listar empleados, aplicar filtros o salir del programa.

#### limpiarPantalla()

Simula la limpieza de la consola imprimiendo múltiples líneas en blanco *(50)*. Esto desplaza el contenido anterior hacia arriba para que la pantalla quede visualmente más limpia antes de mostrar nueva información. Se utiliza en el bucle del método `ejecutar` de `GestorEmpleados`.

#### pausa()

Muestra un mensaje "Pulse una tecla para continuar..." y detiene temporalmente la ejecución del programa hasta que el usuario pulsa una tecla. Se utiliza para que el usuario pueda leer la información mostrada en pantalla antes de continuar con la ejecución del programa. Se utiliza en el bucle del método `ejecutar` de `GestorEmpleados`.
