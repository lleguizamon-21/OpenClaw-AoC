# 🤖 Creación y Configuración del Bot de Telegram
Para que OpenClaw funcione, primero se debe configurar el bot en la infraestructura de Telegram:

## 1. Obtención del Token con @BotFather
1. Abre Telegram y busca al usuario **@BotFather** (el bot oficial de Telegram para crear otros bots).
2. Envía el comando `/newbot`.
3. Sigue las instrucciones:
   - Elige un **nombre** para tu bot (ej: "Mi Asistente Asunción").
   - Elige un **username** único que termine en "bot" (ej: `mi_asistente_py_bot`).
4. @BotFather te entregará un **HTTP API TOKEN**. Es el que usamos en el archivo `.env`.

## 2. Vinculación con OpenClaw
Una vez que tengas el token, asegúrate de que esté en tu configuración de Docker:

```bash
# Comando para verificar que el token está configurado
docker exec -it openclaw-bot-final npx openclaw config get channels.telegram.token
```

## 5. Proceso de Pairing (Seguridad)
Al enviar el primer mensaje al bot, este no responderá por seguridad. Deberás mirar los logs del servidor:
1. Ejecuta: `docker logs -f openclaw-bot-final`
2. Busca un código de 6 dígitos.
3. Ejecuta: `docker exec -it openclaw-bot-final npx openclaw pairing approve telegram [CODIGO]`
