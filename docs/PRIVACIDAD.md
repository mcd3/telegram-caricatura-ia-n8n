# Privacidad y tratamiento de imágenes

Este proyecto procesa fotografías de personas. Antes de abrir el bot al público, define una política clara.

## Servicios que intervienen

Una imagen enviada al bot puede pasar por:

1. Telegram.
2. La instancia de n8n del operador.
3. La API de OpenAI.
4. El chat de Telegram al que se devuelve el resultado.

Cada servicio tiene sus propios términos y políticas.

## Consentimiento

No envíes fotografías de otras personas sin autorización. Si el bot se utiliza en un evento, grupo de amigos o actividad pública, informa de forma visible sobre el tratamiento de las imágenes.

## Historial de n8n

n8n puede guardar datos de las ejecuciones, incluyendo archivos binarios, según la configuración de la instancia.

Para reducir la exposición:

```text
EXECUTIONS_DATA_SAVE_ON_SUCCESS=none
EXECUTIONS_DATA_SAVE_ON_PROGRESS=false
EXECUTIONS_DATA_SAVE_MANUAL_EXECUTIONS=false
EXECUTIONS_DATA_PRUNE=true
```

Ajusta el tiempo de conservación conforme a tus necesidades y obligaciones.

## Bot público

Antes de convertirlo en un servicio público:

- Añade condiciones de uso.
- Limita el tamaño y frecuencia de las peticiones.
- Implementa control de errores.
- Establece un presupuesto máximo.
- Evita almacenar innecesariamente fotografías.
- Define un canal para solicitar la eliminación de datos.
- Valora restringir el bot por identificadores de usuario o chat.

Este documento es una guía técnica y no sustituye asesoramiento jurídico.
