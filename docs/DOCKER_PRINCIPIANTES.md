# Docker para principiantes en Windows

Esta guía te ayuda a instalar Docker Desktop y dejarlo listo para OpenClaw.

## 1. Instalar Docker Desktop

Descarga Docker Desktop desde su web oficial:

- https://docs.docker.com/desktop/setup/install/windows-install/

## 2. Qué debes marcar durante la instalación

Cuando abras el instalador:

- usa la opción con **WSL 2**
- acepta los permisos de administrador si Windows los solicita
- reinicia la PC si el instalador lo pide

## 3. Abrir Docker Desktop por primera vez

Después de instalar:

1. abre `Docker Desktop`
2. acepta los términos
3. espera hasta que diga que Docker está corriendo

Si ves errores de virtualización, normalmente faltan una de estas cosas:

- WSL 2 no está instalado correctamente
- la virtualización está desactivada en BIOS/UEFI

## 4. Cómo comprobar que funciona

Abre **Git Bash** y ejecuta:

```bash
docker --version
docker compose version
docker info
```

Si el último comando muestra información del sistema, Docker ya está listo.

## 5. Prueba rápida con un contenedor

```bash
docker run hello-world
```

Si aparece el mensaje de bienvenida, la instalación está bien.

## 6. Problemas comunes

### `docker: command not found`

Cierra Git Bash y ábrelo otra vez.

### Docker Desktop no inicia

- reinicia Windows
- abre Docker Desktop como administrador
- verifica que WSL esté activo

### Error por virtualización

Entra al BIOS/UEFI y habilita:

- Intel VT-x
- AMD-V
- Virtualization Technology

El nombre cambia según la placa madre.

## 7. Qué usarás luego con OpenClaw

Los comandos más importantes serán estos:

```bash
docker compose ps
docker compose logs --tail=50 openclaw-gateway
docker compose run --rm openclaw-cli dashboard --no-open
```
