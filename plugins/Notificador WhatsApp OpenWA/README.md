# Notificador WhatsApp para UISP (CRM)

Este complemento permite integrar **UISP (CRM)** con la API de WhatsApp (**OpenWA / WAHA Core**) para automatizar el envío de facturas en formato PDF y notificaciones de servicio directamente a tus clientes.

---

## 🚀 Características Principales

* **Envío Automático:** Envío de facturas en formato PDF al momento de la creación.
* **Notificaciones de Servicio:** Soporte para eventos de interrupción (outage).
* **Integración con API Core:** Optimizado para la arquitectura de OpenWA / WAHA.
* **Personalización:** Fácil configuración de mensajes mediante el `public.php`.

---

## 🛠 Requisitos

* **UISP (UCRM):** Con acceso a instalación de plugins.
* **OpenWA (Core/WAHA):** Contenedor Docker configurado y accesible desde la red de UISP.
* **PHP:** Entorno configurado dentro del servidor UISP.

---

## 📦 Instalación

1. Asegúrate de que los archivos estén en la raíz de una carpeta llamada `notificador-whatsapp`.
2. Comprime la carpeta en un archivo `.zip`.
3. Ingresa a tu panel de **UISP > Sistema > Plugins**.
4. Haz clic en **Subir Plugin** y selecciona el archivo `.zip`.
5. Activa el plugin y configúralo con los parámetros requeridos.

---

## ⚙️ Configuración

Dentro de la configuración del plugin (icono de engranaje), asegúrate de establecer:

* **URL de la API:** La dirección IP o dominio donde corre tu instancia de OpenWA (Ej: `http://148.124.204.86:2785/api`).
* **API Key:** La llave de seguridad configurada en tu servidor WAHA.
* **Session ID:** El ID de sesión activo en tu servidor WAHA (ej: `400000cd-ccc3-4002-0050-b00c28a000a4`).

---

## 🔍 Solución de Problemas (Troubleshooting)

Si el envío falla, verifica los logs en el Webhook de UISP. Aquí están los errores comunes resueltos:

### Error 404 (Endpoint no encontrado)

La API de WAHA Core requiere rutas precisas. Actualmente, el plugin utiliza:

* **Para Facturas (PDF):** `/sessions/{sessionId}/send-document`
* **Para Textos:** `/sessions/{sessionId}/send-text`

> **Nota:** Si recibes un 404, asegúrate de que tu instancia de OpenWA esté corriendo la versión de API Core y que los endpoints coincidan con la documentación de tu versión específica.

### Error 400 (Bad Request)

Este error ocurre cuando la estructura del JSON no es la esperada. El plugin actual envía los documentos bajo la siguiente estructura:

```json
{
    "chatId": "57xxxxxxxxx@c.us",
    "caption": "Tu mensaje",
    "document": {
        "url": "data:application/pdf;base64,...",
        "filename": "Factura_123.pdf"
    }
}

```

---

## 📝 Autor

Desarrollado por **Yulian Ernesto Castellanos Daza**.

* **Especialidad:** Análisis de Sistemas y Tecnología / Ingeniería en Telecomunicaciones.
* **Proyecto:** Automatización de infraestructura Airlink Telecomunicaciones.

---

## 📄 Licencia

Este proyecto esta bajo la licencia MIT.