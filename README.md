# Análisis de Entrevistas PDET – Streamlit App

## Estructura del proyecto

```
participa_pdet/
│
├── app/
│   ├── main.py                # Portada y menú principal
│   └── pages/                  # Páginas multipágina de Streamlit
│       ├── 1_transcripcion.py
│       ├── 2_preprocesamiento.py
│       ├── 3_codificacion.py
│       ├── 4_analisis_estadistico.py
│       └── 5_visualizaciones.py
│
├── data/                       # Resultados intermedios, transcripciones, etc.
├── Formularios_Definitivos/     # Formularios originales .docx
├── Notebooks/                   # Notebooks originales (referencia)
├── requirements.txt             # Dependencias del proyecto
├── README.md                    # Este archivo
└── docs/                        # Documentación y planes
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

## Contribución y Protección de Rama

Este repositorio tiene configurada la protección de la rama `main`. Para contribuir:

1. **Crea una nueva rama** para tu trabajo:
   ```bash
   git checkout -b feature/nombre-descriptivo
   ```

2. **Haz tus cambios** y confirma:
   ```bash
   git add .
   git commit -m "Descripción clara del cambio"
   ```

3. **Sube tu rama** y crea un Pull Request:
   ```bash
   git push origin feature/nombre-descriptivo
   ```

4. **Espera la revisión** y que pasen los checks automáticos (CI)

Para más detalles sobre la configuración de protección de rama, consulta [.github/BRANCH_PROTECTION.md](.github/BRANCH_PROTECTION.md).

---

¿Dudas o sugerencias? Consulta la carpeta `docs/` para más detalles sobre el plan de migración y organización del proyecto.
# participa_pdet
Recoger experiencias, valoraciones y propuestas de actores clave sobre la participación comunitaria y el desarrollo de capacidades en la fase de formulación de los PDET/PATR.
