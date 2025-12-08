# README del Proyecto

## Estructura de carpeta del proyecto

nombre_del_proyecto/
├── README.md              # Resumen del proyecto, instrucciones de instalación y uso.
├── requirements.txt       # Lista de dependencias (pip freeze > requirements.txt).
├── .gitignore             # Archivos que Git debe ignorar (ej. datos pesados, credenciales).
│
├── data/                  # NUNCA subas esta carpeta a GitHub si los datos son pesados o privados.
│   ├── raw/               # Datos originales inmutables. Nunca se deben modificar.
│   ├── processed/         # Datos limpios y transformados listos para el modelo.
│   └── external/          # Datos de terceros o fuentes externas.
│
├── notebooks/             # Jupyter Notebooks para exploración y prototipado.
│   ├── 0.1-exploracion.ipynb
│   ├── 0.2-preprocessing.ipynb
│   └── 1.0-modelo-baseline.ipynb
│
├── models/                # Modelos serializados/entrenados (ej. .pkl, .h5, .pt).
│
└── README.md              # Documentación del proyecto o el borrador del paper (LaTeX/Word).