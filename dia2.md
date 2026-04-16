
PowerPlatform:
    - PowerApps                                     Aplicaciones web y mobile
    - PowerAutomate                                 Automatización de procesos   
    - PowerBI                                       Análisis de datos   
    - Copilot builder (antes PowerVirtualAgents)    Creación de chatbots inteligentes y en general procesos IA
    - PowerPages                                    Creación de sitios web de baja codificación     

Además tenemos Dataverse, que es la base de datos común para todas las aplicaciones de PowerPlatform, lo que permite una integración fluida entre ellas.

La powerPlatform va orientada a soluciones muy de nicho.

# Power Automate

Es una herramienta NoCode que permite a los usuarios crear flujos de trabajo automatizados entre aplicaciones y servicios para sincronizar archivos, obtener notificaciones, recopilar datos y más.

    App1    Y movemos datos entre ellas o lanzamos mensajes a ellas
    App2
    App3

    Las apps pueden ser: Office, Google (Gmail, drive, calendar), redes sociales, servicios rest http....

Tenemos 2 tipos de flujos:

    - Flujos de nube: se ejecutan en la nube y pueden ser programados, activados por eventos o manualmente.
    - Flujos de escritorio: se ejecutan en el equipo local y permiten automatizar tareas que requieren interacción con la interfaz de usuario / o con documentos/archivos que tengo en mi equipo.
        ^^^ NOTA: Es posivble crear flujos de escritorio que se ejecuten no en mi equipo, sino en un equipo contratado en cloud.

Usamos mucho los conectores:
    Son programas que saben hablar con otros programas. Me permiten escuchar eventos de esos programas, o lanzar acciones a esos programas. Por ejemplo, un conector de Gmail me permite escuchar cuando llega un nuevo correo, o enviar un correo desde mi flujo.

# Flujo en power automate

Un flujo comienza siempre con un desencadenador (trigger) y luego tiene una secuencia de pasos.
Tanto trigger como los pasos (acciones) pueden necesitar de conectores.

# Acerca del NoCode

Cuidado... sin humo.
Es cierto que no hace falta escribir ni una línea de código.
No implica que no sea necesario tener conocimientos de desarrollo/arquitectura de software y otros.

Microsoft ha cambiado el discurso (con prudencia) y ahora aboga por la implantación de un CoE (Center of Excellence) para garantizar que las soluciones creadas con PowerPlatform sean de calidad, seguras y mantenibles. Esto implica que aunque no se escriba código, es necesario tener un equipo con conocimientos técnicos para supervisar y gestionar las aplicaciones y flujos creados.

El CoE estamos hablando de un DEPARTAMENTO en la empresa que se encarga de gestionar todo lo relacionado con PowerPlatform, desde la formación de los usuarios hasta la supervisión de las aplicaciones y flujos creados, pasando por la gestión de licencias y la seguridad. Proveer plantillas, buenas prácticas, etc.

# Entornos de trabajo

Cualquier trabajo que haga en la powerplatform (y por ende en power automate) se hace dentro de un entorno. Un entorno es un espacio de trabajo que contiene sus propios recursos, como aplicaciones, flujos, conexiones y datos. 
Las bbdd de dataverse también se crean dentro de un entorno.

Y todos esos objetos los podemos replicar/promocionar entre entornos. Por ejemplo, puedo tener un entorno de desarrollo donde creo mis flujos y luego los promociono a un entorno de producción para que los usuarios finales los usen.

Habitualmente esos entornos no los gestiona el usuario que está creando los flujos, sino que los gestiona el equipo del CoE, que se encarga de crear y configurar los entornos según las necesidades de la empresa.

Hay 3 grandes formas de mover elementos entre entornos:

    - Exportar/importar = RUINA! Proceso manual, propenso a errores, no es escalable.
                                 Esto habría que hacer elemento a elemento (objeto a objeto) y no es nada recomendable.
                                 Implica luego cambiar configuraciones manualmente en el entorno de destino, lo que es un error seguro.

    - Soluciones = ESTO ES LO GUAY (al menos el inicio de lo guay!)
      Una solución es un conjunto de elementos/objetos relacionados que se pueden empaquetar y mover juntos entre entornos. Por ejemplo, puedo tener una solución que contenga un flujo, 3 tablas de una BBDD de dataverse y 2 conectores. Al mover la solución, se mueven todos esos elementos juntos, lo que reduce el riesgo de errores y hace el proceso mucho más eficiente.
      Además, con las soluciones puedo usar un sistema de control de versiones, lo que me permite llevar un seguimiento de los cambios realizados en mis flujos y otros elementos, y revertir a versiones anteriores si es necesario.

      Este es un primer paso... Me permite automatizar el proceso de promoción entre entornos
      
    - Lo mejor es irnos en el FUTURO a los pipelines de Azure DevOps , que nos permiten automatizar completamente el proceso de promoción entre entornos, integrando el control de versiones y las pruebas automatizadas. Esto es lo ideal para empresas que quieren escalar su uso de PowerPlatform y garantizar la calidad y seguridad de sus aplicaciones y flujos.  

# Copilot

Copilot es un nombre bajo el que MS agrupa todo lo que tiene que ver con IAs.

Usaremos varios productos con apellido Copilot:
- Crear modelos de IA personalizados con Copilot builder
- Crear los flujos de Power Automate con Copilot

Es importante separar el concepto de MODELO de IA, del concepto de la herramienta que uso para comunicarme con ese modelo de IA. 
Esos modelos son las Redes Neuronales. Tenemos muchas:
- LLM (Large Language Models) como GPT-4, GPT-5, Claude .
- Modelos de visión artificial como DALL-E, Midjourney, Stable Diffusion.
- Modelos de reconocimiento de voz como Whisper.
- Modelos de clasificación
- Modelos de predicción

---

Cuando accedemos a la PowerPlatform, quien autentica al usuario es EntraID de Azure.

# Conceptos básicos de Seguridad

- Identificación    Decir quien soy
- Autenticación     Comprobar que eres quien dices ser      < Esto es lo que hace EntraID
- Autorización      Sabiendo que eres quien dices ser, ver que puedes hacer.
  La autorización (con respecto a la power platform) se efectua a múltiples niveles:
  - Licencia. Microsoft 365 para empresas. Verifica que el usuario tiene licencia.
  - Roles a nivel de entornos.
    Los flujos, las apps, las columnas de una tabla de una BBDD pueden hacer uso de esos roles para verificar si el usuario tiene permiso para usarlos o no.... y cómo pueden usarlos.

    Todo esto ya se configura a nivel de PowerPlatform.

---

Git es un SCM (Source Code Management) que nos permite llevar un control de versiones de nuestro código fuente.

COMMIT
- Verbo         Acción de crear un commit / confirmación
- Sustantivo
        - En otros sistemas de control de versiones, un commit era un paquete de cambios realizados sobre el código.
        - En Git, un commit es una foto COMPLETA (BACKUP COMPLETO) del proyecto en un momento dado del tiempo.
          Es lo mismo que darle botón derecho a una carpeta y hacer "Enviar a > Carpeta comprimida (zip)".
          Además de los ficheros del proyecto, se guardan algunos metadatos:
            - Autor del commit / Persona
            - Fecha y hora del commit
            - Mensaje del commit / Descripción de los cambios realizados
        
Visto así, qué diferencia a GIT de un sistema de copias de seguridad?
El tema con este tipo de herramientas es que:
1. Todo commit (backup) parte de un commit anterior . Lo que tenemos es una secuencia de commits (backups) que forman una línea temporal. Esto nos permite navegar por esa línea temporal y recuperar cualquier estado anterior del proyecto.
2. En realidad no vamos a llevar control de una única línea temporal, sino de varias líneas temporales (ramas/Branches).

Un proyecto de software no sigue una evolución lineal.
En un momento dado del tiempo tenemos varias lineas paralelas de trabajo independientes.

--- main (master)
    En esta rama main:
    - Lo que hay en ella se considera apto para producción
    - Nunca bajo pena capital se puede hacer un commit en esta rama

En TODO proyecto de software siempre tendremos una segunda rama paralela a main, que se llamará:
- develop
- dev
- development
- desa
- desarrollo

    Lo que hay en esa rama es lo que se está desarrollando y está ya aceptado como parte de la siguiente versión (release) que se subirá a producción.

Y ahora... Dependiendo del proyecto/empresa podemos ir creando más ramas...
En un proyecto de software más grande, es habitual acabar con 100/200 ramas.
En un proyecto pequeño, a veces no abrimos ni una sola rama más allá de main y develop.
Esto son ya decisiones!
Cuantos más cambios y más gente trabajando en el proyecto, más ramas quiero crear para organizar el trabajo.

Habitualmente en los proyectos de powerplatform trabaja poca gente (1 persona o 2) y no suelen ser proyectos donde se implementen muchos cambios simultaneamente. Por eso muchas veces nos quedamos solo con la rama main y develop, y no abrimos ramas adicionales. Pero esto es una decisión que cada equipo debe tomar en función de sus necesidades.

Cuando creo un proyecto, por ejemplo: 
    - Un flujo en power automate.
Ese flujo, aunque yo no haya escrito código, Power Automate SI LO ESCRIBE... en ficheros.

Cuando tenga algo medio funcional, genero un commit (backup) de ese estado del proyecto en la rama DESA.
Seguiré trabajando... y haciendo cambios... y cuando me interese generaré otro commit (backup) de ese nuevo estado del proyecto en la rama DESA. Y así sucesivamente:

    DESA:
        C1 -> C2 -> C3 -> C4 > C6 > C7
    MAIN:      \     \       ^       \
                C2 -> C3 --- C5 ----> C7
    HOTFIX:            |     ^
                       C3 -> C5

La idea es que en cada commit guarde lo relativo a una nueva funcionalidad que he implementado.

    C1: Flujo que leer emails de Outlook y copia sus adjuntos a una carpeta de OneDrive
        flujo-v1.codigo
    C2: Ese mismo flujo en el cuál guardo en medio del proceso los metadatos de los adjuntos en una tabla de dataverse.
        flujo-v2.codigo
        tabla-dataverse.codigo
    C3: Ese mismo flujo en el que añado una tarea para mandar un email de confirmación al finalizar el proceso.
        flujo-v3.codigo
        tabla-dataverse.codigo
    C4: Nuevos datos que guardo en la tabla de dataverse... En proceso.

La idea es que pueda en un momento dar marcha atrás!

SIEMPRE la rama main va a estar protegida, solamente unas pocas (o 1) personas van a tener permiso para llevar commits a esa rama (por ejemplo, en el caso de LINUX, Linus Torvalds sigue siendo el único ser en el mundo con permiso para hacer esa operación)

Si el proyecto es más grande, la rama desarrollo (develop) también suele estar protegida, y solo un grupo reducido de personas tiene permiso para hacer commits en esa rama. 

Cuando alguien quiero mezclar lo que ha hecho con lo que hay en desarrollo o en main, solicitan una fusión de cambios: MERGE REQUEST o PULL REQUEST. Esto es un acto burocrático. Una persona solicita mediante un formulario que se revise su trabajo y se fusione con la rama de destino. Esa solicitud es revisada por un responsable del proyecto, que puede aprobarla o rechazarla. Si la aprueba, se fusionan los cambios y se genera un nuevo commit en la rama de destino.

En power platform, por la naturaleza de los proyectos que montamos (mucho más simples que otros proyectos de software) no hacemos tantos commits, ni hay tantas personas, ni tenemos tantas ramas... Ni solemos usar pull requests... Trabajamos 2 y confiamos el uno en el otro. Hacemos un uso muy simplificado de GIT.

Esos commits y esas ramas se guardan en un servidor de alojamiento de repositorios remotos.

Github es un servicio de alojamiento de repositorios remotos que ofrece una plataforma para gestionar proyectos de software utilizando Git. De microsoft.

Pero microsoft tiene otro: Azure devops.

Github se usa para proyectos públicos/opensource
En empresas, lo que usamos es Azure DevOps.

Hay muchos otros servicios de alojamiento de remotos de git:
- Gitlab
- Bitbucket (Atlassian)
- AWS CodeCommit
- Google Cloud Source Repositories
- ...

PowerPlatform tiene integración directa con Azure Devops.

Lo que haremos será crear en Azure Devops un repositorio asociado a cada SOLUCION que creamos.

Por supuesto, no tengo por que hacer esto.... pero atente a las consecuencias!
Y el día que venga un problema (según Murphy, ese día vendrá) si no tengo esto... fliparé!

---

Cada vez que llegue un email, saca sus adjuntos y guárdalos en una carpeta de OneDrive.
    Pregunta: Me puede interesar que ese flujo se ejecute en paralelo varias veces? SI
    Me llegan 10 correos a la vez... pues que se ejecute el flujo 10 veces.. una para cada correo. Esto es lo que se llama ejecución concurrente.

    Pregunta2: Tengo un flujo que entra a una BBDD extrae los datos nuevos desde la ultima ejecución, y los mete en un excel que tengo en OneDrive. Me interesa que ese flujo se ejecute en paralelo varias veces? NO

    Mi proceso puede tardar 3 minutos en ejecutarse.
    Y en esos 3 minutos llegan 35 peticiones de ejecución del proceso adicionales.
    No quiero que encolen todas esas peticiones. Y que se ejecuten las 35 veces.
    Quizás no quiero cola de espera... Y marco una cola de 0

---

# Parámetros y variables

VARIABLE?  Una zona en memoria RAM donde ir guardando DATOS que puedo necesitar en el futuro.
           Las variables tienen un NOMBRE que las identifica... y a través de ese nombre puedo posteriormente recuperar el dato que he guardado en esa variable.
           Lo podemos ver como una cajita... donde meto cosas... con una pegatina por fuera, con el nombre de la variable... y luego cuando quiero recuperar lo que he metido dentro de esa cajita, busco la pegatina con el nombre de la variable y abro la cajita para sacar el dato.

           OJO CON ESA DEFINICION DE VARIABLE. En función del lenguaje / programa que use para desarrollar mi aplicación el concepto de variable cambia.
           Este concepto que he explicado no aplica a JAVA ni Python ni JS, ni a R

```py
nombre = "Hola"
numero = 5
```

```java
String nombre = "Hola";
int numero = 5;
```

Todo lenguaje de programación manipula datos. Y Esos datos será de un tipo u otro:
- Textos
- Números
- Fechas
- Valóres lógicos: TRUE/FALSE
- ...

En función del tipo de dato de un dato, podré hacer sobre él unas operaciones u otras.

    numero = 17
    numero2 = 33
    numero * numero2 ? Es posible hacer esta operación? Porque son 2 números y por tanto pueden multiplicarse

    texto="hola"
    texto2="mundo"
    texto * texto2 ? No es posible hacer esta operación. No tiene sentido multiplicar 2 textos. No existe esa operación para ese tipo de datos.



```py
nombre = "Hola"
```

```java
String nombre = "Hola";
```

1º Crear en RAM un dato de tipo STRING con el valor "Hola"... porque en ambos lenguajes, los datos de tipo string se representan entre comillas. Ese dato se crea en algún sitio de la RAM... que no tengo npi de cual es.
La ram es como un cuaderno de cuadricula... Y en algúna cuadricula se ha escrito el dato "Hola". 
2º Crear una variable llamada nombre.
En python, las variables NO TIENE TIPO DE DATO.
En JAVA, las variables SI TIENEN TIPO DE DATO. En este caso, el tipo de dato de la variable nombre es STRING.

    Una variable es como un postit... en el que escribo "nombre"... no escribo "Hola" en el postit... sino que escribo "nombre" en el postit... y luego pego ese postit en la cuadricula del cuaderno donde he escrito "Hola". 
    El postit referencia al dato. El dato no lo guardo en el postit.

    En Java o pythom o JS una variable es una raeferencia a un dato...
    En C, C++, una variable es una cajita donde guardo un dato... y esa cajita tiene un nombre (nombre de la variable) y un tipo de dato (que me dice que tipo de dato puedo guardar en esa cajita)

    En el caso de JAVA, la variable es de tipo string... es como si tengo postits de colores.
    - Los verdes pueden apuntar a textos (los puedo pegar al lado de textos)
    - Los amarillos pueden apuntar a números (los puedo pegar al lado de números)
    - Los azules pueden apuntar a fechas (los puedo pegar al lado de fechas)
    En python todos los postsis son blancos... y los puedo pegar al lado de lo que sea... porque las variables de python no tienen tipo de dato... pueden apuntar a cualquier tipo de dato.

    Python es un lenguaje de tipado dinámico. En ellos, las variables NO TIENE TIPO. Los datos SI TIENEN TIPO.
    Java es un lenguaje de tipado estático.   En ellos, las variables SI TIENEN TIPO. Los datos también tienen tipo.

    En ambos casos:

    ```py
    nombre = "Hola"
    nombre = "adios"
    ```
    Cúantos datos tengo en RAM en este momento? 2
    En la primera creo "Hola" en RAM... y pego el postit "nombre" al lado del "Hola"
    En la segunda línea, creo "adios" en RAM (en otro sitio... en otra página del cuaderno...) y muevo el postit "nombre" para pegarlo al lado de "adios". El dato "Hola" sigue existiendo en RAM.
    Lo que pasa es que si no hay ninguna variable que apunte a él, se convierte en basura (GARBAGE) ... y quizás is o quizás no... (no tengo control) entre el recolector de basura de python o de java a eliminar ese dato de la RAM para liberar espacio... 

    Los programas que hacemos en Power automate NO FUNCIONAN ASI!
    En ellos:
    - Las variables SI TIENEN TIPO, como en JAVA. Por debajo de power automate hay un lenguaje de tipado estático.
    - Las variables NO SON REFERENCIAS A DATOS EN RAM, sino que SON CAJITAS DONDE GUARDO DATOS. Es decir, el concepto de variable que tenemos en C, C++ es el que se aplica en Power Automate.

Estoy asignando la variable "nombre" al valor "Hola".
En py o java, una variable no es una cajita donde pongo cosas...
Una variable es una referencia a un dato que tengo en RAM.


```py
nombre="Ivan"
nombre=2
```

Esto en python cuela.
En java no... y en power automate tampoco... porque las variables tienen tipo de dato... y no puedo asignar un número a una variable que es de tipo texto.

---

Toda CAJA en un flujo (Sea desencadenador, sea acción...) siempre tendrá datos que le lleguen y tendrá datos que salgan.

    Esos datos, en el 90% de los casos viene prefijados por el tipo de acción!

        Leer un archivo de una carpeta de OneDrive.
        Datos de entrada?
           NOMBRE DEL ARCHIVO: String
           CARPETA DEL ARCHIVO: String
           Conector de OneDrive: Objeto Conector

        Datos de salida?
           CONTENIDO DEL ARCHIVO: String
           FECHA DE CREACION DEL ARCHIVO: DateTime
           TAMAÑO DEL ARCHIVO: Number

    Hay casos que no es así... donde yo los defino explicitamente:
        Trigger de ejecución manual:
            Entrada: Definimos PARAMETROS DE ENTRADA!
            Salida:  Los datos que el usuario rellena para esa información que se ha configurado como parametros de entrada + Datos estandar de quién y cuando ejecuta el proceso.
        Inicializar variable:
            Definimos el TIPO DE DATO de la variable... y el NOMBRE de la variable y su VALOR INICIAL.

El juego va a ser conectar DATOS DE SALIDA de una caja con DATOS DE ENTRADA de otra caja.

    Disparador manual:
        Parametros:
            NOMBRE DEL ARCHIVO: String
            CARPETA DEL ARCHIVO: String

    Leer un archivo de una carpeta de OneDrive.
    Datos de entrada?
       NOMBRE DEL ARCHIVO: String <- Disparador manual [ NOMBRE DEL ARCHIVO ]
       CARPETA DEL ARCHIVO: String <- Disparador manual [ CARPETA DEL ARCHIVO ]
       Conector de OneDrive: Objeto Conector



2026-04-14

2000-05-30

yyyy
2026-2000 = 26 años

MMdd   En el caso de extraer mes es MM M Mayúscula.. La m minúscula es para minutos
0414
0530

Mirar si uno es mayor que otro (orden alfabetico)
 "0414" >= "0530" -> Significa que ha cumplido años ya
 "0414" <  "0530" -> Significa que no ha cumplido años aún (Y en este caso, resto 1 año a la diferencia de años para calcular la edad)


sub(

    sub(                                                     
        int(formatDateTime(body('Hora_actual'),'yyyy')),     
        int(formatDateTime(triggerBody()?['date'],'yyyy'))   
    )
    ,
    if (
        less(                                                
            int(formatDateTime(body('Hora_actual'),'MMdd')),  
            int(formatDateTime(triggerBody()?['date'],'MMdd'))
        ),
        1,
        0
    )
)