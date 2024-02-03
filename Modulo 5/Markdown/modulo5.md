# Modulo 5 
1. Introducción a la criptografía.
2. AlgoritmoHash.
3. Ataques sobre algoritmos de hash.
4. Cifrado.
5. Gestión de contraseñas.
6. KeePass.
7. VeraCrypt.

# Introducción a la Criptografía

## Criptografía
La criptografía engloba técnicas para cifrar mensajes, volviéndolos ininteligibles sin acciones específicas. Se basa en la aritmética, transformando letras a números y realizando cálculos para modificar y asegurar la información. La clave adapta el algoritmo de cifrado.

## Cifrado y Descifrado
El cifrado convierte el texto plano en texto cifrado, ilegible. La sustitución y la transposición son técnicas clásicas. El descifrado recupera el texto original mediante el criptograma y la clave, siguiendo un protocolo criptográfico.

## Criptosistema
Un conjunto de protocolos, algoritmos y gestión de claves forma un criptosistema, con el cual interactúa el usuario final.

## Criptografía Moderna
Claude Shannon, padre de la criptografía matemática, sentó las bases teóricas en 1949. La era moderna empezó a mediados de los 70 con la publicación del Data Encryption Standard (DES) y el artículo de Diffie-Hellman sobre el intercambio de claves.

### Claude Shannon
- Estableció bases teóricas en 1949.
- Padre de la criptografía matemática.

### Data Encryption Standard (DES)
- Publicado en 1975.
- Primer cifrado público avalado por la NSA.
- Reemplazado por Advanced Encryption Standard (AES) en 2001.

### Diffie-Hellman
- Publicación en 1976.
- Introdujo el intercambio de claves.
- Estimuló el desarrollo de algoritmos de cifrado asimétrico.

## Principios de Kerckhoffs
En 1883, Auguste Kerckhoffs estableció principios para sistemas criptográficos:
1. Teóricamente irrompible en la práctica.
2. La efectividad no depende del secreto del diseño.
3. La clave debe ser memorable sin notas.
4. Criptogramas deben ser alfanuméricos.
5. Operable por una persona.
6. Fácil de utilizar.

# Algoritmo Hash

## Algoritmos de Hash
Los algoritmos de hash generan claves únicas para representar datos. Son unidireccionales, permitiendo obtener el hash desde el dato, pero no el dato desde el hash. Se asemejan a huellas dactilares, identifican pero no revelan detalles.

Propiedades:
- Dos entradas distintas generan resultados diferentes.
- Pueden existir colisiones (claves iguales para datos diferentes).

Algoritmos comunes: LM, NTLM, MD5, SHA.

Ejemplos:
- MD5: ebea37120a7c6f155e0c50f9c92ce351
- SHA1: 7dd5de71de03fc27ea218d0d0bd479c713a39fec

## Almacenamiento de Contraseñas
En sistemas informáticos, almacenar contraseñas de forma segura es crucial. Utilizar hashes en lugar de contraseñas en texto claro es una práctica común.

Ejemplo de tabla de usuarios y contraseñas:
| Usuario | Contraseña     |
| ------- | -------------- |
| Admin   | ADM123inistrador |
| Fabian  | pepe2020       |
| Manuel  | emedemama      |

Tabla con hashes:
| Usuario | Contraseña Hash |
| ------- | --------------- |
| Admin   | 52e71b10074c9bfae5dee9652c86217d |
| Fabian  | cb13af1d5b72b5466608ee61e67a030a |
| Juan    | d052a70b81c33146b5b456f88bcb37c2 |
| Manuel  | 65ce8c51bbd6e35527092146d9fbc7ca |

Ahora, leer la base de datos no revela las contraseñas originales, mejorando la seguridad.

# Cifrado al Vuelo (OTFE)

## On The Fly Encryption (OTFE)
El cifrado al vuelo es un método que cifra el contenido de unidades de almacenamiento de forma inmediata, permitiendo el acceso transparente a los datos después de ingresar la clave de descifrado. Se utiliza en herramientas que montan el volumen cifrado como un disco físico, haciéndolo accesible como si no estuviera cifrado.

### Ventaja Principal
La ventaja clave es la accesibilidad inmediata de datos, con cifrado y descifrado transparentes para el usuario. Al apagar el dispositivo o desmontar el volumen cifrado, los datos permanecen seguros.

## Herramientas Destacadas

### VeraCrypt
- Implementa OTFE.
- Código abierto.
- Compatible con Windows, GNU/Linux y Mac.

### BitLocker
- Desarrollado por Microsoft.
- Disponible en Windows Vista (versiones Ultimate y Enterprise).

# Gestión de Contraseñas

## Consejos Generales
1. **Separación:**
   - Usa contraseñas distintas para cuentas importantes.
   - No reutilices contraseñas para cuentas críticas.

2. **Renovación Periódica:**
   - Cambia las contraseñas regularmente para limitar el acceso no autorizado.

3. **Complejidad:**
   - Utiliza números, símbolos y combinaciones de mayúsculas y minúsculas.

4. **Evitar Datos Personales:**
   - Crea contraseñas exclusivas, evita datos personales y patrones predecibles.

5. **Actualizar Métodos de Recuperación:**
   - Mantén actualizada la información de recuperación, como el correo electrónico.

## Almacenamiento Seguro de Contraseñas

### Herramienta Destacada
- **KeePass:**
  - Aplicación de gestión de contraseñas de código abierto.
  - Permite crear bases de datos protegidas por una contraseña maestra.
  - Organiza contraseñas en grupos y subgrupos.
  - Genera contraseñas seguras y mide su fortaleza.
  - Protege la base de datos con AES (Advanced Encryption Standard).
  - [Sitio Oficial de KeePass](https://keepass.info/)


