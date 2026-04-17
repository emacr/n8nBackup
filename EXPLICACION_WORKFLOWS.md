# 🚀 Proyectos destacados de Automatización (n8n)

¡Hola! 👋 Este es un resumen visual y atractivo de algunos proyectos relevantes que he desarrollado usando **n8n**, integrando APIs, IA y automatizaciones que optimizan procesos reales. 

---

## 📚 Índice

1. [Agente de Ventas IA Multicanal (ferretariacompras)](#1-agente-de-ventas-ia-multicanal-ferretariacompras)
2. [Automatización de Búsqueda de Proveedores (busquedaProveedores)](#2-automatización-de-búsqueda-de-proveedores-busquedaproveedores)
3. [Notificaciones y Reportes de Inventario (notificacionStockBajo)](#3-sistema-de-notificaciones-y-reportes-de-inventario-notificacionstockbajo)
4. [Respaldo Automático de Workflows a GitHub (respaldoGithub)](#4-respaldo-automático-de-workflows-a-github-respaldogithub)
5. [Sistema Multiagente para Pedidos (restaurantes)](#5-sistema-multiagente-para-pedidos-restaurantes)
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

# 5. Sistema Multiagente para Pedidos  — `restaurantes`  🍽️🤝

**Descripción corta:**
Sistema conversacional multiagente para gestionar pedidos de restaurante, desde la bienvenida hasta la confirmación, con **PostgreSQL** como base de datos principal.

**Arquitectura y funcionalidades clave:**

* 🧭 **Agente Coordinador (coordinador):** el cerebro que enruta tareas entre agentes; su función es orquestar, no conversar.
* 🧩 **Agentes especialistas (agentTool):** módulos con responsabilidad única — `tomaCombos`, `tomaAlas`, `tomaSalsas`, `tomaBebidas`, `tomaExtras` (presentan opciones desde NocoDB); `tomaNombre`, `tomaEntrega`, `tomaPago`, `tomaComentarios` (solicitan datos faltantes); `tomaUbicacion` (activa para delivery); `actualizaciones` (persiste cambios en NocoDB).
* 🔎 **Verificación de estado del pedido:** al iniciar, verifica si el cliente ya existe y si hay pedidos activos (`pendiente_cliente`) y, antes de finalizar, comprueba que todos los campos obligatorios estén completos.
* 🗺️ **Cálculo de distancia y costo de envío:** extrae lat/lon, usa Google Maps Distance Matrix API para calcular distancia/tiempo desde la sucursal más cercana y aplica una tabla de tarifas para calcular el costo dinámico de envío, luego lo actualiza en PostgreSQL.
* 🧮 **Cálculo total y resumen:** nodo de código `Calcular_Total_y_Resumen` lee todos los datos del pedido desde PostgreSQL, consulta precios, calcula total (incluido envío) y genera un resumen detallado para el cliente.
* ✅ **Finalización y confirmación:** tras la confirmación del cliente, el sistema marca el pedido como `confirmado_sucursal` en la base de datos.

**Stack técnico destacado:**

```
Arquitectura Multiagente · LangChain (Agent Coordinator y Agent Tools) · PostgreSQL · Google Maps Distance Matrix API · JavaScript (Code Node) · Chatwoot (Webhook)
```

---








