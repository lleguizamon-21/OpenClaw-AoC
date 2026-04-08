# Cómo crear y conectar tu bot de Telegram

## 1. Crear el bot con BotFather

Desde Telegram:

1. busca `@BotFather`
2. abre el chat oficial
3. escribe `/newbot`
4. elige un nombre para tu bot
5. elige un username que termine en `bot`

Ejemplo:

- nombre: `Mi Asistente OpenClaw`
- username: `mi_asistente_openclaw_bot`

Al final, BotFather te entregará un **token**.

## 2. Guardar el token

Ese token se ve parecido a esto:

```text
123456789:AAExampleToken
```

Guárdalo como si fuera una contraseña.

## 3. Dónde poner el token

Tienes dos formas simples.

### Opción A: en `.env`

```env
TELEGRAM_BOT_TOKEN=TU_TOKEN_REAL
```

### Opción B: con comando dentro de OpenClaw

```bash
docker compose run --rm openclaw-cli channels add --channel telegram --token "TU_TOKEN_REAL"
```

## 4. Probar que el canal quedó configurado

```bash
docker compose run --rm openclaw-cli channels status --probe
```

## 5. Hablarle al bot

Después de configurarlo:

1. abre Telegram
2. busca tu bot por el username
3. presiona `/Start`
4. envíale un mensaje simple como `hola`

## 6. Si aparece un código de pairing

Eso significa que OpenClaw está pidiendo tu aprobación como usuaria autorizada.

Primero lista las solicitudes:

```bash
docker compose run --rm openclaw-cli pairing list telegram
```

Luego aprueba el código:

```bash
docker compose run --rm openclaw-cli pairing approve telegram CODIGO
```

## 7. Problemas comunes

### El bot aparece, pero no responde

Revisa:

- que el token sea correcto
- que el contenedor esté arriba
- que Gemini también esté configurado

### BotFather dice que el username no sirve

El username:

- debe ser único
- debe terminar en `bot`
- solo puede usar letras, números y `_`

## 8. Recomendación práctica

Primero prueba el bot en un chat privado contigo mismo.  
Después, si todo funciona, recién agrégalo a grupos.

## Fuentes oficiales

- https://core.telegram.org/bots
- https://core.telegram.org/bots/features
- https://core.telegram.org/bots/tutorial
