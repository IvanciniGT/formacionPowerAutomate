
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

