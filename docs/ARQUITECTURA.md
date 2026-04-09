# 🏛️ Arquitectura del Sistema
El bot opera como un puente entre la interfaz de usuario y los modelos de lenguaje (LLM).

## Diagrama de Flujo
- User --> Telegram
- Telegram --> OpenClaw Gateway
- OpenClaw --> Gemini 2.5 Flash
- Gemini --> Tools (Search/Maps)
- Resultado --> User
