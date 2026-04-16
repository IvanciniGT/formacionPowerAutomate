
# Flujos

Comienza con un desencadenador
Continua con acciones

Esas acciones pueden ser lineales, o pueden tener partes que se ejecuten paralelas entre si.

Cada cajita del flujo (desencadenador o acción) recibe y produce datos.
Esos datos pueden ser de distintos tipos.

Todo el juego que tenemos es cuadrar los datos de salida de una cajita con los datos de entrada de otras cajita.

En este sentido vamos a tirar mucho de expresiones, que son como pequeñas funciones que nos permiten transformar los datos de una cajita para que encajen con la siguiente.


---


# Desarrollo

    Desarrollo (escribiendo código) <> Pruebas -> OK -> Refactorización <> Pruebas -> OK -> Desplegar
    ----------------- 50 % del trabajo -------------    ---------- 50 % del trabajo ------


# Deuda técnica

SonarQube es una herramienta de análisis de calidad de código. Hay cientos de herramienats como ella. Quizás es la famosa y usada.
Esas herramientas hacen pruebas al código.... pero no pruebas funcionales. Pruebas de calidad.

Tienes un código que funciona.... ok... pero es decente? Es fácil de mantener? Es fácil de entender? Es fácil de ampliar? Es fácil de modificar?

SonarQube busca/identifica lo que llama SmellCode (código que es una MIERDA!... y por ende huele fatal!)

Es una mierda porque:
- No está escrito como la mayoría de gente espera que esté escrito
- No es fácil de entender para una persona que no lo ha escrito
- Tiene muchas cosas duplicadas, acopladas.

Esto incremente lo que se denomina la deuda técnica -> OK | NOK

La deuda técnica es el sobre-coste que tiene mantener ese código a lo largo del tiempo. Cuanto más código de mierda tengas, más difícil será mantenerlo, y más caro será mantenerlo.... más deuda técnica tendrás.

El concepto "deuda"... Es una hipoteca que debo pagar... Las deudas se pagan en algún momento.
Dentro de 2 años será necesario hacer una modificación (VA A PASAR) y la pregunta es cuánto me va a costar hacer esa modificación tal y como tengo el código, comparado con cuánto me costaría hacer esa modificación si tuviera un código más limpio, más fácil de entender, más fácil de modificar.

Como toda deuda, cuanto más tiempo pasa, más intereses tengo que pagar... en este caso, cuanto más tiempo pasa, más horas tendré que invertir en el futuro para hacer esa modificación, porque el código es tan difícil de entender que me va a costar mucho entenderlo, y además es tan difícil de modificar que me va a costar mucho modificarlo.

A mi, hoy en día, cambiar el nombre de una cajita me cuesta 20 segundos.
Pero el entender qué lecvhes hace esa cajita dentro de 1 año, por otra persona que no soy yo me puede llevar 1 hora o más.


---


# Aprobaciones

Tenemos 4 acciones de aprobación en power automate:

- Crear aprobación                                      Procesos asíncronos
- Esperar aprobación
-----
- Crear y esperar aprobación                            Procesos síncronos
- Crear y esperar aprobación personalizada de texto

---

Al hacerlo asíncrono tengo la oportunidad de hacer otras cosas mientras espero la aprobación, y más adelante cuando ya sea estrictamente necesario esperar la aprobación.

Eso también me permite solicitar varias aprobaciones diferentes!

    Proceso -> Requiere aprobación financiera -> Continuo
            -> Requiere aprobación de RRHH    ->


Hay un deadline de 30 días para responder a una aprobación, pero si no se responde en ese plazo, el flujo produce un error (acaba con error)

Con respecto a la aprobación, podemos optar por:
- Que la dé una persona de entre un grupo de personas (cualquiera de ellas puede dar la aprobación)
- Que todas las personas de un grupo den la aprobación (todas deben dar la aprobación)
- ...

La idea de un flujo de aprobación es que una vez tenga o no la aprobación haga otras cosas.
Querremos más tareas después de la aprobación, quizás tareas para cuando SI me dan la aprobación y otras en caso de que no me aprueben.

Meteré un condicional.. pero qué pongo en la condición?

---

> Todo el juego que tenemos es conectar datos de salida de unas cajas con datos de entrada de otras cajas.

# Atención, debes aprobar esto

El usuario **Federico** quiere acceder a la plataforma... pero tiene solamente *17* años.

¿Debemos darle acceso?

Te recuerdo que:
- Para acceder a la plataforma, el usuario debe ser mayor de edad (18 años o más)
- O tener consentimiento de sus padres/madres/tutores legales
---

replace(
  replace(
    concat(
        '# Atención, debes aprobar esto',
        decodeUriComponent('%0A'),
        decodeUriComponent('%0A'),
        'El usuario **{{NOMBRE}}** quiere acceder a la plataforma... pero tiene solamente *{{EDAD}}* años.',
        decodeUriComponent('%0A'),
        decodeUriComponent('%0A'),
        '¿Debemos darle acceso?',
        decodeUriComponent('%0A'),
        decodeUriComponent('%0A'),
        'Te recuerdo que:',
        decodeUriComponent('%0A'),
        '- Para acceder a la plataforma, el usuario debe ser mayor de edad (18 años o más)',
        decodeUriComponent('%0A'),
        '- O tener consentimiento de sus padres/madres/tutores legales'
    ),
    '{{NOMBRE}}',
    triggerOutputs()?['headers']?['x-ms-user-name']
  ),
  '{{EDAD}}',
  string(variables('edad'))
)

** Negrita
*  Cursiva
*** Negrita y cursiva
~~ Tachado
`  Codigo (Fuente nomoespaciada)

- Item1
+ Item2
* Item3

#
##
####### Títulos

[Mensaje que muestra](http://www.google.com) 
![Texto alternativo](http://www.google.com/image.jpg)

| Item1 | Item2 | Item3 |
|-------|------:|:-----:|
| Item4 | Item5 | Item6 |

---

PowerAutomate -> Configurar un Flujo -> Ejecutamos (PROGRAMA EN EJECUCION INDEPNDIENTE A OTROS PROGRAMAS)

Ese programa hace comunicaciones con otros programas (CONECTORES)
- Por ejemplo, MS ofrece un servicio centralizado (más allá de la power platform) de gestión de Aprobaciones.
  Eso es otro programa, que se llama "Centro de Aprobaciones" (APPROVAL CENTER)
  Mi programa (mi flujo) habla con ese programa por HTTP / REST :
    Oye... dame de alta una nueva aprobación:
        POST https://approvals.microsoft.com/api/approvals
        Body: {
            "title": "Atención, debes aprobar esto",
            "description": "El usuario **Federico** quiere acceder a la plataforma... pero tiene solamente *17* años. ¿Debemos darle acceso? Te recuerdo que: - Para acceder a la plataforma, el usuario debe ser mayor de edad (18 años o más) - O tener consentimiento de sus padres/madres/tutores legales",
            "approvers": ["
                "profesor@yo.com"
            ]
        }
Al hacer esa petición pueden aparecer errores:
- Problema de conexión de red
- El servicio de aprobaciones está caído (HTTP Status 500)

Ante eso... como quiero que se comporte mi programa?


- No tenga permisos para crear aprobaciones (HTTP Status 403)



De repente mandamos 500 de golpe... saturamos el servicio... empieza a encolarlas.. pero tieme un límite en la cola.
Y en un momento dado nos saca de la cola y nos da un timeout... o un error 500... o un error 503...

Qué hago? Lo normal es volver a mandarlo.... aplicamos en este caso politicas de reintento exponenciales...
De forma que el primer reintento se haga a los 5 segundos, el segundo a los 10 segundos, el tercero a los 20 segundos... y así sucesivamente... hasta un máximo de reintentos o un máximo de tiempo.

---

Al empezar a trabajar en un flujo:
- Siempre empiezo por lo que llamamos el Happy Path -> El camino feliz, el camino que todo el mundo espera que se ejecute, el camino sin errores, el camino sin excepciones.
- Una vez tenemos el happy path implementado, empezamos a blindarlo...

---

# Solicitud

La solicitud es una plantilla de prompt.
ES UN TEXTO.
En ese texto puedo añadir placeholders, que son como huecos que luego se rellenan con datos concretos (que deben ser textos).


---

Hay mucho tipos de objetivos que buscamos hoy en día con las IAS:

- Clasificar (Detectar idioma, sentimientos, dar etiquetas)
- Generativos (Generar texto, generar código, generar imágenes, generar audio, generar video)
- Extractores (Extraer información concreta de un texto, como por ejemplo, extraer el nombre de una persona, o extraer el número de teléfono, o extraer la fecha de un evento...)
  Esto está también disponible para imágenes. 

Le paso un email:
- Quiero que extraiga todas las personas, con sus telefonos y sus email y otra infor que pueda haber.
- Lugares
- Incidentes en una instalación

Hola buenos días, 

                         Tipo de lugar<-Emplazamiento
                         ------------   -------
Tenemos un problema en la instalación de Madrid, se ha caído el sistema de refrigeración y 
                                                       ---------------------------------
                                                        tipo de incidente: 00294
se ha inundado la sala de servidores. Necesitamos que alguien venga Juan a arreglarlo lo antes posible.
    ---------------------------------
    incidente: 0019287


    ha dejado de funcionar todo lo del fresquito!
    ---------------------------------------------
    tipo de incidente: 00294


Hago mis tareas previas... y pido a una IA un mensaje de bienvenida...
Y solicito aprobación de ese mensaje de bienvenida...
Y mando lo que se haya modificado/aprobado (eso se hace desde teams)
En cuanto tenga aprobación:
- Guardo la petición original, texto IA y el texto corregido/aprobado en una base de datos 
- Con esa información voy mejorando la plantilla de solicitud, para que la próxima vez que tenga que hacer una petición similar a la IA, esa plantilla ya esté mejorada con lo que he aprendido de esta interacción.

La gracia además es ir aprovechando todo el output de este proceso para mejorar la IA

Cuando el 99% sean buenos.. quito la aprobación de texto!

---
    Disparador
     v
edad = resultadoCalculo(fechaDeNacimiento)
     v
if(edad > 18) :
    pass
else:
    resultado = solicitoAprobacion()

if(edad > 18 or resultado == 'aprobado') :
    pedir mensaje a la IA


---

try: 
    edad = resultadoCalculo(fechaDeNacimiento)

    accesoPermitido = edad > 18   # Inicializar variable

    if(!accesoPermitido) :
        resultado = solicitoAprobacion()
        accesoPermitido = resultado == 'aprobado'    # Establecer variable

    if(accesoPermitido) :
        pedir mensaje a la IA

except:
    # Aquí gestiono el error, por ejemplo, enviando un email a soporte técnico o registrando el error en un log para que luego lo revise un desarrollador.
