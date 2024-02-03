# Modulo 4
### Objetivos
- Directiva de Seguridad Local.
- AppLocker
- Introducción al Malware
- Softwareantivirus

### PDF del Modulo 3
- App locker
- Malware
- Local security
- Proteccion contra Malware
- Software antivirus

## Local Security Policy 
### Directiva de seguridad local
La `directiva de seguridad local` permite definir aspectos del sistema relacionados con la seguridad, exclusivamente a nivel local. A diferencia de las directivas de grupo en Active Directory, esta es únicamente local y no se aplica a través de la red.

Para abrir la herramienta de administración de la directiva de seguridad local, puedes ejecutar el siguiente comando:

```md
secpol.msc
```



## Account Policies
Permite definir parámetros acerca de las cuentas de usuario local.

### Password Policy
- `Enforce Password History`: Define historial de contraseñas para evitar repeticiones.
- `Maximum Password Age`: Establece el tiempo máximo de vida de una contraseña.
- `Minimum Password Length`: Indica la longitud mínima de una contraseña.
- `Password Must Meet Complexity Requirements`: Requiere complejidad en contraseñas.

### Account Lockout Policy
- `Account Lockout Threshold:` Número de intentos fallidos para bloquear la cuenta.
- `Account Lockout Duration`: Tiempo para desbloqueo automático.

# Local Policies

## User Rights Assignment
- **Act as part of the operating system:** Permite ejecutar procesos en nombre de cualquier usuario sin autenticación.
- **Allow logon through Remote Desktop Services:** Permite acceso a través de RDP.
- **Load and unload device drivers:** Permite cargar y descargar controladores.
- **Take ownership of files or other objects:** Permite modificar la propiedad de archivos y objetos.

## Security Options
- **Accounts: Administrator account status:** Habilita/deshabilita la cuenta de administrador local.
- **Accounts: Guest account status:** Habilita/deshabilita la cuenta de invitado.
- **Interactive Logon: Display user information when the session is locked:** Define si se muestran datos del usuario al bloquear la sesión.
- **Interactive Logon: Do not display last user name:** Define si se muestra la última cuenta que accedió al sistema.
- **Interactive Logon: Do not require CTRL+ALT+DEL:** Define si se requiere CTRL+ALT+DEL para iniciar sesión.
- **Network Security: Do not store LAN Manager Hash value on next password change:** Evita almacenar el hash LM al cambiar la contraseña.
- **Network Access: Do not allow anonymous enumeration of SAM accounts:** Evita enumeración anónima de cuentas SAM.

# AppLocker

AppLocker es una característica disponible en las versiones Enterprise y Ultimate de Windows 7. Las directivas de AppLocker son similares a las de restricción de software, aunque AppLocker posee varias ventajas, puede ser aplicado a usuario, cuentas de grupo y la capacidad de aplicar a todas las versiones de un producto.

AppLocker se basa en un servicio denominado Identidad de la aplicación y el tipo de inicio de este servicio está configurado como Manual. Al probar AppLocker, se recomienda mantener el tipo de inicio como Manual. Si se configura una regla de forma incorrecta puedes reiniciar el equipo y la regla de AppLocker dejará de estar en vigor. Sólo cuando estemos seguros de que las directivas se aplican correctamente debemos configurar el inicio Tipo de Servicio de Identidad de la aplicación en Automático. La configuración incorrecta de AppLocker puede bloquear un equipo de forma inutilizable.

## Reglas predeterminadas
Existen reglas que se deben crear de forma automática y que permiten el acceso por defecto de Windows y archivos de programa. Son necesarias porque AppLocker limita la ejecución de cualquier aplicación que no esté en una regla de permiso. Esto significa que cuando se habilita AppLocker, no se puede ejecutar ninguna aplicación, script o instalador que no figure en una regla Permitir.

## Reglas de Bloqueo
Es necesario añadir una regla de bloqueo sólo si otra regla de AppLocker permite una aplicación, podemos utilizar explícitamente reglas definidas de bloqueo para impedir la ejecución de aplicaciones que son activadas a través de las reglas predeterminadas.

## Reglas ejecutables
Aplicadas a los archivos Exe y Com, por defecto son reglas de ruta que permiten a todos ejecutar todas las aplicaciones en la carpeta Archivos de programa y la carpeta de Windows. Las reglas predeterminadas también permiten a los administradores ejecutar aplicaciones en cualquier lugar en el equipo. Es necesario utilizar las reglas por defecto, ya que Windows no funcionará correctamente a menos que ciertas aplicaciones, cubiertas por estas reglas, tengan autorización para ejecutar.

## Reglas de instalación
Por defecto, permite a todos utilizar archivos firmados por Windows Installer en la carpeta % SystemDrive% \Windows y los miembros del grupo de administradores local para ejecutar cualquier archivo msi o msp. Las reglas predeterminadas permiten la instalación y actualización de software a través de Directivas de grupo. Es importante recordar que incluso si una regla de AppLocker permite a todos acceder a un archivo de instalación en particular, todavía necesitan los permisos administrativos pertinentes para instalar software en el ordenador.

## Reglas de comandos
Incluye los archivos bat, cmd, vbs y extensiones js. Aunque es posible el uso de reglas de publicador con secuencias de comandos, la mayoría de scripts se crean sobre una base ad-hoc por administradores y rara vez son firmados digitalmente. Podemos utilizar las reglas de hash con los scripts que son rara vez modificados y reglas de ruta con directorios que contienen secuencias de comandos que se actualizan periódicamente.

## Reglas DLL
Bibliotecas, archivos DLL y extensiones ocx, estas reglas no están habilitadas de forma predeterminada en AppLocker, es necesario crear una regla para cada DLL utilizada por las aplicaciones, aunque la creación de reglas es fácil generando reglas automáticamente.

## Reglas de publicador
A diferencia de una regla de certificados de restricción de software, no es necesario obtener un certificado para utilizar una regla editor porque los detalles de la firma digital son extraídos del archivo de aplicación de referencia. Si un archivo no tiene firma digital, no se puede restringir ni permitir mediante reglas de AppLocker editor. Permiten más flexibilidad que las reglas hash porque se puede especificar no sólo una versión específica de un archivo, también todas las versiones futuras de ese archivo.

## Reglas hash
Permiten identificar un archivo binario específico que no está firmado digitalmente, podemos utilizar la identificación por hash. Podemos utilizar el asistente de creación de reglas para automatizar la creación de hash de archivo para todos los archivos en una ubicación específica.

## Reglas de ruta
Las reglas de ruta permiten definir rutas en las cuales se van a poder ejecutar programas (tanto para un archivo específico como para todo un directorio). Debemos tener en consideración que los usuarios con permisos de modificación sobre los archivos y/o directorios, pueden afectar el comportamiento de la política. Por ejemplo, reemplazando un archivo que tiene permisos para ser ejecutado, por otro archivo totalmente diferente.

## Configurar excepciones
Permiten a aplicaciones específicas estar exentas de reglas más generales. Se puede utilizar cualquier método para especificar una excepción, y el método que elija no dependerá del tipo de regla que se está creando. Podemos crear excepciones para las reglas de bloqueo, así como reglas de permiso.

## Auditoría
Esto permite comprobar qué aplicaciones son afectadas por AppLocker sin llegar a bloquear la ejecución. Se puede configurar AppLocker para auditar normas en lugar de hacerlas cumplir. Los eventos de auditoría de AppLocker se encuentran en Visor de Eventos \aplicaciones y servicios \Microsoft \Windows. Los eventos contienen la siguiente información:
- El nombre de la regla.
- El SID del usuario atacado o grupo.
- Archivo afectado por qué regla y trayectoria.
- Si el archivo está bloqueado o permitido.
- El tipo de regla (hash editor, ruta de acceso o archivo).

# Introducción a Malware

## Definición
Malware son programas que se infiltran sin consentimiento para robar información o causar daño.

## Historia
- 1972: Creeper, el primer virus, infecta máquinas ARPANET.
- 1984: Frederick B. Cohen acuña el término "virus informático".
- 2000: Aparición de gusanos masivos como I Love You.
- Actualidad: Windows y Android son las plataformas más atacadas.

## Clasificación
Subtipos de malware incluyen Adware, Backdoor, Gusano, Keylogger, Rogue, Rootkit, Stealer, Spyware, Troyano, Ransomware, y Virus.

## Descripción de Subtipos
- **Adware:** muestra publicidad excesiva.
- **Backdoor:** crea una puerta trasera para acceso.
- **Gusano:** se duplica y se propaga a través de medios electrónicos.
- **Keylogger:** graba las teclas pulsadas.
- **Rogue:** simula ser una solución anti-malware.
- **Rootkit:** oculta a otros malware y a sí mismo.
- **Stealer:** captura contraseñas almacenadas y escritas.
- **Spyware:** recopila información sobre la actividad del usuario.
- **Troyano:** se infiltra aparentando ser inofensivo, da control remoto.
- **Ransomware:** restringe acceso y pide rescate.
- **Virus:** causa daño y se reproduce.

# Protección contra el Malware

## Capacitación de Usuarios
Si bien existen diversas soluciones de seguridad, la capacitación de usuarios es la primera medida esencial. Conocer las amenazas potenciales es clave.

## Camuflaje de Malware
- **Joiners (Binders):** Herramientas que unen malware con archivos benignos.
- **Extensiones de Archivo:** Modificar la configuración para ver extensiones reales.
- **Formatos de Archivo:** Malware no se limita a .exe, también en formatos como .jar, .py, .pl.

## Métodos de Distribución
- **Correo Electrónico:** Evitar Spam y descargas no solicitadas.
- **Mensajería Instantánea:** Confirmar enlaces enviados.
- **Redes P2P:** Precaución al descargar archivos.
- **Sitios web de Descarga:** Analizar archivos antes de ejecutarlos.

## Detectar Infecciones
### Procesos
- Revisar procesos en el Administrador de Tareas.
- Conocer procesos del sistema y de aplicaciones instaladas.
- Buscar información adicional sobre procesos desconocidos.

### Conexiones
- Usar `netstat -a` para ver conexiones y puertos.
- Usar `netstat -b` para identificar ejecutables asociados a conexiones.
- Cerrar aplicaciones antes de ejecutar para obtener resultados más precisos.

### Auto-Arranque
- Utilizar la herramienta "autoruns" de Sysinternals para verificar técnicas de auto arranque.

## Síntomas de Infección
- Disminución de rendimiento.
- Desaparición de archivos o menús.
- Funciones deshabilitadas.
- Nuevos archivos con nombres extraños.
- Cuelgues y/o pantallazos azules (BSOD).

Recuerda siempre analizar minuciosamente cualquier comportamiento sospechoso y tomar medidas preventivas.

# Protección contra el malware

## Introducción
En el ámbito de la seguridad informática, la protección contra el malware es esencial. Aunque existen diversas soluciones de seguridad, la primera línea de defensa debería ser la capacitación de los usuarios para que estén alerta a posibles amenazas. Este resumen aborda varios aspectos clave para protegerse contra el malware.

## Joining (Unión de Archivos)
El malware a menudo se camufla uniéndose a archivos benignos mediante herramientas llamadas joiners o binders. Estas herramientas crean un ejecutable que contiene tanto el malware como el archivo benigno. Es esencial estar atento a extensiones de archivo sospechosas, ya que los atacantes pueden ocultar ejecutables maliciosos con iconos relacionados con el archivo benigno.

## Extensiones de Archivo
Configurar Windows para mostrar las extensiones de archivo ayuda a identificar posibles amenazas. Ocultar las extensiones es una práctica de seguridad desfavorable. La detección de extensiones inusuales, como un archivo que parece una imagen pero tiene extensión .exe, es una señal de posible malware.

## Formatos de Archivo
Aunque los archivos .exe son comunes, otros formatos como .jar (Java), .py (Python), y .pl (Perl) también pueden contener malware. Conocer los formatos utilizados por el malware es crucial para una defensa efectiva.

## Métodos de Distribución
El malware se propaga a través de diversos medios, incluyendo correo electrónico, mensajería instantánea, redes P2P y sitios de descargas. Evitar descargar archivos no solicitados y verificar la autenticidad de los enlaces son prácticas fundamentales para prevenir infecciones.

## Detectar Infecciones
Los comportamientos extraños en un sistema, como disminución de rendimiento o desaparición de archivos, pueden indicar infecciones. Revisar los procesos en el administrador de tareas, analizar conexiones activas y verificar el autoarranque son métodos para detectar posibles amenazas.

# Software Antivirus

## Introducción
Un antivirus es esencial para detectar y eliminar códigos maliciosos. Va más allá de los virus y aborda gusanos, troyanos, rootkits y spyware. La detección y eliminación de amenazas son funciones cruciales de un antivirus.

## Detección Reactiva: Base de Firmas
Los antivirus tradicionales utilizan firmas o vacunas para detectar malware. Este método compara archivos con una base de datos de firmas conocidas. La actualización regular de la base de datos es crucial, pero este enfoque tiene limitaciones, ya que solo puede detectar amenazas conocidas.

## Detección Proactiva: Heurística
La detección heurística es proactiva y se basa en algoritmos que analizan el comportamiento de archivos en busca de posibles amenazas. A diferencia de la detección basada en firmas, la heurística puede identificar amenazas desconocidas. Ambos métodos se complementan para una protección integral.

## Tipos de Heurística
La heurística puede ser genérica, pasiva o activa. La heurística genérica compara similitudes con amenazas conocidas, la pasiva evalúa acciones sospechosas, y la activa ejecuta el código en un entorno seguro para observar su comportamiento.

## VirusTotal
VirusTotal es un servicio web que utiliza múltiples motores antivirus para analizar archivos o URLs. Proporciona informes detallados sobre la detección de amenazas y es una herramienta valiosa para verificar la seguridad de archivos y enlaces.

# Desinfección
En caso de infección, la desconexión del sistema de internet es el primer paso. La desinfección manual implica la identificación y eliminación del malware, mientras que las herramientas antivirus y CD de arranque externos también pueden utilizarse para un análisis más profundo y desinfección automatizada.

Este resumen proporciona una visión general de las medidas de protección y los métodos de detección y desinfección contra el malware, brindando una guía práctica para fortalecer la seguridad informática.


































