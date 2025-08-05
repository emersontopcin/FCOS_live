FROM pytorch/pytorch:1.8.1-cuda10.2-cudnn7-devel

# Adiciona a chave pública da NVIDIA para evitar erro de GPG
RUN apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/3bf863cc.pub

# Instala dependências básicas do sistema
RUN apt-get update && apt-get install -y \
    git \
    python3-dev \
    build-essential \
    gcc \
    g++ \
    libsm6 \
    libxext6 \
    libxrender-dev \
    wget \
    && rm -rf /var/lib/apt/lists/*

# Instala dependências Python extras
RUN pip install --upgrade pip && \
    pip install ipython ninja yacs cython matplotlib tqdm

# Clona e instala cocoapi
RUN git clone https://github.com/cocodataset/cocoapi.git /cocoapi && \
    cd /cocoapi/PythonAPI && \
    python3 setup.py build_ext install

# Clona e instala FCOS
RUN git clone https://github.com/emersontopcin/FCOS_live.git /FCOS_live && \
    cd /FCOS_live && \
    python3 setup.py build develop --no-deps

WORKDIR /FCOS_live

CMD ["bash"]