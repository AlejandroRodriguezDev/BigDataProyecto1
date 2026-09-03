# Proyecto 1 — Frameworks y Herramientas para Big Data

## 📓 Entorno Jupyter (`/jupyter`)

El directorio `jupyter/` contiene un entorno **JupyterLab + PySpark** completamente dockerizado, listo para desarrollar y ejecutar notebooks.

### Estructura

```
jupyter/
├── Dockerfile             # Imagen personalizada basada en jupyter/pyspark-notebook
├── docker-compose.yml     # Orquestación del contenedor
└── notebooks/             # Volumen montado donde se guardan los notebooks (.ipynb)
```

### ¿Qué incluye?

La imagen está basada en `jupyter/pyspark-notebook:latest` y agrega:

| Característica | Detalle |
|---|---|
| **PySpark** | Incluido en la imagen base |
| **JupyterLab** | Interfaz web principal |
| **jupyterlab-lsp** | Autocompletado inteligente (Language Server Protocol) |
| **python-lsp-server** | Backend del LSP con soporte completo |
| **Auto-cierre de brackets** | Configurado en notebook, editor y celdas de código |
| **Hinting continuo** | Sugerencias de código mientras se escribe |

### Puertos expuestos

| Puerto | Servicio |
|---|---|
| `8888` | JupyterLab (interfaz web) |
| `4040` | Spark UI (monitoreo de jobs) |

### Cómo correr el entorno

#### Requisitos previos
- Docker y Docker Compose instalados y corriendo.

#### 1. Construir la imagen y levantar el contenedor

```bash
cd jupyter/
docker compose up --build -d
```

> La primera vez tarda unos minutos porque descarga la imagen base y compila los paquetes.

#### 2. Acceder a JupyterLab

Abre el navegador en:

```
http://localhost:8888
```

Cuando pida el **token**, ingresa:

```
bigdata2026
```

#### 3. Acceder al Spark UI

Para monitorear los jobs de Spark (disponible solo cuando hay una sesión activa):

```
http://localhost:4040
```

#### 4. Detener el contenedor

```bash
docker compose down
```

### Guardar notebooks

Los notebooks se guardan en `jupyter/notebooks/`. Esta carpeta está montada como volumen en el contenedor (`/home/jovyan/work`), por lo que **los archivos persisten** aunque el contenedor se detenga o se elimine.

---
