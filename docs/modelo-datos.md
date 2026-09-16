# Modelo de datos relacional — Sistema de préstamo de equipo del laboratorio

> Se consume en: [documento de análisis y diseño](./analisis-diseno.md) · Se compara con: [modelo de documentos](./modelo-documentos.md) · Decisión en: [decisión de motor](./decision-motor.md)

## Entidades

| Entidad | Campos | Nota |
| --- | --- | --- |
| `usuario` | `id_usuario`, `tipo_usuario`, `nombre`, `apellido_paterno`, `apellido_materno`, `correo`, `contraseña`, `matricula`, `telefono`, `estado_de_cuenta` | Registra la información de los usuarios del sistema. |
| `administrador` | `id_administrador`, `id_usuario`, `nivel_acceso`, `estado` | Registra la información administrativa asociada a un usuario. |
| `prestamo` | `id_prestamo`, `id_usuario`, `id_material`, `fecha_prestamo`, `fecha_limite`, `fecha_devolucion`, `estado_prestamo`, `observaciones`, `confirmacion_devolucion` | Registra los préstamos realizados por los usuarios y su seguimiento. |
| `material` | `id_material`, `nombre_material`, `descripcion`, `materia`, `cantidad`, `estado`, `condicion`, `disponibilidad`, `costo_reposicion`, `fecha_registro` | Registra los materiales que forman parte del inventario del laboratorio. |

## Relaciones

1. Un `usuario` tiene un `administrador`.
2. Un `usuario` puede realizar cero o varios `prestamos`.
3. Un `prestamo` pertenece a un `usuario`.
4. Un `material` puede estar incluido en cero o varios `prestamos`.
5. Un `prestamo` incluye un `material`.
6. `administrador.id_usuario` referencia a `usuario.id_usuario`.
7. `prestamo.id_usuario` referencia a `usuario.id_usuario`.
8. `prestamo.id_material` referencia a `material.id_material`.

## Reglas de negocio

1. Los usuarios del sistema se identifican mediante `id_usuario`.
2. La matrícula del usuario debe ser única.
3. Un usuario puede realizar múltiples préstamos.
4. Cada préstamo se encuentra asociado con un usuario y un material.
5. Un material puede aparecer en diferentes préstamos.
6. Los préstamos registran su fecha de realización mediante `fecha_prestamo`.
7. Cada préstamo registra una fecha límite mediante `fecha_limite`.
8. La fecha en que se devuelve un material se registra mediante `fecha_devolucion`.
9. El estado de un préstamo se registra mediante `estado_prestamo`.
10. Las observaciones permiten almacenar información adicional relacionada con el préstamo.
11. `confirmacion_devolucion` permite registrar si la devolución ha sido confirmada.
12. La disponibilidad de un material se registra mediante `disponibilidad`.
13. La cantidad disponible de cada material se registra mediante `cantidad`.

## Claves y restricciones

| Entidad | Clave primaria | Clave foránea | Restricción |
| --- | --- | --- | --- |
| `usuario` | `id_usuario` | — | `matricula` es UNIQUE |
| `administrador` | `id_administrador` | `id_usuario` → `usuario.id_usuario` | Relación 1:1 con `usuario` |
| `prestamo` | `id_prestamo` | `id_usuario` → `usuario.id_usuario` | `id_material` → `material.id_material` |
| `material` | `id_material` | — | — |

## Tipos de datos

| Entidad | Campo | Tipo |
| --- | --- | --- |
| `usuario` | `id_usuario` | `int` |
| `usuario` | `tipo_usuario` | `string` |
| `usuario` | `nombre` | `string` |
| `usuario` | `apellido_paterno` | `string` |
| `usuario` | `apellido_materno` | `string` |
| `usuario` | `correo` | `string` |
| `usuario` | `contraseña` | `string` |
| `usuario` | `matricula` | `int` |
| `usuario` | `telefono` | `string` |
| `usuario` | `estado_de_cuenta` | `bool` |
| `administrador` | `id_administrador` | `int` |
| `administrador` | `id_usuario` | `int` |
| `administrador` | `nivel_acceso` | `string` |
| `administrador` | `estado` | `bool` |
| `prestamo` | `id_prestamo` | `int` |
| `prestamo` | `id_usuario` | `int` |
| `prestamo` | `id_material` | `int` |
| `prestamo` | `fecha_prestamo` | `date` |
| `prestamo` | `fecha_limite` | `date` |
| `prestamo` | `fecha_devolucion` | `date` |
| `prestamo` | `estado_prestamo` | `string` |
| `prestamo` | `observaciones` | `string` |
| `prestamo` | `confirmacion_devolucion` | `bool` |
| `material` | `id_material` | `int` |
| `material` | `nombre_material` | `string` |
| `material` | `descripcion` | `string` |
| `material` | `materia` | `string` |
| `material` | `cantidad` | `int` |
| `material` | `estado` | `bool` |
| `material` | `condicion` | `string` |
| `material` | `disponibilidad` | `bool` |
| `material` | `costo_reposicion` | `float` |
| `material` | `fecha_registro` | `date` |

## Relación con los requisitos no funcionales

| RNF | Relación con el modelo |
| --- | --- |
| **RNF1** | Los campos `correo`, `contraseña` y `estado_de_cuenta` de `usuario` se relacionan con el acceso a las cuentas. |
| **RNF2** | El requisito corresponde principalmente a la interfaz y navegación del sistema, por lo que no requiere un atributo específico en el modelo. |
| **RNF3** | La información almacenada en las entidades debe formar parte de los respaldos periódicos del sistema. |
| **RNF4** | Los campos `cantidad` y `disponibilidad` de `material` permiten registrar la información relacionada con la disponibilidad de los materiales. |

## Consideraciones

El modelo utiliza una estructura relacional en la que `usuario`, `administrador`, `prestamo` y `material` representan las principales entidades del sistema.

Las relaciones se establecen mediante claves foráneas. Un usuario puede realizar múltiples préstamos, mientras que cada préstamo se relaciona con un usuario y un material.

La entidad `administrador` mantiene una relación uno a uno con `usuario`, permitiendo asociar los permisos administrativos con una cuenta existente.

El modelo conserva la información de los préstamos mediante sus fechas, estado, observaciones y confirmación de devolución, mientras que la información relacionada con el inventario se concentra en `material`.