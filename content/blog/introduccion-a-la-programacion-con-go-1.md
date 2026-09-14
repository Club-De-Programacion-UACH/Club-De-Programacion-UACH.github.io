---
title: Introducción a la Programación con Go parte 1
date: 2026-09-12
---

<iframe
  src="/presentations/intro_1.pdf"
  width="100%"
  height="400"
  style="border: none;"
></iframe>

## Antes de ver código

Antes de empezar a programar considero necesario entender tres cosas:

- ¿Qué es una computadora?
- ¿Qué es un programa?
- ¿Qué es son los datos?
- [Instalar las herramientas necesarias](/blog/instalar-go-code)

## Computadora

{{< img src="img/programa.png" size="800x" center="true" >}}

Una computadora es un dispositivo o máquina que recibe una entrada (_input_), la procesa o transforma de alguna
manera, y produce una salida (_output_).

## Programa

Un programa es una secuencia de instrucciones que la computadora ejecuta.
Esta secuencia puede variar su flujo de ejecución mediante la toma de decisiones o la repetición de tareas (ciclos).

```go
calentar(agua)
taza.Agregar(cafe)
if hayLeche {
    taza.Agregar(leche)
}
taza.Servir(agua)
for i := 0; i < 10; i++ {
    taza.Revolver()
}
```

## Datos

Para la computadora todo se reduce a lo mismo: números. Y cada número está compuesto por un conjunto de _bits_.
Un bit es la unidad mínima de información y solo puede tener dos valores: 1 o 0 (encendido o apagado).

{{< img src="img/bits.png" size="400x" center="true" >}}

Dependiendo de cómo se interpreten estos bits, podemos representar números, caracteres (texto),
valores booleanos (verdadero o falso) o colecciones de estos valores.

## Interpretación

{{< img src="img/comp.png" size="800x" center="true" >}}

Para poder _ejecutar_ código, primero es necesario traducirlo o interpretarlo de forma que la computadora
entienda las instrucciones: mediante lenguaje máquina (números binarios).

En nuestro caso se va a usar el compilador de Go, el lenguaje de programación del que se va a hablar en este
curso.
