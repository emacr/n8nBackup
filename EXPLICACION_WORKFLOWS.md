# 🚀 Proyectos destacados de Automatización (n8n)

¡Hola! 👋 Aquí tienes un resumen visual y atractivo de algunos proyectos relevantes que he desarrollado usando **n8n**, integrando APIs, IA y automatizaciones que optimizan procesos reales. Este README está pensado para que lo pegues en tu `README.md` de GitHub — ya viene con estructura, emojis y formato Markdown listo para usar.

---

## 📚 Índice

1. [Agente de Ventas IA Multicanal (ferretariacompras)](#1-agente-de-ventas-ia-multicanal-ferretariacompras)
2. [Automatización de Búsqueda de Proveedores (busquedaProveedores)](#2-automatización-de-búsqueda-de-proveedores-busquedaproveedores)
3. [Notificaciones y Reportes de Inventario (notificacionStockBajo)](#3-sistema-de-notificaciones-y-reportes-de-inventario-notificacionstockbajo)
4. [Respaldo Automático de Workflows a GitHub (respaldoGithub)](#4-respaldo-automático-de-workflows-a-github-respaldogithub)

---

# 1. Agente de Ventas IA Multicanal — `ferretariacompras` 🛠️🤖

**Descripción corta:**
Asistente virtual que gestiona el ciclo completo de ventas y soporte por **WhatsApp** y **Telegram**, con capacidades multimodales (texto, audio, imagen).

**Funcionalidades clave:**

* 🔁 **Multicanal & Multimodal**: Texto, notas de voz (transcripción con *Whisper*), y análisis de imágenes con *GPT-4o*.
* 🧠 **Agente inteligente (LangChain)**: Decide qué herramienta usar según la petición del cliente.
* 📚 **Base de conocimiento (RAG)**: Respuestas precisas sobre garantías y devoluciones consultando Pinecone.
* 📦 **Inventario en tiempo real**: Conexión a Airtable para consultar y actualizar stock.
* 🧾 **Memoria conversacional**: Historial en PostgreSQL para contexto y personalización.
* 📊 **Reportes visuales**: Lectura de Google Sheets + generación de gráficos con QuickChart y envío al usuario.

**Stack técnico destacado:**

```
LangChain · OpenAI (GPT-4o, Whisper) · Airtable · Pinecone · PostgreSQL · Google Sheets · WhatsApp · Telegram · QuickChart
```

---

# 2. Automatización de Búsqueda de Proveedores — `busquedaProveedores` 🕵️‍♂️📋

**Descripción corta:**
Bot de WhatsApp que automatiza la búsqueda y enriquecimiento de la base de datos de proveedores.

**Funcionalidades clave:**

* 🧩 **Clasificador de intención (IA)**: Determina si el usuario quiere consultar o buscar nuevos proveedores.
* 📄 **Consulta en tiempo real**: Lee y devuelve datos desde Google Sheets.
* 🌐 **Extracción y scraping**: Si se solicita búsqueda, extrae ubicación y cantidad; usa API (Apify/Google Places) para obtener negocios.
* 🔁 **Enriquecimiento automático**: Filtra y sube resultados a Google Sheets manteniendo la DB centralizada.

**Stack técnico destacado:**

```
WhatsApp · LangChain (Text Classifier, Extractor) · Google Sheets · HTTP Requests (Apify)
```

---

# 3. Sistema de Notificaciones y Reportes de Inventario — `notificacionStockBajo` 📉🔔

**Descripción corta:**
Workflow proactivo que monitorea stock en Airtable, genera alertas y reportes visuales distribuidos por Slack, Telegram y Gmail.

**Funcionalidades clave:**

* 👀 **Monitoreo de stock**: Trigger desde Slack que revisa inventario en Airtable.
* ⚠️ **Alertas inteligentes**: Agrupa productos con stock bajo y notifica en Slack.
* 🗂️ **Registro histórico**: Guarda entradas en Google Sheets para seguimiento.
* 🔢 **Procesamiento (Code Node)**: JS para generar listados de top10 (mayor/menor stock).
* 📈 **Gráficos automáticos**: QuickChart genera barras que se envían por Telegram y Gmail.

**Stack técnico destacado:**

```
Airtable · Slack · Google Sheets · Telegram · Gmail · JavaScript (Code Node) · QuickChart
```

---

# 4. Respaldo Automático de Workflows a GitHub — `respaldoGithub` 💾🔁

**Descripción corta:**
Meta-workflow para respaldar los workflows de n8n en un repo de GitHub, con lógica para crear o actualizar archivos automáticamente.

**Funcionalidades clave:**

* ⏰ **Ejecución programada**: Schedule trigger (p. ej. diario).
* 🔌 **Interacción con n8n API**: Obtiene la lista y el JSON de cada workflow.
* 🧾 **Integración GitHub**: Comprueba si el archivo existe, lo crea o actualiza con commits.
* 🔁 **Lógica de control**: Bucles y condicionales para iterar sobre workflows.

**Stack técnico destacado:**

```
n8n API · GitHub API · Schedule Trigger · Lógica condicional y bucles
```

---

# ✨ Extras y notas de valor

* ✅ **Automatizaciones robustas** preparadas para producción (manejo de errores, reintentos y logs).
* 🔒 **Buenas prácticas** para seguridad en credenciales y acceso a APIs.
* ⚙️ **Diseño modular**: cada workflow pensado para ser reutilizable y escalable.

---


