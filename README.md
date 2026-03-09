
# PRUEBA 02 – 2º Trimestre

**Módulo:** Entornos de Desarrollo
**Duración:** 2 horas

---

# 1. Objetivo

Se desea desarrollar un programa en **Java** que permita gestionar la **plantilla de empleados de una empresa**.

Los empleados pueden ser de dos tipos, pero no vamos a usa ninguna clase enumerada:

* **Técnicos**
* **Comerciales**

El sueldo de cada tipo de empleado se calculará de forma distinta.

La estructura del programa está descrita en el **diagrama UML proporcionado**, el cual debes respetar.

<img width="2000" height="1426" alt="image" src="https://github.com/user-attachments/assets/4d38c6b6-d0bd-4586-8f82-92fe98095c03" />

* La clase `Empleado` es **abstracta** y el método `getSueldo()` también es **abstracto**.

---

# 2. Reglas de cálculo del sueldo

### Técnicos

El sueldo se calculará como su sueldo base más la categoría multiplicada por 100.

---

### Comerciales

El sueldo se calculará como su sueldo base más el 10% de las ventas realizadas.

---

# 3. Clase Plantilla

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

# 4. Gestión mediante menú

El programa se ejecutará mediante un menú:

```
1 - Contratar empleado
2 - Listar todos los empleados
3 - Listar empleados con filtro
4 - Salir
```

El programa deberá ejecutarse en un bucle hasta seleccionar **Salir**.

---

## Opción 1 – Contratar empleado

Se preguntará el tipo de empleado:

```
1 - Técnico
2 - Comercial
```

Después se solicitarán los datos necesarios para crear el empleado.

---

## Opción 2 – Listar todos

Debe mostrar todos los empleados **ordenados por nombre**.

Formato de salida:

```
N - Nombre Apellidos: Sueldo €
```

---

## Opción 3 – Listar con filtro

Se pedirá un texto y se mostrarán los empleados cuyo nombre o apellidos contengan dicho texto.

---

# 5. Ordenación de la lista

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

# 6. Comprobación del funcionamiento

Para comprobar que el programa funciona correctamente, introduce los siguientes empleados:

### Técnico

```
Nombre: Pablo
Apellidos: Bicicletas
DNI: 11111111H
Sueldo base: 1000
Categoría: 1
```

---

### Técnico

```
Nombre: Omar
Apellidos: Mediterraneo
DNI: 22222222J
Sueldo base: 1000
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

# Resultado esperado al listar todos

```
1 - Luna Rota: 1400 €
2 - Pablo Bicicletas: 1100 €
3 - Omar Mediterraneo: 1200 €
```

---

# Resultado esperado al filtrar por "ta"

```
1 - Luna Rota: 1400 €
2 - Pablo Bicicletas: 1100 €
```

