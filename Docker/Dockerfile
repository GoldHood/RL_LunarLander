FROM python:3.12-slim

ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1 \
    PYGAME_HIDE_SUPPORT_PROMPT=1 \
    SDL_VIDEODRIVER=dummy \
    MPLBACKEND=Agg \
    XDG_RUNTIME_DIR=/tmp

# Dependencias del sistema necesarias para box2d/ffmpeg/compilación
RUN apt-get update && apt-get install -y --no-install-recommends \
    swig ffmpeg build-essential \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app
COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

# (Opcional: si vas a correr notebooks dentro del contenedor, añade jupyterlab)
# RUN pip install --no-cache-dir jupyterlab ipykernel

COPY . .
# Cambia el CMD según tu entrypoint real
CMD ["python", "main.py"]
