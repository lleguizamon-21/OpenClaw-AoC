# 📋 Pre-requisitos del Sistema

Antes de ejecutar el script `docker-setup.sh`, es obligatorio tener configurado el entorno de Docker correctamente.

## 1. Instalación de Docker y Herramientas
Ejecuta estos comandos para instalar el motor de Docker y el soporte para scripts avanzados:


# Actualizar repositorios e instalar Docker y Buildx
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo apt install -y docker.io docker-buildx docker-compose-v2

## 2. Configuración de Permisos
Para que el script de OpenClaw pueda gestionar los contenedores, tu usuario debe pertenecer al grupo de Docker:

sudo usermod -aG docker $USER
# Aplicar cambios de grupo de inmediato
newgrp docker

## 3. Activación de BuildKit
El script oficial de OpenClaw utiliza funciones avanzadas de construcción (Step 20+). Es necesario activar **BuildKit**:

# Activar de forma permanente para el usuario
echo "export DOCKER_BUILDKIT=1" >> ~/.bashrc
source ~/.bashrc

# Configurar el demonio de Docker para usarlo por defecto
sudo mkdir -p /etc/docker
echo '{
  "features": {
    "buildkit": true
  }
}' | sudo tee /etc/docker/daemon.json

# Reiniciar Docker para aplicar cambios
sudo systemctl restart docker

## 4. Crear el Constructor (Builder)
Si el script falla al compilar, crea una instancia de construcción nueva:
docker buildx create --name openclaw_builder --use
docker buildx inspect --bootstrap


