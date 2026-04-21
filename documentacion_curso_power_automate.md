# Curso de Power Automate

## Introducción

Power Automate es una herramienta de automatización de procesos incluida dentro de Microsoft Power Platform. Su propuesta de valor es permitir la construcción de flujos de trabajo que conectan aplicaciones, servicios, datos y personas sin necesidad de programar en un lenguaje tradicional.

Ahora bien, que una herramienta sea **low-code** o **no-code** no significa que diseñar soluciones con ella sea trivial. Un flujo de Power Automate sigue siendo software. Por tanto, aparecen los mismos problemas que en cualquier desarrollo serio:

- necesidad de diseño
- necesidad de pruebas
- necesidad de mantenimiento
- gestión de errores
- seguridad
- control de cambios
- deuda técnica
- gobierno y estandarización

Por eso, este curso no plantea Power Automate como una “caja de magia”, sino como una herramienta útil para automatizar procesos pequeños y medianos, especialmente valiosa cuando permite ahorrar tiempo en tareas repetitivas, integrar sistemas y reducir errores manuales.

---

## 1. Automatizar: qué significa realmente

Automatizar consiste en hacer que una máquina ejecute tareas que antes realizaba una persona.

Un ejemplo clásico fuera del mundo IT es una lavadora. Antes una persona lavaba la ropa a mano. Ahora una máquina realiza ese trabajo. Además, puede variar su comportamiento mediante programas de lavado.

En el mundo informático ocurre lo mismo:

- la máquina es un ordenador
- automatizar equivale a construir un programa
- ese programa ejecuta tareas que antes hacía un humano

En el ámbito empresarial, estas tareas suelen ser:

- mover datos entre sistemas
- generar avisos o notificaciones
- validar información
- solicitar aprobaciones
- clasificar entradas
- lanzar acciones en aplicaciones externas
- componer mensajes o documentos

---

## 2. DevOps y automatización

DevOps puede entenderse como una cultura, filosofía o movimiento orientado a reducir fricción entre desarrollo y operación, favoreciendo la colaboración y la automatización.

Dicho de forma simple: DevOps empuja a automatizar todo lo que haya entre **DEV** y **OPS**.

Power Automate no es una herramienta “DevOps” en sentido estricto, pero sí es una herramienta de automatización. Y, por tanto, comparte una idea central con DevOps: **automatizar todo aquello que tenga sentido automatizar**.

---

## 3. NoCode sin humo

### 3.1 Qué significa no-code

No-code significa que la construcción de la solución no requiere escribir código tradicional en un lenguaje como Java, C#, Python o JavaScript.

### 3.2 Lo que no significa

No significa:

- que cualquiera pueda construir cualquier cosa sin conocimientos técnicos
- que desaparezcan los problemas de diseño
- que no haya que pensar en seguridad, mantenimiento o arquitectura
- que no haga falta un gobierno mínimo de la plataforma

La promesa comercial de “democratizar el desarrollo” tiene parte de verdad, pero debe matizarse. Una empresa que adopta Power Platform de forma seria necesita control y coordinación.

### 3.3 El papel del CoE

Por eso Microsoft y muchas organizaciones apuestan por un **Center of Excellence (CoE)** o **Centro de Excelencia**.

Ese equipo suele encargarse de:

- definir buenas prácticas
- proporcionar plantillas
- controlar entornos
- vigilar licencias
- establecer normas de seguridad
- evitar duplicidades
- acompañar a usuarios y equipos
- supervisar el ciclo de vida de las soluciones

No-code no elimina la ingeniería. La desplaza parcialmente desde la escritura de código hacia el diseño, el modelado, la integración y el gobierno.

---

## 4. Power Platform: visión general

Power Automate forma parte de la suite **Power Platform**, compuesta principalmente por:

- **Power Apps**: creación de aplicaciones web y móviles
- **Power Automate**: automatización de procesos y flujos de trabajo
- **Power BI**: análisis y visualización de datos
- **Copilot Studio**: creación de agentes, asistentes y experiencias basadas en IA
- **Power Pages**: creación de sitios web de baja codificación
- **Dataverse**: base de datos nativa del ecosistema

La gran ventaja del ecosistema es la integración entre sus piezas. Una aplicación Power Apps puede trabajar contra Dataverse, desencadenar flujos en Power Automate y mostrar resultados en Power BI.

---

## 5. Qué es Power Automate

Power Automate es una herramienta orientada a crear **flujos de trabajo automatizados**.

Estos flujos permiten:

- escuchar eventos
- reaccionar a esos eventos
- ejecutar acciones
- mover datos entre sistemas
- coordinar personas y aplicaciones

Ejemplos típicos:

- cuando llega un correo, guardar sus adjuntos en OneDrive
- cuando alguien envía un formulario, registrar la solicitud en Dataverse
- cuando se aprueba una solicitud, enviar un correo de bienvenida
- cuando un sistema devuelve datos por HTTP, transformarlos y almacenarlos

### 5.1 Qué tipo de problemas resuelve bien

Power Automate encaja especialmente bien en:

- automatizaciones departamentales
- procesos sencillos o medianos
- integraciones rápidas entre sistemas existentes
- tareas repetitivas con lógica razonable
- circuitos de aprobación
- notificaciones y consolidación de datos

### 5.2 Qué no conviene pedirle

No suele ser la mejor opción para:

- megaprocesos transversales muy complejos
- automatizaciones críticas con muchísima carga y lógica muy sofisticada
- arquitecturas fuertemente acopladas a medida que deberían construirse como software específico

---

## 6. Tipos de flujos

Power Automate permite varios tipos de flujos según cómo se inician.

### 6.1 Flujos instantáneos o manuales

Se ejecutan cuando una persona los lanza manualmente.

Ejemplo:

- un usuario pulsa un botón para iniciar una tarea

### 6.2 Flujos programados

Se ejecutan siguiendo una planificación temporal.

Ejemplo:

- todos los días a las 08:00
- todos los lunes a las 09:00

### 6.3 Flujos automatizados o reactivos

Se ejecutan cuando ocurre un evento en otro sistema.

Ejemplos:

- llega una respuesta nueva a Microsoft Forms
- se inserta un registro en Dataverse
- se recibe un correo
- cambia un elemento en SharePoint

### 6.4 Flujos cloud y flujos desktop

También distinguimos entre:

- **flujos de nube (cloud flows)**
- **flujos de escritorio (desktop flows)**

#### Flujos cloud

Se ejecutan en la infraestructura cloud de Microsoft.

Permiten:

- responder a eventos
- ejecutarse en horarios programados
- integrarse con servicios online
- conectar aplicaciones y APIs

#### Flujos desktop

Se ejecutan sobre un equipo local o un equipo preparado para ello, y sirven para automatizar:

- interfaces gráficas
- tareas sobre aplicaciones instaladas
- documentos o archivos locales
- escenarios RPA

Un flujo desktop requiere condiciones operativas adicionales:

- máquina disponible
- software preparado
- contexto de ejecución adecuado

---

## 7. Estructura básica de un flujo

Todo flujo tiene dos piezas esenciales:

- **desencadenador (trigger)**
- **acciones (actions)**

### 7.1 Trigger

Es el evento que inicia la ejecución.

### 7.2 Actions

Son los pasos que se ejecutan después del trigger.

### 7.3 Datos de entrada y salida

Cada caja del flujo, ya sea trigger o acción, recibe y produce datos.

Por eso, una buena forma de entender Power Automate es esta:

> Todo el juego consiste en conectar datos de salida de unas cajas con datos de entrada de otras cajas.

Y cuando los datos no encajan directamente, usamos **expresiones** para transformarlos.

---

## 8. Triggers, actions y conectores

### 8.1 Conectores

Los conectores son componentes que saben hablar con sistemas externos.

Ejemplos:

- Outlook
- Teams
- OneDrive
- SharePoint
- Forms
- Dataverse
- SQL Server
- HTTP
- servicios de aprobación

Gracias a ellos, desde Power Automate podemos trabajar con acciones de alto nivel como:

- enviar un correo
- leer una respuesta de Forms
- crear una fila en Excel
- consultar una tabla en Dataverse
- invocar un servicio HTTP

### 8.2 API y conector

Por debajo, cada sistema expone una forma de comunicación concreta: su **API**.

El conector encapsula esa API y nos evita tener que manejarla directamente en muchos casos.

### 8.3 Conectores estándar y premium

No todos los conectores están disponibles en todas las licencias.

Hay conectores:

- estándar
- premium

Además, una cosa es tener licencia para usar un conector y otra disponer realmente del sistema al que apunta.

### 8.4 Conexiones y autenticación

Cuando usamos un conector, hay que configurarlo.

Esa configuración suele incluir:

- credenciales
- consentimiento
- permisos
- parámetros específicos del sistema destino

Buenas prácticas:

- evitar cuentas personales cuando la automatización es corporativa
- preferir cuentas de servicio cuando proceda
- entender que la conexión es parte crítica del ciclo de vida

---

## 9. Conexiones, referencias de conexión y variables de entorno

Cuando una solución se mueve entre entornos, el flujo no debería quedar atado a valores concretos de desarrollo.

### 9.1 Problema

Ejemplos de cosas que cambian entre desarrollo y producción:

- correo del aprobador
- archivo Excel
- tabla concreta
- URL de un servicio
- canal de Teams
- conexión usada por un conector

### 9.2 Variables de entorno

Permiten parametrizar valores que cambian entre entornos.

Ejemplos:

- nombre del fichero Excel
- nombre de la tabla
- correo del aprobador
- URL base de un servicio

### 9.3 Referencias de conexión

Aportan un nivel de indirección entre una acción y la conexión real.

En vez de tener:

- acción → conexión fija

podemos tener:

- acción → referencia de conexión → conexión real del entorno

Esto mejora el despliegue y reduce errores al promocionar soluciones.

---

## 10. Entornos de trabajo

Todo lo que hacemos en Power Platform vive dentro de un **entorno**.

Un entorno es un espacio lógico que contiene:

- flujos
- aplicaciones
- conexiones
- tablas de Dataverse
- configuraciones asociadas

Lo habitual es trabajar al menos con:

- desarrollo
- pruebas
- producción

Y lo sano es que esos entornos no se gestionen de forma caótica, sino gobernados por el equipo responsable.

---

## 11. Mover soluciones entre entornos

### 11.1 Exportar e importar manualmente

Existe, pero es una vía pobre y propensa a errores.

Problemas:

- trabajo manual repetitivo
- alto riesgo de olvidar ajustes
- mala escalabilidad
- dificultad para repetir el proceso con fiabilidad

### 11.2 Soluciones

Una solución permite agrupar artefactos relacionados:

- flujos
- tablas
- referencias de conexión
- variables de entorno
- otros componentes

Ventajas:

- empaquetado coherente
- promoción entre entornos más limpia
- mejor trazabilidad
- integración con ALM

### 11.3 Azure DevOps y automatización del ciclo de vida

A partir de cierto nivel de madurez, interesa automatizar también:

- promoción entre entornos
- pruebas
- despliegues
- control de cambios

Ahí entran en juego las pipelines y la integración con Azure DevOps.

---

## 12. Git, repositorios y control de versiones

Aunque no escribamos código tradicional, Power Platform genera definiciones técnicas de las soluciones.

Por eso sigue teniendo sentido usar:

- repositorios Git
- commits
- ramas
- control de versiones

### 12.1 Qué aporta Git

- historial de cambios
- posibilidad de volver atrás
- trabajo organizado por ramas
- trazabilidad
- integración con pipelines

### 12.2 Uso típico simplificado

En muchos proyectos Power Platform pequeños:

- hay poca gente
- no hay muchas ramas
- no se usa una burocracia compleja

Aun así, conviene al menos distinguir:

- `main` o `master`: estable, orientada a producción
- `develop` o similar: trabajo en curso

### 12.3 Integración con Azure DevOps

Azure DevOps es especialmente relevante en entornos corporativos para:

- alojar repositorios
- construir pipelines
- automatizar despliegues
- controlar calidad y entregas

---

## 13. Variables, parámetros y tipos de datos

Power Automate trabaja con datos tipados.

Tipos frecuentes:

- texto (`string`)
- entero (`integer`)
- decimal / número
- booleano (`true` / `false`)
- fecha/hora
- array
- objeto

### 13.1 Parámetros de entrada

Algunos triggers permiten definir entradas.

Ejemplo típico:

- nombre
- fecha
- edad
- carpeta

### 13.2 Variables

Las variables permiten almacenar datos para usarlos más adelante durante la ejecución del flujo.

Operaciones habituales:

- inicializar variable
- establecer variable
- anexar a variable de cadena
- anexar a array

### 13.3 Buenas prácticas con variables

- inicializarlas al principio del flujo
- usar nombres claros
- evitar mezclarlas sin orden con la lógica principal
- declarar solo las necesarias

---

## 14. Contenido dinámico y expresiones

Power Automate ofrece dos mecanismos complementarios para trabajar con datos:

- **dynamic content**
- **expresiones**

### 14.1 Dynamic content

Es la forma visual de reutilizar datos que salen de pasos anteriores.

### 14.2 Expresiones

Son pequeñas funciones que permiten:

- transformar texto
- convertir tipos
- comparar valores
- trabajar con fechas
- construir mensajes
- componer condiciones

Funciones frecuentes:

- `concat()`
- `replace()`
- `if()`
- `greaterOrEquals()`
- `less()`
- `string()`
- `int()`
- `formatDateTime()`
- `empty()`
- `guid()`

---

## 15. Diseño por bloques conceptuales y uso de scopes

Una buena práctica importante es organizar el flujo en **bloques conceptuales**.

En Power Automate esto se puede reflejar con **scopes**.

Estructura típica:

1. Disparador
2. Inicialización de variables
3. Tareas principales
4. Gestión de errores

Y dentro de “Tareas principales”, más scopes:

- obtener datos
- validar datos
- calcular edad
- solicitar aprobación
- generar mensaje IA
- guardar resultados
- notificar

### 15.1 Ventajas de los scopes

- mejor legibilidad
- más claridad conceptual
- mejor tratamiento de errores
- facilita el uso de `Configure run after`

### 15.2 Precaución práctica

Cuando un flujo ya está muy montado, insertar scopes a posteriori puede ser molesto y romper parte de la estructura visual. Por eso suele ser mejor pensarlos desde el principio.

### 15.3 Limitación práctica

La inicialización de variables no suele colocarse dentro de scopes; lo habitual es dejarla al inicio del flujo.

---

## 16. Cómo plantear el desarrollo de un flujo

Al construir un flujo hay una recomendación clave:

> diseñar primero contra requisitos, no contra una fuente concreta de datos.

No queremos que la lógica de negocio dependa de si la entrada llega por:

- Forms
- correo
- Excel
- SharePoint
- HTTP
- base de datos

La fuente puede cambiar. La lógica de negocio no debería quedar secuestrada por esa fuente.

### 16.1 Enfoque recomendado

Primero pensar en bloques como:

- capturar entrada
- validar
- calcular
- decidir
- aprobar
- enriquecer
- persistir
- notificar

Después, ya se conectan esos bloques con conectores concretos.

---

## 17. Happy path, pruebas y refactorización

Un flujo debe desarrollarse progresivamente.

Secuencia mental recomendable:

1. construir el **happy path**
2. comprobar que funciona
3. blindarlo frente a errores y excepciones
4. refactorizar si la solución empieza a crecer

### 17.1 Happy path

Es el camino ideal, sin errores, sin datos anómalos y sin caídas externas.

### 17.2 Después del happy path

Cuando el flujo ya hace “lo esperado”, toca preguntarse:

- ¿qué pasa si falla una llamada HTTP?
- ¿qué pasa si una aprobación expira?
- ¿qué pasa si falta un dato?
- ¿qué pasa si hay timeout?
- ¿qué pasa si no tengo permisos?

---

## 18. Deuda técnica y mantenibilidad

Que un flujo funcione no significa que esté bien diseñado.

Un flujo puede ser técnicamente pobre si:

- es difícil de leer
- tiene nombres malos
- repite lógica
- mezcla responsabilidades
- acopla demasiadas cosas
- cuesta modificarlo sin miedo

Eso genera **deuda técnica**.

La deuda técnica es el sobrecoste futuro de mantener una solución mal diseñada hoy.

### 18.1 Manifestaciones típicas en Power Automate

- pasos con nombres poco expresivos
- bloques sin separar
- variables sin sentido claro
- lógica duplicada
- dependencias ocultas entre acciones
- valores fijos que deberían parametrizarse

### 18.2 Consecuencia real

Hoy cambiar una caja puede llevar 20 segundos.
Dentro de un año, entender por qué existe esa caja puede costar una hora o más.

---

## 19. Condicionales, bucles y control de flujo

### 19.1 Condiciones

Permiten bifurcar el flujo:

- si se cumple una condición, seguir por una rama
- si no, seguir por otra

### 19.2 Switch

Útil cuando hay varias alternativas según un valor.

### 19.3 Apply to each

Permite iterar sobre colecciones.

Ejemplo:

- recorrer actividades devueltas por un servicio HTTP
- recorrer registros de una consulta

### 19.4 Do until

Se usa cuando se repite algo hasta que se cumple una condición.

---

## 20. Concurrencia y comportamiento en ejecución

Una cosa es el flujo como definición. Otra, sus ejecuciones reales.

Un flujo puede ejecutarse varias veces en paralelo si llegan varios eventos.

### 20.1 Cuándo interesa concurrencia

Ejemplo:

- llegan 10 correos con adjuntos
- queremos procesarlos en paralelo

### 20.2 Cuándo no interesa

Ejemplo:

- un flujo extrae datos y escribe en un recurso compartido delicado, como un Excel
- varias ejecuciones simultáneas pueden chocar entre sí

Aquí hay que pensar en:

- concurrencia
- cola
- solapamiento
- idempotencia

---

## 21. Aprobaciones en Power Automate

Power Automate permite construir circuitos de aprobación.

### 21.1 Modalidades frecuentes

- crear aprobación
- esperar aprobación
- crear y esperar aprobación
- crear y esperar aprobación de sugerencia de texto

### 21.2 Síncrono y asíncrono

#### Síncrono

El flujo se bloquea esperando la aprobación.

#### Asíncrono

Podemos lanzar la aprobación y seguir haciendo otras cosas antes de esperar el resultado.

### 21.3 Casos de uso típicos

- aprobación de acceso
- aprobación de vacaciones
- validación de un texto generado por IA
- aprobación por una persona de un grupo
- aprobación obligatoria por todos los miembros

### 21.4 Importante

Las aprobaciones no son magia: implican dependencia de un servicio externo y pueden fallar o expirar.

---

## 22. Construcción dinámica de mensajes

En muchos flujos necesitamos componer mensajes personalizados.

Ejemplo típico:

- insertar nombre y edad en un texto de aprobación
- construir asuntos de correo
- montar mensajes enriquecidos para Teams

Para ello usamos expresiones como:

- `concat()`
- `replace()`
- `string()`
- `decodeUriComponent('%0A')` para saltos de línea

También se puede trabajar con sintaxis tipo Markdown en determinados contextos:

- `#` títulos
- `**texto**` negrita
- `*texto*` cursiva
- `-` listas

---

## 23. Gestión de errores y `Configure run after`

Todo flujo serio debe contemplar los fallos.

### 23.1 Tipos de error habituales

- error de red
- timeout
- permisos insuficientes
- servicio caído
- datos no válidos
- respuesta inesperada

### 23.2 Scopes de errores

Una práctica muy útil es tener:

- un scope de tareas principales
- un scope de gestión de errores

Y configurar el segundo para que se ejecute cuando el primero:

- falle
- expire

### 23.3 Notificaciones de error

El tratamiento puede consistir en:

- enviar un correo
- registrar un log
- marcar un estado en Dataverse
- crear una incidencia

---

## 24. Reintentos y resiliencia

Cuando trabajamos con sistemas externos, los fallos transitorios son normales.

Ejemplos:

- saturación del servicio
- error 500
- error 503
- timeout temporal

En esos casos puede tener sentido aplicar políticas de reintento, a menudo con **backoff exponencial**.

Ejemplo conceptual:

- reintento 1: 5 segundos
- reintento 2: 10 segundos
- reintento 3: 20 segundos

Siempre con límites razonables.

---

## 25. Seguridad: identificación, autenticación y autorización

### 25.1 Identificación

Decir quién soy.

### 25.2 Autenticación

Comprobar que realmente soy quien digo ser.

En el ecosistema Microsoft esto suele recaer en **Entra ID**.

### 25.3 Autorización

Una vez autenticado, decidir qué puedo hacer.

La autorización puede apoyarse en:

- licencias
- roles de entorno
- permisos sobre tablas
- permisos sobre columnas
- permisos sobre artefactos concretos

### 25.4 Buenas prácticas

- no incrustar credenciales sin control
- evitar usuarios personales en automatizaciones corporativas
- usar variables de entorno y conexiones gobernadas
- revisar permisos de conectores y datos

---

## 26. Dataverse

Dataverse es la base de datos nativa de Power Platform.

Es una pieza fundamental para escenarios donde queremos:

- persistir datos de forma estructurada
- desacoplar entrada y procesamiento
- modelar estados
- disparar flujos por cambios de datos

### 26.1 Cuándo usar Dataverse

Resulta especialmente adecuado cuando el proceso madura y deja de ser un simple prototipo.

### 26.2 Ventajas sobre Excel como núcleo del proceso

Excel puede servir como interfaz o almacenamiento rápido, pero Dataverse ofrece:

- mejor estructura
- relaciones
- tipado más sólido
- automatización basada en eventos
- mejor gobernanza

---

## 27. Modelado de solicitudes con Dataverse

Un ejemplo trabajado en el curso fue el de solicitudes de acceso.

Tabla conceptual de solicitudes:

- Nombre — obligatorio
- Email — obligatorio
- Fecha de nacimiento — opcional
- Edad — opcional
- Observaciones — opcional
- Origen — obligatorio
- Estado — obligatorio

Tabla de estados normalizada:

- Pendiente de revisar
- Pendiente de procesar
- Procesado
- Rechazado
- Error
- Aprobado
- Denegado

### 27.1 Idea importante

Conviene distinguir entre:

- **estado del proceso**
- **resultado funcional o de negocio**

Si no se distinguen bien, la solución se vuelve confusa.

---

## 28. Procesos desacoplados y separación de responsabilidades

Una de las ideas más importantes del curso fue evitar el megaflujo monolítico cuando la solución empieza a crecer.

### 28.1 Evolución natural

1. primer flujo monolítico para entender el proceso extremo a extremo
2. refactorización por bloques
3. separación en varios flujos conectados por datos o eventos

### 28.2 Ejemplo de partición

- flujo de captura desde Forms hacia Dataverse
- flujo de revisión inicial de datos
- flujo de procesamiento de solicitudes válidas
- flujo de notificación posterior

### 28.3 Principio de SoC

**Separation of Concerns**: separar responsabilidades para evitar mezclar cosas distintas.

No es lo mismo:

- capturar una solicitud
- validar datos
- calcular la edad
- aprobar el acceso
- generar un mensaje IA
- enviar una notificación

---

## 29. HTTP, APIs REST y servicios externos

Power Automate permite invocar servicios HTTP.

### 29.1 Qué es una URL

Una URL identifica un recurso y puede incluir:

- protocolo
- servidor
- puerto
- ruta
- query string
- fragmento

Ejemplo conceptual:

`https://servidor:443/ruta?param1=valor1&param2=valor2`

### 29.2 Verbo HTTP

Operaciones habituales:

- `GET` → consultar
- `POST` → crear
- `PATCH` → modificar parcialmente
- `DELETE` → borrar

### 29.3 Headers y body

Toda petición y toda respuesta HTTP puede incluir:

- cabeceras (`headers`)
- cuerpo (`body`)

El body es la carga útil o **payload**.

### 29.4 Códigos de estado

Familias importantes:

- `2xx` → éxito
- `3xx` → redirección
- `4xx` → error del cliente
- `5xx` → error del servidor

En Power Automate solemos trabajar con el éxito o fracaso de la acción, aunque conceptualmente conviene entender el código de estado.

---

## 30. JSON y Parse JSON

Cuando un servicio HTTP devuelve datos, muchas veces vienen en JSON.

### 30.1 Diferencia entre datos y estructura

No basta con ver ejemplos de datos. Hay que entender la **estructura**.

Ejemplo conceptual:

- lista de objetos
- cada objeto tiene propiedades concretas
- algunas son obligatorias y otras opcionales

### 30.2 JSON Schema

El esquema JSON define formalmente esa estructura:

- tipos
- propiedades
- obligatoriedad
- formatos esperados

### 30.3 Utilidad práctica

En Power Automate esto es clave para acciones como:

- `Parse JSON`
- acceso seguro a propiedades
- validación del contenido esperado

---

## 31. SQL Server y otros conectores premium

Entre los conectores premium relevantes del curso están:

- Dataverse
- SQL Server
- HTTP
- servicios IA

SQL Server puede usarse para:

- ejecutar consultas
- leer y escribir datos
- integrarse con procesos ya existentes

Como siempre, importa tanto el conector como la conexión y su ciclo de vida.

---

## 32. IA, Copilot e IA Builder

### 32.1 Copilot

Copilot es una marca comercial de Microsoft para distintas experiencias basadas en IA.

En Power Platform puede ayudarnos a:

- generar flujos a partir de lenguaje natural
- sugerir pasos
- asistir en el diseño

### 32.2 IA Builder

Permite integrar capacidades de IA en procesos:

- generación de texto
- clasificación
- extracción
- tratamiento de formularios
- otros escenarios según modelo

### 32.3 Idea importante

Hay que separar:

- el **modelo** de IA
- la **herramienta** con la que interactuamos con ese modelo

---

## 33. Usar IA con criterio

La IA en automatización debe introducirse con prudencia.

No conviene, el día 1, dejar que un modelo tome decisiones críticas sin supervisión.

### 33.1 Estrategia recomendable

1. usar IA para proponer
2. introducir revisión humana
3. almacenar propuesta y corrección
4. analizar resultados
5. retirar supervisión solo cuando la fiabilidad sea suficiente

### 33.2 Casos útiles

- generar mensajes de bienvenida
- clasificar solicitudes
- resumir correos
- extraer información de textos
- enriquecer procesos con texto generado

---

## 34. Caso práctico principal del curso

El caso principal fue una **solicitud de acceso** que fue evolucionando durante la formación.

### 34.1 Primera versión: flujo monolítico

El flujo inicial partía de **Microsoft Forms** y hacía, en esencia, lo siguiente:

1. capturar nombre, email, fecha de nacimiento y observaciones
2. calcular la edad
3. determinar si la persona es mayor de edad
4. si no lo es, solicitar aprobación manual
5. si tiene acceso, obtener actividades desde un servicio HTTP
6. usar IA para generar un mensaje de bienvenida
7. pedir aprobación del texto
8. enviar un correo
9. registrar el resultado en Excel

Este flujo se fue complicando progresivamente, y se utilizó para introducir conceptos como:

- variables
- scopes
- expresiones
- aprobaciones
- HTTP
- Parse JSON
- IA Builder
- Excel Online
- gestión de errores

### 34.2 Segunda fase: comenzar a partir el flujo

A medida que crecía, empezó a refactorizarse en varios flujos:

- captura desde Forms hacia Dataverse
- revisión inicial de datos
- procesamiento posterior y notificación

No quedó completamente partido durante el curso, pero sí se avanzó hacia un diseño más desacoplado.

---

## 35. Caso práctico: captura desde Forms

Objetivo:

- recibir una respuesta del formulario
- obtener sus detalles
- crear una solicitud en Dataverse
- dejarla en estado “Pendiente de revisar”

Aprendizajes clave:

- uso de Microsoft Forms como trigger
- captura de campos
- búsqueda de referencia al estado en Dataverse
- alta de registro en tabla de solicitudes

---

## 36. Caso práctico: revisión inicial de datos

Objetivo:

- revisar si la solicitud tiene datos suficientes
- si tiene edad, continuar
- si no tiene edad pero tiene fecha de nacimiento, calcularla
- si faltan datos esenciales, rechazar
- actualizar el estado según el resultado

Aprendizajes clave:

- tratamiento de opcionales
- expresiones con fechas
- actualización de registros en Dataverse
- modelado por estados

---

## 37. Caso práctico: aprobación y acceso

Objetivo:

- determinar si el usuario puede acceder
- si es mayor de edad, conceder acceso automáticamente
- si no lo es, solicitar aprobación manual

Aprendizajes clave:

- condicionales
- aprobación síncrona
- construcción dinámica del mensaje de aprobación
- uso del resultado de la aprobación para continuar o no

---

## 38. Caso práctico: obtención de actividades por HTTP

Objetivo:

- invocar un servicio HTTP que devuelve actividades
- parsear la respuesta JSON
- recorrer los elementos
- componer un texto acumulado con título y fecha

Aprendizajes clave:

- acción HTTP
- `Parse JSON`
- `Apply to each`
- concatenación en variable de cadena

---

## 39. Caso práctico: mensaje de bienvenida con IA

Objetivo:

- usar IA para redactar un texto personalizado
- incorporar nombre, edad y actividades
- solicitar revisión humana del texto
- enviar el resultado aprobado por correo

Aprendizajes clave:

- IA Builder
- aprobación de sugerencia de texto
- separación entre propuesta IA y texto final enviado
- enfoque human-in-the-loop

---

## 40. Excel como salida e interfaz temporal

En una de las versiones del flujo se registraban datos en Excel:

- Nombre
- Email
- Fecha de nacimiento
- Observaciones
- Mensaje de bienvenida
- Fecha de alta
- Aprobado o no

Lección importante:

- Excel puede servir muy bien como herramienta de apoyo o interfaz rápida
- pero cuando el proceso madura, Dataverse suele ser mejor núcleo de datos

---

## 41. Buenas prácticas resumidas

### Diseño

- empezar por requisitos y bloques conceptuales
- no atar la lógica a una fuente concreta
- evitar megaflujos cuando crecen demasiado
- usar scopes desde el inicio
- nombrar bien las acciones

### Datos

- tipar bien las variables
- usar Dataverse cuando el proceso madure
- diferenciar estado de proceso y resultado funcional
- parametrizar valores por entorno

### Operación

- diseñar primero el happy path
- después cubrir errores y timeout
- pensar en concurrencia
- usar reintentos con sentido

### Gobierno

- controlar conexiones
- preferir cuentas adecuadas
- usar soluciones
- mover artefactos con ALM y no a mano
- versionar en repositorio

### IA

- introducirla de forma gradual
- no automatizar decisiones críticas a ciegas
- conservar revisión humana mientras haga falta
- aprovechar las correcciones para mejorar el sistema

---

## 42. Cierre

Power Automate es una herramienta muy potente cuando se usa con criterio.

Su verdadero valor no está en “poner cajitas”, sino en combinar:

- automatización
- integración
- modelado de datos
- control operativo
- mantenibilidad
- gobierno

Con un enfoque adecuado, permite resolver muy bien procesos reales de negocio. Con un mal enfoque, puede generar automatizaciones difíciles de mantener, inseguras y frágiles.

La diferencia no la marca solo la herramienta. La marca cómo se diseña y cómo se gobierna la solución.
