# 💬 Comandos y Uso
# ==========================================================
# 🦞 BITÁCORA DE COMANDOS: PROYECTO OPENCLAW 2026
# ==========================================================

# ==========================================================
# 🛠️ COMANDOS POST-INSTALACIÓN (RECUPERACIÓN Y ACTIVACIÓN)
# ==========================================================

# 1. ACTUALIZACIÓN DEL CEREBRO (El script oficial traía el modelo 1.5 que daba error 404)
docker exec -it openclaw-bot-final npx openclaw config set model "google/gemini-2.5-flash"

# 2. RESET DE SESIÓN (Para que el bot olvide el error 404 y use el nuevo modelo)
docker exec -it openclaw-bot-final rm -rf /home/node/.openclaw/agents/main/sessions/sessions.json

# 3. SEGURIDAD (Aprobar el código que te mandó el bot a Telegram para que pueda hablar)
docker exec -it openclaw-bot-final npx openclaw pairing approve telegram [TU_CODIGO_AQUI]

# 4. APERTURA DE CANALES (El script oficial lo deja bloqueado por defecto)
docker exec -it openclaw-bot-final npx openclaw config set channels.telegram.allowFrom '["*"]'
docker exec -it openclaw-bot-final npx openclaw config set channels.telegram.dmPolicy "open"
docker exec -it openclaw-bot-final npx openclaw config set channels.telegram.groupPolicy "open"

# 5. ACTIVACIÓN DE HERRAMIENTAS (El script oficial no activa el buscador web por defecto)
docker exec -it openclaw-bot-final npx openclaw config set tools.profile "messaging"

# 6. INSTALACIÓN DE MAPAS (Para la PoC de las milanesas)
docker exec -it openclaw-bot-final npx playbooks add skill openclaw/skills --skill google-maps

# 7. PERMISOS DE HERRAMIENTAS (Para que el bot reconozca los plugins nuevos)
docker exec -it openclaw-bot-final npx openclaw config set tools.alsoAllow '["web_search", "browser", "google_maps"]'

# 8. IDIOMA (Para que deje de contestar en inglés)
docker exec -it openclaw-bot-final npx openclaw config set agents.defaults.instructions "Responde siempre en español de Paraguay."  
También se le puede indicar por  el chat pero existe la posibilidad  de que  lo recuerde por menos  tiempo

# 9. REINICIO FINAL (Para "soldar" todos estos cambios manuales)
docker restart openclaw-bot-final


# Comandos Gestión y Control

Esta sección detalla los comandos necesarios para operar, monitorear y mantener el bot en funcionamiento.

## 📊 Monitoreo y Diagnóstico

Para saber qué está pasando "en la cabeza" de la IA y verificar la conexión.

`docker logs -f openclaw-bot-final` **Logs en tiempo real:**
Ver qué mensajes llegan y qué está pensando el bot.

`docker exec -it openclaw-bot-final npx openclaw status` **Estado rápido:**
Verifica si los canales (Telegram) están conectados.

`docker exec -it openclaw-bot-final npx openclaw status --deep`  **Diagnóstico profundo:** 
Muestra qué herramientas (Maps, Search) están activas. 

## 🕹️ Control del Contenedor (Docker)

Para detener, iniciar o aplicar cambios físicos en el sistema.

`docker restart openclaw-bot-final` **Reiniciar:** 
Útil tras cambiar configuraciones o si el bot se queda "colgado".

`docker stop openclaw-bot-final` **Detener:** 
Apaga el bot por completo.

`docker start openclaw-bot-final`**Encender:** 
Inicia el bot si está detenido.

`docker stats openclaw-bot-final` **Recursos:** 
Ver cuánto consumo de RAM y CPU tiene el bot. 

## 🛠️ Comandos de Configuración (OpenClaw CLI)

Comandos internos para modificar el comportamiento sin editar archivos JSON.

`docker exec -it openclaw-bot-final npx openclaw config get`
Ver la configuración completa actual.

`docker exec -it openclaw-bot-final npx openclaw pairing list`
Ver solicitudes de emparejamiento de Telegram pendientes.

`docker exec -it openclaw-bot-final npx openclaw configure`
Abre un asistente interactivo para cambiar modelos o llaves API.


## 🧹 Limpieza de Emergencia

Si el bot empieza a responder cosas raras o da errores de "contexto".

# Borrar la sesión actual (Reset de memoria inmediata)

docker exec -it openclaw-bot-final rm -rf /home/node/.openclaw/agents/main/sessions/sessions.json && docker restart openclaw-bot-final


