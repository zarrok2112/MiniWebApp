# Utilizar una imagen base oficial de Python
FROM python:3.8-slim

# Establecer el directorio de trabajo en el contenedor
WORKDIR /app

# Instalar dependencias del sistema
RUN apt-get update && apt-get install -y \
    python3-dev \
    default-libmysqlclient-dev \
    build-essential \
    pkg-config \
    default-mysql-client \
    gcc \
    && apt-get clean

# Copiar el archivo de requerimientos
COPY requirements.txt requirements.txt

# Instalar las dependencias de Python
RUN pip install --no-cache-dir -r requirements.txt

# Copiar el contenido de la aplicación en el directorio de trabajo
COPY . .

# Establecer la variable de entorno para Flask
ENV FLASK_APP=run.py

# Exponer el puerto que utiliza Flask
EXPOSE 5000

# Comando por defecto para ejecutar la aplicación
CMD ["flask", "run", "--host=0.0.0.0"]
