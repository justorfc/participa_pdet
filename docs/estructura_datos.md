# Estructura de Datos del Proyecto

Este documento describe la organización y formato de los datos en el proyecto participa_pdet.

## 1. Directorios de Datos

### `audios/`
**Propósito:** Almacena archivos de audio originales de las entrevistas.

**Formato de archivos:** `.m4a`, `.mp3`, `.wav`

**Nomenclatura sugerida:**
- `{tipo_actor}_{identificador}.m4a`
- Ejemplos: `comunidad_voz_036.m4a`, `institucion_voz_035.m4a`

**Tipos de actores:**
- `comunidad`: Representantes comunitarios
- `institucion`: Actores institucionales
- `nacional`: Nivel nacional
- `regional`: Nivel regional
- `local`: Nivel local

### `txts/`
**Propósito:** Contiene transcripciones en texto plano de las entrevistas.

**Formato de archivos:** `.txt` (UTF-8)

**Nomenclatura:** Debe coincidir con el archivo de audio correspondiente
- Ejemplo: `comunidad_voz_036.txt` corresponde a `comunidad_voz_036.m4a`

**Estructura del contenido:**
```
[Metadatos opcionales al inicio]
Entrevistador: [Nombre]
Entrevistado: [Código/Pseudónimo]
Fecha: [DD/MM/AAAA]
Lugar: [Ubicación]
---

[Transcripción del audio]
```

### `data/transcripciones/`
**Propósito:** Transcripciones procesadas y estructuradas.

**Formatos:**
- `transcripciones.csv`: Tabla con todas las transcripciones
- `transcripcion_{id}.json`: Transcripción individual en JSON

**Estructura CSV:**
```csv
id,archivo,tipo_actor,fecha,texto_completo,duracion_segundos
1,voz_035,institucion,2024-01-15,"texto...",1234
```

**Estructura JSON:**
```json
{
  "id": "voz_035",
  "tipo_actor": "institucion",
  "fecha": "2024-01-15",
  "metadata": {
    "duracion": 1234,
    "ubicacion": "Montes de María",
    "calidad_audio": "alta"
  },
  "transcripcion": "texto completo...",
  "segmentos": [
    {
      "inicio": 0,
      "fin": 30,
      "texto": "fragmento..."
    }
  ]
}
```

### `data/codificaciones/`
**Propósito:** Resultados de codificación cualitativa.

**Archivos principales:**
- `codigos_abiertos.csv`: Códigos de codificación abierta
- `codigos_axiales.csv`: Códigos de codificación axial
- `codigos_selectivos.csv`: Códigos de codificación selectiva
- `matriz_codificacion.csv`: Matriz completa de codificación

**Estructura de codigos_abiertos.csv:**
```csv
id_fragmento,archivo,fragmento,codigo_abierto,categoria_axial,nota
1,voz_035,"texto del fragmento...","participación activa","Participación","observación"
```

**Estructura de matriz_codificacion.csv:**
```csv
archivo,tipo_actor,codigo,categoria,frecuencia,contexto
voz_035,institucion,participacion_activa,Participación,5,"descripción contextual"
```

### `data/resultados/`
**Propósito:** Resultados finales de análisis.

**Subdirectorios:**
- `estadisticos/`: Tablas de análisis estadístico
- `visualizaciones/`: Gráficos exportados (PNG, PDF)
- `reportes/`: Reportes generados (Markdown, HTML, PDF)

**Archivos típicos:**
- `frecuencias_codigos.csv`: Tabla de frecuencias
- `coocurrencias.csv`: Matriz de coocurrencias
- `analisis_por_actor.csv`: Análisis comparativo por tipo de actor
- `resumen_ejecutivo.md`: Resumen de hallazgos

### `data/intermedios/`
**Propósito:** Archivos temporales y procesamiento intermedio.

**Contenido:**
- Archivos de preprocesamiento de texto
- Caches de modelos
- Resultados parciales durante el análisis
- Archivos temporales de visualizaciones

**Nota:** Este directorio puede limpiarse periódicamente.

## 2. Formularios

### `Formularios_Definitivos/`
**Propósito:** Formularios de entrevista originales.

**Archivos:**
1. `1. Formulario_Entrevista_Comunidades_PDET_FINAL_REVISADO UVFINAL.docx`
2. `2. Formulario_Entrevista_Nivel_Nacional_PDET_UVFINAL.docx`
3. `3. Formulario_Entrevista_Nivel_Regional_PDET_FINALUV..docx`
4. `4. Formulario_Entrevista_Nivel_Local_PDET_FINALUV.docx`
5. `5. Formulario_Entrevista_Procuraduria_PDET_CORREGIDOUVFINAL (3).docx`
6. `6. Formulario_Entrevista_Contraloria_PDET_FINALUV.docx`
7. `7. Formulario_Entrevista_Comision_Paz_PDET_FINALUV.docx`
8. `8.Formulario_Entrevista_Cooperacion_Internacional_PDET_FINALUV.docx`

## 3. Flujo de Datos

```
1. ENTRADA
   audios/ (audio original)
   ↓
2. TRANSCRIPCIÓN
   txts/ (transcripción cruda)
   ↓
   data/transcripciones/ (transcripción estructurada)
   ↓
3. PREPROCESAMIENTO
   data/intermedios/ (texto limpio y segmentado)
   ↓
4. CODIFICACIÓN
   data/codificaciones/ (códigos aplicados)
   ↓
5. ANÁLISIS
   data/resultados/ (estadísticas, visualizaciones)
   ↓
6. SALIDA
   Reportes, gráficos, tablas exportables
```

## 4. Consideraciones Técnicas

### Codificación de caracteres
- **Usar UTF-8** en todos los archivos de texto
- Especialmente importante para textos en español (tildes, ñ)

### Separadores CSV
- Usar coma (`,`) como separador
- Entrecomillar campos con texto largo o con comas

### Formato de fechas
- ISO 8601: `YYYY-MM-DD` o `YYYY-MM-DD HH:MM:SS`
- Ejemplo: `2024-01-15` o `2024-01-15 14:30:00`

### Identificadores
- Usar identificadores únicos y consistentes
- Preferir códigos alfanuméricos: `voz_035`, `comm_01`
- Evitar espacios y caracteres especiales

### Tamaño de archivos
- Audios: Pueden ser grandes (>100MB), considerar compresión
- Transcripciones: Generalmente pequeñas (<1MB)
- Resultados: Variables según tipo de análisis

## 5. Privacidad y Ética

### Datos sensibles
- **Anonimizar** toda información personal identificable
- Usar **pseudónimos** o códigos en lugar de nombres reales
- Remover referencias a ubicaciones específicas si es necesario

### Gestión de datos
- No compartir datos crudos sin consentimiento
- Mantener respaldos seguros
- Documentar el proceso de anonimización

### Control de acceso
- Limitar acceso a datos sensibles
- Usar `.gitignore` para evitar subir datos al repositorio público
- Considerar cifrado para archivos muy sensibles

## 6. Respaldo y Recuperación

### Estrategia de respaldo
1. **Local:** Copias en disco externo o NAS
2. **Nube:** Almacenamiento encriptado (Google Drive, Dropbox, etc.)
3. **Frecuencia:** Semanal o después de cada sesión de trabajo importante

### Estructura de respaldo recomendada
```
backup_participa_pdet_YYYYMMDD/
├── audios/
├── txts/
├── data/
└── Notebooks/
```

### Archivos críticos a respaldar
- ✅ Audios originales
- ✅ Transcripciones
- ✅ Codificaciones
- ✅ Resultados finales
- ⚠️ Notebooks (importante pero versionados en git)
- ❌ Archivos intermedios (regenerables)

---

## Referencias

- Plan de migración: `docs/plan_migracion_streamlit.md`
- Análisis de estructura: `docs/analisis_estructura_proyecto.md`

---

**Última actualización:** 15 de octubre de 2025  
**Versión:** 1.0
