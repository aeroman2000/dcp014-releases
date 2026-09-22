# DCP Automation

Aplicación de escritorio para Windows que automatiza la creación de DCPs con
DCP-o-matic: descarga el material (WeTransfer, Dropbox, Google Drive, OneDrive,
pCloud, FTP…), lo analiza, genera y verifica el DCP y lo envía a su destino,
dejando registro de cada trabajo.

Este repositorio solo contiene los instaladores.

## 1. Antes de instalar

La app no incluye estas herramientas; tienen que estar en el PC:

| Herramienta | Para qué | Cómo conseguirla |
|---|---|---|
| **DCP-o-matic 2.18 o superior** | Crear y verificar los DCP | [dcpomatic.com/download](https://dcpomatic.com/download). Instálalo en la ruta por defecto (`C:\Program Files\DCP-o-matic 2`) o indica otra en Configuración |
| **FFmpeg** (`ffmpeg` y `ffprobe`) | Analizar el audio y el vídeo | En una terminal: `winget install Gyan.FFmpeg` (después, cierra y vuelve a abrir la app), o indica la ruta de los `.exe` en Configuración |

Opcionales: **VLC** (abrir vídeos que el reproductor integrado no admite) y
**clairmeta** + **MediaInfo** (control de calidad extra del DCP).

Hace falta Windows 10 u 11 de 64 bits.

## 2. Descargar

Entra en **[la última versión](https://github.com/aeroman2000/dcp014-releases/releases/latest)**
y descarga **`DCP-Automation-Setup-<versión>.exe`**.

> Usa el **instalador** (`Setup`), no el `.exe` suelto: la versión portable
> funciona, pero **no se actualiza sola**.

## 3. Instalar: aviso de Windows

El instalador todavía no está firmado digitalmente, así que la primera vez
Windows lo trata como un programa desconocido. Es normal:

1. Al abrirlo aparece **"Windows protegió su PC"**.
2. Pulsa **"Más información"**.
3. Pulsa **"Ejecutar de todas formas"**.

Puede que el navegador también avise al descargarlo ("no se descarga
habitualmente"); elige **Conservar**.

Si en vez de ese aviso Windows dice que ha **bloqueado** la aplicación sin dar
opción de continuar, el PC tiene activado el *Control inteligente de
aplicaciones*. Avisa antes de desactivar nada.

Este aviso solo sale en la primera instalación: las actualizaciones no lo muestran.

## 4. Primer arranque

1. Abre **Configuración** (arriba a la derecha).
2. En **Carpetas Fuente**, indica la carpeta donde dejaréis el material de cada
   proyecto. Cada subcarpeta será un proyecto.
3. Opcional: **Carpeta de salida de DCPs**. Si la dejas vacía, cada DCP se
   guarda en `<carpeta del proyecto>\dcp\`.
4. Guarda.

Si aparece una **franja amarilla** arriba, falta alguna herramienta del paso 1
o su ruta no es correcta: la franja dice cuál y lleva directamente a
Configuración.

## 5. Actualizaciones

La app comprueba si hay versión nueva al abrirse y cada 4 horas. Si la hay, la
descarga sola y se instala **al cerrar la app**. También puedes pulsar
**"Reiniciar y actualizar"** (arriba, o en Configuración → Actualizaciones),
salvo mientras se esté generando un DCP o enviando uno: nunca se corta un
trabajo en curso.

## 6. Si algo no funciona

Genera un **diagnóstico** y envíalo:

- Problema general: **Configuración → Diagnóstico → Exportar diagnóstico…**
- Problema con un trabajo concreto: abre su **Log** y pulsa **Exportar diagnóstico**.

Se crea un `.zip` con las versiones de la app y de las herramientas, la
configuración y los logs de los trabajos. **No incluye contraseñas, tokens ni
API keys**, pero sí rutas de carpetas y nombres de proyectos.

## Dónde guarda sus datos

En `%APPDATA%\dcp-automation-app` (base de datos, configuración y temporales).
Desinstalar la app no borra esa carpeta, así que al reinstalar se conserva todo.
