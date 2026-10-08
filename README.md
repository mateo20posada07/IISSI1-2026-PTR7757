# FitManager_S.O_Edition

## Miembros del grupo L2-ABS-7

1. Posada Quintero, Mateo
2. Herrero González, María del Pilar
3. Pablo Morales, Adrián
4. González García, Valeria

## 1. Introducción al problema

# 1. Introducción al problema
# 1. Introducción y Planteamiento del Problema

**FitManager** es una plataforma integral de gestión diseñada para centros deportivos. Su modelo operativo abarca áreas de musculación, entrenamiento funcional y una oferta variada de disciplinas dirigidas (como Spinning, Pilates o Yoga). La dinámica diaria del centro implica la interacción constante de cuatro perfiles de usuario: equipo de administración, cuerpo técnico/monitores, personal de mantenimiento y servicios, y los propios socios.

Actualmente, el gimnasio opera mediante un modelo híbrido basado en procesos manuales y soluciones informáticas aisladas. Esta falta de integración genera serios cuellos de botella e ineficiencias operativas que afectan directamente a la calidad del servicio:

* **Saturación y falta de control en los accesos:** El control en recepción se basa en la verificación visual de carnés por parte del personal, lo que provoca aglomeraciones constantes en las horas de mayor afluencia. Asimismo, la instalación carece de un sistema electromecánico automatizado (tornos con validación por NFC) capaz de bloquear la entrada a usuarios con cuotas pendientes o abonos suspendidos, o de restringir el paso continuado con un mismo distintivo en intervalos breves.

  ![Tornos electromecánicos con lector NFC](https://encrypted-tbn0.gstatic.com/licensed-image?q=tbn:ANd9GcSwWoastgeLAevmZ_27i1htmD9ICODWeohSq96N_g8s22XSCE2igpC_akFpnP-4HfdYVxFEICbfbpewU_E)

* **Deficiente organización de las actividades dirigidas:** La reserva de plazas se gestiona de forma presencial, un método propenso al exceso de aforo en las sesiones más demandadas o a la reserva de plazas que finalmente quedan desiertas. Por otro lado, el personal instructor no dispone de un medio en tiempo real para verificar el listado definitivo de asistentes antes de iniciar la sesión.

* **Desconexión en la gestión de cobros e impagados:** La emisión de facturas y el cobro de mensualidades se tramitan de manera independiente al expediente de cada socio. Esta desconexión complica el seguimiento de las devoluciones bancarias y dificulta la detección temprana de saldos deudores.

* **Mantenimiento reactivo de la maquinaria:** El reporte de averías o desperfectos en el equipamiento se realiza verbalmente o mediante partes en papel. Esto deriva en un seguimiento deficiente de los tiempos de reparación y en la imposibilidad de llevar un historial de incidencias por máquina que ayude a planificar su sustitución.

---

### Expectativas del Sistema

La implementación de la plataforma **FitManager** tiene como propósito centralizar y automatizar la gestión global del centro deportivo. A partir del análisis de las necesidades del gimnasio, las metas del nuevo sistema se articulan según las expectativas de cada perfil involucrado:

* **Perspectiva del Socio:** Contar con una plataforma intuitiva para revisar sus cuotas y contratos, verificar la disponibilidad real de plazas en las actividades colectivas, formalizar sus reservas y acceder al centro de forma ágil mediante tornos con lectores NFC.
* **Perspectiva de la Administración:** Disponer de una visión centralizada del expediente de socios y empleados, gestionar la oferta de tarifas, auditar los registros de paso físico, llevar el control automatizado de la facturación y aplicar restricciones de acceso en función del estado contable del usuario.
* **Perspectiva del Monitor:** Disponer de una herramienta donde consultar su cuadrante de clases asignadas —previniendo solapamientos de horario— y acceder al listado actualizado aforo de cada sesión.
* **Perspectiva del Personal de Mantenimiento:** Disponer de un canal unificado para la recepción de avisos de avería, facilitando la ordenación por prioridad, el seguimiento del estado de reparación de los equipos y la consulta de su historial.
## 2. Glosario de términos

- Términos específicos del dominio del problema, ordenados alfabéticamente. Se valorará la presencia de información multimedia.

## 3. Visión general del sistema

### 3.1. Requisitos generales

### 3.2. Usuarios del sistema

## 4. Catálogo de requisitos

### 4.1. Requisitos funcionales

#### R.F.01. Listar socios por estado

Como administrador quiero listar los socios filtrando por estado (alta, baja o suspendido) para conocer la situación de la base de socios.

**Prueba de aceptación**

- El listado muestra DNI, nombre, apellidos, teléfono, email y estado de cada socio.
- Al filtrar por un estado, solo aparecen los socios con ese estado.
- Si ningún socio cumple el filtro, el sistema muestra un listado vacío.

#### R.F.02. Consultar el historial de accesos de un socio

Como administrador quiero consultar los accesos de un socio a las instalaciones para revisar su asistencia y los intentos de entrada denegados.

**Prueba de aceptación**

- Se muestran fecha, hora exacta, torno de entrada y resultado de cada acceso.
- Los accesos aparecen ordenados del más reciente al más antiguo.
- Al filtrar por rango de fechas o por resultado, solo se muestran los accesos que lo cumplen.

#### R.F.03. Listar recibos por estado de pago

Como administrador quiero listar los recibos filtrando por estado (pendiente, pagado o devuelto) para controlar los impagos y las devoluciones.

**Prueba de aceptación**

- Cada recibo muestra número, fecha de emisión, fecha de pago (si existe), importe, método de pago, estado y socio.
- Al filtrar por estado, solo aparecen los recibos de ese estado.
- Se puede acotar el listado por rango de fechas de emisión.

#### R.F.04. Consultar mis pagos

Como socio quiero consultar mis recibos y la tarifa que tengo contratada para saber qué he pagado y qué me falta por pagar.

**Prueba de aceptación**

- Se muestran únicamente los recibos del socio que consulta.
- Se muestra el nombre, el precio y la periodicidad de su tarifa.
- Se distinguen claramente los recibos pendientes de los pagados.

#### R.F.05. Consultar las clases colectivas con plazas disponibles

Como socio quiero listar las clases colectivas programadas con las plazas libres que quedan para elegir a cuál quiero asistir.

**Prueba de aceptación**

- Cada clase muestra disciplina, fecha, hora de inicio, hora de fin, sala, monitor y plazas libres (aforo máximo menos reservas confirmadas).
- Se puede filtrar por disciplina y por fecha.

#### R.F.06. Consultar mis reservas

Como socio quiero consultar mis reservas de clases colectivas y su estado (confirmada o cancelada) para recordar a qué clases tengo que ir.

**Prueba de aceptación**

- Se muestran solo las reservas del socio que consulta, con la clase asociada y la fecha de reserva.
- Al filtrar por estado, solo aparecen las reservas de ese estado.
- Las reservas aparecen ordenadas por fecha de la clase.

#### R.F.07. Consultar la lista de asistentes de una clase

Como monitor quiero consultar el número de socios con reserva confirmada en una de mis clases para saber cuántas personas van a asistir.

**Prueba de aceptación**

- Solo se puede consultar una clase impartida por el propio monitor.
- Las reservas canceladas no se tienen en cuenta.
- Se muestra el total de asistentes frente al aforo máximo.

#### R.F.08. Consultar mi horario de clases

Como monitor quiero listar las clases que imparto, ordenadas por fecha y hora para organizar mi jornada.

**Prueba de aceptación**

- Se muestran disciplina, fecha, hora de inicio, hora de fin y sala de cada clase.
- Se puede filtrar por rango de fechas.
- Solo aparecen las clases del monitor que consulta.

#### R.F.09. Listar averías pendientes de resolver

Como personal de limpieza/mantenimiento quiero listar las averías sin resolver con la máquina afectada para priorizar las reparaciones.

**Prueba de aceptación**

- Cada avería muestra código y nombre de la máquina, ubicación, fecha de reporte y descripción del fallo.
- Solo aparecen las averías no resueltas.
- Se ordenan de la más antigua a la más reciente.

#### R.F.10. Consultar el historial de averías de una máquina

Como personal de limpieza/mantenimiento quiero consultar todas las averías que ha tenido una máquina para detectar las que fallan con más frecuencia.

**Prueba de aceptación**

- Se muestran fecha de reporte, descripción, estado, si está resuelta y fecha de reparación.
- Se incluyen tanto las averías resueltas como las pendientes.
- Se muestra el número total de averías de la máquina.

#### 4.1.1. Requisitos de información

##### R.I.01. Registro y Expediente del Socio
Como **Administrador**,  quiero **almacenar y consultar el expediente completo de cada socio**  para **gestionar sus datos personales, controlar el estado de su cuenta y vincular sus credenciales físicas de acceso**.

**Pruebas de aceptación**
- El sistema debe verificar que el DNI, el Email y el código del dispositivo NFC introducidos no pertenezcan a un usuario ya registrado en la base de datos.
- Se debe guardar obligatoriamente: DNI, Nombre, Apellidos, Teléfono, Email, Fecha de Nacimiento, Dirección, Estado (`Alta`, `Baja`, `Suspendido`), Código de Llavero/Tarjeta NFC asignado y la Tarifa contratada.
- Se debe vincular el identificador único del llavero NFC (`UID_NFC`) al socio para autorizar el paso en los tornos.


##### R.I.02. Expediente e Historial de Trabajadores
Como **Administrador**, quiero **registrar los datos personales, contractuales y la especialización de cada empleado** para **gestionar la plantilla del gimnasio y organizar la asignación de tareas o clases**.

**Pruebas de aceptación**
- El sistema debe verificar que el DNI y el IBAN del trabajador no estén previamente registrados.
- Se debe guardar obligatoriamente: DNI, Nombre completo, Teléfono, Email, IBAN, NUSS y Salario Base.
- En caso de ser *Monitor*, se debe registrar su área de especialidad deportiva.
- En caso de ser *Personal de Limpieza o Mantenimiento*, se debe registrar su turno de trabajo y zona asignada.


##### R.I.03. Catálogo de Tarifas y Oferta Comercial
Como **Administrador**, quiero **definir y mantener actualizado el catálogo de tarifas y cuotas** para **establecer los precios, periodicidad de cobro y condiciones de uso del gimnasio**.

**Pruebas de aceptación**
- El sistema debe comprobar que el Nombre de la tarifa sea único en el catálogo.
- Se debe guardar obligatoriamente: Nombre de la tarifa, Precio, Periodicidad (número de meses: 1 para mensual, 12 para anual) y un booleano sobre si incluye o no acceso a las clases colectivas.


##### R.I.04. Historial de Pagos y Transacciones
Como **Administrador**, quiero **almacenar los registros de todos los cobros y recibos emitidos** para **llevar el control de la facturación, identificar impagos y gestionar vías de cobro**.

**Pruebas de aceptación**
- El sistema debe generar un Número de Recibo secuencial y único para cada transacción.
- Se debe guardar obligatoriamente: Número de Recibo, Socio asociado, Tarifa cobrada, Fecha de Emisión, Fecha de Pago, Importe, Método de Pago (`Tarjeta`, `Efectivo`, `Domiciliación`) y Estado del Pago (`Pendiente`, `Pagado`, `Devuelto`).


##### R.I.05. Registro de Fichajes y Accesos Físicos
Como **Sistema de Control de Acceso**, quiero **almacenar cada intento de lectura del llavero NFC en el torno de entrada** para **mantener la trazabilidad de afluencia y verificar el cumplimiento de las políticas de acceso**.

**Pruebas de aceptación**
- El sistema debe registrar de forma automática la Fecha y Hora exacta de cada lectura del dispositivo NFC.
- Se debe guardar obligatoriamente: ID del Socio (asociado al `UID_NFC`), Fecha, Hora exacta, Torno de entrada y Resultado del acceso (`Permitido`, `Denegado`).


##### R.I.06. Planificación de Clases Colectivas
Como **Monitor**, quiero **consultar la programación de las clases asignadas y el listado de reservas** para **impartir la actividad conociendo el número de plazas ocupadas**.

**Pruebas de aceptación**
- Para cada clase colectiva programada se debe guardar: Disciplina, Fecha, Hora de Inicio, Hora Fin, Sala asignada, Aforo máximo y Monitor responsable.
- Para cada reserva vinculada a la clase se debe guardar: Socio solicitante, Fecha de Reserva y Estado de la reserva (`Confirmada`, `Cancelada`).


##### R.I.07. Parte de Incidencias de Maquinaria
Como **Personal de Mantenimiento**, quiero **registrar y consultar el estado de las máquinas averiadas o en revisión** para **planificar las tareas de reparación y coordinar el estado de las instalaciones**.

**Pruebas de aceptación**
- El sistema debe guardar obligatoriamente: Código de la máquina, Nombre, Marca, Ubicación, Estado (`Operativa`, `Averiada`, `En Mantenimiento`), Fecha de Reporte, Descripción del fallo y un indicador booleano de si está resuelta (adjuntando la Fecha de reparación en caso afirmativo).

#### 4.1.2. Reglas de negocio

##### R.N.01. Tiempo mínimo entre accesos

 No se podrá acceder por el torno más de una vez con el mismo NFC hasta que no hayan transcurrido 4 horas de su último uso.

##### R.N.02. Límite de reservas por aforo

El número de reservas confirmadas para una clase no puede superar el aforo disponible.

##### R.N.03. No duplicidad de horarios del monitor

Un monitor no puede tener asignadas dos clases cuyo día y hora se solapen.

##### R.N.04. Acceso condicionado al estado del socio

Un socio solo puede acceder al centro si su cuenta está en estado "Alta" y no tiene recibos impagados. Si está en "Baja" o "Suspendida", el torno deniega la entrada.

##### R.N.05. Asignación de tareas según el tipo de trabajador

Solo los trabajadores de tipo "Monitor" pueden ser asignados como responsables de clases. El personal de Limpieza/Mantenimiento solo puede tener asignados turnos y tareas de mantenimiento, y no clases.

##### R.N.06. No solapamiento de clases en una misma sala

Una sala no puede tener programadas dos clases cuyo día y hora se solapen. Además, la clase debe impartirse en una sala adecuada a su disciplina (por ejemplo, Spinning en la sala de Spinning).


### 4.2. Mapa de historias de usuario (opcional)

### 4.3. Requisitos no funcionales (opcional)

**R.N.F. 01. Título requisito no funcional**
Como [tipo de usuario]
quiero [servicio]
para [razón]

-- fin entregable 1 --

## 5. Modelo conceptual

### 5.1. Diagramas de clases UML

- con restricciones.

### 5.2. Escenarios de prueba

- con descripción textual y diagrama de objetos UML.

## 6. Matrices de trazabilidad

- Matriz de trazabilidad entre los elementos del modelo conceptual y los requisitos.

|       | EntidadX   | AsociaciónX  | RestricciónX  | Entidad2 ...   | 
|:------|:-----------|:-----------|:-----------|:-----------|
| RI-1  | X          | X          | X          | X          |
| RI-2  |            | X          |            | X          |
| RF-1  |            | X          |            | X          |
| RF-2  | X          |            | X          | X          |
| RN-1  |            | X          |            |            |
| RN-2  | X          | X          | X          |            |
| ...   |            |            |            |            |

-- fin entregable 2 --

## 7. Modelo relacional en 3FN

- Relaciones obtenidas al aplicar la transformación del modelo conceptual.

### 7.1.  Justificación de la estrategia de transformación de jerarquías

- si se identificaron jerarquías en el MC.


### 8. Matriz de trazabilidad MC/SQL (opcional):

- Restricciones sobre el MC / Elementos del modelo tecnológico (SQL) (Triggers, checks, etc.)
- Incluir Reglas de negocio — Constraints/Triggers en las matrices de trazabilidad para el entregable 3

|       | EntidadX   | AsociaciónX  | RestricciónX  | Entidad2 ...   | 
|:-------|:-------|:-------|:-------|:-------|
| TABLA-1 |        |        |        |        |
| TABLA-2 |        |        |        |        |
| TABLA-3 |        |        |        |        |
| TABLA-4 |        |        |        |        |
| TRIG-1 |        |        |        |        |
| TRIG-2 | X      | X      |        | X      |
| TRIG-3 |        | X      |        | X      |
| TRIG-4 |        |        | X      |        |
| CONST-1 |        |        |        |        |
| CONST-2 | X      | X      |        | X      |
| CONST-3 |        | X      |        | X      |
| CONST-4 |        |        | X      |        |

Se consideran todo tipo de constraints declarativas (aquellas definidas durante el CREATE TABLE).
-- fin entregable 3 --

## Referencias


