# Visor cervical educativo v2

Esta carpeta contiene una versión conservadora del visor original. Mantiene el formato visual y añade un organizador local de informes.

## Qué hace

- Acepta PDF, TXT, JPG y PNG.
- Extrae texto de PDF con PDF.js y texto de imágenes con Tesseract.js.
- Procesa los archivos en el navegador.
- Detecta fragmentos candidatos mediante reglas simples.
- Exige revisión y confirmación manual antes de considerar un hallazgo confirmado.
- Guarda solo metadatos, texto detectado y fragmentos en `localStorage`; no sube archivos a un servidor propio.
- Permite exportar un resumen JSON y borrar los datos locales.

## Limitaciones deliberadas

Esta versión no diagnostica, no interpreta DICOM, no mide compresión, no calcula un riesgo individual, no recomienda ejercicios, collar o cirugía y no sustituye a un profesional. La detección automática es solo un filtro de búsqueda y puede equivocarse.

## Estructura

- `index.html`: aplicación completa.
- `Person002_wrap.obj`: modelo 3D utilizado por el visor.
- `README.md`: esta guía.

## Probar localmente

No abras el archivo con `file://`, porque los módulos y el modelo 3D pueden ser bloqueados por el navegador. Desde esta carpeta ejecuta:

```bash
python3 -m http.server 8000
```

Luego abre `http://localhost:8000/`.

## Crear otra carpeta en GitHub

1. Crea un repositorio nuevo, por ejemplo `visor-cervical-educativo`.
2. En la rama principal, crea una carpeta nueva si vas a conservar el repositorio original, o sube estos tres archivos en la raíz del repositorio nuevo.
3. Sube `index.html`, `Person002_wrap.obj` y `README.md`.
4. En GitHub abre **Settings → Pages**.
5. Selecciona **Deploy from a branch**, rama `main`, carpeta `/root`, y guarda.
6. Espera la publicación y abre la URL de GitHub Pages.

## Advertencia de privacidad

La aplicación intenta procesar localmente los archivos, pero PDF.js, Tesseract.js y Three.js se cargan desde CDN. No se envía el contenido del informe a esos CDN por esta implementación, pero para una versión de producción conviene alojar y fijar localmente las dependencias, aplicar una política de seguridad de contenido y realizar una revisión de privacidad. No publiques informes médicos reales dentro del repositorio.

## Mejoras siguientes recomendadas

- Añadir edición de fecha, tipo de examen y página del hallazgo.
- Mostrar el texto original completo solo bajo demanda.
- Añadir una línea de tiempo por examen.
- Separar explícitamente `hallazgo reportado`, `síntoma declarado` e `hipótesis educativa`.
- Incorporar pruebas con profesionales y revisión legal/privacidad antes de uso público.
