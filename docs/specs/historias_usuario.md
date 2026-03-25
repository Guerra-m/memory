1. Subida de Contenido en Calidad Original mediante Código QR
Como asistente al evento, quiero acceder a un repositorio centralizado escaneando un código QR para subir mis fotos y videos en calidad original, para que pueda compartir mis recuerdos en tiempo real sin sufrir la compresión agresiva de las aplicaciones de mensajería tradicionales.
Criterios de Aceptación:
Fricción Cero: El escaneo del QR debe redirigir al usuario directamente a la interfaz de selección y subida de archivos, sin requerir la creación obligatoria de una cuenta (Guest Mode o sesión temporal).
Preservación del Activo (DAM): El sistema debe extraer y almacenar los metadatos EXIF originales y procesar el archivo sin alterar su resolución, formato nativo ni tamaño de compresión.
Gestión de Conectividad (Offline): Si la conexión a internet se interrumpe durante una transferencia activa, la aplicación debe pausar la subida y reanudarla automáticamente desde el punto exacto de interrupción (resumable uploads) una vez que se restablezca la red, sin que el archivo quede corrupto.

2. Encolado de Archivos y Sincronización en Segundo Plano (Offline-First)
Como asistente al evento, quiero poder seleccionar y confirmar la subida de contenido incluso si me encuentro en una zona sin cobertura celular, para que pueda seguir disfrutando del evento sin tener que mantener la aplicación abierta esperando a que haya señal.
Criterios de Aceptación:
Operatividad Offline: La interfaz debe permitir seleccionar contenido de la galería local y presionar el botón de "Subir" independientemente del estado actual de la red del dispositivo.
Cola de Sincronización: Los archivos confirmados se deben almacenar en una cola local dentro de la aplicación, mostrando un indicador visual de estado (ej. "En espera de red").
Ejecución de Conectividad (Offline): Tan pronto como el sistema operativo detecte una conexión a internet estable (WiFi o datos móviles), la cola de caché local debe iniciar la sincronización de los activos hacia el servidor en segundo plano, enviando una notificación silenciosa al finalizar.

3. Validación de Sincronización y Prevención de Duplicados
Como asistente al evento, quiero tener visibilidad clara del estado de mis archivos y evitar subir la misma foto accidentalmente, para que tenga la certeza de que mi contenido está a salvo en el repositorio sin generar desorden en la galería colectiva.
Criterios de Aceptación:
Confirmación Visual: Una vez que el archivo alcanza el 100% de la sincronización en el servidor, debe aparecer instantáneamente en la línea de tiempo (timeline) cronológica del usuario con una etiqueta de "Sincronizado".
Descarte de Duplicados: Al seleccionar archivos, el sistema local debe calcular un hash único de cada imagen/video y compararlo. Si el archivo ya existe en el repositorio del evento o en la cola de subida, la interfaz debe bloquear la subida duplicada y notificar al usuario.
Resolución de Conflictos (Offline): Si un archivo en la cola local experimenta un timeout de red recurrente (más de 3 intentos fallidos), la aplicación debe detener los reintentos automáticos para ahorrar batería, cambiar el estado del archivo a "Error de red", y ofrecer al usuario un botón manual para "Reintentar solo con WiFi".

Detección:
No encontramos grandes fallas o alucinaciones en las historias que nos dio el modelo. Aunque sí agregó la validación de sincronización y prevención de duplicados, nosotros la vemos como un acierto y una falta nuestra en el análisis
