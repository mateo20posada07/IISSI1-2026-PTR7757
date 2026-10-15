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
* **Perspectiva del Monitor:** Disponer de una herramienta donde consultar su cuadrante de clases asignadas —previniendo solapamientos de horario— , acceder al listado actualizado aforo de cada sesión y notificar averías.
* **Perspectiva del Personal de Mantenimiento:** Disponer de un canal unificado para la recepción de avisos de avería, facilitando la ordenación por prioridad, el seguimiento del estado de reparación de los equipos y la consulta de su historial.

## 2. Glosario de términos
**Roles del sistema:**
* Administrador: Personal encargado de la gestión integral del centro.
* Monitor: Empleado responsable de impartir las clases colectivas y controlar el aforo en la sala.
* Personal de mantenimiento: Empleado encargado de la recepción, priorización y resolución de los partes de avería del equipamiento.
* Socio: Cliente del centro con permisos para consultar su estado contable, realizar reservas y acceder a las instalaciones.

**Planificación:**
* Aforo máximo: Número límite de asistentes permitidos en una clase colectiva o sala, determinado por motivos de capacidad y seguridad.
* Clase colectiva: Sesión deportiva programada en una fecha, horario, sala y disciplina concretas, impartida por un monitor.
* Disciplina: Especialidad deportiva que determina el tipo de sala y equipamiento requerido.
* Plazas libres: Número de vacantes disponibles para una clase colectiva o sala. Se calcula como la diferencia entre el aforo máximo y el número de reservas confirmadas.
* Reserva de plazas: Vinculación formal entre un socio y una clase colectiva que le garantiza la asistencia.
* Sala: Espacio físico del centro asignado a una clase colectiva, donde no se puede producir un solapamiento.
* Solapamiento: Conflicto horario que ocurre cuando se le asigna la misma hora y día a una misma sala o a un monitor en diferentes clases. 

**Control de acceso:**
* Dispositivo NFC: Credencial física, en forma de llavero o tarjeta, que debe llevar el socio para identificarse en el centro.
* Registro de acceso: Evento automático que registra la fecha, hora, torno y resultado del acceso de cada intento de paso del socio.
* Tiempo de carencia: Periodo mínimo de espera obligatorio (4 horas) entre dos usos seguidos del mismo dispositivo NFC.
* Torno de acceso: Dispositivo electromecánico que bloquea o permite el acceso tras validar el estado del socio.
* UID_NFC: Código alfanumérico único grabado en el dispositivo NFC y asociado a un único expediente del socio.

**Gestión económica:**
* Periodicidad: Duración del ciclo de facturación de una tarifa desde su activación hasta su renovación.
* Recibo: Documento de cobro generado a un socio, el cual incluye un número de recibo único, el importe, fecha de emisión, estado y método de pago.
* Tarifa: Oferta comercial contratada por el socio que define el precio, la periodicidad del cobro y los servicios que incluye.

**Equipamiento:**
* Máquina: Elemento físico diseñado para facilitar la realización de los ejercicios físicos, identificado de forma única mediante un código, una marca y una ubicación.
* Parte de avería: Registro digital para la notificación, priorización y seguimiento de la reparación de una máquina.

**Valores posibles de los estados:**
* Estado de acceso: Resultado de la validación en el torno. Puede ser: 
  *	PERMITIDO (cumple la cuota y el tiempo de carencia).
  *	DENEGADO (bloqueado por impago, cuenta suspendida o reintento de entrada antes de 4 horas).
* Estado de la máquina: Situación operativa del equipamiento del centro. Puede ser:
  *	OPERATIVA (está disponible).
  *	AVERIADA (tiene una incidencia reportada).
  *	EN MANTENIMIENTO (está en proceso de reparación).
* Estado de la reserva: Situación de la plaza de una clase colectiva. Puede ser:
  *	CONFIRMADA (el socio tiene su plaza reservada).
  *	CANCELADA (el socio ha dejado su plaza libre).
* Estado del pago: Situación financiera de un recibo. Puede ser:
  *	PENDIENTE (el pago ha sido emitido, pero no cobrado).
  *	PAGADO (el pago ha sido cobrado con éxito).
  *	DEVUELTO (el pago ha sido rechazado por el banco).
* Estado del socio: Situación administrativa del socio. Puede ser:
  *	ALTA (está activo y al corriente).
  *	BAJA (el socio ha sido desvinculado).
  *	SUSPENDIDO (el socio ha sido bloqueado por impago).


## 3. Visión general del sistema

### 3.1. Requisitos generales

- **RG.01. Gestión de usuarios:** El sistema tiene que guardar todos los datos personales y contratos tanto de los socios como de los trabajadores, controlando en todo momento si una cuenta está de alta, de baja o suspendida.

- **RG.02. Control de los tornos:** La aplicación se encargará de gestionar las entradas físicas al gimnasio leyendo el NFC de los socios. Solo abrirá el torno si el cliente está al corriente de pago y si ha pasado el tiempo mínimo obligatorio desde su última entrada.

- **RG.03. Pagos y tarifas:** El sistema debe controlar las distintas cuotas que ofrece el centro, generar los recibos y bloquear automáticamente el acceso y las reservas a los socios que devuelvan un recibo o dejen de pagar.

- **RG.04. Reservas y clases dirigidas:** Tiene que haber un horario donde los socios puedan apuntarse a las clases. El sistema se asegurará de que nunca se apunte más gente del aforo permitido en la sala y de que a los monitores no se les solapen las clases.

- **RG.05. Averías y mantenimiento:** La plataforma debe permitir registrar si una máquina se rompe, para que el personal de mantenimiento sepa qué reparar y quede guardado un historial de todas las incidencias del gimnasio.

### 3.2. Usuarios del sistema

**Socio:**
Cliente del gimnasio. Puede:

- Consultar su estado de cuenta y su NFC de acceso.
- Reservar y cancelar plazas en clases dirigidas.
- Consultar su historial de pagos.

**Monitor:**
Trabajador que imparte clases. Puede:

- Consultar su cuadrante de clases asignadas.
- Ver la lista de socios con reserva en sus clases.
- Notificar averías del material de su sala.

**Personal de Mantenimiento:**
Trabajador de limpieza y mantenimiento. Puede:

- Consultar sus turnos, zonas y tareas asignadas.
- Registrar y actualizar el estado de las averías.

**Administración:**
Responsable que gestiona el día a día comercial. Puede:

- Dar de alta, baja y suspender socios.
- Gestionar tarifas, cobros, remesas y recibos devueltos.
- Gestionar las salas y sus aforos.
- Asignar cuadrantes y clases.

## 4. Catálogo de requisitos

### 4.1. Requisitos funcionales

#### R.F.01. Listar socios por estado

Como **administrador** quiero **listar los socios filtrando por estado (alta, baja o suspendido)** para **conocer la situación de la base de socios.**

**Prueba de aceptación**

- El listado muestra DNI, nombre, apellidos, teléfono, email y estado de cada socio.
- Al filtrar por un estado, solo aparecen los socios con ese estado.
- Si ningún socio cumple el filtro, el sistema muestra un listado vacío.

#### R.F.02. Consultar el historial de accesos de un socio

Como **administrador** quiero **consultar los accesos de un socio a las instalaciones** para **revisar su asistencia y los intentos de entrada denegados.**

**Prueba de aceptación**

- Se muestran fecha, hora exacta, torno de entrada y resultado de cada acceso.
- Los accesos aparecen ordenados del más reciente al más antiguo.
- Al filtrar por rango de fechas o por resultado, solo se muestran los accesos que lo cumplen.

#### R.F.03. Listar recibos por estado de pago

Como **administrador** quiero **listar los recibos filtrando por estado (pendiente, pagado o devuelto)** para **controlar los impagos y las devoluciones.**

**Prueba de aceptación**

- Cada recibo muestra número, fecha de emisión, fecha de pago (si existe), importe, método de pago, estado y socio.
- Al filtrar por estado, solo aparecen los recibos de ese estado.
- Se puede acotar el listado por rango de fechas de emisión.

#### R.F.04. Consultar mis pagos

Como **socio** quiero **consultar mis recibos y la tarifa que tengo contratada** para **saber qué he pagado y qué me falta por pagar.**

**Prueba de aceptación**

- Se muestran únicamente los recibos del socio que consulta.
- Se muestra el nombre, el precio y la periodicidad de su tarifa.
- Se distinguen claramente los recibos pendientes de los pagados.

#### R.F.05. Consultar las clases colectivas con plazas disponibles

Como **socio** quiero **listar las clases colectivas programadas con las plazas libres que quedan** para **elegir a cuál quiero asistir.**

**Prueba de aceptación**

- Cada clase muestra disciplina, fecha, hora de inicio, hora de fin, sala, monitor y plazas libres (aforo máximo menos reservas confirmadas).
- Se puede filtrar por disciplina y por fecha.

#### R.F.06. Consultar mis reservas

Como **socio** quiero **consultar mis reservas de clases colectivas y su estado (confirmada o cancelada)** para **recordar a qué clases tengo que ir.**

**Prueba de aceptación**

- Se muestran solo las reservas del socio que consulta, con la clase asociada y la fecha de reserva.
- Al filtrar por estado, solo aparecen las reservas de ese estado.
- Las reservas aparecen ordenadas por fecha de la clase.

#### R.F.07. Consultar la lista de asistentes de una clase

Como **monitor** quiero **consultar el número de socios con reserva confirmada en una de mis clases** para **saber cuántas personas van a asistir.**

**Prueba de aceptación**

- Solo se puede consultar una clase impartida por el propio monitor.
- Las reservas canceladas no se tienen en cuenta.
- Se muestra el total de asistentes frente al aforo máximo.

#### R.F.08. Consultar mi horario de clases

Como **monitor** quiero **listar las clases que imparto, ordenadas por fecha y hora** para **organizar mi jornada.**

**Prueba de aceptación**

- Se muestran disciplina, fecha, hora de inicio, hora de fin y sala de cada clase.
- Se puede filtrar por rango de fechas.
- Solo aparecen las clases del monitor que consulta.

#### R.F.09. Listar averías pendientes de resolver

Como **personal de mantenimiento** quiero **listar las averías sin resolver con la máquina afectada** para **priorizar las reparaciones.**

**Prueba de aceptación**

- Cada avería muestra código y nombre de la máquina, ubicación, fecha de reporte y descripción del fallo.
- Solo aparecen las averías no resueltas.
- Se ordenan de la más antigua a la más reciente.

#### R.F.10. Consultar el historial de averías de una máquina

Como **personal de mantenimiento** quiero **consultar todas las averías que ha tenido una máquina** para **detectar las que fallan con más frecuencia.**

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
- En caso de ser *Personal de Mantenimiento*, se debe registrar su turno de trabajo y zona asignada.


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

**Pruebas de aceptación**
- Positiva: Dado un socio cuyo último acceso con su NFC fue a las 10:00, cuando lo usa de nuevo en el torno a las 14:30, entonces el acceso se registra y el torno se abre.

- Negativa: Dado un socio cuyo último acceso fue a las 10:00, cuando intenta entrar con su mismo NFC a las 12:00, entonces el sistema deniega el acceso y no registra ningún acceso nuevo.

##### R.N.02. Límite de reservas por aforo

El número de reservas confirmadas para una clase no puede superar el aforo disponible.

**Pruebas de aceptación**
- Positiva: Dada una clase con aforo 20 y 19 reservas confirmadas, cuando un socio reserva plaza, entonces la reserva se confirma (20/20).

- Negativa: Dada una clase con aforo 20 y 20 reservas confirmadas, cuando otro socio intenta reservar, entonces el sistema rechaza la reserva y el número de reservas sigue en 20.

##### R.N.03. No duplicidad de horarios del monitor

Un monitor no puede tener asignadas dos clases cuyo día y hora se solapen.

**Pruebas de aceptación**
- Positiva: Dado un monitor con una clase el lunes de 10:00 a 11:00, cuando se le asigna otra clase el lunes de 11:00 a 12:00, entonces la asignación se guarda correctamente.

- Negativa: Dado el mismo monitor con la clase del lunes de 10:00 a 11:00, cuando se le asigna otra clase el lunes de 10:30 a 11:30, entonces el sistema rechaza la asignación por solapamiento.

##### R.N.04. Acceso condicionado al estado del socio

Un socio solo puede acceder al centro si su cuenta está en estado "Alta" y no tiene recibos impagados.

**Pruebas de aceptación**
- Positiva: Dado un socio en estado “Alta” sin recibos impagados, cuando pasa su NFC por el torno, entonces se autoriza la entrada.

- Negativa: Dado un socio en estado “Suspendido” , “Baja”, o “Alta” con un recibo devuelto, cuando pasa su NFC por el torno, entonces el torno deniega la entrada y no se registra acceso.

##### R.N.05. Asignación de tareas según el tipo de trabajador

Solo los trabajadores de tipo "Monitor" pueden ser asignados como responsables de clases. El "Personal de Mantenimiento" solo puede tener asignado zona y tareas de mantenimiento, y no clases.

**Pruebas de aceptación**
- Positiva: Dado un trabajador de tipo “Monitor”, cuando se le asigna como responsable de una clase, entonces la asignación se guarda correctamente.

- Negativa: Dado un trabajador de tipo “Personal de Mantenimiento”, cuando se intenta asignarlo como responsable de una clase, entonces el sistema rechaza la operación.

##### R.N.06. No solapamiento de clases en una misma sala

Una sala no puede tener programadas dos clases cuyo día y hora se solapen. Además, la clase debe impartirse en una sala adecuada a su disciplina (por ejemplo, Spinning en la sala de Spinning).

**Pruebas de aceptación**
- Positiva: Dada la sala de Spinning con una clase el martes de 18:00 a 19:00, cuando se programa una clase de Spinning el mismo día de 19:00 a 20:00, entonces la clase se guarda correctamente.

- Negativa: Se rechaza la programación en estos dos casos: una clase de Spinning el martes de 18:30 a 19:30 en la misma sala (solapamiento) o una clase de Pilates en la sala de Spinning (sala no adecuada a su disciplina).

### 4.2. Mapa de historias de usuario (opcional)

### 4.3. Requisitos no funcionales
##### R.N.F. 01. Latencia en la validación de acceso NFC
Como **Administrador**, quiero **procesar la lectura del llavero NFC, consultar el estado del socio y responder al torno electromecánico en menos de 1 segundo (esperado < 500 ms)** para **evitar la formación de colas en los tornos durante las horas de máxima afluencia**.

##### R.N.F. 02. Disponibilidad 24/7
Como **Administrador**, quiero **que la disponibilidad del sistema sea del 99.5%** para **que cada socio pueda consultar el estado de su cuenta o realizar cambios en sus datos personales cuando lo desee**.

##### R.N.F. 03. Privacidad del usuario y cifrado de datos
Como **Socio**, quiero **que mi información fiscal y bancaria (IBAN) sea almacenada mediante cifrado, únicamente descifrable para el Administrador** para **proteger mi privacidad y evitar la exposición o fuga de mis datos personales**.

##### R.N.F. 04. Reserva intuitiva en aplicación móvil
Como **Socio**, quiero **que la aplicación móvil permita que la reserva de las clases se pueda realizar como máximo en 4 toques** para **facilitar la experiencia del usuario sin necesidad de un conocimiento previo**.

##### R.N.F. 05. Notificación para agilización de la atención presencial
Como **Administrador**, quiero **disponer de un sistema de avisos/alertas en el panel de recepción para atender a los socios en mostrador en un tiempo inferior a 50 segundos** para **agilizar la atención al cliente presencial y minimizar los tiempos de espera**.

##### R.N.F. 06. Restricción de interfaz para el personal de mantenimiento (Seguridad y Privacidad)
Como **Personal de Mantenimiento**, quiero **visualizar únicamente la sección de partes de avería e incidencias de maquinaria** para **garantizar la privacidad de los datos personales y bancarios de los socios y trabajadores**.

##### R.N.F. 07. Expiración automática de la sesión por inactividad
Como **Administrador**, quiero **que la sesión activa se cierre de forma automática tras 10 minutos continuos de inactividad** para **evitar usos no autorizados en los ordenadores de la recepción cuando el puesto quede desatendido**.

##### R.N.F. 08. Tolerancia a fallos en la validación de acceso (Resiliencia)
Como **Administrador**, quiero **que el torno registre temporalmente las lecturas NFC en modo local en caso de desconexión con el servidor** para **permitir el paso fluido de socios y sincronizar los accesos automáticamente una vez restablecida la red**.

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


