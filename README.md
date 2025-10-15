# Análisis de Entrevistas PDET – Streamlit App

## Descripción del proyecto

Recoger experiencias, valoraciones y propuestas de actores clave sobre la participación comunitaria y el desarrollo de capacidades en la fase de formulación de los PDET/PATR.

**Tesis doctoral:** Ciudadanía, participación y capacidades en la formulación de los PDET en la subregión de Montes de María  
**Autor:** Mario Chamie Mazzillo – Universidad Externado de Colombia

## Estructura del proyecto

```
participa_pdet/
│
├── app/
│   ├── main.py                     # Portada y menú principal
│   └── pages/                      # Páginas multipágina de Streamlit
│       ├── 1_transcripcion.py
│       ├── 2_preprocesamiento.py
│       ├── 3_codificacion.py
│       ├── 4_analisis_estadistico.py
│       └── 5_visualizaciones.py
│
├── audios/                         # Archivos de audio de entrevistas
├── txts/                           # Transcripciones de texto
├── data/                           # Resultados intermedios procesados (CSV, análisis)
├── Formularios_Definitivos/        # Formularios originales .docx
├── Notebooks/                      # Notebooks originales (referencia)
├── requirements.txt                # Dependencias del proyecto
├── README.md                       # Este archivo
└── docs/                           # Documentación y planes
```

## ¿Cómo ejecutar la app?

1. Activa el entorno virtual:
	```bash
	source .venv/bin/activate
	```
2. Instala dependencias:
	```bash
	pip install -r requirements.txt
	```
3. Ejecuta la app:
	```bash
	streamlit run app/main.py
	```

## ¿Cómo agregar nuevas páginas?

Crea un nuevo archivo `.py` en `app/pages/` y Streamlit lo detectará automáticamente como una página del menú lateral.

---

¿Dudas o sugerencias? Consulta la carpeta `docs/` para más detalles sobre el plan de migración y organización del proyecto.
