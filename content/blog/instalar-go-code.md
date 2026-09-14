---
title: Instalación de Go y Visual Studio Code
date: 2026-09-13
---

Visita [go.dev](https://go.dev/dl/) para descargar el compilador de Go y [code.visualstudio.com](https://code.visualstudio.com/download) para descargar el editor de texto:

{{< img src="img/go_install_1.png" size="800x" center="true" >}}

Solo es necesario hacer doble clic en ambos instaladores y avanzar seleccionando _Siguiente_ e _Instalar_:

{{< img src="img/go_install_2.png" size="600x" center="true" >}}

Una vez finalizada la instalación y al ejecutar Visual Studio Code por primera vez, basta con seleccionar la opción _Continuar sin iniciar sesión_:

{{< img src="img/go_install_3.png" size="800x" center="true" >}}

Con Visual Studio Code abierto, crea una carpeta en tu computadora y dentro de ella crea un archivo llamado `main.go`:

{{< img src="img/go_install_4.png" size="800x" center="true" >}}

## Windows

Presiona `Ctrl + Shift + P`, busca la opción `Terminal: Create New Terminal` (o `Nueva terminal`)
y selecciona `PowerShell` entre las opciones. Se abrirá un panel en la parte inferior donde podrás
escribir comandos; esta es una terminal.

Dentro de esta terminal, al escribir `go version` y `go run main.go`, deberías ver
resultados similares a los que se muestran en la imagen.

```go
package main

import "fmt"

func main() {
fmt.Println("Hola mundo")
}
```

En caso de ver un error similar a:

```
go : The term 'go' is not recognized as the name of a cmdlet, function, script file, or
operable program. Check the spelling of the name, or if a path was included, verify that the path is
correct and try again.
```

Cerrando y volviendo abrir Visual Studio Code deberia de resolverlo
