---
title: Introducción a la Programación con Go parte 2
date: 2026-10-11
---

## Lo básico de Go

En esta segunda parte se ven conceptos generales de programación que se ven en practicamente
todos los lenguajes de programación: variables, tipos, funciones, control de flujo y colecciones.

## Variables y tipos

Una variable es un nombre asociado a un valor. Su tipo indica qué valores puede almacenar y
qué operaciones se pueden realizar con ellos.

Recordando la [parte 1](/blog/introduccion-a-la-programacion-con-go-1), todos los valores son realmente `0` y `1` para
la computadora, por lo que el tipo de valor es importante para definir correctamente su interpretacion.

```go
var edad int = 20
var nombre = "Ana"
ciudad := "Puebla"

const pi = 3.14159

var activo bool
var contador int
var texto string
```

- `var edad int = 20` declara el nombre, el tipo y el valor.
- `var nombre = "Ana"` permite que Go infiera el tipo `string`.
- `ciudad := "Puebla"` es la version corta que también infiere el tipo de la variable.
- `const` es una constante: su valor no puede cambiar.

Y para evitar comportamientos no definidos o inesperados, las variables siempre tienen
un _valor cero_, es decir, que aun y cuando no se especifique un valor a una variable,
esta termina iniciando de igual manera con uno por defecto.

> Estos comportamientos los encontraran en lenguajes como C

## Funciones

Una función agrupa instrucciones bajo un nombre que puede ser reutilizados para ejecutar el conjunto
de instrucciones rapidamente.

```go
func sumar(a int, b int) int {
	return a + b
}
```

Primero se escribe el nombre, después los _parámetros_ con su tipo y, al final, el tipo del resultado.
`return` retorna el resultado y termina la función.

En Go se permite devolver más de un valor: `(valor, error)` es una convención bastante común:

```go
func dividir(a, b float64) (float64, error) {
	if b == 0 {
		return 0, errors.New("no se puede dividir entre cero")
	}

	return a / b, nil
}
```

Este ejemplo usa `errors` para definir cuando ocurre un _error esperado_ dentro de la función.

## Control de flujo

El control de flujo se usa para alterar el orden en el qué las instrucciones se ejecutan, o cuantas veces se repiten.

### Condiciones

```go
if edad >= 18 {
	fmt.Println("mayor")
} else {
	fmt.Println("menor")
}
```

### Ciclos

```go
for i := 0; i < 5; i++ {
	fmt.Println(i)
}
```

También puede tener solo una condición, como se puede ver con un `while` en otros lenguajes:

```go
i := 0
for i < 10 {
	i++
}
```

Sin condición, el ciclo se repite infinitamente:

```go
for {
	break
}
```

La palabra `break` se puede usar para terminar el ciclo, comunmente con condicionales.

## Colecciones y structs

### Slices

Un slice representa un conjunto de elementos del mismo tipo:

```go
nums := []int{3, 1, 2}
nums = append(nums, 7)
fmt.Println(len(nums)) // 4
fmt.Println(nums[1:3]) // [1 2]

for i, n := range nums {
	fmt.Println(i, n)
}

for _, n := range nums {
	fmt.Println(n)
}
```

Las posiciones empiezan en los arreglos empizan en `0`. La expresión `nums[1:3]` selecciona desde la posición 1 hasta la 3, no inclusivo: `[1 2]`.

`range` entrega el índice y el valor. Usa `_` para descartar el índice cuando no lo necesitas.

## Ejemplos

Cada bloque es un programa independiente. Guarda el que quieras probar en `main.go` y ejecútalo con:

```sh
go run main.go
```

### Registrar gastos

Este programa combina lectura de datos, slices, funciones y condiciones.
`fmt.Scanln` recibe la dirección de una variable (`&cantidad`, por ejemplo) para guardar el dato ingresado.
Para este ejemplo, ingresa una cantidad entera no negativa y gastos numéricos usando punto decimal.

```go
package main

import "fmt"

func calcularTotal(precios []float64) float64 {
	total := 0.0

	for _, precio := range precios {
		total += precio
	}

	return total
}

func main() {
	var cantidad int

	fmt.Print("¿Cuántos gastos quieres registrar? ")
	fmt.Scanln(&cantidad)

	var gastos []float64

	for i := 0; i < cantidad; i++ {
		var gasto float64

		fmt.Printf("Gasto %d: $", i+1)
		fmt.Scanln(&gasto)

		gastos = append(gastos, gasto)
	}

	total := calcularTotal(gastos)
	fmt.Printf("\nTotal gastado: $%.2f\n", total)

	if total > 1000 {
		fmt.Println("Aviso: gastaste más de $1000")
	} else {
		fmt.Println("Tus gastos no superan los $1000")
	}
}
```
