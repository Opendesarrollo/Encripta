<div align="left">
  <pre style="font-family: monospace; line-height: 1.1; overflow-x: auto;">
███████╗███╗   ██╗ ██████╗██████╗ ██╗██████╗ ████████╗ █████╗
██╔════╝████╗  ██║██╔════╝██╔══██╗██║██╔══██╗╚══██╔══╝██╔══██╗
█████╗  ██╔██╗ ██║██║     ██████╔╝██║██████╔╝   ██║   ███████║
██╔══╝  ██║╚██╗██║██║     ██╔══██╗██║██╔═══╝    ██║   ██╔══██║
███████╗██║ ╚████║╚██████╗██║  ██║██║██║        ██║   ██║  ██║
╚══════╝╚═╝  ╚═══╝ ╚═════╝╚═╝  ╚═╝╚═╝╚═╝        ╚═╝   ╚═╝  ╚═╝
  </pre>
</div>

## ¿Qué es Encripta?

**Encripta** permite proteger información desde la línea de comandos mediante cifrado.

Su objetivo es que una persona pueda convertir información legible en datos protegidos y recuperarlos únicamente con la clave correspondiente.

### ¿Qué obtienes al usarlo?

- Proteges información sensible antes de almacenarla o compartirla.
- Evitas que los datos puedan leerse directamente si alguien obtiene el contenido cifrado.
- Puedes cifrar información utilizando una clave pública.
- Solo la clave privada correspondiente permite recuperar la información.
- Puedes detectar si los datos cifrados fueron modificados.
- No necesitas conocer criptografía para realizar las operaciones básicas.

---

## Misión

Permitir que cualquier persona pueda **proteger información sensible de forma sencilla**, reduciendo el riesgo de exposición de los datos y manteniendo el control sobre quién puede recuperarlos.

---

## Visión

Facilitar el uso del cifrado para que proteger información sea una acción cotidiana y accesible, tanto para usuarios comunes como para desarrolladores.

---

## ¿Qué problema resuelve?

La información almacenada o compartida sin protección puede ser leída por cualquier persona que consiga acceso a ella.

Encripta permite transformar esa información en datos cifrados antes de almacenarlos o enviarlos.

| Estado | Qué ocurre | Resultado |
|---|---|---|
| **Sin protección** | La información se guarda o comparte de forma legible. | Si alguien obtiene acceso, puede leerla directamente. |
| **Con Encripta** | La información se transforma mediante cifrado antes de guardarse o compartirse. | Los datos quedan protegidos y no pueden interpretarse directamente sin la clave correspondiente. |


## Compilar

### Windows 64 bits

```cmd

set GOOS=windows
set GOARCH=amd64
go build -o encripta-windows-amd64.exe

```

### Linux 64 bits

```cmd

set GOOS=linux
set GOARCH=amd64
go build -o encripta-linux-amd64

```


### Android 64 bits ARM

```cmd

set GOOS=android
set GOARCH=arm64
set CGO_ENABLED=0
go build -o encripta-android-arm64

```

# Manual de uso de Encripta

Encripta es una herramienta de línea de comandos que permite proteger y recuperar información mediante cifrado.

Este manual está dirigido al usuario final. No es necesario conocer programación ni criptografía para utilizar la aplicación.

---

## 1. Uso general

La estructura general de los comandos es:

```bash
encripta <comando> [argumentos]
```

Ejemplo:

```bash
encripta estado
```

Para consultar los comandos disponibles:

```bash
encripta ayuda
```

---

## 2. Comandos disponibles

| Comando        | Alias | Descripción                                     |
| -------------- | ----- | ----------------------------------------------- |
| `crear-claves` | —     | Crea un nuevo par de claves para cifrado.       |
| `cifrar`       | `c`   | Cifra un mensaje y genera un archivo protegido. |
| `descifrar`    | `d`   | Descifra un archivo y recupera su contenido.    |
| `configurar`   | —     | Define las claves que utilizará Encripta.       |
| `estado`       | `e`   | Muestra el estado actual de la configuración.   |
| `ayuda`        | `a`   | Muestra la ayuda disponible.                    |
| `version`      | `v`   | Muestra la versión instalada de Encripta.       |

---

# 3. Primer uso

Antes de cifrar o descifrar información se recomienda realizar los siguientes pasos:

```text
1. Crear las claves
        ↓
2. Configurar Encripta
        ↓
3. Cifrar o descifrar información
```

Primero ejecute:

```bash
encripta crear-claves
```

Después configure las claves que utilizará:

```bash
encripta configurar
```

Puede verificar la configuración mediante:

```bash
encripta estado
```

Una vez completados estos pasos, Encripta estará listo para realizar operaciones de cifrado y descifrado.

---

# 4. Crear claves

## Comando

```bash
encripta crear-claves
```

Este comando crea un nuevo par de claves compuesto por:

* una **clave pública**;
* una **clave privada**.

La clave pública puede compartirse con otras personas.

La clave privada debe mantenerse protegida y permanecer únicamente bajo control de su propietario.

Durante el proceso, Encripta solicitará establecer una contraseña para proteger la clave privada.

Ejemplo:

```text
CREAR CLAVES

Defina una contraseña para proteger su clave privada.

Contraseña: ************
Confirmar contraseña: ************
```

Si ambas contraseñas coinciden, Encripta genera las claves y muestra los nombres de los archivos creados.

### Importante

La contraseña protege la clave privada.

No comparta:

* la contraseña;
* la clave privada.

Puede compartir:

* la clave pública.

La clave pública permite cifrar información destinada al propietario de la clave privada, pero no permite recuperar directamente la información protegida.

---

# 5. Configurar Encripta

## Comando

```bash
encripta configurar
```

Este comando permite definir las claves que utilizará Encripta durante sus operaciones.

Debe ejecutarse después de crear o recibir las claves correspondientes.

La configuración permite que Encripta conozca qué archivos utilizar cuando sea necesario cifrar o descifrar información.

Después de realizar la configuración puede comprobar su estado mediante:

```bash
encripta estado
```

---

# 6. Consultar el estado

## Comando

```bash
encripta estado
```

También puede utilizar:

```bash
encripta e
```

Este comando muestra el estado actual de Encripta y permite verificar si las claves necesarias se encuentran configuradas.

Se recomienda utilizarlo cuando:

* se acaba de instalar Encripta;
* se han creado nuevas claves;
* se ha cambiado la configuración;
* una operación de cifrado o descifrado indica que faltan claves.

Ejemplo:

```bash
encripta estado
```

---

# 7. Cifrar información

## Comando

```bash
encripta cifrar
```

También puede utilizar:

```bash
encripta c
```

Este comando permite proteger un mensaje mediante cifrado.

Encripta utiliza la clave pública configurada para generar un archivo cifrado.

El resultado puede almacenarse o enviarse a otra persona sin exponer directamente el contenido original.

El proceso general es:

```text
Mensaje original
      ↓
   Encripta
      ↓
Archivo cifrado
```

El archivo generado contiene la información protegida y no debe interpretarse como texto legible.

### Ejemplo

```bash
encripta cifrar
```

Después siga las instrucciones mostradas por la aplicación.

---

# 8. Descifrar información

## Comando

```bash
encripta descifrar <archivo>
```

También puede utilizar:

```bash
encripta d <archivo>
```

Ejemplo:

```bash
encripta descifrar mensaje.seg
```

o:

```bash
encripta d mensaje.seg
```

El comando utiliza la clave privada configurada para intentar recuperar el contenido original.

Durante el proceso, Encripta solicitará la contraseña utilizada para proteger la clave privada.

Ejemplo:

```text
DESCIFRAR MENSAJE

Ingrese la contraseña de su clave privada para descifrar el mensaje.

Contraseña: ************
```

Si la contraseña y las claves son correctas, Encripta recuperará el mensaje.

Ejemplo:

```text
El mensaje fue descifrado correctamente.

Mensaje: Información protegida
```

Si la contraseña no corresponde a la clave privada, la operación no podrá completarse.

---

# 9. Archivo `.seg`

Los archivos cifrados por Encripta utilizan la extensión:

```text
.seg
```

Ejemplo:

```text
mensaje.seg
```

Un archivo `.seg` contiene información protegida por Encripta.

No debe modificarse manualmente, ya que alterar su contenido puede impedir que sea descifrado correctamente.

Para recuperar su contenido utilice:

```bash
encripta descifrar mensaje.seg
```

---

# 10. Ayuda

## Comando

```bash
encripta ayuda
```

También puede utilizar:

```bash
encripta a
```

Muestra una referencia rápida de los comandos disponibles.

Ejemplo:

```bash
encripta ayuda
```

La ayuda incluye:

* sintaxis general;
* comandos disponibles;
* argumentos;
* alias;
* ejemplos básicos.

---

# 11. Consultar la versión

## Comando

```bash
encripta version
```

También puede utilizar:

```bash
encripta v
```

Este comando muestra la versión de Encripta instalada en el equipo.

Puede ser útil para verificar qué versión se está utilizando al solicitar soporte o instalar una actualización.

---

# 12. Flujo habitual de trabajo

Un usuario que utiliza Encripta por primera vez puede seguir este flujo:

### Paso 1 — Crear claves

```bash
encripta crear-claves
```

### Paso 2 — Configurar las claves

```bash
encripta configurar
```

### Paso 3 — Verificar la configuración

```bash
encripta estado
```

### Paso 4 — Cifrar información

```bash
encripta cifrar
```

### Paso 5 — Descifrar un archivo recibido

```bash
encripta descifrar mensaje.seg
```

---

# 13. Clave pública y clave privada

Encripta utiliza un esquema basado en dos claves diferentes.

## Clave pública

La clave pública puede compartirse.

Su función es permitir que información destinada a usted pueda ser protegida.

Ejemplo:

```text
USTED
 │
 └── comparte su clave pública
             ↓
          PERSONA B
             ↓
        cifra información
             ↓
        archivo protegido
```

Compartir la clave pública no implica compartir la capacidad de descifrar la información.

---

## Clave privada

La clave privada permite recuperar la información protegida correspondiente.

Debe mantenerse bajo control exclusivo de su propietario.

```text
Archivo cifrado
      +
Clave privada
      +
Contraseña
      ↓
   Encripta
      ↓
Mensaje original
```

Nunca envíe su clave privada a otra persona.

---

# 14. Contraseña de la clave privada

Cuando se ejecuta:

```bash
encripta crear-claves
```

Encripta solicita una contraseña.

Esta contraseña protege la clave privada almacenada.

Se recomienda utilizar una contraseña:

* suficientemente larga;
* difícil de adivinar;
* diferente a las utilizadas en otros servicios;
* que no contenga únicamente información personal conocida.

Evite contraseñas como:

```text
12345678
password
admin
qwerty
```

Una contraseña más extensa y difícil de predecir ofrece mayor protección.

### Importante

Conserve su contraseña de forma segura.

Si pierde la contraseña y no dispone de otro mecanismo de recuperación, podría perder el acceso a la información protegida con esa clave.

---

# 15. Recomendaciones de seguridad

Para utilizar Encripta de forma adecuada:

1. **No comparta su clave privada.**
2. **No comparta la contraseña de su clave privada.**
3. **Puede compartir su clave pública.**
4. Mantenga una copia de respaldo segura de sus claves.
5. Utilice contraseñas largas y difíciles de predecir.
6. No modifique manualmente los archivos `.seg`.
7. Verifique siempre qué clave pública está utilizando antes de cifrar información destinada a otra persona.
8. Mantenga los archivos de claves en dispositivos de confianza.
9. Evite almacenar la contraseña junto al archivo de la clave privada.
10. Mantenga actualizada su instalación de Encripta.

---

# 16. Respaldo de claves

Las claves son elementos importantes para poder acceder a la información protegida.

Se recomienda mantener una copia de respaldo de:

* la clave privada;
* la clave pública.

El respaldo debe almacenarse en un lugar seguro.

Por ejemplo:

```text
Equipo principal
      +
Unidad externa protegida
```

No se recomienda depender de una única copia de la clave privada.

La pérdida definitiva de la clave privada puede impedir recuperar información cifrada para esa clave.

---

# 17. Compartir información de forma segura

Cuando necesite enviar información protegida a otra persona:

```text
1. Obtenga la clave pública del destinatario.
2. Configure la clave correspondiente.
3. Cifre la información.
4. Envíe el archivo .seg.
```

El destinatario utilizará su propia clave privada para recuperar la información.

La clave privada **nunca debe enviarse junto con el archivo cifrado**.

---

# 18. Mensajes frecuentes

## No hay claves configuradas

Si Encripta muestra:

```text
No hay claves configuradas.
Ejecute: encripta configurar
```

ejecute:

```bash
encripta configurar
```

---

## No hay una clave privada configurada

Significa que Encripta no conoce qué clave privada debe utilizar.

Ejecute:

```bash
encripta configurar
```

y seleccione o configure la clave correspondiente.

---

## Contraseña incorrecta

Si Encripta indica que la contraseña es incorrecta, compruebe que está utilizando:

* la contraseña correcta;
* la clave privada correcta.

Las contraseñas distinguen entre los caracteres ingresados y deben escribirse exactamente como fueron definidas.

---

## El archivo no puede descifrarse

Compruebe:

* que el archivo no haya sido modificado;
* que esté utilizando la clave privada correcta;
* que la contraseña sea correcta;
* que el archivo corresponda a un archivo generado por Encripta.

---

# 19. Referencia rápida

```text
CREAR CLAVES

encripta crear-claves
```

```text
CONFIGURAR

encripta configurar
```

```text
VER ESTADO

encripta estado
encripta e
```

```text
CIFRAR

encripta cifrar
encripta c
```

```text
DESCIFRAR

encripta descifrar mensaje.seg
encripta d mensaje.seg
```

```text
AYUDA

encripta ayuda
encripta a
```

```text
VERSIÓN

encripta version
encripta v
```

---

# 20. Buenas prácticas

Recuerde esta regla:

```text
Clave pública  → se puede compartir.

Clave privada  → no se comparte.

Contraseña     → no se comparte.
```

Encripta protege la información mediante cifrado, pero la seguridad también depende del cuidado con el que se administren las claves y las contraseñas.

---

© 2026 OpenDesarrollo. Todos los derechos reservados.
