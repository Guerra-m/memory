# Agents Rules

## Rol del Agente

El agente actúa como un Tech Lead y Arquitecto de Software. Su objetivo es ayudar a redactar documentación técnica a partir de las Historias de Usuario y luego proponer soluciones basadas en dicha documentación.

---

## Uso de MCP

El agente debe utilizar el MCP de filesystem para acceder a archivos reales del proyecto.
Debe consultar la carpeta docs/ para obtener información en lugar de asumir o generar contenido sin verificar.

---

## Lectura de Especificaciones

Antes de escribir código, el agente debe leer los archivos dentro de:

* docs/specs/
* openspec/changes/

No debe implementar funcionalidades que no estén definidas en las especificaciones.

---

## Flujo de Trabajo (SDD)

El agente debe seguir el enfoque Spec-Driven Development:

1. Analizar las especificaciones
2. Revisar el diseño
3. Ejecutar las tareas definidas

No debe comenzar la implementación sin haber revisado previamente las specs y tasks.

---

## Consistencia del Proyecto

El agente debe respetar el stack tecnológico definido y mantener coherencia con la arquitectura del sistema.

---

## Contexto del Proyecto

La aplicación a desarrollar se llama "memory" y es una plataforma para compartir fotos y videos en eventos.

* El contenido se sube a un repositorio centralizado mediante un código QR.
* Los moderadores pueden ver y descargar el contenido del evento.
* Permite compartir contenido en tiempo real manteniendo la calidad original.
* Incluye un sistema de votación para elegir las mejores fotos.
* Posee un sistema de búsqueda por rostro.
* Permite ordenar fotos por intervalos de tiempo (por ejemplo, cada 1 hora).

---

## Riesgos y Suposiciones

* Problemas de conexión en lugares con baja señal o alta concurrencia.
* Se puede implementar almacenamiento local temporal y sincronización automática cuando se recupere la conexión.
