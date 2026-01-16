# 📧 Smart Inbox Manager & Job Opportunity Filter

![Diagrama del Flujo](diagram.png)

## 💡 Descripción
Este workflow convierte una bandeja de entrada caótica en un pipeline organizado de oportunidades. Diseñado para automatizar la gestión de correos electrónicos, el sistema actúa como un filtro inteligente que separa el "ruido" (Spam/Promociones) de la información crítica (Propuestas laborales de LinkedIn, Workana, Freelancer).

El bot lee los correos no leídos, extrae metadatos clave (Remitente, Asunto, Fecha), y aplica lógica condicional para decidir su destino: una base de datos de seguimiento o la papelera.

## ⚙️ Flujo Técnico (Logic)
1. **Trigger:** Se ejecuta periódicamente o por webhook.
2. **ETL (Extract):** Obtiene mensajes no leídos vía **Gmail API**.
3. **Clasificación:**
   - Cruza el remitente con una "White List" (LinkedIn, Workana, etc.).
   - Utiliza nodos `IF` para determinar la relevancia del contenido.
4. **Acción (Load):**
   - **Alta Importancia:** Registra el lead en **Google Sheets** y envía alerta inmediata a **Telegram/Discord**.
   - **Baja Importancia/Spam:** Elimina el correo automáticamente para mantener el "Inbox Zero".

## 🛠️ Stack Tecnológico
* **Orquestador:** n8n (Self-Hosted).
* **Integraciones:** Gmail API, Google Sheets API, Telegram Bot API.
* **Conceptos:** JSON Parsing, Conditional Logic, Data Persistence.

## 🚀 Cómo usarlo
1. Descargá el archivo `workflow.json` de esta carpeta.
2. Importalo en tu instancia de n8n.
3. Configurá tus credenciales de Gmail (OAuth2) y Telegram.
