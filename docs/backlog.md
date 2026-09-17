>Se consume en: [Documento de Análisis y Diseño](./analisis-diseno)
## Historias de usuario priorizadas (MoSCoW)

### Must have
#### Admin. Lab.
- Como **Administrador de laboratorio**, quiero revisar los préstamos, para tener control del equipo del lab.
- Como **Administrador de laboratorio**, quiero un inventario, para tener un control de él.
- Como **Administrador de laboratorio**, quiero registrar un equipo disponible, para meterlo al inventario.
- Como **Administrador de laboratorio**, quiero modificar la información del inventario, para mantener los datos actualizados.
- ~~Como **Administrador de laboratorio**, quiero un sistema para prestar material, para poder prestar material del lab.~~
- Como **Administrador de laboratorio**, quiero respaldar la información, para no perderla en caso de emergencia.

#### Usuario
- Como **Usuario** quiero saber la cantidad de materiales disponibles, para decidir si aportar o no material.
- Como **Usuario**, quiero solicitar material del lab, para utilizarlo en el laboratorio.
- ~~Como **Usuario**, quiero pedir un material, para usarlo.~~
- Como **Usuario**, quiero tener un acceso seguro a mi cuenta, para que mi información sensible no tenga un mal uso.
- ~~Como **Usuario**, quiero consultar los materiales disponibles, para saber qué puedo pedir.~~
### Should have
#### Admin. Lab.
- Como **Administrador de laboratorio**, quiero un historial de préstamos, para tener trazabilidad de los materiales.
- Como **Administrador de laboratorio**, quiero que el usuario no pueda registrar una devolución sin confirmarlo, para mantener el registro coherente.
- ~~Como **Administrador de laboratorio**, quiero un registro de préstamos, para ubicar el paradero del equipo.~~

#### Usuario
 - Como **Usuario** quiero una vista de "carrito", para facilitar el proceso de préstamo haciéndolo más intuitivo y cómodo.
- Como **Usuario** quiero buscar y filtrar el material por materia, para encontrar más fácil los materiales.
- Como **Usuario**, quiero consultar los préstamos activos, para conocer qué materiales tengo.
- Como **Usuario**, quiero consultar la fecha límite de devolución, para saber cuándo entregar el material.

### Could have
#### Admin. Lab.
- Como **Administrador de laboratorio**, quiero generar un reporte del uso del material, para llevar un control periódico y tomar decisiones informadas.
- Como **Administrador de laboratorio** quiero saber el historial de movimientos, para saber qué alumno hizo mal uso del material y aplicar el cobro correspondiente.
- Como **Administrador de laboratorio**, quiero saber el estado actual del material, para mantenerlo en buenas condiciones.

#### Usuario
- Como **Usuario**, quiero consultar la disponibilidad del material en tiempo real, para saber qué puedo solicitar antes de acudir al laboratorio.
- Como **Usuario**, quiero acceso a mi historial de préstamos, para futuras aclaraciones y consultas.
- Como **Usuario**, quiero una confirmación de que el material fue devuelto en tiempo y forma, para fundamentar que el material ha sido devuelto.
- Como **Usuario**, quiero recibir una notificación por correo cuando se acerque la fecha límite de mi préstamo, para evitar excederme del plazo.

### Won't have
#### Admin. Lab.
- Como **Administrador de laboratorio**, quiero una notificación cuando se devuelva el material, para actualizar el inventario.
- Como **Administrador de laboratorio**, quiero que se envíen automáticamente correos de confirmación al registrar un préstamo, para formalizar el proceso sin intervención manual.
- Como **Administrador de laboratorio**, quiero generar un reporte manual, para generar estadísticas y mejorar la toma de decisiones.