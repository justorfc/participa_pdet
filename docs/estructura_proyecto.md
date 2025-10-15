# Documentación de la Estructura del Proyecto

## Estado Actual de la Implementación

Esta documentación describe la estructura actual del proyecto `participa_pdet` y el estado de implementación de cada componente.

## Estructura de Directorios

```
participa_pdet/
│
├── app/                            # Aplicación Streamlit
│   ├── main.py                     # ✅ IMPLEMENTADO - Portada principal
│   └── pages/                      # Páginas multipágina
│       ├── 1_transcripcion.py      # ⏳ STUB - Por implementar
│       ├── 2_preprocesamiento.py   # ⏳ STUB - Por implementar
│       ├── 3_codificacion.py       # ⏳ STUB - Por implementar
│       ├── 4_analisis_estadistico.py  # ⏳ STUB - Por implementar
│       └── 5_visualizaciones.py    # ⏳ STUB - Por implementar
│
├── audios/                         # ✅ Archivos de audio de entrevistas
│   ├── Voz 035.m4a
│   ├── Voz 036.m4a
│   └── Voz_Prueba_Piloto_01.m4a
│
├── txts/                           # ✅ Transcripciones en texto plano
│   ├── comunidad_prueba_01.txt
│   ├── comunidad_voz_036.txt
│   └── institucion_voz_035.txt
│
├── data/                           # ✅ CREADO - Resultados procesados
│   └── README.md                   # Documentación del directorio
│
├── Formularios_Definitivos/        # ✅ Formularios de entrevista (.docx)
│   ├── 1. Formulario_Entrevista_Comunidades_PDET_FINAL_REVISADO UVFINAL.docx
│   ├── 2. Formulario_Entrevista_Nivel_Nacional_PDET_UVFINAL.docx
│   └── ... (8 formularios en total)
│
├── Notebooks/                      # ✅ Notebooks Jupyter originales
│   ├── 01_Transcripcion_Audio_Whisper_Colab.ipynb
│   ├── 02_Notebook_Unificado_Transcripcion_Analisis.ipynb
│   └── ... (15 notebooks en total)
│
├── docs/                           # ✅ Documentación del proyecto
│   ├── plan_migracion_streamlit.md     # Plan de migración a Streamlit
│   └── estructura_proyecto.md          # Este archivo
│
├── requirements.txt                # ✅ Dependencias Python
├── README.md                       # ✅ Documentación principal
├── .gitignore                      # ✅ Archivos ignorados por Git
└── LICENSE                         # ✅ Licencia del proyecto
```

## Estado de Componentes

### ✅ Completamente Implementado

- **app/main.py**: Página principal con título y descripción del proyecto
- **Estructura de directorios**: Todos los directorios necesarios existen
- **Documentación base**: README.md y plan de migración
- **Configuración**: requirements.txt con dependencias necesarias

### ⏳ Pendiente de Implementación

Las siguientes páginas de Streamlit son stubs (esqueletos) que necesitan implementación:

1. **1_transcripcion.py**: Transcripción de audios usando Whisper
2. **2_preprocesamiento.py**: Limpieza y normalización de textos
3. **3_codificacion.py**: Codificación cualitativa automática/manual
4. **4_analisis_estadistico.py**: Análisis cuantitativo de códigos
5. **5_visualizaciones.py**: Gráficos y visualizaciones de resultados

### ❌ Recomendado pero No Implementado

- **app/utils.py**: Módulo con funciones utilitarias reutilizables
- **app/nlp_tools.py**: Módulo con herramientas de procesamiento de lenguaje natural
- **tests/**: Directorio con pruebas unitarias (opcional para este proyecto)

## Convenciones de Nombres

### Archivos de Audio
- Formato: `{tipo}_{identificador}.m4a`
- Ejemplo: `Voz 035.m4a`, `Voz_Prueba_Piloto_01.m4a`

### Transcripciones
- Formato: `{tipo}_{identificador}.txt`
- Ejemplo: `comunidad_voz_036.txt`, `institucion_voz_035.txt`

### Datos Procesados
- Se guardarán en `/data/` con nombres descriptivos
- Formato recomendado: `{proceso}_{fecha}_{descripcion}.{ext}`
- Ejemplo: `codificacion_2025-10-15_comunidad.csv`

## Próximos Pasos Recomendados

1. **Migrar funcionalidad de notebooks a páginas Streamlit**: Comenzar con el notebook más simple
2. **Crear módulos utilitarios**: Extraer código común a `app/utils.py`
3. **Implementar persistencia**: Guardar resultados intermedios en `/data/`
4. **Añadir interactividad**: Widgets de Streamlit para carga de archivos y configuración
5. **Documentar funciones**: Añadir docstrings a todas las funciones implementadas

## Referencia

Para más detalles sobre el plan de migración, consultar:
- `docs/plan_migracion_streamlit.md`: Plan completo de migración de notebooks a Streamlit
- `README.md`: Guía rápida de inicio y uso de la aplicación
