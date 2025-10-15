# Análisis de Entrevistas PDET – Streamlit App

## Estructura del proyecto

```
participa_pdet/
│
├── app/
│   ├── main.py                      # Portada y menú principal
│   └── pages/                        # Páginas multipágina de Streamlit
│       ├── 1_transcripcion.py
│       ├── 2_preprocesamiento.py
│       ├── 3_codificacion.py
│       ├── 4_analisis_estadistico.py
│       └── 5_visualizaciones.py
│
├── audios/                          # Archivos de audio de entrevistas
├── txts/                            # Transcripciones de entrevistas en formato texto
├── Formularios_Definitivos/         # Formularios originales .docx
├── Notebooks/                       # Notebooks originales (referencia)
├── docs/                            # Documentación y planes
├── requirements.txt                 # Dependencias del proyecto
├── .gitignore                       # Archivos a ignorar en git
├── LICENSE                          # Licencia del proyecto
└── README.md                        # Este archivo
```

**Nota:** La carpeta `data/` para resultados intermedios se creará automáticamente al ejecutar la aplicación.

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

## Documentación adicional

- **Plan de migración:** Consulta `docs/plan_migracion_streamlit.md` para detalles sobre la migración de notebooks a Streamlit
- **Análisis de estructura:** Revisa `docs/analisis_estructura_proyecto.md` para un análisis detallado de la organización del proyecto

## Sobre el proyecto

Este proyecto tiene como objetivo recoger experiencias, valoraciones y propuestas de actores clave sobre la participación comunitaria y el desarrollo de capacidades en la fase de formulación de los PDET/PATR.

**Tesis doctoral:** Ciudadanía, participación y capacidades en la formulación de los PDET en la subregión de Montes de María  
**Autor:** Mario Chamie Mazzillo – Universidad Externado de Colombia

---

¿Dudas o sugerencias? Abre un issue en el repositorio o contacta al autor del proyecto.
