FROM python:3.12-slim

ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1 \
    PYGAME_HIDE_SUPPORT_PROMPT=1 \
    SDL_VIDEODRIVER=dummy \
    MPLBACKEND=Agg \
    XDG_RUNTIME_DIR=/tmp

# deps del sistema
RUN apt-get update && apt-get install -y --no-install-recommends \
    swig ffmpeg build-essential \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

# PyTorch CPU primero
RUN pip install --no-cache-dir --index-url https://download.pytorch.org/whl/cpu torch==2.5.1

# Dependencias del proyecto
COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

# 👇 Instala jupyterlab/ipykernel dentro de la imagen (no en runtime)
RUN pip install --no-cache-dir jupyterlab ipykernel

COPY . .

# Deja el CMD vacío; lo define docker-compose
