# Cómo obtener la API key de Gemini 2.5 Flash

## 1. Entrar a Google AI Studio

Abre:

- https://aistudio.google.com/

## 2. Iniciar sesión con tu cuenta de Google

Usa la cuenta con la que vas a trabajar tu proyecto.

## 3. Crear o elegir un proyecto

Dentro de Google AI Studio:

1. entra a la sección de proyectos si te la solicita
2. importa o selecciona un proyecto de Google Cloud
3. ve a la sección de API keys

## 4. Crear la API key

En la página de claves:

1. crea una nueva clave
2. copia la clave generada
3. guárdala en un lugar seguro

## 5. Agregarla a OpenClaw

La forma más simple es ponerla en `.env`:

```env
GEMINI_API_KEY=TU_API_KEY_REAL
```

OpenClaw también reconoce `GOOGLE_API_KEY`, pero lo más claro es usar `GEMINI_API_KEY`.

## 6. Usar Gemini como modelo principal

Si haces la configuración desde el asistente Docker u onboarding, selecciona:

- provider: `google`
- model: `gemini-2.5-flash`

## 7. Advertencia importante

Gemini 2.5 Flash **free tier** tiene límites de uso.  
Si tu bot conversa mucho, puedes recibir errores `429` por cuota.

Si más adelante quieres reducir ese cuello de botella, tienes tres caminos:

- pasar a un plan con billing
- cambiar de provider
- usar un modelo local

## 8. Recomendación de seguridad

No pegues la API key:

- en commits
- en capturas de pantalla
- en archivos que vayan a GitHub

## Fuentes oficiales

- https://ai.google.dev/gemini-api/docs/api-key?hl=es-419
- https://ai.google.dev/gemini-api/docs/quickstart
