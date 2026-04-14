# QUICKSTART TELEGRAM — OpenClaw

Guía mínima para levantar OpenClaw y tener el bot de Telegram funcionando.

---

## 1. Instalar Docker

👉 https://docs.docker.com/engine/install/

---

## 2. Clonar repositorio

```bash
git clone https://github.com/openclaw/openclaw.git
cd openclaw
```
---

## 3. Levantar el sistema

```bash
bash ./docker-setup.sh
```
👉 Durante este proceso, el sistema te pedirá:

- TELEGRAM_BOT_TOKEN
- GEMINI_API_KEY

Ingresa los valores cuando te los solicite
---

## 4. Comandos post-instalación

```bash
docker ps
docker logs openclaw-bot-final
docker exec -it openclaw-bot-final bash
exit
```

---

## 5. Pairing (autorización)

Aprobar:

```bash
docker exec -it openclaw-bot-final npx openclaw pairing approve telegram CODIGO
```

(Reemplazar `CODIGO` por el código mostrado en el chat con el bot de telegram si ya se inició la conversación o en los logs)

---

## 6. Verificación

Ir a Telegram y enviar:

```
hola
```

Si el bot responde, el sistema está funcionando ✅

---

## Notas

* Este flujo es el mínimo necesario
* La documentación completa está en otros archivos del proyecto, incluyendo la guia para crear el bot de telegram y obtener la API key de Gemini
* Si algo falla, revisar logs del contenedor

---
