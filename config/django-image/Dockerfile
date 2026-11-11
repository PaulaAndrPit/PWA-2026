# Imagen base solicitada por la consigna
FROM python:3.12.2-bookworm

# Instalamos dependencias del sistema
RUN apt-get update && apt-get install -y \
    python3-dev \
    graphviz-dev \
    && rm -rf /var/lib/apt/lists/*

# Directorio de trabajo dentro del contenedor
WORKDIR /usr/src/app

# Actualizamos las herramientas de Python
RUN pip install --upgrade pip && pip install --upgrade setuptools

# Copiamos el archivo de dependencias
COPY requirements.txt ./

# Instalamos las dependencias de Python
RUN pip install --no-cache-dir -r requirements.txt

# Exponemos el puerto de Django
EXPOSE 8000

# Creamos la carpeta para los scripts
RUN mkdir -p /scripts

# Copiamos el script de inicio
COPY runserver.sh /scripts/runserver.sh

# Damos permisos de ejecución
RUN chmod +x /scripts/runserver.sh

# Ejecutamos el script al iniciar el contenedor
CMD ["/scripts/runserver.sh"]