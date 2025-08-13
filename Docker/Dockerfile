FROM python:3.12-slim

ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1 \
    PYGAME_HIDE_SUPPORT_PROMPT=1 \
    SDL_VIDEODRIVER=dummy \
    MPLBACKEND=Agg \
    XDG_RUNTIME_DIR=/tmp

# deps del sistema para Box2D/ffmpeg/compilación
RUN apt-get update && apt-get install -y --no-install-recommends \
    swig ffmpeg build-essential \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app
COPY requirements.txt ./

# 1) PyTorch CPU desde el índice oficial
RUN pip install --no-cache-dir --index-url https://download.pytorch.org/whl/cpu torch==2.5.1

# 2) Resto de dependencias del proyecto
RUN pip install --no-cache-dir -r requirements.txt

COPY . .
CMD ["python", "main.py"]
