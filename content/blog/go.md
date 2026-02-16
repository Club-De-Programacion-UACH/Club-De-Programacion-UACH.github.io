---
title: Introducción a Go
date: 2026-02-14
---

## ¿Qué es Go?

**Go (Golang)** es un lenguaje de programación diseñado en Google en 2007 por Robert Griesemer, Rob Pike y Ken Thompson para ser:

* Simple y legible
* Rápido y compilado
* Concurrente

## Instalación

### En Linux

```bash
# apt (debian/ubuntu)
sudo apt install golang
# pacman (arch)
sudo pacman -S go
# dnf (fedora/redhat)
sudo dnf install go
```

### En macOS
```bash
brew install go
```

### En Windows

Descargar desde [go.dev](https://go.dev/dl/)

```sh
# prueba que funciona
go version
# si no, prueba el PATH de instalación directamenete
C:\Program Files\Go\bin\go.exe version
```


## Estructura básica de un programa en Go

Archivo: `main.go`

```go
package main

import "fmt"

func main() {
    fmt.Println("Hola, mundo")
}
```

### Explicación:

* `package main`. Define el [paquete principal](https://go.dev/doc/tutorial/getting-started).
* `import`. Importar librerías.
* `func main()`. Punto de entrada del programa.
* `fmt.Println()`. Imprime texto en consola.

Ejecutar:

```bash
go run main.go
```

Compilar:

```bash
go build
```

## Variables y tipos básicos

Go es un lenguaje **tipado**:

```go
var nombre string = "Juan"
// el operador ":=" (walrus operator) infiere el tipo y ahorra el uso de "var"
edad := 20
var activo bool = true
```

Tipos comunes:

* `int`
* `float64`
* `string`
* `bool`

## Estructuras de control

### Condicionales

```go
if edad >= 18 {
    fmt.Println("Mayor de edad")
} else {
    fmt.Println("Menor de edad")
}
```

### Ciclos

Go solo tiene `for`, pero es usado para `for`, `while` y `range` (rangos).

```go
for i := 0; i < 5; i++ {
    fmt.Println(i)
}
```

Tipo while:

```go
i := 0
for i < 5 {
    i++
}
```

Tipo `range`:

```go
for i := range 5 {
    fmt.Println(i)
}
```

## Funciones

```go
func saludar(nombre string) string {
    return "Hola " + nombre
}
```

Funciones con múltiples retornos:

```go
func dividir(a, b float64) (float64, error) {
    if b == 0 {
        return 0, fmt.Errorf("no se puede dividir entre cero")
    }
    return a / b, nil
}
```

Go trata a los errores como valores y se suele ver mucho el patrón `(valor, error)`.

## Introducción a servidores HTTP

Go incluye un servidor HTTP en su librería estándar: `net/http`.

### Servidor básico

```go
package main

import (
    "fmt"
    "net/http"
)

func handler(w http.ResponseWriter, r *http.Request) {
    fmt.Fprintln(w, "Hola desde mi servidor en Go")
}

func main() {
    http.HandleFunc("/", handler)
    fmt.Println("Servidor corriendo en http://localhost:8080")
    http.ListenAndServe(":8080", nil)
}
```

Ejecuta:

```bash
go run main.go
```

Despues abre [localhost:8080](http://localhost:8080).

### ¿Qué está pasando?

* `http.HandleFunc`. Registra una ruta (puedes visualizarlo como lo que sigue despues del `.com/`).
* `ResponseWriter`. Permite *escribir* la respuesta.
* `Request`. Contiene información de la petición.
* `ListenAndServe`. Inicia el servidor.

## Buenas prácticas y herramientas

* Manejar errores explícitamente
```go
// vas a toparte con este tipo de condicionales por todos lados usando Go
if err != nil {
    return err
}
```
* Usar `go fmt` para formatear código
* Usar `go mod init` para proyectos nuevos

## Recursos adicionales

- Recomendado: [Tour de Go](https://go.dev/tour/welcome/1)
- Recomendado: [Go by Example](https://gobyexample.com/)
