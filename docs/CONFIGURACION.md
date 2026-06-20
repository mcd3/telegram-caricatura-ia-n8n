# Configuración detallada

## 1. Importación del workflow

El archivo que debes importar es:

```text
workflow/Telegram_Caricatura_IA_sin_credenciales.json
```

La importación crea los siguientes nodos:

1. `Telegram Trigger`
2. `¿Hay imagen?`
3. `Trabajando`
4. `Crear caricatura con OpenAI`
5. `Base64 a imagen`
6. `Devolver caricatura`
7. `Pedir una imagen`

## 2. Credencial de Telegram

Crea una credencial de tipo **Telegram API** e introduce el token generado por `@BotFather`.

Asigna esa credencial manualmente a todos los nodos de Telegram. El archivo contiene nombres e identificadores ficticios para evitar compartir los originales.

## 3. Clave de OpenAI

En el nodo `Crear caricatura con OpenAI`, abre:

```text
Headers → Authorization
```

Sustituye:

```text
Bearer YOUR_OPENAI_API_KEY
```

por la clave real.

No escribas la clave en una copia que vayas a subir a GitHub.

## 4. Entrada binaria

El nodo `Telegram Trigger` descarga la imagen recibida y la expone en:

```text
$binary.data
```

El nodo `¿Hay imagen?` comprueba que esa propiedad exista.

El nodo HTTP envía el archivo mediante `multipart/form-data` con:

```text
Campo: image
Binary property: data
```

## 5. Petición de imagen

La petición utiliza:

```text
POST https://api.openai.com/v1/images/edits
```

Campos enviados:

```text
image         → archivo binario de Telegram
model         → gpt-image-1.5
size          → 1024x1536
quality       → medium
output_format → png
prompt        → instrucciones de la caricatura
```

## 6. Conversión de la respuesta

OpenAI devuelve la imagen codificada en Base64 dentro de:

```text
data[0].b64_json
```

El nodo `Base64 a imagen` crea un binario de n8n con:

```text
mimeType: image/png
fileName: caricatura.png
```

## 7. Respuesta a Telegram

El nodo `Devolver caricatura` envía el binario al mismo `chat.id` que originó la ejecución:

```text
$('Telegram Trigger').item.json.message.chat.id
```

## 8. Publicación y pruebas

Para producción:

1. Guarda el workflow.
2. Comprueba que el webhook es público y HTTPS.
3. Activa el workflow.
4. Envía una imagen al bot.

Para pruebas, evita utilizar simultáneamente el mismo bot en una URL de prueba y en producción, porque Telegram solo mantiene un webhook activo por bot.

## 9. Recomendaciones de producción

- Utiliza una credencial de n8n para el encabezado de OpenAI.
- Limita el acceso por `Chat ID` o `User ID` si el bot no será público.
- Configura límites de gasto en OpenAI.
- Evita guardar ejecuciones correctas si contienen fotografías personales.
- Activa el borrado periódico de ejecuciones antiguas.
- Usa un bot independiente para desarrollo.
- Añade manejo de errores y un mensaje de fallo antes de abrir el servicio al público.
