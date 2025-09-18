## Chess Opening Graph

El siguiente repositorio contiene el trabajo final de la de especialización en Explotación de Datos y Descubrimiento del Conocimiento, entregado por la Facultad de Ciencias Exactas y la Facultad de Ingeniería (UBA). El proyecto explora patrones de elección de aperturas en ajedrez a partir de partidas en formato PGN, construyendo una matriz bipartita jugador–apertura y, a partir de ella, una red de coocurrencia de aperturas para analizar metricas topológicas de las redes y encontrar comunidades, para 3 grupos de jugadores que fueron clasificados segun el ELO.

### Objetivos
- **Extracción** de los metadatos de los archivos PGN.
- **Modelar** el repertorio de aperturas por jugador con una matriz bipartita.
- **Generar** la coocurrencia entre aperturas y construir los grafos correspondientes.
- **Calcular** las metricas correspondientes para cada red.
- **Detectar** comunidades y extraer métricas de las redes.

## Estructura del repositorio
- `notebooks/`
  - `pgn_parser.ipynb`: parseo de archivos PGN y generación del dataset.
  - `main.ipynb`: análisis exploratorio, modelado de la matriz bipartita, generación de la matriz de coocurrencia y construción de los grafos, métricas y comunidades.
- `data/`
  - `raw/`: colocar aquí los archivos `.pgn` originales (fuente de datos cruda).
  - `processed/`: salidas intermedias generadas por el parser.
- `requirements.txt`: dependencias del proyecto.
- `README.md`: este documento.

> Nota: si tu carpeta se llama `Data/` con mayúscula, usala de forma consistente (`Data/raw/`).

## Requisitos
- Python ≥ 3.12.5 
- Pip actualizado
- Jupyter Notebook o JupyterLab (incluido en `requirements.txt`)

## Instalación (Windows PowerShell)
```powershell
# Ubicarse en la carpeta del proyecto
# Crear y activar un entorno virtual
python -m venv .venv
.\.venv\Scripts\Activate.ps1
# Actualizar pip e instalar dependencias
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### Alternativa (Unix/macOS)
```bash
python -m venv .venv
source .venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt
```

## Datos de entrada
1. Descargá los archivos PGN de las partidas que quieras analizar.
2. Copiá los **primeros 3 meses de 2018** (por ejemplo: `2018-01.pgn`, `2018-02.pgn`, `2018-03.pgn`) dentro de `data/raw/`.

Estructura esperada:
```
Chess-opening-graph/
  data/
    raw/
      lichess_db_standard_rated_2018-01.pgn
      lichess_db_standard_rated_2018-02.pgn
      lichess_db_standard_rated_2018-03.pgn
```

## Ejecución del pipeline
1. Iniciar Jupyter:
   ```powershell
   jupyter lab
   # o
   jupyter notebook
   ```
2. Ejecutar `notebooks/pgn_parser.ipynb` de principio a fin:
   - Lee los `.pgn` desde `data/raw/`.
   - Genera un dataset tabular y lo guarda en `data/processed/` (formato/nombre definidos en el notebook).
3. Ejecutar `notebooks/main.ipynb`:
   - Construye la matriz bipartita jugador × apertura-color (`ECO_color`).
   - Obtiene la coocurrencia y el grafo de aperturas.
   - Calcula métricas, detecta comunidades y crea las figuras/tablas.

> Si cambiás rutas o nombres de archivos, actualizalos en las celdas de configuración de cada notebook.

## Resultados esperados
- Dataset procesado en `data/processed/` listo para análisis.
- Figuras y tablas generadas por `main.ipynb` (guardadas según la configuración del notebook).

## Reproducibilidad
- Usá la **misma versión** de dependencias (`requirements.txt`) y **el mismo conjunto de PGN** para obtener resultados comparables.
- Si el notebook establece semillas aleatorias, mantenelas fijas para replicar particiones/algoritmos estocásticos.

