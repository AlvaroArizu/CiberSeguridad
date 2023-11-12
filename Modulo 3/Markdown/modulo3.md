# Modulo 3
## Objetivos
- Seguridad informatica y defensa en profundidad
- Privilegios de usuarios en windows
- User Account control
- Backup en windows 

# Seguridad informatica y defensa en profundidad
### Dato versus información
En Informática, los conceptos de "dato" y "información" son distintos aunque relacionados. Un dato es una entidad cuantificable, como un número o letra, que carece de análisis por sí mismo. En cambio, la información se forma al procesar datos, creando un conjunto revelador que contribuye a la toma de decisiones, generación de hipótesis o resolución de problemas. En resumen, la información, derivada del procesamiento de datos, proporciona un mayor conocimiento sobre un tema específico.
### Cual es la diferencia?
- Los datos suelen ser individuales, concretos y específicos, mientras que la información está integrada por un conjunto de datos distintos o no, y agrupados en gran extensión para poder producir análisis.

- La información tiene por objeto comunicar algo, mientras que el dato no muestra mensaje alguno, es decir, por sí solo y de manera aislada no produce un mensaje coherente.


### ¿Qué es la Seguridad Informática?
La Seguridad Informática es la disciplina que se encarga de proteger la confidencialidad, integridad y disponibilidad de la información dentro un sistema informático.

### ¿Por qué proteger la información?
La protección de la información es crucial en la actualidad debido a su valor en diversos contextos. En entornos organizacionales, la información es vital para la toma de decisiones y puede representar un activo fundamental, como en el caso de secretos industriales. Además, la información es esencial para las operaciones diarias, incluso si no es propiedad directa de las empresas, ya que puede pertenecer a clientes o usuarios. Por esta razón, la protección de la información ha ganado mayor relevancia en los últimos años.

## Defensa en profundidad
La defensa en profundidad, concebida por la NSA, busca proteger un activo mediante la implementación de múltiples capas de seguridad. Originada como estrategia militar para retrasar el avance del enemigo, ahora se aplica en seguridad informática y electrónica. Se basa en el paradigma de Proteger, Detectar y Reaccionar, requiriendo medidas equilibradas en Personas, Tecnología y Operaciones. Esto implica incorporar mecanismos de protección, prepararse para ataques, implementar métodos de detección y procedimientos para reaccionar y recuperarse eficientemente.

### Personas
Lograr una seguridad óptima requiere compromiso de la alta gerencia, entendimiento de amenazas, políticas claras, asignación de roles y recursos, capacitación del personal y medidas de seguridad física y control de acceso en instalaciones críticas.
### Tecnología
Para asegurar que las tecnologías implementadas son las correctas, deben ser establecidas políticas y procedimientos para la adquisición de la tecnología. Debemos implementar varios mecanismos de seguridad entre las amenazas y sus objetivos. Cada una debe incluir mecanismos de protección y detección.
### Operaciones
Se enfoca en las actividades necesarias para sostener la seguridad de la organización en las tareas del día a día. Este tipo de medidas incluye las que enumeramos a continuación: mantener una clara política de seguridad, documentar todos los cambios hechos en la infraestructura, realizar análisis de seguridad periódicos e implementar métodos de recuperación.

# Privilegios de usuario en windows
En Windows, los privilegios de usuarios se gestionan mediante grupos. Los grupos, también conocidos como grupos de seguridad, son colecciones de cuentas con derechos de seguridad comunes. Las cuentas pueden pertenecer a más de un grupo, como usuarios estándar o administradores. Se pueden crear grupos personalizados con derechos específicos si se tiene una cuenta de administrador

En Windows 7, y con una cuenta con permisos de administrador, se podría acceder a
la consola de gestión de grupos de usuarios,
al hacer clic con el botón derecho del mouse sobre el ícono de Mi PC / Computer, luego
clic en Administrar / Manage y por último en Grupos / Groups dentro de Usuarios Locales y Grupos / Local Users and Groups.

## Grupos por defecto
Una instalación tradicional de Windows 7 incluye varios grupos de usuarios locales.

En las siguientes pantallas, detallamos los más utilizados:
- Administradores
- Usuarios

### Administradores
El grupo Administradores en Windows tiene control total sobre el equipo, con la capacidad de asignar derechos y permisos. La cuenta llamada Administrador es automáticamente miembro de este grupo. Al unirse a un dominio, se agrega automáticamente el grupo Administradores de dominio, por lo que se debe tener precaución al agregar usuarios debido al control total que posee este grupo.

**Permisos más importantes:**
- Tener acceso a este equipo desde la red.
- Ajustar las cuotas de la memoria para un proceso.
- Permitir el inicio de sesión mediante los Servicios de Escritorio remoto.
- Hacer copias de seguridad de archivos y directorios.
- Cambiar la hora y zona horaria del sistema.
- Depurar programas.
- Suplantar a un cliente tras la autenticación.
- Cargar y descargar controladores de dispositivo.
- Administrar registro de seguridad y auditoría.
- Tomar posesión de archivos y otros objetos.

### Usuarios
El grupo Usuarios permite tareas comunes como ejecutar aplicaciones, usar impresoras y bloquear el equipo. No pueden compartir directorios ni crear impresoras locales. Grupos como Usuarios de dominio, Usuarios autenticados e Interactivo son miembros por defecto.

**Permisos importantes:**
- Acceso remoto al equipo.
- Inicio de sesión local.
- Cambiar la zona horaria.
- Aumentar el espacio de trabajo de un proceso.
- Apagar el sistema.

# User Account Control
## UAC (User Account Control)
UAC (User Account Control) en Windows Vista y superior minimiza los privilegios de administración, reduciendo llamadas al help desk y mitigando riesgos de virus/malware.

### Funcionamiento UAC:

Durante el logon, se genera un token de acceso. Si se detectan privilegios elevados, se divide en un token estándar y otro elevado (Protected Admin). Usuarios con privilegios de administración actúan como estándar por defecto, requiriendo aviso y credenciales para privilegios elevados.

**Condiciones para el Split del Token:**
- El usuario es miembro de grupos administrativos como Domain Admins, Domain Controllers, Power Users, Print Operators, etc.
- El usuario posee privilegios elevados como Create a token object, Act as part of the operating system, Debug Programs, Impersonate a client after authentication, etc.
  
![](../Pic/Sin%20título.png)

**Comportamiento UAC para Usuarios Estándar:**
- Si un usuario estándar ejecuta una aplicación que requiere privilegios de administrador, se solicitarán las credenciales de administrador para completar la operación.
- No se produce el split del token para usuarios estándar, ya que no tienen los SIDs o privilegios necesarios.
- Los administradores built-in (administrador del equipo y administrador del dominio) tampoco experimentan el split del token, ya que no están protegidos por UAC.

**Cuatro Tipos de Notificaciones UAC:**
1. Cuadro de diálogo de permisos o contraseña necesario.
2. Cuadro de diálogo de configuración del programa.
3. Cuadro de diálogo de configuración del sistema.
4. Cuadro de diálogo de configuración de Windows.

![](../Pic/Sin%20título1.png)

**Configuración de UAC:**

Para abrir la Configuración del Control de cuentas de usuario:
1. Haz clic en el botón Inicio.
2. Luego, haz clic en Panel de control.
3. En el cuadro de búsqueda, escribe "uac".
4. Haz clic en "Cambiar configuración de Control de cuentas de usuario".

A continuación, se describe la configuración de UAC y su posible impacto en la seguridad del equipo.

![](../Pic/Sin%20título2.png)

**Notificarme siempre:**

Esta configuración es la más segura. Recibirás notificaciones antes de que los programas realicen cambios en el equipo o la configuración de Windows, que requieran permisos de administrador. Cuando se te notifique, el escritorio aparecerá atenuado y deberás aprobar o denegar la solicitud en el cuadro de diálogo de UAC antes de realizar cualquier acción en el equipo.

Esta opción es una buena medida de precaución que te ayudará a proteger tu PC contra posibles ataques

**Por cambios en el equipo:**

- Se te notificará antes de que los programas realicen cambios en el equipo que requieran permisos de administrador.
- No recibirás notificaciones si intentas hacer cambios en la configuración de Windows que requieran permisos de administrador.
- Se te notificará si un programa fuera de Windows intenta realizar cambios en la configuración de Windows.

Por lo general, es seguro permitir cambios en la configuración de Windows sin notificación. Sin embargo, debes tener precaución al permitir programas que pueden ejecutarse en el equipo, ya que ciertos programas malintencionados pueden aprovecharse de esto para instalar archivos o cambiar la configuración del equipo.

**Por cambios en el equipo (sin atenuar escritorio):**

- Se te notificará antes de que los programas realicen cambios en el equipo que requieran permisos de administrador.
- No se te notificará si intentas realizar cambios en la configuración de Windows que requieran permisos de administrador.
- Se te notificará si un programa fuera de Windows intenta realizar cambios en la configuración de Windows.

Debido a que el cuadro de diálogo de UAC no se encuentra en el escritorio seguro con esta configuración, es posible que otros programas interfieran con el aspecto visual del diálogo. Esto supone un pequeño riesgo para la seguridad si ya tienes un programa malintencionado ejecutándose en el equipo.

**Nunca:**

- No se te notificará antes de que se realicen cambios en el equipo. Si has iniciado sesión como administrador, los programas pueden hacer cambios en el equipo sin que lo sepas.
- Si has iniciado sesión como usuario estándar, se denegarán automáticamente los cambios que requieran permisos de administrador.
- En esta opción, UAC queda desactivado y no protege el equipo, lo que puede suponer un riesgo importante para la seguridad.
