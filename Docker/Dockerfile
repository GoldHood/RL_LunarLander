FROM pytorch/pytorch

USER root

# ============= Actualizar contenedor =============
COPY requirements.txt /requirements.txt
RUN pip install --no-cache-dir -r /requirements.txt

CMD ["jupyter", "lab", "--ip=0.0.0.0", "--allow-root", "--NotebookApp.disable_check_xsrf=True", "--NotebookApp.token=''", "--NotebookApp.password=''", "--NotebookApp.allow_origin='*'", "--NotebookApp.notebook_dir=/"]
