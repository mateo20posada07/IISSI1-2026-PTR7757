# FitManager_S.O_Edition

## Miembros del grupo LX-XXX-X (sustituir)

1. Posada Quintero, Mateo
2. Herrero González, María del Pilar
3. Pablo Morales, Adrián
4. González García, Valeria

## 1. Introducción al problema

- Descripción del problema para poner en contexto el proyecto, incluyendo información sobre los clientes y usuarios, la situación actual, problemas, expectativas, etc. Se valorará la presencia de información multimedia (fotos, gráficos, documentos escaneados, etc.).

## 2. Glosario de términos

- Términos específicos del dominio del problema, ordenados alfabéticamente. Se valorará la presencia de información multimedia.

## 3. Visión general del sistema

### 3.1. Requisitos generales

### 3.2. Usuarios del sistema

## 4. Catálogo de requisitos

### 4.1. Requisitos funcionales

#### R.F.01. Título requisito funcional

Como [tipo de usuario]
quiero [servicio]
para [razón]

**Prueba de aceptación**
- Descripción de la primera comprobación a realizar
- Descripción de la segunda comprobación a realizar
- Se debe aplicar la regla de negocio R.N.XX.
- ...

#### 4.1.1. Requisitos de información

##### R.I.01. Registro y Expediente del Socio
Como **Administrador**,  
quiero **almacenar y consultar el expediente completo de cada socio**  
para **gestionar sus datos personales, controlar el estado de su cuenta y vincular sus credenciales físicas de acceso**.

**Pruebas de aceptación**
- El sistema debe verificar que el DNI, el Email y el código del dispositivo NFC introducidos no pertenezcan a un usuario ya registrado en la base de datos.
- Se debe guardar obligatoriamente: DNI, Nombre, Apellidos, Teléfono, Email, Fecha de Nacimiento, Dirección, Estado (`Alta`, `Baja`, `Suspendido`), Código de Llavero/Tarjeta NFC asignado y la Tarifa contratada.
- Se debe vincular el identificador único del llavero NFC (`UID_NFC`) al socio para autorizar el paso en los tornos.


##### R.I.02. Expediente e Historial de Trabajadores
Como **Administrador**,  
quiero **registrar los datos personales, contractuales y la especialización de cada empleado**  
para **gestionar la plantilla del gimnasio y organizar la asignación de tareas o clases**.

**Pruebas de aceptación**
- El sistema debe verificar que el DNI y el IBAN del trabajador no estén previamente registrados.
- Se debe guardar obligatoriamente: DNI, Nombre completo, Teléfono, Email, IBAN, NUSS y Salario Base.
- En caso de ser *Monitor*, se debe registrar su área de especialidad deportiva.
- En caso de ser *Personal de Limpieza o Mantenimiento*, se debe registrar su turno de trabajo y zona asignada.


##### R.I.03. Catálogo de Tarifas y Oferta Comercial
Como **Administrador**,  
quiero **definir y mantener actualizado el catálogo de tarifas y cuotas**  
para **establecer los precios, periodicidad de cobro y condiciones de uso del gimnasio**.

**Pruebas de aceptación**
- El sistema debe comprobar que el Nombre de la tarifa sea único en el catálogo.
- Se debe guardar obligatoriamente: Nombre de la tarifa, Precio, Periodicidad (número de meses: 1 para mensual, 12 para anual) y un booleano sobre si incluye o no acceso a las clases colectivas.


##### R.I.04. Historial de Pagos y Transacciones
Como **Administrador**,  
quiero **almacenar los registros de todos los cobros y recibos emitidos**  
para **llevar el control de la facturación, identificar impagos y gestionar vías de cobro**.

**Pruebas de aceptación**
- El sistema debe generar un Número de Recibo secuencial y único para cada transacción.
- Se debe guardar obligatoriamente: Número de Recibo, Socio asociado, Tarifa cobrada, Fecha de Emisión, Fecha de Pago, Importe, Método de Pago (`Tarjeta`, `Efectivo`, `Domiciliación`) y Estado del Pago (`Pendiente`, `Pagado`, `Devuelto`).


##### R.I.05. Registro de Fichajes y Accesos Físicos
Como **Sistema de Control de Acceso**,  
quiero **almacenar cada intento de lectura del llavero NFC en el torno de entrada**  
para **mantener la trazabilidad de afluencia y verificar el cumplimiento de las políticas de acceso**.

**Pruebas de aceptación**
- El sistema debe registrar de forma automática la Fecha y Hora exacta de cada lectura del dispositivo NFC.
- Se debe guardar obligatoriamente: ID del Socio (asociado al `UID_NFC`), Fecha, Hora exacta, Torno de entrada y Resultado del acceso (`Permitido`, `Denegado`).


##### R.I.06. Planificación de Clases Colectivas
Como **Monitor**,  
quiero **consultar la programación de las clases asignadas y el listado de reservas**  
para **impartir la actividad conociendo el número de plazas ocupadas**.

**Pruebas de aceptación**
- Para cada clase colectiva programada se debe guardar: Disciplina, Fecha, Hora de Inicio, Hora Fin, Sala asignada, Aforo máximo y Monitor responsable.
- Para cada reserva vinculada a la clase se debe guardar: Socio solicitante, Fecha de Reserva y Estado de la reserva (`Confirmada`, `Cancelada`).


##### R.I.07. Parte de Incidencias de Maquinaria
Como **Personal de Mantenimiento**,  
quiero **registrar y consultar el estado de las máquinas averiadas o en revisión**  
para **planificar las tareas de reparación y coordinar el estado de las instalaciones**.

**Pruebas de aceptación**
- El sistema debe guardar obligatoriamente: Código de la máquina, Nombre, Marca, Ubicación, Estado (`Operativa`, `Averiada`, `En Mantenimiento`), Fecha de Reporte, Descripción del fallo y un indicador booleano de si está resuelta (adjuntando la Fecha de reparación en caso afirmativo).

#### 4.1.2. Reglas de negocio

##### R.N.01. Título regla negocio

Descripción de la regla de negocio.

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


