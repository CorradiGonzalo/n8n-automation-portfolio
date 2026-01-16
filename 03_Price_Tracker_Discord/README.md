# 📉 Automated E-commerce Price Tracker & Alert System

## 💡 Descripción
Bot de monitoreo de precios en tiempo real diseñado para detectar oportunidades de compra en plataformas de e-commerce (MercadoLibre).

A diferencia de las alertas nativas de los sitios, este sistema permite un control total sobre los umbrales de precio y mantiene un histórico propio. El workflow realiza scraping del sitio objetivo, compara el precio actual con registros históricos y dispara notificaciones instantáneas solo cuando se detecta una baja real o una oportunidad de arbitraje.

## ⚙️ Flujo Técnico (Logic)
1. **Schedule:** Ejecución automática vía Cron (cada X horas).
2. **Web Scraping:** Petición HTTP + Parsing de HTML para extraer el precio "limpio" (sin símbolos de moneda).
3. **Data Analysis:**
   - Consulta el último precio registrado en la base de datos (**Google Sheets**).
   - Nodo `IF`: Compara `Precio_Actual < Precio_Anterior` O `Precio_Actual < Target`.
4. **Notification:** Si la condición es `TRUE`, envía un payload JSON a un canal privado de **Discord** vía Webhook.
5. **History:** Guarda el nuevo punto de datos para futuros análisis.

## 🛠️ Stack Tecnológico
* **Orquestador:** n8n.
* **Técnicas:** Web Scraping (HTML Extraction), HTTP Requests.
* **Notificaciones:** Discord Webhooks (JSON Payloads).
* **Base de Datos:** Google Sheets.

## 🚀 Cómo usarlo
1. Descargá el archivo `workflow.json`.
2. Modificá el nodo "HTTP Request" con la URL del producto que querés seguir.
3. Ajustá los selectores CSS en el nodo "HTML Extract" según la tienda.
4. Pegá tu URL de Webhook de Discord.
