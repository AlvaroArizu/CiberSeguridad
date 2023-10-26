# Modulo 2
- Mecanismos de autenticación.
- Hardening.
- Gestion de vulnerabilidades.
## Mecanismos de autenticación
La autenticación es el proceso de verificar que algo o alguien es quien dice ser

Metodos de autenticacion 
1. Algo que el usuario sabe: contraseñas, PIN, patrón, etc.
2. Algo que el usuario tiene: tarjeta de coordenadas, códigos de Token, USB keys.
3. Algo que el usuario es: reconocimiento facial, dactilar, de iris, de voz, etc.

### Contraseñas
Una de las principales dificultades para las personas que utilizan tecnología es la gestión de numerosas cuentas de usuario. Esto incluye redes sociales, correos electrónicos, servicios bancarios en línea, almacenamiento en la nube y más, lo que puede resultar en más de 15 cuentas para administrar. La gestión se complica aún más debido a los requisitos de seguridad que exigen contraseñas complejas y cambios frecuentes. Esto puede llevar a prácticas inseguras:
- Como el uso de la misma contraseña en varios lugares. 
- Almacenar contraseñas en lugares accesibles.
- Tener dificultades para recordarlas.

Además de los problemas generados por los usuarios, las empresas que ofrecen servicios también contribuyen a los desafíos de seguridad. Almacenan los datos de usuario y contraseña en bases de datos, y si no se protegen adecuadamente, existe un alto riesgo de que los datos sean vulnerables y se puedan robar. Incidentes de seguridad como filtraciones de datos son bastante comunes. Por ejemplo, la filtración masiva "Collection #1" expuso más de 700 millones de cuentas y sus contraseñas en Internet. Es esencial ser consciente de la importancia de proteger nuestras contraseñas en un entorno tan hostil como Internet.

### Filtraciones de datos
Para verificar si hemos sido víctimas de una filtración de datos y si nuestras credenciales personales están expuestas en línea, podemos utilizar el sitio web haveibeenpwned.com. Después de ingresar nuestro correo electrónico en la página y hacer clic en el botón "pwned?", el resultado indicará si nuestros datos han sido filtrados en la web. Si aparece en rojo, significa que se han filtrado nuestros datos, y podemos verificar en qué plataforma o servicio ocurrió y cuándo. En este caso, es crucial cambiar las contraseñas de ese correo y de todos los servicios relacionados. Si el resultado es verde, significa que no hemos sido víctimas de una filtración de datos en ese momento, pero es recomendable verificar regularmente para mantener la seguridad de nuestras cuentas de correo.


  
### Complejidad de las contraseñas
Tener en cuenta la robustez de las contraseñas es esencial para garantizar la seguridad de nuestras cuentas. Es necesario crear contraseñas que sean complejas y difíciles de adivinar, lo que ayuda a protegerlas contra ataques de fuerza bruta o diccionario. Cuanto más complejas sean las contraseñas, más difícil será para un atacante obtenerlas, lo que garantiza la seguridad de nuestras cuentas de usuario. La robustez de las contraseñas es un factor crítico en la seguridad en línea.

`Para que una clave sea compleja, tener en cuenta estas características:`
- `Tener más de 10 caracteres.`
- `Utilizar letras, números y caracteres especiales.`
- `Utilizar mayúsculas y minúsculas.`
- `No utilizar datos personales, tales como nombres, fechas, etc.`

Crear contraseñas complejas es importante. Puedes hacerlo usando frases, como "Me gusta Soda Stereo", que incluyen mayúsculas, minúsculas, caracteres especiales y son fáciles de recordar. Verifica la complejidad con herramientas como `Password Kaspersky`, pero nunca uses datos reales.

### Gestores de contraseñas locales y de nube
Para gestionar múltiples contraseñas, se recomienda el uso de Gestores de Contraseñas, como `Keepass o LastPass`. Estos programas almacenan contraseñas de forma segura en una base de datos cifrada, garantizando la confidencialidad. Esto evita que los usuarios tengan que recordar o anotar sus contraseñas en papel.

### ¿Cómo funcionan?
El programa solicita la creación de una contrase- ña “Maestra” la cual tendrá que ser muy robusta porque será la única que tendremos que utilizar para acceder a la base donde tenemos almace- nadas el resto. Entonces, al ingresar esta contra- seña, podemos usar las que están allí guardadas.

La base de datos podemos guardarla en nuestro dispositivo, tenerla en la nube, o en algún soporte como discos externos o pendrives y llevarlo al lugar donde lo necesitemos.

Este programa posee una versión portable, lo cual permitiría que abramos la base desde cualquier computadora sin la necesidad de instalar el software. Para los usuarios será de gran utilidad ya que podrán almacenar allí todas sus contraseñas con una alta seguridad.

Los usuarios de Windows pueden usar Keepass, KeepassXC que también funciona en sistemas Linux y MAC (https://keepassxc.org/)

### estor de contraseñas en la nube: Bitwarden
Bitwarden es una alternativa gratuita, de código abierto y multiplataforma para gestionar contraseñas. A diferencia de los gestores locales, no genera una base de datos en el equipo; en su lugar, almacena los datos en la nube de Bitwarden, lo que permite el acceso desde cualquier dispositivo a través de una aplicación móvil o navegador web. El usuario solo necesita recordar la contraseña maestra para iniciar sesión. Esta opción es práctica y elimina la necesidad de hacer respaldos manuales de contraseñas en soportes externos.

### Autenticación de Dos Factores (2FA)
El uso de contraseñas robustas y gestores de contraseñas mejora la seguridad, pero aún existe el riesgo de que los ciberdelincuentes roben contraseñas. La Autenticación de Dos Factores (2FA) es una medida adicional de seguridad que requiere un código de token, enviado al propietario de la cuenta a través de una aplicación móvil, además de usuario y contraseña, para iniciar sesión y proteger los datos personales.

xisten muchas aplicaciones de 2FA en el mercado, entre las mejores podemos mencionar:
- Authy
- Google Authenticator
- Latch
- Microsoft Authenticator

En caso de utilizar un 2FA, es recomendable hacerlo a través de alguna de las aplicaciones mencionadas y evitar, en la medida de lo posible, los códigos de token enviados por medio del SMS, ya que este es un canal de comunicación que no cifra los datos y podrían quedar expuestos a un tercero que los podría leer.

## Hardening (Asegurar las tecnologías)
Muchas tecnologías se centran en la facilidad de uso para llegar a más usuarios, pero a menudo, la seguridad se pasa por alto, ya que agregar medidas de seguridad puede complicar la usabilidad. En consecuencia, es importante encontrar un equilibrio entre la funcionalidad y la seguridad en el diseño de tecnología.

Ejemplo 1:

- Cuando una persona compra un celular, éste no lo obliga a utilizar un mecanismo de autenticación para acceder. Es el usuario quien debe, a elección, configurar un patrón, una contraseña, un pin o algún dato biométrico. Como se ve, se pone por delante la funcionalidad a la seguridad.

Ejemplo 2:
- WhatsApp: es una aplicación de mensajería muy funcional y popular a nivel mundial, pero tuvo problemas de seguridad en el pasado debido a la falta de cifrado en los mensajes. Esto se solucionó con la implementación del cifrado punto a punto.

Ejemplo 3:
- Homebanking - Seguridad : Los sistemas bancarios priorizan la seguridad sobre la funcionalidad, implementando medidas como el cambio de contraseña periódico, la prohibición de usar contraseñas anteriores, bloqueo del usuario después de varios intentos fallidos y la introducción del segundo factor de autenticación (2FA). Aunque estas medidas pueden resultar incómodas para los usuarios, son necesarias para prevenir problemas y delitos informáticos.

Por suerte hoy se está buscando mezclar ambos mundos para crear tecnologías funcionales y seguras, lo que convierte en un escenario mucho más favorable para los usuarios al contar con sistemas o dispositivos que integran lo mejor de los dos mundos y no uno solo.

`Al proceso de asegurar una tecnología se le denomina Hardening.`

### El proceso de Hardening
El proceso de hardening es crucial para asegurar que un dispositivo o software esté configurado de manera segura, protegiéndolo contra cambios no deseados o posibles ataques. Para determinar los cambios necesarios en la configuración, se pueden utilizar guías proporcionadas por el fabricante, organismos de seguridad reconocidos o expertos en seguridad. Estas guías ofrecen pautas sobre las configuraciones más seguras, pero es importante equilibrar la seguridad con la funcionalidad, ya que configuraciones demasiado seguras pueden complicar el uso de un dispositivo o software.

### Guias que podemos utilizar 
Para llevar a cabo el proceso de hardening y asegurar dispositivos o software, se pueden utilizar guías proporcionadas por el Center of Internet Security (CIS) y el organismo español CCN CERT. El CIS ofrece guías de hardening llamadas CIS Benchmarks en inglés, que cubren una variedad de sistemas y dispositivos. El CCN CERT proporciona guías en español para una amplia gama de plataformas y productos. Estas guías contienen buenas prácticas y herramientas para mejorar la seguridad.

### Consideraciones al momento de llevar a cabo un Hardening
Al llevar a cabo el proceso de hardening, es fundamental realizar los cambios de configuración en un entorno de pruebas antes de aplicarlos en el ambiente de producción. Esta precaución es necesaria para verificar cómo responden los dispositivos o el software a los cambios. No se deben aplicar directamente en producción, ya que podrían afectar el funcionamiento y causar problemas. Del mismo modo en que se prueban las actualizaciones de parches antes de implementarlas, estos cambios de configuración de seguridad deben someterse a pruebas iniciales. Si no se detectan conflictos ni problemas en las pruebas, entonces pueden implementarse en el ambiente de producción.

## Gestión de vulnerabilidades
Una vulnerabilidad es una debilidad en un sistema que pone en riesgo la seguridad de la información, permitiendo a los atacantes comprometer su integridad, disponibilidad o confidencialidad. Las tecnologías son propensas a fallas, y los investigadores de seguridad regularmente identifican y reportan vulnerabilidades para su corrección. Por lo tanto, es esencial conocer el hardware y software utilizados y estar al tanto de las nuevas fallas de seguridad. Mantener los sistemas operativos y aplicaciones actualizados es una parte crucial de una estrategia de seguridad, lo que implica contar con las últimas versiones instaladas en todo momento.

### Actualización del sistema o aplicación
Mantener los sistemas y aplicaciones actualizados es esencial para corregir errores y vulnerabilidades. La actualización debe ser una actividad cíclica que se lleva a cabo regularmente. Se recomienda realizar el control de versiones y actualizar al menos una vez al mes.

Las actualizaciones son importantes tanto en dispositivos móviles como en computadoras. Los sistemas operativos y las aplicaciones suelen verificar en línea si hay actualizaciones disponibles y las descargan automáticamente. Sin embargo, si todos los dispositivos de una red realizan esta tarea al mismo tiempo, puede causar problemas de congestión en la red.

Para solucionar este problema, se suele designar a un equipo de la red para que descargue las actualizaciones y luego se implementen en un horario que no afecte a los usuarios. Esto mejora el rendimiento de la red y garantiza que las actualizaciones se realicen de manera eficiente.

### Escáneres de vulnerabilidades
Los escáneres de vulnerabilidades son herramientas útiles para identificar posibles fallos o vulnerabilidades en los sistemas de una red. Algunos programas populares en esta categoría incluyen Nessus, GFI Languard, Rapid7 y OpenVAS.

- Nessus es una herramienta de escaneo de vulnerabilidades que verifica diversos sistemas operativos en busca de posibles fallos. Ofrece una versión de prueba con un límite de 16 direcciones IP y una versión paga más completa. Nessus puede comprobar desde puertos abiertos hasta exploits que podrían usarse para atacar sistemas vulnerables. Proporciona resultados detallados y exportables, aunque su interfaz puede resultar algo compleja.
  - https://es-la.tenable.com/products/nessus

- GFI Languard es otra herramienta de escaneo de vulnerabilidades, especialmente utilizada en entornos Microsoft. Al igual que Nessus, automatiza la identificación de vulnerabilidades, pero la corrección de estas vulnerabilidades requerirá tiempo y esfuerzo, generalmente realizado por el equipo de IT o Seguridad Informática de una organización. Estos programas son esenciales para ayudar a prevenir ataques cibernéticos al descubrir y remediar vulnerabilidades antes de que los atacantes puedan explotarlas.
  - https://www.gfi.com/es

Ambas herramientas son fundamentales para mantener la seguridad de una red y requerirán un enfoque y recursos dedicados para implementar las correcciones una vez que se detecten las vulnerabilidades.

### Escáneres de vulnerabilidades para uso personal
Existen programas que permiten identificar vulnerabilidades en sistemas operativos y aplicaciones. Algunas de las opciones incluyen:

- MSBA 2.3: Un programa descontinuado creado por Microsoft para identificar errores y malas configuraciones de seguridad en productos de Microsoft, como servidores, bases de datos y estaciones de trabajo. Este programa es gratuito y útil para auditorías, pero ya no cuenta con soporte oficial de Microsoft.
  - https://www.techspot.com/downloads/3886-microsoft-baseline-security-analyzer.html

- Sumo Updater: Este software gratuito, desarrollado por KC Software, permite identificar aplicaciones desactualizadas en los equipos y proporciona enlaces directos para actualizarlas. Es una forma efectiva de mantener actualizados tanto el sistema operativo como las aplicaciones instaladas en los equipos.
  - https://kcsoftwares.com/?sumo

Estos programas ayudan a garantizar la seguridad al identificar y corregir vulnerabilidades en sistemas operativos y aplicaciones, lo que es esencial para prevenir ataques cibernéticos.

### Ambientes de prueba
Es clave tener en cuenta probar todo cambio o implementación nueva que queramos incluir en el ambiente de trabajo de una organización.
Explicado de una forma sencilla, existen tres ambientes:
- Ambiente de desarrollo: donde se crea.
- Ambiente de prueba: donde se verifica lo que se creó.
- Ambiente de producción: donde funciona lo que se creó.

Cuando se identifica la necesidad de aplicar una actualización para solucionar una vulnerabilidad, es esencial seguir un proceso de pruebas antes de instalarla en los equipos productivos. Esto se debe a que las actualizaciones pueden causar problemas inesperados si no se ha verificado su compatibilidad con el entorno específico de la organización.

A menudo, los desarrolladores de software realizan pruebas en un entorno que difiere del entorno de producción de una organización, lo que puede resultar en problemas si la actualización se instala directamente en los equipos de producción. Por lo tanto, se requiere un entorno de pruebas para evaluar y verificar el correcto funcionamiento de la actualización antes de implementarla en el entorno de producción.

### ¿Qué deberíamos tener en cuenta para crear un ambiente de pruebas?

Al realizar pruebas de actualización en un ambiente de pruebas antes de implementar cambios en el entorno de producción, se deben seguir estos pasos:

1. Los equipos en el ambiente de pruebas deben ser representativos del total de dispositivos en producción.
   
2. Los equipos de pruebas deben tener las mismas características que los de producción, incluyendo el mismo sistema operativo, aplicaciones y configuraciones.
   
3. Evitar el uso de dispositivos obsoletos o fuera de servicio, ya que no representan con precisión el entorno de producción.
   
4. Informar a todos los usuarios cuyos dispositivos estén en el ambiente de pruebas para recopilar retroalimentación.
   
5. Si las pruebas en el ambiente de pruebas son exitosas y el cambio se comporta como se esperaba sin problemas, entonces está listo para implementarse en el ambiente de producción.
   
Es fundamental seguir estos pasos para evitar problemas inesperados al implementar cambios directamente en producción, ya que podrían ser más complicados que la vulnerabilidad que se intenta solucionar.

### Actualizaciones
La gran mayoría de las vulnerabilidades serán corregidas cuando implementemos los parches de actualización y otras se solucionarán con algunos cambios de configuración.

Es muy importante implementar los parches porque de no hacerlo, estamos provocando una dilatación en nuestra exposición, frente a una determinada vulnerabilidad.

- Consideraciones a tener en cuenta al actualizar:
  - Instalar actualizaciones gradualmente en los equipos, no todos juntos ni en el mismo día.
  - Realizar la tarea fuera del horario laboral.
  - No permitir que los equipos se actualicen
por sí solos.
  - Centralizar la actualización desde un equipo al resto (WSUS).
  - Descargarlas desde repositorios oficiales.

