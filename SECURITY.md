# Política de seguridad

## Credenciales

Este repositorio no debe contener:

- Claves de OpenAI.
- Tokens de bots de Telegram.
- Exportaciones de credenciales de n8n.
- Claves privadas o certificados.
- URL privadas que incorporen tokens.
- Capturas donde se vean secretos.

## Si una credencial se publica

1. Revócala inmediatamente en el servicio correspondiente.
2. Genera una credencial nueva.
3. Actualiza n8n.
4. Elimina el secreto del historial de Git.
5. Revisa las ejecuciones y el consumo de la cuenta.
6. No confíes únicamente en borrar el archivo del último commit.

## Comunicación de problemas

No publiques claves ni datos personales en una incidencia pública. Utiliza una alerta de seguridad privada del repositorio o contacta de forma privada con el responsable del proyecto.

## Alcance

Se agradecen avisos sobre:

- Credenciales visibles.
- Filtraciones en capturas o documentación.
- Ejecución no autorizada del bot.
- Posibles abusos que generen costes.
- Conservación innecesaria de fotografías.
