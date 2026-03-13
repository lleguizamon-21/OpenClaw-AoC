# 📊 Análisis, Lecciones Aprendidas y Mejoras

Este documento resume la experiencia técnica tras la implementación de la PoC y las recomendaciones para el futuro del proyecto.

## 🧠 Lecciones Aprendidas
1. **Sensibilidad del Modelo**: El cambio de Gemini 1.5 a 2.5 Flash fue crítico. Los modelos más nuevos en 2026 gestionan mucho mejor las llamadas a herramientas externas (Tools).
2. **Persistencia de Sesión**: Se aprendió que al cambiar configuraciones profundas del sistema, es obligatorio borrar el archivo `sessions.json` para que el agente "despierte" con los nuevos parámetros.
3. **Sandbox vs Skills**: Los Skills externos (como Google Maps) requieren que el nivel de Sandbox del agente sea ajustado (`off`) para que el bot pueda leer los archivos fuera de su raíz.

## ⚠️ Limitaciones Observadas
- **Español Paraguayo (Jopara)**: El bot es excelente en español neutro, pero la interpretación del "Jopara" o regionalismos muy específicos de Paraguay es algo imprecisa. Tiende a ser muy formal.
- **Rate Limiting**: Al usar la versión gratuita de la API, las búsquedas web intensas (browsing) pueden causar bloqueos temporales por saturación de pedidos.
- **Traducción**: A veces el bot intenta traducir nombres de locales que deberían quedar en su nombre original.

## 🚀 Recomendaciones de Escalabilidad

### 📱 Canales
- **WhatsApp**: **NO SE RECOMIENDA**. El  proceso de aprobación de Meta para bots autónomos con navegación web es muy riguroso y el agente en algunos casos realiza acciones para las cuales  no se le  dio autorización como por ejemplo responder mensajes de texto, si se quiere configurar con WhatsApp se recomienda no hacerlo con tu número personal.
- **Google Chat**: **ALTAMENTE RECOMENDADO**. Es el entorno ideal para escalar en empresas. Su integración con Gemini es nativa y más estable, aunque la configuración inicial de Google Cloud es más compleja que la de Telegram.
- **Telegram/Slack**: Excelentes para uso técnico, equipos internos y prototipado rápido.

### 🛠️ Mejoras Sugeridas (Roadmap)
1. **Skill de TripAdvisor**: Para complementar los datos de Google Maps con reseñas reales de comensales.
2. **Personalidad Local**: Refinar el `System Prompt` con un glosario de términos paraguayos para que el bot suene más cercano
3. **Integración RAG**: Permitir que el bot lea archivos PDF de menús actualizados de restaurantes de Asunción para dar precios exactos sin navegar.

