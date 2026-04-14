# 🚀 OpenClaw-AoC 

---

# 📌 Requisitos

* Docker instalado
* Git instalado
* Cuenta de Telegram (bot token)
* API Key de Gemini

---

# 🐧 LINUX — Instalación rápida

## 1. Clonar repositorio

```bash
git clone https://github.com/openclaw/openclaw.git
cd openclaw
```

---

## 2. Crear variables de entorno

```bash
cp .env.example .env
```

Editar `.env`:

```env
GEMINI_API_KEY=tu_api_key
TELEGRAM_BOT_TOKEN=tu_token
OPENCLAW_GATEWAY_TOKEN=token_seguro
```

---

## 3. Levantar sistema

```bash
bash ./docker-setup.sh
```

---

## 4. Verificar

```bash
docker compose ps
docker compose logs -f openclaw-gateway
```

---

## 5. Pairing Telegram

```bash
docker exec -it openclaw-bot-final npx openclaw pairing approve telegram CODIGO
```

---

## 6. Probar

Enviar mensaje en Telegram:

```
hola
```

---

---

# 🪟 WINDOWS 

📋 Requisitos

Windows 10/11 (64 bits)
Git Bash
Docker Desktop


## 1. Abrir Git Bash

---

## 2. Ir a carpeta de trabajo

```bash
cd /c/Users/EJEMPLO
```

---

## 3. Clonar repositorio

```bash
git clone https://github.com/openclaw/openclaw.git
cd openclaw
```

---

## 4. Crear `.env`

```bash
cp .env.example .env
```

Editar:

```env
GEMINI_API_KEY=tu_api_key
TELEGRAM_BOT_TOKEN=tu_token
OPENCLAW_GATEWAY_TOKEN=token_seguro
```

---

## 5. Levantar sistema

```bash
bash ./docker-setup.sh
```

---

## 6. Verificar

```bash
docker compose ps
docker compose logs -f openclaw-gateway
```

---

## 7. Pairing Telegram

```bash
docker exec -it openclaw-bot-final npx openclaw pairing approve telegram CODIGO
```

---

## 8. Probar

Enviar:

```
hola
```

---

# ⚡ COMANDOS ÚTILES

```bash
docker compose up -d
docker compose down
docker compose ps
docker compose logs -f openclaw-gateway
```

---

# 📌 NOTAS

* Este README es solo flujo mínimo funcional
* La arquitectura y documentación avanzada están en `/docs`
* Usar Docker siempre recomendado

---
