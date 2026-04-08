# OpenClaw en Windows con Docker, Telegram y Gemini

Esta guía está pensada para una instalación local en **Windows** usando **Git Bash** y **Docker Desktop**.

## Qué vas a lograr

Al terminar vas a poder:

- clonar el repositorio de OpenClaw
- levantar OpenClaw localmente con Docker
- conectar un bot de Telegram
- configurar Gemini 2.5 Flash con tu API key
- hablar con tu bot desde Telegram

## Ruta recomendada

1. Instala Docker Desktop y verifica que funcione.
2. Abre Git Bash y clona el repositorio.
3. Ejecuta el asistente Docker de OpenClaw.
4. Configura Gemini.
5. Configura Telegram.
6. Prueba el bot desde tu chat privado.

## Requisitos mínimos

- Windows 10/11 de 64 bits
- Git instalado
- Git Bash
- Docker Desktop funcionando
- una cuenta de Telegram
- una cuenta de Google para crear la API key de Gemini

## Instalación rápida

Abre **Git Bash** y ejecuta:

```bash
cd <ruta>/ubicacion_de_tu_carpeta #Seleciona una ubicación para clonar el repositorio.
git clone https://github.com/openclaw/openclaw.git
cd openclaw
bash ./docker-setup.sh
```

Durante el proceso, OpenClaw puede pedirte datos de configuración. Si prefieres hacerlo con más calma, sigue las guías de abajo.

## Orden sugerido de lectura

- [1. Docker para principiantes](./README_DOCKER_PRINCIPIANTES.md)
- [2. Clonar y preparar OpenClaw en Git Bash](./README_GITBASH_OPENCLAW.md)
- [3. Crear el bot de Telegram](./README_TELEGRAM_BOT.md)
- [4. Obtener la API key de Gemini 2.5 Flash](./README_GEMINI_API.md)

## Flujo corto recomendado

Cuando ya tengas Docker, Telegram y Gemini listos:

```bash
cd <ruta_de_tu_carpeta>/openclaw
bash ./docker-setup.sh
docker compose ps
```

Si el contenedor ya está levantado, puedes agregar Telegram manualmente con:

```bash
docker compose run --rm openclaw-cli channels add --channel telegram --token "TU_TOKEN_DE_BOT"
```

## Primeras comprobaciones

Verifica que Docker esté corriendo:

```bash
docker --version
docker compose version
docker info
```

Verifica que OpenClaw esté arriba:

```bash
docker compose ps
docker compose logs --tail=50 openclaw-gateway
```

## Si tu bot no responde

Revisa esto en orden:

1. Docker Desktop debe estar abierto.
2. El token del bot de Telegram debe ser correcto.
3. La API key de Gemini debe ser válida.
4. El contenedor debe aparecer como `Up` en `docker compose ps`.
5. Si OpenClaw te da un código de pairing, debes aprobarlo.

## Comando útil para pairing

Si Telegram te muestra un código de autorización:

```bash
docker compose run --rm openclaw-cli pairing approve telegram CODIGO
```

## Nota importante

No subas nunca a GitHub valores reales de:

- `GEMINI_API_KEY`
- `TELEGRAM_BOT_TOKEN`
- tokens de gateway

Guárdalos en `.env` o configúralos durante el onboarding.
