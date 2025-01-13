---
title: Introduction
sidebar: mydoc_sidebar
permalink: mydoc_introduction.html
folder: mydoc
---

# Introducción a Docker  
**UD 01: Introducción a los contenedores y a Docker**

**Licencia:**  
Reconocimiento – NoComercial - CompartirIgual (BY-NC-SA). No se permite un uso comercial de la obra original ni de sus posibles derivadas. La distribución debe hacerse bajo la misma licencia.
**Autor:** Sergi García Barea  
---

## Índice de contenido
1. [Introducción](#1-introducción)  
2. [Conceptos previos](#2-conceptos-previos)  
   - [Virtualización](#21-virtualización)  
   - [¿Qué es una máquina virtual?](#22-qué-es-una-máquina-virtual)  
   - [¿Qué es una máquina virtual de proceso?](#23-qué-es-una-máquina-virtual-de-proceso)  
   - [¿Qué es un hipervisor?](#24-qué-es-un-hipervisor)  
3. [Contenedores](#3-contenedores)  
   - [¿Qué son los contenedores?](#31-qué-son-los-contenedores)  
   - [Analogía con contenedores marítimos](#32-analogía-con-contenedores-de-transporte-marítimo)  
   - [Desarrollo y despliegue de aplicaciones](#33-contenedores-para-desarrollo-y-despliegue-de-aplicaciones)  
   - [Despliegue de servicios](#34-contenedores-para-despliegue-de-servicios)  
   - [Ventajas e inconvenientes](#35-ventajas-e-inconvenientes-del-uso-de-contenedores)  
   - [Resumen](#36-en-resumen-cuándo-es-adecuado-usar-contenedores)  
4. [Contenedores en sistemas Linux](#4-contenedores-en-sistemas-linux)  
   - [Antecedentes en Unix](#41-es-nuevo-el-concepto-de-entornos-privados-en-sistemas-unix)  
   - [Sistemas modernos en Linux](#42-sistemas-privados-modernos-en-linux-contenedores)  
   - [Funcionamiento en Linux](#43-cómo-funcionan-los-contenedores-modernos-en-linux)  
   - [Creación manual](#44-puedo-poner-en-marcha-un-contenedor-linux-a-mano)  
   - [Compatibilidad con otros sistemas](#45-los-contenedores-linux-pueden-funcionar-en-sistemas-como-windows-o-macos)  
5. [Contenedores Docker](#5-contenedores-docker)  
   - [¿Qué es Docker?](#51-qué-es-docker)  
   - [Arquitectura Docker](#52-la-arquitectura-de-docker)  
6. [Docker en sistemas Windows y MacOS](#6-docker-en-sistemas-windows-y-macos)  
7. [Docker corriendo contenedores Windows y MacOS](#7-docker-corriendo-contenedores-windows-server-core-y-contenedores-macos)  
8. [Conclusión](#8-conclusión)  
9. [Bibliografía](#9-bibliografía)  
10. [Licencias de elementos externos](#10-licencias-de-elementos-externos-utilizados)  

---

## 1. Introducción  
En esta unidad exploraremos el concepto de contenedores, enfocándonos en contenedores Linux y, en particular, en Docker.

---

## 2. Conceptos previos  

### 2.1 Virtualización  
La virtualización abstrae hardware para crear recursos virtuales. Es usada en sistemas, desarrollo, análisis de malware, y más.  

### 2.2 ¿Qué es una máquina virtual?  
Permite simular una máquina física para probar software y configuraciones.  
Tipos principales:  
- Máquinas virtuales de proceso  
- Hipervisores  
- Contenedores (Docker pertenece a esta categoría)  

### 2.3 ¿Qué es una máquina virtual de proceso?  
Ejecuta programas diseñados para arquitecturas diferentes como procesos locales. Ejemplos:  
- **JVM:** Máquina virtual de Java  
- **Wine:** Ejecuta apps de Windows en otros sistemas  

### 2.4 ¿Qué es un hipervisor?  
Emula hardware para virtualizar sistemas operativos. Ejemplos:  
- VirtualBox  
- VMWare  

Más información: [Wikipedia - Hipervisor](https://es.wikipedia.org/wiki/Hipervisor)  

---

## 3. Contenedores  

### 3.1 ¿Qué son los contenedores?  
Virtualizan a nivel de sistema operativo en lugar de hardware.  
Más información: [OS-level virtualization](https://en.wikipedia.org/wiki/OS-level_virtualization)  

### 3.2 Analogía con contenedores de transporte marítimo  
Cumplen estándares que los hacen transportables independientemente del contenido.  

### 3.3 Contenedores para desarrollo y despliegue de aplicaciones  
- Facilitan la compilación y pruebas en diferentes entornos.  
- Integración con CI/CD (Continuous Integration/Continuous Delivery).  

### 3.4 Contenedores para despliegue de servicios  
Permiten replicar configuraciones localmente para despliegues en la nube.  

### 3.5 Ventajas e inconvenientes del uso de contenedores  
**Ventajas:**  
- Ocupan menos espacio.  
- Más rápidos que hipervisores.  

**Inconvenientes:**  
- Acceso a datos persistentes es más complejo.  
- Uso mayormente vía línea de comandos.  

### 3.6 En resumen ¿Cuándo es adecuado usar contenedores?  
- Pruebas rápidas.  
- Desarrollo con portabilidad entre local y nube.  

---

## 4. Contenedores en sistemas Linux  

### 4.1 ¿Es nuevo el concepto de entornos privados en sistemas Unix?  
No. Ejemplos históricos:  
- [Chroot](https://es.wikipedia.org/wiki/Chroot)  
- [Jail en FreeBSD](https://es.wikipedia.org/wiki/FreeBSD_jail)  

### 4.2 Sistemas privados modernos en Linux: contenedores  
Desde 2008 con LXC ([Linux Containers](https://linuxcontainers.org/)).  

### 4.3 ¿Cómo funcionan los contenedores modernos en Linux?  
Características del kernel utilizadas:  
- **Namespaces:** Aislan recursos.  
- **Cgroups:** Limitan recursos asignados.  

Más información: [Namespaces](https://en.wikipedia.org/wiki/Linux_namespaces) y [Cgroups](https://en.wikipedia.org/wiki/Cgroups)  

### 4.4 ¿Puedo poner en marcha un contenedor Linux “A mano”?  
Sí. Ejemplo: [Guía de Julia Evans](https://gist.github.com/jvns/ea2e4d572b4e2285148b8e87f70eed73)  

---

## 5. Contenedores Docker  

### 5.1 ¿Qué es Docker?  
Sistema de contenedores para Linux.  
Más información: [Docker](https://www.docker.com/)  

### 5.2 La arquitectura de Docker  
Componentes principales:  
- Cliente  
- Servidor  
- Tienda de imágenes  

---

## 6. Docker en sistemas Windows y MacOS  
Uso de Docker Desktop para optimización.

---

## 7. Docker corriendo contenedores Windows Server Core y MacOS  
Posibilidades para ejecutar sistemas operativos alternativos.  

---

## 8. Conclusión  
Docker facilita desarrollo, pruebas y despliegues con contenedores.  

---

## 9. Bibliografía  
1. [WizardZines: How containers work](https://wizardzines.com/zines/containers/)  
2. [Docker Docs](https://docs.docker.com/)  

---

## 10. Licencias de elementos externos utilizados  
- Figura 1: [Apache 2.0](https://github.com/docker/docker.github.io/blob/master/engine/images/architecture.svg)  
- Figura 2: [CC BY SA](https://commons.wikimedia.org/wiki/File:Docker-containerized-and-vm-transparent-bg.png)  
