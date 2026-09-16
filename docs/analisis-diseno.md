# Diseño y distribución de info - Análisis de diseño

**Título:** Documento de análisis y diseño - Sistema de préstamo de equipo del laboratorio

**Equipo 1 - Integrantes:** Arantza García Vázquez, Edna Samantha Cortés Carrisoza, Carlos Andrés Hernández Díaz, Marco Antonio Beltrán Rosales

**Fecha:** 14 de septiembre 2026

**Repositorio:** Proyecto-software

**Asignatura:** Diseño de Software. Otoño 2026

**Documentos de los que depende:** [backlog](./backlog.md), [decision-motor](./decision-motor.md), [modelo-datos](./modelo-datos.md), [modelo-documentos](./modelo-documentos.md)

---

## 1. Descripción del sistema

**¿Qué problema resuelve?**
El laboratorio presta equipo. Actualmente, el registro de los préstamos se realiza de forma manual en una libreta ubicada en el mostrador.

Este método es poco eficiente para el seguimiento de los equipos, ya que no permite consultar de manera inmediata qué equipo está prestado y quién lo tiene. Además, cuando un equipo es devuelto dañado, no existe un registro confiable que permita identificar al responsable, y los retrasos en las devoluciones suelen detectarse hasta que alguien solicita un equipo que no se encuentra disponible.


**¿Para quién?**
El usuario principal del sistema es el administrador del laboratorio, quien se encarga de registrar y autorizar los préstamos, así como de recibir los equipos devueltos. 
Los prestatarios, que pueden ser alumnos o profesores (reciben el mismo tratamiento dentro del sistema), pueden consultar sus préstamos y realizar solicitudes de equipo.

**¿Qué no va a hacer el sistema?**

Información tomada de MoSCoW, disponible en el [backlog](./backlog.md).

1. Enviar notificaciones al admin de lab cuando el material sea devuelto.
2. Envío automatizado de correos de confirmación.
3. Generar reportes manuales.
4. Notificar a los usuarios para saber si tienen un material apartado.

---

## 2. Backlog priorizado

**Backlog completo:** [backlog](./backlog.md)

| Prioridad  | Número | Historia                                                                                                                                                     |
| ---------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Must**   | HU08   | Como administrador de laboratorio, quiero consultar y gestionar los préstamos, para mantener el control del equipo del laboratorio.                          |
| **Must**   | HU09   | Como estudiante, quiero solicitar material del laboratorio, para utilizarlo durante mis prácticas.                                                           |
| **Must**   | HU25   | Como usuario, quiero autenticarme de forma segura, para proteger mi información personal y el acceso a mi cuenta.                                            |
| **Should** | HU01   | Como administrador, quiero consultar y modificar el inventario, para mantener actualizada la información de los materiales.                                  |
| **Should** | HU07   | Como estudiante, quiero consultar mi historial de préstamos, para realizar futuras aclaraciones y consultas.                                                 |
| **Should** | HU23   | Como jefe de laboratorio, quiero recibir una notificación cuando se devuelva un material, para actualizar su disponibilidad en el inventario.                |
| **Could**  | HU02   | Como usuario, quiero visualizar un carrito de materiales, para facilitar y hacer más intuitivo el proceso de préstamo.                                       |
| **Could**  | HU03   | Como usuario, quiero buscar y filtrar los materiales por materia, para encontrar fácilmente el material que necesito.                                        |
| **Could**  | HU31   | Como administrador, quiero generar reportes estadísticos, para apoyar la toma de decisiones y mejorar la gestión del laboratorio.                            |
| **Won't**  | HU30   | Como administrador, quiero enviar correos de confirmación de manera automatizada, para formalizar los préstamos realizados.                                  |
| **Won't**  | HU32   | Como usuario, quiero recibir correos de notificación antes de la fecha de vencimiento de un préstamo, para evitar exceder el plazo de devolución.            |
| **Won't**  | HU33   | Como usuario, quiero recibir una notificación cuando se registre un material que he aportado, para confirmar que mi aportación fue registrada correctamente. |

> **Nota:** Se dejaron fuera 4 historias de usuario del backlog original debido a que algunas eran redundantes con otras historias y, en otros casos, la redacción no permitía comprender claramente la funcionalidad solicitada.

### Justificación de las historias Won't
Las historias clasificadas como **Won't** no se consideran indispensables para el desarrollo del **MVP**, ya que corresponden principalmente a funcionalidades complementarias, como el envío de notificaciones y correos automatizados. Aunque estas funciones pueden mejorar la experiencia de los usuarios y facilitar el seguimiento de los préstamos, el sistema puede cumplir con sus funciones principales sin incluirlas en la primera versión. Por ello, se consideran funcionalidades que pueden implementarse en versiones posteriores.

### Requisitos no funcionales

| Número   | Verificación (¿cómo se verifica?)                                                                                                                                        | Formulación (enunciado)                                                                                                                                              |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **RNF1** | **Prueba:** intentar acceder a una cuenta utilizando credenciales válidas, incorrectas y vacías, verificando que únicamente las credenciales válidas permitan el acceso. | El sistema deberá proporcionar un acceso seguro a las cuentas de usuario para proteger su información sensible.                                                      |
| **RNF2** | **Prueba:** realizar las operaciones principales —consulta, búsqueda, solicitud y devolución— utilizando únicamente el teclado, sin necesidad de utilizar el mouse.      | El sistema deberá permitir que el usuario navegue y utilice las funciones principales mediante teclado, facilitando el acceso a personas con diferentes capacidades. |
| **RNF3** | **Inspección:** revisar el registro de respaldos y comprobar que exista al menos un respaldo válido dentro de cada periodo de 24 horas.                                  | El sistema deberá respaldar la información para evitar su pérdida en caso de emergencia.                                                                             |
| **RNF4** | **Prueba:** registrar un préstamo o devolución y medir el tiempo transcurrido hasta que el cambio en la disponibilidad sea visible para el usuario.                      | El sistema deberá actualizar la disponibilidad de los materiales en tiempo real para que los estudiantes conozcan su disponibilidad actual.                          |

---

## 3. Modelado de datos

**Forma:** Relacional (SQL)

**Modelado completo:** [modelo-datos](./modelo-datos.md), [modelo-documentos](./modelo-documentos.md), [motor-decision](./motor-decision.md)

### Modelado de datos

| Entidad | Campos |
|---|---|
| **Administrador** | `id_administrador` (PK), `id_usuario` (FK), `estado_acceso` (string), `nivel_acceso` (bool) |
| **Usuario** | `id_usuario` (PK), `tipo_usuario` (string), `nombre` (string), `apellido_paterno` (string), `apellido_materno` (string), `correo` (string), `contraseña` (string), `matricula` (int, UNIQUE), `telefono` (string), `estado_de_cuenta` (bool) |
| **Préstamo** | `id_prestamo` (PK), `id_usuario` (FK), `id_material` (FK), `fecha_prestamo` (date), `fecha_limite` (date), `fecha_devolucion` (date), `estado_prestamo` (string), `observaciones` (string), `confirmacion_devolucion` (bool) |
| **Material** | `id_material` (PK), `nombre_material` (string), `descripcion` (string), `materia` (string), `cantidad` (int), `estado` (bool), `condicion` (string), `disponibilidad` (bool), `costo_reposicion` (float), `fecha_registro` (date) |