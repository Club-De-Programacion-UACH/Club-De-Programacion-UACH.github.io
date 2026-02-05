---
title: Introducción a Git y Control de Versiones
date: 2025-12-05
tags:
  - "git"
  - "control de versiones"
  - "tutorial"
  - "herramientas"
categories:
  - "Tutoriales"
  - "Git"
---

Git es un sistema de control de versiones distribuido que permite rastrear cambios en archivos y colaborar con otros desarrolladores. Es una herramienta esencial para cualquier programador.

> VCS (Version Control System): es un sistema que controla y administra los cambios de archivos a traves del tiempo. Estos sistemas cuentan con la posibilidad de *volver atras* y *traer de vuelta* cualquiera de los *cambios*.

## ¿Qué es Git?

Git es un sistema que permite:

* **Rastrear cambios**: Ver el historial completo de modificaciones
* **Trabajar en equipo**: Colaborar con otros sin sobrescribir cambios
* **Experimentar**: Crear *ramas* que se desvian de los cambios principales
* **Recuperar**: Volver a cualquier punto en el historial

## Instalación

### En Linux

```bash
# apt (debian/ubuntu)
sudo apt update
sudo apt install git
# pacman (arch)
sudo pacman -S git
```

### En macOS

```bash
brew install git
```

### En Windows

Descargar desde [git-scm.com](https://git-scm.com/download/win)

## Configuración inicial

Configurar nombre y email:

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "matricula@uach.mx"
```

## Comandos básicos

### Inicializar un repositorio

```bash
git init
```

### Ver el estado

```bash
git status
```

### Agregar archivos

```bash
git add archivo.py # Agregar un archivo específico
git add . # Agregar todos los archivos
```

### Hacer un commit

```bash
git commit -m "Descripción de los cambios"
```

### Ver el historial

```bash
git log
```

## Trabajando con GitHub

GitHub es una plataforma que permite guardar repositorios de Git en la nube.

> GitHub, la plataforma, no es lo mismo Git, la herramienta

### Clonar un repositorio

```bash
git clone https://github.com/usuario/repositorio.git
```

### Subir cambios

```bash
git add .
git commit -m "Mis cambios"
git push origin main
```

### Actualizar desde el repositorio remoto (GitHub)

```bash
git pull origin main
```

## Flujo de trabajo básico

1. **Modifica archivos**
2. **Revisar cambios** `git status`
3. **Agregar cambios** `git add`
4. `git commit`
5. **Subir cambios** con `git push`

## Recursos adicionales

* **Recomendado**: [Libro oficial de Git](https://git-scm.com/book/en/v2)
* [Documentación oficial de Git](https://git-scm.com/doc)
* [GitHub Guides](https://guides.github.com/)

