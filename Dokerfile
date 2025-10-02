FROM ubuntu:16.04

# Evita prompts en instalación
ENV DEBIAN_FRONTEND=noninteractive

# Instalar dependencias básicas
RUN apt-get update && apt-get install -y \
    build-essential \
    wget \
    curl \
    gnupg \
    ca-certificates \
    && rm -rf /var/lib/apt/lists/*

# Agregar repo de CUDA 9.0
RUN wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/cuda-repo-ubuntu1604_9.0.176-1_amd64.deb && \
    dpkg -i cuda-repo-ubuntu1604_9.0.176-1_amd64.deb && \
    apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/7fa2af80.pub && \
    apt-get update && \
    apt-get install -y cuda-toolkit-9-0 && \
    rm -f cuda-repo-ubuntu1604_9.0.176-1_amd64.deb

# Variables de entorno de CUDA
ENV PATH=/usr/local/cuda-9.0/bin${PATH:+:${PATH}}
ENV LD_LIBRARY_PATH=/usr/local/cuda-9.0/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}

# Comando por defecto
CMD ["nvidia-smi"]