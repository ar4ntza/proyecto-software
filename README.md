> **Versión 1.0 — Actualizada el 16 de septiembre de 2026**
>
> Esta documentación corresponde a la primera versión del proyecto. Los modelos, requisitos, decisiones de diseño y funcionalidades descritas pueden modificarse conforme avance el análisis y desarrollo del sistema.

# Sistema de Préstamo de Equipo del Laboratorio

**Diseño de Software · Otoño 2026 · IBERO Puebla**

> Proyecto académico de análisis, diseño y modelado de un sistema para la gestión de préstamos de equipo y materiales de laboratorio.

---

## Sobre el proyecto

El **Sistema de Préstamo de Equipo del Laboratorio** surge a partir de la necesidad de organizar y facilitar el control de los materiales utilizados en las prácticas académicas.

Actualmente, el proceso de préstamo se lleva a cabo mediante registros manuales, lo que puede dificultar la consulta de los materiales disponibles, identificar quién tiene un equipo prestado y dar seguimiento a las fechas de devolución.

La propuesta busca centralizar esta información y establecer una estructura que permita gestionar de manera más clara los **usuarios, administradores, materiales y préstamos**.

---

## Objetivo

Diseñar una solución que permita gestionar el proceso de préstamo de materiales del laboratorio, considerando las necesidades de los usuarios y administradores, así como los requisitos funcionales y no funcionales identificados durante el análisis.

El proyecto contempla tanto el **modelo relacional** como una alternativa de **modelo orientado a documentos**, con el propósito de analizar las opciones de almacenamiento y fundamentar la selección del motor de base de datos.

---

## Alcance inicial

Para la primera versión, el sistema considera principalmente:

- Autenticación segura de usuarios.
- Solicitud de materiales de laboratorio.
- Gestión y consulta de préstamos.
- Consulta y modificación del inventario.
- Consulta del historial de préstamos.
- Control de la disponibilidad de los materiales.

Las funcionalidades complementarias que no forman parte del alcance inicial se mantienen identificadas dentro del backlog para futuras versiones.

---

## Equipo


| Integrantes |
|---|
| Arantza García Vázquez |
| Edna Samantha Cortés Carrisoza |
| Carlos Andrés Hernández Díaz |
| Marco Antonio Beltrán Rosales |

---

## Documentación

La documentación del proyecto se encuentra organizada dentro de la carpeta `docs/`, donde cada archivo aborda una parte específica del análisis y diseño.

| Documento | Contenido |
|---|---|
| [`analisis-diseno.md`](docs/analisis-diseno.md) | Análisis general del problema, alcance, backlog y requisitos no funcionales. |
| [`backlog.md`](docs/backlog.md) | Historias de usuario y priorización de funcionalidades mediante MoSCoW. |
| [`modelo-datos.md`](docs/modelo-datos.md) | Modelo de datos relacional, entidades, atributos, relaciones y reglas de negocio. |
| [`modelo-documentos.md`](docs/modelo-documentos.md) | Propuesta alternativa utilizando un modelo orientado a documentos. |
| [`decision-motor.md`](docs/decision-motor.md) | Comparación y justificación de la decisión sobre el motor de base de datos. |

---

## Modelo del sistema

El modelo relacional está compuesto por cuatro entidades principales:

**USUARIO · ADMINISTRADOR · PRESTAMO · MATERIAL**

Estas entidades permiten representar los elementos principales involucrados en el proceso de préstamo y establecer las relaciones necesarias para consultar quién realiza un préstamo, qué material se encuentra asociado y cuál es su estado.

El modelo completo se encuentra en [`modelo-datos.md`](docs/modelo-datos.md).

---

## Requisitos no funcionales

Además de las funcionalidades del sistema, se consideran aspectos relacionados con:

- **Seguridad:** acceso mediante credenciales válidas.
- **Accesibilidad:** navegación de las operaciones principales mediante teclado.
- **Respaldo:** disponibilidad de al menos un respaldo válido cada 24 horas.
- **Disponibilidad:** actualización de la disponibilidad del material después de realizar un préstamo o devolución.

---

## Estructura del repositorio

```text
.
├── docs/
│   ├── analisis-diseno.md
│   ├── backlog.md
│   ├── decision-motor.md
│   ├── modelo-datos.md
│   └── modelo-documentos.md
│
├── .gitignore
├── LICENSE
└── README.md