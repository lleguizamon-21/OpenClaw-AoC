# 🦞 OpenClaw Telegram Bot (Asunción 2026)

Asistente inteligente autónomo basado en **OpenClaw v2026.3.8** y **Google Gemini 2.5 Flash**. Diseñado para navegación web, geolocalización y asistencia gastronómica local.

## ✨ Funciones principales
- 🧠 **Cerebro Gemini 2.5 Flash**: Respuestas rápidas y precisas.
- 🌐 **Web Search**: Capacidad de buscar datos reales en internet (PoC: Milanesas en Asunción).
- 📍 **Maps & Skills**: Integración con Google Maps para ubicar locales y generar rutas.
- 🇵🇾 **Contexto Local**: Configurado para entender y asistir en Paraguay.

## 🏗️ Arquitectura
**Docker** + **OpenClaw Gateway** + **Telegram API** + **Google AI (Gemini)**.

## 🚀 Instalación rápida
1. **Clonar y entrar:**
   `git clone https://github.com/openclaw/openclaw`
   `cd openclaw-bot`
2. **Configurar entorno:** Crea un archivo `.env` basado en el `.env.example`.
3. **Levantar con Docker, Ejecutar el scrip:**
   `docker-setup.sh`
El script docker-setup.sh que encontrás en el repositorio oficial de OpenClaw es básicamente el "cerebro instalador" que automatiza todo, pero de una manera estructurada para que cualquier usuario pueda empezar desde cero.

Realiza:

1. Verificación del Entorno
Antes de tocar nada, el script revisa si tu sistema tiene lo mínimo indispensable para correr:

Chequea si Docker y Docker Compose están instalados y funcionando.

Verifica los permisos del usuario.

2. Creación de la Estructura de Carpetas
El script crea el directorio de trabajo (normalmente ~/.openclaw) donde se guardarán:

Configuraciones: El archivo openclaw.json.

Sesiones: La memoria de tus chats.

Skills: Los plugins (como el de Maps que instalamos).

3. Configuración Interactiva (El Asistente)
Aquí es donde te pide:

Tu API Key de Google (Gemini) o Anthropic.
Para generar la API Key de Gemini accede a: https://aistudio.google.com/app/api-keys?project=gen-lang-client-0829857863 y luego crear clave  de API

El modelo que querés usar (aunque por defecto suele traer uno viejo, yo utlicé el 2.5 Flash de  Gemini).

Tu Token de Telegram (o de otros canales como Slack o Discord).
Para  el Token  de  Telegram se encuentra  toda la  información necesaria en el archivo telegram_setup.md 

4. Generación del archivo docker-compose.yml
En lugar de que vos lo escribas, el script detecta tu sistema operativo y arquitectura genera un archivo docker-compose.yml optimizado para vos.

5. El "Pull" de la Imagen y el "Start"
Finalmente, el script ejecuta:

docker compose pull: Baja la última versión de la imagen de OpenClaw.

docker compose up -d: Levanta el contenedor en segundo plano.

6. Inicialización del Gateway
Una vez que el contenedor está arriba, el script lanza los procesos internos para que el "Gateway" de OpenClaw empiece a escuchar los mensajes de Telegram.

Todo esto lo realiza dentro de un Docker

4. **Aprobar Pairing:**
   `docker exec -it openclaw-bot npx openclaw pairing approve telegram [CODIGO]`

----------------------------------------------------------------------------
###En el archivo comandos.md se especifican los comandos que se ejecutan ###para  continuar con la integración de OpenClaw