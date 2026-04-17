
# Ambito / Scopes

- Inicializar variable NO PUEDE IR EN UN SCOPE
  Lo que metemos es el establecer variable 

- Si tengo ya un flujo y quiero poner scopes... al mover cosas se me jode el flujo.
    [    A -> B -> D   ]
        -> C ->

- Los scopes, la buena práctica es usarlos lo primero de todo.

---

# Cómo planteamos el desarrollo de un flujo

- El flujo tendrá BLOQUES CONCEPTUALES

    1. Disparador

    2. Declarar mis variables

    3. Tareas <- Scope
        |
        | Solo cuando falla o tenemos un timeout
        v
    5. Gestión de errores <- Scope


Lo ideal cuando empiezo un desarrollo es olvidarme de conectores... olvidarme de los actions.
Los conectores sería algo que pondría al final!

Cuando programo:
- Programar contra datos / contra mi caso concreto
- Programar contra requisitos / Especificación        <<< ESTO QUIERO !

A mi me da igual que los datos me lleguen de un form, de un excel, de un mail, de una bbdd... ESO DA IGUAL
No quiero bajo ningún concepto mi flujo atado a esas cosas.

Lo que empezamos es definiendo SCOPES!



    1. Disparador

    2. Declarar mis variables

    3. Tareas <- Scope

            Calcular una edad <- Scope

            Solicitar aprobación si es menor de edad <- Scope
                -> Quiero dar un trámite especial de error!

            Solicitar a una IA un mensaje  <- Scope


        |
        | Solo cuando falla o tenemos un timeout
        v
    4. Gestión de errores <- Scope

---

# Compartir flujos!

Los flujos los puedo querer compartir por distintos motivos:
- Que un colega vaya a montar algo similar a lo mio... y quiera partir de ello
- Que lo quiero poner en otro entorno (por ejemplo producción)

En cualquiera de esos casos, una cosa es el flujo... que puedo querer copiarlo tal cual!
Pero hay mucha información que se usa en el flujo y que no quiero copiar!
    - Conexiones (en el entorno de desarrollo, quizás uso un usuario/canal de teams... pero en producción quiero usar otro).. O los emails que mando.
    - Datos concretos: Revisores, nombres de canales/chats, carpetas OneDrive, etc... < Variables de entorno

Opción 1:
- Largo el flujo y cambia todo en el nuevo entorno...  RUINA!
  - Propenso a errores:
    - Se me olvide cambiar algo
    - Que deje algo mal puesto
  - Este trabajo posiblemente lo haga muchas veces!

Aquí nos salen 2 conceptos que vamos a usar para evitar estas situaciones:
- Variables de entorno
- Referencias de Conexión

Nos ofrecen un nivel de indirección en una asociación.

    Action -> Conector          En lugar de esto, que es lo que tenemos!

    Action -> VARIABLE? <- Conector
               ^^^^^
               Referencia de conexión

    La referencia de conexión actúa como una variable que contendrá en cada entorno el conector que le asignemos en ese entorno. Y eso se mantendrá a futuro, si hago nuevos despliegues.

    Action 
        Propiedad de configuración                      
            "A qué correo mando esto para aprobación?"  -> ~~federico~~
            "A qué correo mando esto para aprobación?"  -> VARIABLE DE ENTORNO <- federico



---


# Que metemos en el EXCEL?

Nombre
Email
Fecha de Nacimiento
Observaciones
Mensaje de bienvenida
Fecha de alta
Aprobado o no

---

# Pasos que necesitamos dar:

- Tener un excel donde meter esto. Necesitamos crearlo
- Y dentro del excel meteremos una TABLA con esas columnas. TABLA , TABLA!
- Donde lo guardo? ??????       VARIABLE DE ENTORNO (RUTA Y NOMBRE DEL ARCHIVO)
  - OneDrive, SharePoint
- Tarea: 
  - Insertar fila en una tabla -> Excel Online (Business)
  - Necesito una conexión a Excel Online (Business)
  - Y dentro de esa conexión, necesito una referencia de conexión a ese excel concreto.


---

Mañana lo primero será llevar el dato a una BBDD relacional.
Partir el flujo!

    ACPETACION O NO DE LA SOLICITUD
FLUJO 1: El flujo tiene que acabe grabando en un excel si se admite o no la persona.
    
    
    EXCEL es la interfaz

    TRAMITE CUANDO HAY UNA SOLICITUD ACEPTADA
Flujo 2: Que lee cada fila que se mete en el excel
    Caso que sea necesario:
    - Genera mensaje de IA
    - Manda Email
    - Guarda los buenos BBDD
    - ...
  - 
  
---



# Este flujo que tenemos, cómo l partimos / refactorizamos... para que tenga sentido y sea más facil de mantener y evolucionar!

- Logica / Salidas
- Funciones pequeñas y una que orqueste!
- Orquestador

---

Hoy en día la tendencia es:
- Nada de monolitos (Mega flujo que hace todo).. Y cuidado... Un orquestador... es una forma encubierta de eso.
- Queremos componentes desacoplados!
- Cómo comunicamos esos componentes:
  - Colas de mensajes / BBDD
  - Reactividad (eventos)

Nuestro proceso hace muchas cosas! Y queremos que sean cosas Que no estén acopladas entre si.
Que no dependan unas de otras.

    Ahora mismo el procesamiento (el determinar si le doy acceso o no) depende FORMS

Lo que queremos es que esos componentes que vamos a crear dependan de APIs. No quiero que dependan entre si.

    Formulario Microsoft <- Lógica de validación <- Base de datos

Necesitamos establecer puntos intermedios = API = ARTEFACTOS


    Formulario Forms -> Lógica de validación

    Formulario Forms                -> BBDD <- Lógica de validación -> BBDD <- Tramite cuando le damos acceso       Mandar un email de bienvenida
    Formulario Forms v2             -> BBDD                                 <- Tramite cuando le no damos acceso
    Emails / IA Extracción de datos -> BBDD                                 <- Tramite 2 cuando le damos acceso     Mandar una notificacion a teams consolidad al día


