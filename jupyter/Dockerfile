FROM jupyter/pyspark-notebook:latest

# Instalar Language Server Protocol para autocompletado inteligente
RUN pip install --no-cache-dir \
    jupyterlab-lsp \
    python-lsp-server[all]

# Configurar JupyterLab: auto-cerrado de brackets + completado continuo
RUN mkdir -p /home/jovyan/.jupyter/lab/user-settings/@jupyterlab/completer-extension && \
    echo '{"showDocPanel": true, "continuousHinting": true}' > \
    /home/jovyan/.jupyter/lab/user-settings/@jupyterlab/completer-extension/plugin.jupyterlab-settings && \
    mkdir -p /home/jovyan/.jupyter/lab/user-settings/@jupyterlab/notebook-extension && \
    echo '{"codeCellConfig": {"autoClosingBrackets": true, "matchBrackets": true}}' > \
    /home/jovyan/.jupyter/lab/user-settings/@jupyterlab/notebook-extension/tracker.jupyterlab-settings && \
    mkdir -p /home/jovyan/.jupyter/lab/user-settings/@jupyterlab/fileeditor-extension && \
    echo '{"editorConfig": {"autoClosingBrackets": true, "matchBrackets": true}}' > \
    /home/jovyan/.jupyter/lab/user-settings/@jupyterlab/fileeditor-extension/plugin.jupyterlab-settings
