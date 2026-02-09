# Guía breve de programación en C

El lenguaje C es fundamental en el desarrollo de sistemas operativos, sistemas embebidos, compiladores y software de alto rendimiento. Su estudio permite entender cómo se implementan las abstracciones de los lenguajes modernos y cómo interactúan los programas con el hardware.

---

## 1. El lenguaje C y la programación estructurada

C es un lenguaje:

* Compilado
* Imperativo
* De tipado estático
* De bajo nivel relativo

La programación estructurada en C se basa en tres mecanismos fundamentales:

1. Secuencia de instrucciones
2. Selección
3. Iteración

El flujo de ejecución es explícito y controlado directamente por el programador, lo que lo hace cercano al modelo real del procesador.

---

## 2. Variables y tipos de datos

### 2.1 Definición de variables

Una variable en C representa una **posición en memoria** asociada a un tipo de dato.

```c
int x = 10;
```

* `int` define el tipo de dato
* `x` es el identificador
* `10` es el valor almacenado en memoria

Toda variable en C ocupa memoria y tiene una dirección asociada.

---

### 2.2 Tipos de datos básicos

| Tipo     | Tamaño típico | Descripción                                   |
| -------- | ------------- | --------------------------------------------- |
| `char`   | 1 byte        | Carácter o entero pequeño                     |
| `int`    | 4 bytes       | Entero                                        |
| `float`  | 4 bytes       | Punto flotante                                |
| `double` | 8 bytes       | Punto flotante de doble precisión             |
| `long`   | 8 bytes       | Entero largo (dependiente de la arquitectura) |

El tamaño exacto puede consultarse usando `sizeof`.

---

### 2.3 Declaración e inicialización

```c
int a;        /* declaración */
a = 5;        /* asignación */

int b = 10;   /* declaración + inicialización */
```

Las variables locales **no se inicializan automáticamente** en C.

---

## 3. Estructuras de control

### 3.1 Selección con `if / else`

```c
if (x > y) {
    max = x;
} else {
    max = y;
}
```

Esta estructura se traduce internamente en comparaciones y saltos condicionales.

---

### 3.2 Iteración

```c
for (int i = 0; i < 5; i++) {
    suma += i;
}
```

Todo ciclo puede expresarse como:

* Inicialización
* Evaluación de condición
* Actualización
* Salto

---

## 4. Estructura de selección `switch`

La estructura `switch` permite seleccionar una rama de ejecución a partir del valor de una expresión entera o equivalente. Es especialmente útil cuando existen múltiples alternativas discretas.

```c
switch (opcion) {
    case 1:
        resultado = 10;
        break;
    case 2:
        resultado = 20;
        break;
    case 3:
        resultado = 30;
        break;
    default:
        resultado = -1;
}
```

### Características principales

* La expresión del `switch` se evalúa una sola vez
* Cada `case` corresponde a un valor constante
* `break` finaliza la ejecución del `switch`
* `default` se ejecuta si no hay coincidencias

Si no se utiliza `break`, la ejecución continúa en el siguiente `case`, lo que se conoce como *fall-through*. Este comportamiento es legal en C y debe usarse de forma intencional.

---

## 5. Arreglos

### 5.1 Definición

Un arreglo es una **colección de elementos del mismo tipo**, almacenados de forma contigua en memoria.

```c
int arr[5] = {1, 2, 3, 4, 5};
```

Cada elemento ocupa el mismo tamaño y las posiciones de memoria son consecutivas.

---

### 5.2 Acceso a arreglos

```c
int x = arr[2];
arr[0] = 10;
```

C **no realiza verificación automática de límites**, por lo que el programador debe garantizar accesos válidos.

---

## 6. Apuntadores

### 6.1 Concepto básico

Un apuntador es una variable que **almacena la dirección de memoria de otra variable**.

```c
int x = 10;
int *p = &x;
```

* `&x` obtiene la dirección de `x`
* `p` apunta a esa dirección
* `*p` accede al valor almacenado allí

---

### 6.2 Operadores relacionados con apuntadores

| Operador | Significado          |
| -------- | -------------------- |
| `&`      | Dirección de memoria |
| `*`      | Desreferenciación    |

```c
*p = 20;   /* modifica el valor de x */
```

---

## 7. Relación entre arreglos y apuntadores

En C, el nombre de un arreglo se comporta como un apuntador al primer elemento.

```c
int arr[3] = {10, 20, 30};
int *p = arr;
```

Las siguientes expresiones son equivalentes:

```c
arr[0] == *p
arr[1] == *(p + 1)
arr[2] == *(p + 2)
```

Esta relación es clave para comprender la aritmética de apuntadores y el acceso eficiente a memoria.

---

## 8. Funciones y uso de `return`

### 8.1 Funciones con valor de retorno

La palabra clave `return` se utiliza para **finalizar una función y devolver un valor al llamador**.

```c
int suma(int a, int b) {
    return a + b;
}
```

El valor retornado debe ser compatible con el tipo de la función.

---

### 8.2 Funciones `void`

En funciones que no devuelven valor, `return` puede usarse sin expresión para terminar la función anticipadamente.

```c
void validar(int x) {
    if (x < 0) {
        return;
    }
}
```

---

### 8.3 `return` en la función `main`

La función `main` devuelve un entero que indica el estado de terminación del programa.

```c
int main(void) {
    return 0;
}
```

* `0` indica ejecución correcta
* Un valor distinto de cero suele indicar error

Desde el estándar C99, si `main` finaliza sin ejecutar `return`, se asume implícitamente `return 0;`.

---

## 9. Relación con programación de bajo nivel

Las construcciones fundamentales de C tienen una traducción directa a bajo nivel:

* `return` se implementa mediante la instrucción de retorno del procesador (`ret`)
* `if` y `switch` se traducen en comparaciones y saltos
* `switch` puede generar tablas de salto cuando el compilador optimiza

Por esta razón, C es un lenguaje ideal para comprender código ensamblador y el comportamiento real de un programa.

---

## 10. Errores comunes

* Usar apuntadores sin inicializar
* Acceder fuera de los límites de un arreglo
* Confundir valor con dirección
* Asumir inicialización automática de variables locales
* Olvidar `break` en estructuras `switch`

## TAREA

La tarea de este tema se encuentra en el archivo [TAREA.md](TAREA.md).

---

