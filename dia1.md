# Qué significa Automatizar?

Crear una máquina (o cambiar el comportamiento de una mediante un programa) que haga lo que antes hacía un humano (con sus manos).

Automatizar el lavado de la ropa (lavadora), que incluso puedo cambiar su comportamiento mediante programas (de lavado).
En el mundo IT, la máquina es una computadora... y automatizar = crear un programa que haga lo que antes hacía un humano (con sus manos).

# Devops... qué es eso?

Cultura, Movimiento, filosofía en pro de la automatización. Automatizar qué? Todo lo que está entre el DEV -> OPS



# Qué significa NoCode?

No tirar ni una línea de código... incluso llegando al extremos de no tener necesidad de conocer ~~acerca de desarrollo~~ lenguajes de programación.

En los panfletos me dicen:
Power platform es una herramienta para democratizar el desarrollo de software, es decir, que cualquier persona pueda crear aplicaciones sin necesidad de ser un desarrollador profesional.

ESO ES FALSO!
De hecho... con el tiempo Microsoft (y otros) han ido cambiando el discurso... claro... evitando confrontación con el discurso anterior.
Es verdad... pero hace falta crear un CoE (Centro de Excelencia) para que nop haya problemas al usar estas herramientas.

Crear un sistema (automatización/programa) es complejo:
- No es sólo escribir un código (usando o no un lenguaje de programación)
- Seguridad de la información
- Duplicación de automatizaciones (trabajo)
- Arquitectura de la información (datos)
- Evolución de esos trabajos (mantenimiento)
- Integraciones entre sistemas / Impacto de tu desarrollo (cambios) en otros sistemas
- Coste (LLC: Coste del Ciclo de Vida)

En las empresas al final, lo que suele haber es un equipo de desarrollo centralizado (CoE) que se encarga de crear/mantener/orientar/estandarizar sobre el desarrollo de estos sistemas.


Desarrollador tradicional -> Arquitecto de sistemas.

## Crisis del software??

Esto fue a finales de los años 60. Esta crisis vino desencadenada por la dificultad de mantener/evolucionar los sistemas que años atrás se habían desarrollado.

Un producto de software por definición es un producto sujeto a cambios y mantenimiento.
Que un programa funciones es lo de menos. Se da por descontado.

# Qué es Power Automate?

Es una de las 5 herramientas de la PowerPlatform de Microsoft:
- Power Apps                                 App web y móvil
- Power Automate                             Automatización de flujos de trabajo
- Power BI                                   Análisis de datos
- Power Virtual Agents -> Copilot Studio     Agentes basados en IA
- Power Pages                                Creación de sitios web


- Herramienta NoCode
- Automatización de flujos de trabajo
- Framework 3 elementos: Trigger, Actions, Herramientas (Conectores)
- Automatización de tareas y acciones para conectarse a distintos sistemas.

## Más sobre power automate

El objetivo va a ser crear programas que automaticen flujos de trabajo. Y sobre todo, tendremos muchos beneficios en la integración de sistemas:
- Sacar datos de un sistema (excel, videollamada de teams, datos de mi erp...) y meterlos en otro(email, bbdd, programa externo...

Los flujos tienen:
- Trigger: Evento que desencadena la ejecución del flujo de trabajo automatizado (de nuestro programa)
- Actions: Acciones que se ejecutan como parte del flujo de trabajo automatizado (los pasos que se ejecutan después de que el trigger se active)
- Entre medias de esto nos van a salir los Conectores/Conexiones.

## Conexiones

Cuando queremos hablar con GMAIL, OneDrive, Excel... necesitamos entender/conocer la forma de hablar con esos sistemas. Eso es lo que nos dan los conectores.

Microsoft tiene más de 2.000 conectores... y cada día van añadiendo más.

La forma de comunicarnos con un sistema viene definida por su API (ojo... cuando hablo de API no necesariamente me refiero a una API REST... hay otros tipos de APIs).

Esos APIs son muy específicos de cada sistema:
- API DE GMAIL permite operaciones como enviar un email, leer un email, borrar un email...
- API DE EXCEL permite operaciones como leer una celda, escribir en una celda, crear una tabla...

Lo que ha hecho microsoft es crear programas (conectores) que se encargan de conocer los APIs de cada sistema y permitirme invocarlos (llamarlos) desde mis flujos de trabajo de Power Automate sin necesidad de que yo tenga que conocer esos APIs... solo necesito conocer las ACCIONES que quiero realizar (enviar un email, leer un email, escribir en una celda...) y el conector se encargará de traducir esa acción a la llamada al API correspondiente.

OJO!
Dependiendo de la licencia de PowerPlatform que tenga tendré acceso a unos conectores u otros. Hay conectores que son gratuitos y otros (premium) que requieren una licencia específica.

Y otra cosa... una cosa es que tenga licencia para el conector... y otra cosa es que tenga licencia de ese sistema. Por ejemplo, puedo tener licencia para el conector de SAP... pero si mi empresa no tiene SAP, pues no podré usar ese conector.

Esos conectores tendremos que configurarlos al crear un flujo que los necesite.
Lo haremos con formularios. Cada conector tendrá un formulario específico que me pedirá la información necesaria para configurar esa conexión.
En general, en todo conector tendré que dar información de autenticación (usuario, contraseña, token...) para que el conector pueda autenticarse en ese sistema y realizar las acciones que le pida.
En ocasiones es necesario aportar información adicional. Si quiero conectarme a un servicio WEB, el conector me pedirá la URL de ese servicio. Si quiero conectarme a una base de datos, el conector me pedirá la cadena de conexión a esa base de datos...

Aquí hay un tema importante. Haay que tener cuidado de no usar CUENTAS DE USUARIO PERSONALES para configurar los conectores... porque si esa persona se va de la empresa, el conector dejará de funcionar. Lo ideal es usar cuentas de servicio (cuentas genéricas) para configurar los conectores.

Las conexiones las usaremos tanto para sacar datos de un sistema como para meter datos en un sistema. Por ejemplo, puedo usar el conector de Gmail para leer los emails que me llegan a mi cuenta de Gmail y luego usar el conector de Excel para escribir esos datos en una hoja de cálculo de Excel.
O lo contrario: puedo usar el conector de Excel para leer datos de una hoja de cálculo y luego usar el conector de Gmail para enviar esos datos por email.

# Disparadores (Triggers)

Hay 3 tipos de triggers... o más bien de flujos, dependiendo del tipo de trigger que usemos:
- Flujos de ejecución manual. Son flujos que se ejecutan cuando YO HUMANO aprieto el botón de play! AHORA!
- Flujos de ejecución programada. Son flujos que se ejecutan en un horario que yo defina. Por ejemplo, todos los días a las 8 de la mañana, o todos los lunes a las 9 de la mañana...
- Flujos de ejecución reactiva. Son flujos que se ejecutan cuando ocurre un EVENTO específico en un sistema. Por ejemplo, cuando recibo un email, o cuando se crea un nuevo registro en una base de datos...

# Acciones

Vamos a separarlas en 2 tipos:
- Acciones que involucran operaciones sobre sistemas externos. Por ejemplo, enviar un email, escribir en una celda de Excel, crear un nuevo registro en una base de datos... (ESTAS ACCIONES NECESITAN CONECTORES)
- Acciones que involucran operaciones internas de Power Automate. Sobre todo lógica de mi flujo y operaciones con datos. Por ejemplo, crear una variable, hacer un bucle, hacer una condición (IF), concatenar textos, convertir un número a texto...

---

Una cosa son los flujos de trabajo... y otra cosa son las ejecuciones de esos flujos de trabajo. 
- Un flujo de trabajo es un programa
- Una ejecución es la ejecución de ese programa.

Los flujos puedo:
- Activarlos, desactivarlos, editarlos
- Ejecutarlos
- Exportarlos, importarlos, compartirlos...

Las ejecuciones puedo:
- Verlas, analizarlas, monitorizarlas, depurarlas...

Esas ejecuciones las haremos sobre ENTORNOS de trabajo.

Un flujo solo lo tengo en un entorno... Los fluojs no pueden estar a la vez en varios entornos... aunque sí puedo exportar un flujo de un entorno e importarlo en otro entorno:
- Desarrollo
     | 
     v
- Producción

Un entorno es un espacio LOGICO dentro de PowerPlatform donde puedo crear mis flujos de trabajo, mis aplicaciones, mis bases de datos... y todo lo que tenga que ver con la PowerPlatform. Es como un contenedor donde guardo/ejecuto todos mis programas.

Asociado a un entorno hay una infraestructura física (servidores, almacenamiento...) que es la que se encarga de ejecutar los programas que yo cree en ese entorno. Esa infraestructura física es la que me cobra Microsoft por el uso de la PowerPlatform.
Esa infra la ofrece AZURE! *1


*1 NOTA: Realmente hay 2 tipos de flujos en power automate:
- Flujos que se ejecutan en la infraestructura de Microsoft (Azure) : Flujos de nube o cloud
- Flujos que se ejecutan en mi máquina local (on-premises) : Flujos de escritorio o desktop

Los creamos con programas separados:
- Power Automate (cloud) -> Flujos de nube
- Power Automate Desktop -> Flujos de escritorio

Quiero acceder a los archivos que tengo en una carpeta de mi ordenador... no puedo hacerlo desde un flujo de nube... necesito un flujo de escritorio.

Todo tiende hacia la nube... pero hay casos en los que es necesario seguir trabajando con flujos de escritorio.

Además, para que se pueda ejecutar un flujo de escritorio, es necesario que mi máquina local esté encendida... y que tenga el programa de Power Automate Desktop abierto.

# Movimiento de flujos entre entornos

Para llevar flujos de un entorno a otro puedo usar:
- Exportar/Importar (esto es lo primero que se metió... y lo más cutre!)
- Pipelines / Colas de trabajo (esto es lo que se metió después... y es lo más habitual hoy en día)
- Pipelines de Azure DevOps (esto es lo más profesional... y lo que se usa en empresas grandes)

Lo que estamos creando son programas... y como tales, necesitan un proceso de desarrollo, pruebas, despliegue... y mantenimiento.

- Pregunta. Cuántas veces voy a hacer cambios en mi programa a lo largo del tiempo? NPI.... pero seguro que MUCHAS!
- Esos cambios los haré en el entorno de producción? NO! Los haré en el entorno de desarrollo... y luego los llevaré a producción.

Eso implica que la operación de llevar un flujo de desarrollo a producción es una operación que haré muchas veces a lo largo del tiempo... y por lo tanto, esa operación me puede interesar: AUTOMATIZARLA!

Si lo pensaís... no es sino otro FLUJO de trabajo!

- Exportar/Importar es una operación manual... que no es difícil... pero es fácil meter la pata, ya que...
  Cuando exporto, exporto todo: Trigger, acciones, conexiones... En el entorno de producción, tendré las mismas conexiones que en el entorno de desarrollo? No!
  Al mover manualmente cosas de un entorno a otro, en el entorno de destino tendré posteriormente que revisar y modificar las conexiones para que apunten a los sistemas correctos... y esto es un proceso manual que puede ser propenso a errores.

  ESTO ME INTERESA AUTOMATIZARLO:
  - No solo porque voy a tardar menos tiempo... sino porque voy a reducir el riesgo de meter la pata al hacer ese proceso manualmente.

Esto es lo que me permiten las pipelines de PowerPlatform (lo tenemos dispobible en PowerApps, Power Automate y Power BI)

Estos pipelines me permiten definir procesos de migración de programas (flujos de trabajo, apps, dashboards...) de un entorno a otro... y lo hacen de forma automatizada, controlada y segura. En esos procesos de migración puedo hacer que se cambien unos conectores por otros... o que se cambien las conexiones por otras... o que se cambien los parámetros de las conexiones... o que se cambien los datos de las conexiones... o que se cambien los usuarios de las conexiones...

Azure DEVOPS es una herramienta de automatización de trabajo. Pero no es equivalente a Power Automate.
Es equivalente a: 
- Bamboo (Atlassian)
- Jenkins
- GitHub Actions
- GitLab CI/CD
- Travis CI

Es el antiguo: TFS (Team Foundation Server) rebautizado y reflotado.

Esta especializada en este tipo de tareas de automatización :
- Migraciones entre entornos
- Despliegues a producción
- Automatización de pruebas
- Automatización de tareas de mantenimiento

Hemos dicho que nuestro objetivo es AUTOMATIZAR LO MAS QUE PUEDA... de hecho, para que leches si no voy a estar usando Power Automate?
1º Lo primero que quiero automatizar es mi flujo de trabajo (Tareas que hago a diario) <- POWER AUTOMATE  = FLUJOS
2º La migración de esos flujos de trabajo entre entornos <- PIPELINES (Canalizaciones, Colas de trabajo)
3º Las pruebas!
   Tengo algo en desarrollo... y lo voy a llevar a producción... pero para llevarlo necesito antes hacer PRUEBAS!
   Lo que pasa es que las pruebas NO SOLO ME INTERESA HACERLAS cuando voy a hacer una migración entre entornos.... sino en cualquier momento mientras estoy tocando el código para saber que tal voy. Me voy a pasar el día haciendo pruebas -> AUTOMATIZAR LAS PRUEBAS!

   Eso es lo que me ofrece Azure DevOps... además de la automatización de las migraciones entre entornos... y la automatización de los despliegues a producción.

# Casos de uso de Power Automate

- Automatización de tareas repetitivas: Por ejemplo, enviar un email de seguimiento cada vez que se crea un nuevo registro en una base de datos.
- Extraer un excel de un email que me mandan cada semana y meter esos datos en una base de datos.
- Enviar un email a mi jefe todas las semanas con un informe de las ventas de la semana.
- Automatizar tareas de manipulación de datos cuando recibo un email con un adjunto excel... por ejemplo, leer ese excel, hacer unos cálculos con esos datos y luego escribir esos datos en una base de datos o enviarlos por email a otra persona.
- Envío de notificaciones a teams cuando ocurre un evento específico en un sistema... por ejemplo, cuando se crea un nuevo registro en una base de datos, o cuando se recibe un email con un asunto específico...

Son problemas pequeños. Si lo que quiero es automatizar un flujo grande y transversal que involucre a muchos sistemas... probablemente Power Automate no sea la mejor herramienta para eso... Ahí es donde haré un desarrollo a medida centralizado y más controlado.

Cuando hay problemas pequeños... pero que me consumen mucho tiempo... ahí es donde Power Automate me puede ayudar a ahorrar mucho tiempo... y a reducir el riesgo de meter la pata al hacer esas tareas manualmente.

# Sobre los flujos de Power Automate

Queremos huir de los procesos (flujos) grandes.

En lugar de un proceso grande, me interesa más crear 5 procesos pequeños que se encarguen de hacer tareas específicas... y luego integrar esos procesos pequeños entre sí para conseguir el resultado que quiero.

- Esto es más fácil de desarrollar (problema pequeño)
- Aporta valor más rápido (problema pequeño resuelto antes)
- Es más fácil de mantener
- Es más fácil de evolucionar
- Es más fácil de reutilizar

Puedo hacer que un flujo se ejecute después de otro (por ejemplo, mediante un trigger de tipo "Cuando se complete un flujo")... 

# Dataverse

Es la BBDD de la PowerPlatform. Es una base de datos relacional (como un SQL Server o un Oracle) en la nube que me permite almacenar y gestionar datos de forma estructurada. Es el lugar donde puedo guardar los datos que necesito para mis flujos de trabajo, mis aplicaciones, mis análisis...

    Power Apps
        App web y móvil
        - Solicitar reembolsos de dinero
        - Ver el seguimiento de mis solicitudes de reembolso
        - Aprobar o rechazar solicitudes de reembolso
        Todo eso esta trabajando contra dataverse.

        A lo mejor, una vez aprobada una solicitud quiero:
        - Mandar un email a la persona (Power automate)
        - Dar de alta el registro en la base de datos de mi ERP (Power Automate) 

---

# Azure?

El cloud de microsoft.

## Qué es un cloud?

Es el conjunto de servicios que una empresa de IT ofrece a través de internet de forma:
- Desatendida / automatizada
- Mediante un modelo de pago por uso (pay as you go)

Ahí hablamos de servicios de :
- Infraestructura (IaaS): Servidores, almacenamiento, redes...
- Plataforma (PaaS): Bases de datos, servicios de inteligencia artificial, servicios de análisis
- Software (SaaS): Aplicaciones completas que puedo usar directamente (Office 365, Dynamics 365, PowerPlatform...)


---

# Modelos de IA.

    Cúal es la forma de darle información a los modelos? PROMPT

    Esto es IAs en modo pregunta (ASK)
        HUMANO -> Pregunta -> Chatbot -> llm -> Respuesta -> HUMANO
                   PROMPT

    Hoy en día, usamos las IAs en modo AGENTE! La IA no solo genera una respuesta textual, sino que también puede generar acciones (ejecutar un programa, hacer una búsqueda en internet, enviar un email...)

    Cuando trabajamos en modo agente, los prompts no valen para nada!
    Lo importante cuando trabajamos en modo agente es el contexto. Ahí es donde aportamos el 99% de la información a la IA para que pueda tomar decisiones y generar acciones.

    De hecho ese contexto puede ser enorme!

    Antrhopic, que es una empresa que genera los mejores modelos de lenguaje a gran escala (LLMs) del mundo, definieron un "estandar" para hacer llegar información a los modelos: MCP= Model Context Protocol. Es un protocolo para enviar información a los modelos de forma estructurada, con un formato específico, para que puedan entenderlo y procesarlo de la mejor manera posible.

    Hoy en día puedo enganchar un modelo a mi BBDD SQL Server.






---

# Qué entendemos por una IA?

Una IA tradicionalmente ha sido cualquier programa que simulara un comportamiento humando donde fuese necesario un mínimo proceso de razonamiento.

Hay 2 formas de montar estos programas:
- Programación tradicional: Escribir un programa con reglas y lógica para simular ese comportamiento humano (IFs, Condicionales)
- Machine Learning:         En este caso, nosotros no escribimos el programa. Dejamos a un programa que genere el programa que nos interesa.
                            En este caso, al programa que generará mi programa le paso un montón de datos procesados ya por humanos. De forma que su misión será consatruir un nuevo programa que antes los mismos datos, tomase las mismas decisiones que el humano.  
                            En este sentido, los programas que mejor han funcionado son los que llamamos redes neuronales profundas (Deep learning)... y cuidado. No todas las redes neuronales profundas son LLMs (Modelos de Lenguaje a Gran Escala). De hecho, los LLMs son sólo una parte de las redes neuronales profundas.

Hoy en día, se usa el término IA para referirnos a redes neuronales profundas, y dentro de estas, a los LLMs.

# Es copilot una IA?

Copilot no es una IA... es un nombre comercial que Microsoft da a todos sus productos que tiene que ver con IAs.

- Copilot Studio (power platform)
- Copilot (365)
- Github Copilot

El conocimiento lo aportan las redes neuronales profundas (modelos)... y hay modelos de:
- Lenguaje (LLMs)
- Visión (CV)
- Audio (ASR)
- ...
Dentro de la Powerplatform, podremos usar Copilot (productos que tengan que ver con IA... que usen modelos-redes neuronales profundas) para muchas cosas:
- Ayudarme a crear un flujo de trabajo en power automate
- Ayudarme a crear una app en power apps
- Ayudarme a crear generar un modelo de datos de una BBDD en Dataverse

Otro uso que tenemos es el de integrar un modelo en un flujo de trabajo de Power Automate (Copilot Studio) para que me ayude a tomar decisiones dentro de ese flujo de trabajo.

    Podría usar Copilot para crear el flujo de trabajo de abajo:

                                         ----- Copilot Studio ---
    Al recibir un email -> Contenido ---> Modelo de lenguaje (LLM) -> Resumen -> Email a otra persona
    
    Al recibir un email -> Contenido ---> Modelo de clasificación -> Prioridad -> Tome ciertas acciones dependiendo de la prioridad


Los modelos que entrenaremos / usemos dentro de nuestros flujos... hemos de tratarlos como entes vivos.
El primero que monte NUNCA va a funcionar bien... funcionará más o menos bien.
Poco a poco lo iré perfilando, para que funcioné mejor! 
Y lo haré hasta que consiga un resultado que sea suficientemente bueno para el uso que quiero darle a ese modelo.

Y Esto va a tener un impacto ENORME en la forma de montar los flujos de trabajo en Power Automate.

    Día 1 puedo montar este flujo? SI.... va a funcionar bien? NPI
    Porque no sé si ese modelo está haciendo una buena clasificación o no... no sé si el resumen que me está dando es bueno o no...
    
    Al recibir un email -> Contenido ---> Modelo de clasificación -> Prioridad -> Tome ciertas acciones dependiendo de la prioridad

    Decisión: El día 1 nunca montaría un flujo como este.

    Al recibir un email -> Contenido ---> Modelo de clasificación -> Prioridad -> EXCEL
            TAREA MANUAL DE REVISION de las prioridades que me ha dado el modelo.
    EXCEL -> Tome ciertas acciones dependiendo de la prioridad

    Pero... a su vez... de la revisión que haga, uso esa información. (en cuántos discrepo y en cuántos estoy de acuerdo) para ir generando una nueva versión de ese modelo que me dé mejores resultados.

    Y legará un día en que mi revisión resulte inutil... porque el modelo ya me da resultados suficientemente buenos como para que no tenga que revisar nada.

    Y ese día : 
    Al recibir un email -> Contenido ---> Modelo de clasificación -> Prioridad -> Tome ciertas acciones dependiendo de la prioridad


    El resultado de esto es que:
    - El flujo, que es un programa (una automatización) no va a tener una única versión. Irá evolucionando a lo largo del tiempo.
    - El modelo, que es un programa (una automatización) no va a tener una única versión. Irá evolucionando a lo largo del tiempo.

    Y tendré versiones de mi modelo... y versiones de mi flujo

        Y quizás la v1 del modelo la ejecuto contra la versión 1 del flujo... día 1
        El día 30: Tengo la v2 del modelo y la v1 del flujo... y las ejecuto juntas.
        El día 60: Tengo la v2 del modelo y la v2 del flujo... y las ejecuto juntas.

    Y esto se empieza a complicar... Y aunque no necesite picar ni una linea de código... desde luego empieza a asomar la idea de que si debo tener amplios conocimientos de desarrollo de sistemas para poder montar estas cosas.

        Dia N-1 trabajar 8 horas en una tarea -> Día N trabajar 0 horas en esa tarea... ESTO NO VA A PASAR! Y si intento forzarlo, será un desastre!
        El proceso es iterativo:
            Día N: Trabajo 8 horas en esa tarea
            Día N+1: Trabajo 4 horas en esa tarea (porque el modelo o la automatización ya me ayuda a hacer parte del trabajo)
            Día N+2: Trabajo 2 horas en esa tarea
            Día N+3: Trabajo 1 hora en esa tarea
            Día N+4: Trabajo 5 minutos en esa tarea (porque el modelo o la automatización ya me ayuda a hacer todo el trabajo)

# Hay que tener mucho cuidado con los modelos.

- Cuánto cuesta crear un modelo? Muy caro...
  GPT 4.5
  Gemini 3.0 


  71B params -> Tiene que ver con el temaño de la red neuronal.

        71B (Americanos) = 71 Millardos -> 71.000.000.000

    P1      Q1      J1

    P2      Q2      J2

    P3      Q3      J3

    PN      QM      JL

- Cuánto cuesta usar uno de estos modelos entrenados? TAMBIEN ES MUY CARO!
    Un modelo de 71B de parámetros, cada tarea al menos hará 71B de operaciones matemáticas... y eso se traduce en un coste económico muy alto.
    Esto es CARO Y LENTO!

    En muchos casos me interesa usar modelos más pequeños.


- Quiero un modelo que sea capaz de entender qué dígito hay en una imagen.

    Imágen de 6 x 6 pizels -> 36 píxeles (0/1)

    +-+-+-+-+-+-+
    |0|0|0|0|0|0|           Entrada 1      (0/1)
    +-+-+-+-+-+-+           Entrada 2      --->    Programa 1 (1/0) en base a si hay más 1s en la parte de arriba de la imagen
    |0|1|1|1|1|0|           Entrada 3              Programa 2 (1/0) en base a si hay más 1s en la parte de abajo de la imagen
    +-+-+-+-+-+-+                                  Programa 3 (1/0) en base a si hay más 1s en la parte de la izquierda de la imagen 
    |0|1|0|0|1|0|           Entrada 36             Programa 4 (1/0) en base a si hay más 1s en la parte de la derecha de la imagen 
    +-+-+-+-+-+-+
    |0|1|0|0|1|0|
    +-+-+-+-+-+-+
    |0|1|1|1|1|0|
    +-+-+-+-+-+-+
    |0|0|0|0|0|0|
    +-+-+-+-+-+-+  
    
    Todos esos programas me dan 0... qué número es? 0, 8, I, 5, 2

    Podría montar otro programa que en función de las salidas de esos N programas que he hecho determine qué número es.

    Y ESTO ES UNA RED NEURONAL.

    La llamo así si esos programas no los creo yo... sino que dejo a otro programa que los cree.

                                                    Este es el uso que quiero dar a ese aprendizaje!
                                                    vvv
        Capa 1 N Entradas -> Capa 2 M Programas -> Capa 3 1 Programa -> Salida (Número)             Arquitectura de la red neuronal.
                                ^^^                Capa 3 1 Programa 2 -> Salida (0|1) La foto es de un 8 o no!
                                ^^^                Capa 3 1 Programa 3 -> Salida (0|1) La foto es de un número simétrico o no!
                                Aquí es donde está el aprendizaje

        Programa 1 = 0.9*E1 + 1*E2 + 1*E3 + 1*E4 + 1*E5 + 1*E6 + 1*E7 + 1*E8 + 1*E9 + 1*E10 + 1*E11 + 1*E12 + 1*E13 + 1*E14 + 1*E15 + 1*E16 + 1*E17 + 1*E18 - 1*E19  - 1*E20 - 1*E21 - 1*E22 - 1.2*E23 - 1*E24 - 1*E25 - 1*E26 - 1*E27 - 1*E28 - 1*E29 - 1*E30 - 1*E31 - 1*E32 - 1*E33 - 1*E34 - 1*E35 - 1*E36 > 0

         E = Entrada (Píxel)

         Programa = Función matemática que combina las entradas (píxeles) con unos pesos (coeficientes) para determinar la salida (si hay más píxeles encendidos en la parte de arriba, abajo, izquierda o derecha de la imagen)

         Capa de entrada -> Capa oculta -> Capa de salida

         En este caso, la capa oculta tiene N programas (funciones matemáticas) que procesan las entradas y luego una capa de salida que toma las salidas de esos N programas para determinar el número que representa la imagen.


- Quiero generar una imagen de un dígito
