# Clonar y preparar OpenClaw en Git Bash

Esta parte explica cómo trabajar con el repositorio localmente desde **Git Bash**.

## 1. Abrir Git Bash

Busca `Git Bash` en el menú de Windows y ábrelo.

## 2. Ir a la carpeta donde quieres guardar el proyecto

Ejemplo:

```bash
cd /c/Users/HP/Documents
```

Puedes usar cualquier carpeta que prefieras.

## 3. Clonar el repositorio

```bash
git clone https://github.com/openclaw/openclaw.git
cd openclaw
```

## 4. Confirmar que estás dentro del proyecto

```bash
pwd
ls
```

Deberías ver archivos como:

- `docker-setup.sh`
- `docker-compose.yml`
- `.env.example`

## 5. Crear tu archivo `.env`

Si quieres tener un archivo local base:

```bash
cp .env.example .env
```

Luego puedes editarlo con un editor de texto.

## 6. Configuración mínima sugerida en `.env`

Como mínimo, más adelante te servirán estas variables:

```env
GEMINI_API_KEY=PEGA_AQUI_TU_API_KEY
TELEGRAM_BOT_TOKEN=PEGA_AQUI_TU_TOKEN
OPENCLAW_GATEWAY_TOKEN=crea_un_token_largo_y_dificil
```

## 7. Levantar OpenClaw con Docker

La forma más simple es:

```bash
bash ./docker-setup.sh
```

Si todo sale bien, el script:

- prepara la configuración
- construye o usa la imagen
- levanta los contenedores
- deja listo el gateway

## 8. Verificar que OpenClaw arrancó

```bash
docker compose ps
docker compose logs --tail=50 openclaw-gateway
```

## 9. Abrir el panel local

Si necesitas la dirección del panel:

```bash
docker compose run --rm openclaw-cli dashboard --no-open
```

Normalmente el gateway queda disponible en:

```text
http://127.0.0.1:18789/
```

## 10. Comandos que usarás seguido

```bash
docker compose ps
docker compose up -d
docker compose down
docker compose logs -f openclaw-gateway
docker compose run --rm openclaw-cli pairing list telegram
docker compose run --rm openclaw-cli pairing approve telegram CODIGO
```
