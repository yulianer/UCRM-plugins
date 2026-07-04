Notificador WhatsApp Core para UISP (CRM)
Este complemento integral conecta UISP (CRM) con la API de OpenWA Core, automatizando la comunicación con los clientes mediante notificaciones instantáneas de WhatsApp. El sistema procesa de forma inteligente los webhooks de UISP, maneja archivos PDF en Base64 y cuenta con un sistema avanzado de control de flujo (Rate-Limit) para evitar el spam.

🚀 Características Principales
Soporte Multievento: Cobertura total del ciclo de vida del cliente:

Facturación: Nuevas facturas (con envío de PDF adjunto), recordatorios de pago próximo a vencer y avisos de facturas vencidas.

Pagos: Confirmación inmediata de pagos recibidos con detalle de monto y método.

Servicios: Alertas de interrupciones, suspensiones, reactivaciones, posposiciones y creación de nuevos servicios.

Clientes: Mensaje automatizado de bienvenida para nuevos registros.

Envío Nativo de Documentos: Descarga y codificación de facturas PDF al vuelo para enviarlas como documentos nativos de WhatsApp sin requerir almacenamiento temporal en disco.

Sistema Anti-Spam (Rate-Limit): Lógica avanzada que evalúa el historial de alertas mediante un archivo local (alert_log.json) para restringir envíos duplicados en períodos de 30 minutos a 24, dependiendo de la criticidad del evento.

Estructura OpenWA Core: Optimizado bajo los estándares de las versiones más recientes de la API (/send-document y /send-text), utilizando estructuras planas de JSON (Flat JSON).

🛠 Requisitos del Entorno
Servidor UISP (UCRM): Versión compatible con instalación de plugins personalizados.

OpenWA Core / WAHA: Contenedor Docker configurado, activo y con una sesión vinculada.

PHP: Extensiones cURL y JSON habilitadas en el entorno del servidor UISP.

Permisos de escritura: El complemento requiere permisos de escritura en la carpeta data/ para gestionar el archivo alert_log.json.

📦 Instalación y Despliegue
Asegúrese de que todos los archivos (incluidos public.php y la carpeta data/) estén en la raíz del directorio del complemento.

Comprima el directorio completo en un archivo .zip.

Ingresa al panel administrativo de UISP > Sistema > Complementos.

Haz clic en Subir Plugin y selecciona tu archivo .zip.

Active el complemento en la interfaz.

⚙️ Configuración (Panel UISP)
Al instalar, configure los siguientes parámetros obligatorios en la sección de ajustes del complemento:

URL de la API: La ruta base de tu contenedor OpenWA (Ej: http://144.xxx.xxx.xx:2785/api ).

Clave API: Clave de autenticación configurada en las variables de entorno de tu Docker.

ID de sesión: El identificador exacto de la sesión activa de WhatsApp (Ej: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).

App Key de UISP: Generada automáticamente por el sistema para autorizar las solicitudes internas (descarga de PDFs y datos de clientes).

🔍 Solución de Problemas (Registros)
El complemento está diseñado para registrar sus acciones directamente en el visor de Webhooks de UISP.

Código 201/200: Envío exitoso.

Código 400: La carga útil enviada a la API de WhatsApp está mal formateada. Revisar variables de teléfono.

Código 404: La ruta del endpoint en OpenWA no coincide con la versión instalada.

Registro de límite de tasa: Si un mensaje no se envía por control de flujo, el registro indicará: "Límite de tasa: ya se notificó {evento} al cliente {ID}".

📝 Autor
Desarrollado por Yulian Ernesto Castellanos Daza .

Especialidad: Análisis de Sistemas y Tecnología / Ingeniería en Telecomunicaciones.
📄 Licencia
Este proyecto esta bajo la licencia MIT.
