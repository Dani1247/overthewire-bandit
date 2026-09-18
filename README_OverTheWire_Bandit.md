# OverTheWire: Bandit — 32 niveles superados

Resolución progresiva de los retos de [OverTheWire Bandit](https://overthewire.org/wargames/bandit/), un wargame orientado a practicar fundamentos de seguridad en sistemas Linux mediante conexiones SSH sucesivas, donde cada nivel superado da acceso al siguiente.

## Objetivo

Reforzar y poner en práctica conocimientos de administración de sistemas Linux, redes y seguridad básica en un entorno controlado y progresivo, enfrentándome a retos reales de línea de comandos, permisos, redes y control de versiones.

## Habilidades demostradas

- **Línea de comandos y sistema de ficheros Linux**: navegación avanzada, búsqueda de archivos ocultos y con nombres especiales, manejo de permisos y propietarios.
- **Escalada de privilegios**: identificación y explotación de binarios con permisos especiales (SUID/SGID) para ejecutar acciones con privilegios de otro usuario.
- **Gestión de claves SSH**: copia, protección de permisos (`chmod 600`) y uso de claves privadas para autenticación entre niveles.
- **Redes y protocolos**: uso de `netcat`, `openssl s_client` y `nmap` para establecer conexiones directas, comunicarse con servicios en texto plano o cifrados (TLS) y escanear puertos abiertos.
- **Automatización con Bash**: scripts para ataques de fuerza bruta controlados y para explotar tareas `cron` mal configuradas que ejecutan ficheros de un directorio con permisos inseguros.
- **Codificación y cifrado**: decodificación de Base64, hexadecimal y ROT13.
- **Git a nivel avanzado**: inspección de historial de commits, comparación de ramas (`git diff`, `git log`), listado y lectura de tags, y localización de información oculta en el historial de un repositorio.
- **Evasión de shells restringidas**: comprensión de cómo una shell restringida intercepta comandos y cómo variables especiales (`$0`) permiten obtener una shell sin restricciones.

## Algunos retos destacados

- **Shell restringida (nivel 32)**: una terminal convertía todo lo escrito a mayúsculas para impedir ejecutar comandos. La solución consistió en ejecutar `$0`, una variable especial que el shell sustituye por el nombre del propio proceso en ejecución, evitando así la transformación a mayúsculas y obteniendo una shell normal.
- **Tarea cron insegura (nivel 23)**: un script se ejecutaba automáticamente cada minuto como otro usuario, ejecutando cualquier archivo que encontrara en un directorio determinado. Aprovechando esto, se dejó un script propio en ese directorio para que la tarea lo ejecutara con privilegios ajenos y devolviera la contraseña del siguiente nivel.
- **Información oculta en Git (niveles 27–31)**: la contraseña de estos niveles no estaba en los archivos visibles del repositorio, sino en commits antiguos, ramas secundarias o tags, lo que requirió inspeccionar el historial completo con `git log`, `git branch -a`, `git tag` y `git show`.

## Herramientas y comandos utilizados

`ssh` · `netcat` · `openssl s_client` · `nmap` · `find` (búsqueda por permisos SUID/SGID) · `base64` · `tr` (ROT13) · `xxd`/`hexdump` · `git` (log, diff, branch, tag, show) · scripting en `bash`

## Nota

Este repositorio documenta el proceso y las técnicas empleadas en cada nivel. Por las normas del propio wargame, no se publican las contraseñas obtenidas en cada nivel.

## Documentación completa

La memoria completa con capturas de pantalla paso a paso de los 32 niveles está disponible en [`OverTheWire_Bandit.docx`](./) *(o en PDF, según lo que subas)*.
