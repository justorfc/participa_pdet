# Directorio de Datos

Este directorio contiene los datos procesados y resultados intermedios generados por la aplicación.

## Estructura de subdirectorios

### `transcripciones/`
Contiene las transcripciones procesadas de las entrevistas en formato estructurado (CSV, JSON).

### `codificaciones/`
Almacena los resultados de la codificación cualitativa (abierta, axial y selectiva) de las entrevistas.

### `resultados/`
Contiene los resultados finales de análisis estadísticos, visualizaciones exportadas y reportes.

### `intermedios/`
Guarda archivos temporales y resultados intermedios del procesamiento de datos.

## Gestión de datos

- **No se versionan en git:** Por razones de privacidad y tamaño, los archivos de datos no se incluyen en el control de versiones.
- **Backup recomendado:** Se recomienda hacer respaldos regulares de este directorio.
- **Formato de archivos:** Preferiblemente usar formatos abiertos (CSV, JSON, TXT) para garantizar la reproducibilidad.

## Consideraciones de privacidad

Este directorio puede contener información sensible de entrevistas. Asegúrate de:
- Anonimizar datos personales antes de compartir
- No incluir información identificable en repositorios públicos
- Seguir las normativas de protección de datos aplicables

---

**Nota:** Este directorio se crea automáticamente si no existe al ejecutar la aplicación.
