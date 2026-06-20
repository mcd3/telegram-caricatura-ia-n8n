# Publicar el proyecto en GitHub

## Datos recomendados

**Nombre del repositorio**

```text
telegram-caricatura-ia-n8n
```

**Descripción**

```text
Workflow de n8n que recibe una foto por Telegram, genera una caricatura con OpenAI y devuelve el resultado al mismo chat.
```

**Topics**

```text
n8n
telegram-bot
openai
gpt-image
image-generation
automation
ai
caricature
workflow
no-code
```

## Opción A: desde la web de GitHub

1. Crea un repositorio nuevo.
2. Usa el nombre `telegram-caricatura-ia-n8n`.
3. Elige visibilidad pública.
4. No marques la creación automática de README, licencia o `.gitignore`, porque ya están incluidos.
5. Descomprime el ZIP de este proyecto.
6. Sube todo el contenido de la carpeta, no la carpeta contenedora.
7. Confirma los archivos.
8. Añade la descripción y los topics.

## Opción B: mediante Git

Desde la carpeta del proyecto:

```bash
git init
git add .
git commit -m "Publica workflow de caricaturas por Telegram"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/telegram-caricatura-ia-n8n.git
git push -u origin main
```

## Antes de publicar

Ejecuta estas comprobaciones:

```bash
git grep -n "sk-"
git grep -n "Bearer sk-"
git grep -n "api.telegram.org/bot"
git grep -n "YOUR_OPENAI_API_KEY"
```

Los tres primeros comandos no deben devolver secretos. El último sí debe encontrar únicamente el marcador genérico dentro del workflow o la documentación.

Comprueba también visualmente las capturas para asegurarte de que no muestran pestañas, barras de direcciones, tokens, IP privadas o credenciales.

## Crear la primera versión

Después de publicar:

1. Abre **Releases**.
2. Selecciona **Draft a new release**.
3. Crea la etiqueta `v1.0.0`.
4. Título: `Primera versión compartible`.
5. Indica que el JSON no contiene credenciales reales.
6. Publica la versión.
