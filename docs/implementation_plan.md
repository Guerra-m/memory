# Plan de Implementación - Historia de Usuario #1

## Objetivo
Desarrollar la Historia de Usuario #1: "Subida de Contenido en Calidad Original mediante Código QR".
Esto incluye el acceso por código QR (Guest Mode), la extracción de metadatos EXIF, y la subida del archivo sin pérdida de calidad y con capacidad de reanudación (Resumable Uploads) en caso de pérdida de conexión.

## User Review Required
> [!IMPORTANT]
> El plan se centra **exclusivamente** en la HU #1 según lo solicitado. 
> Las funcionalidades de "offline-first" avanzado (cola local) y prevención de duplicados (HU #2 y #3) se implementarán en etapas posteriores. No obstante, la arquitectura planteada aquí mediante TUS sentará las bases para manejar cortes de red de forma robusta.

## Proyecto

### Frontend (React/Vite)
#### [NEW] `frontend/package.json`
#### [NEW] `frontend/src/App.jsx`
#### [NEW] `frontend/src/pages/UploadPage.jsx`
#### [NEW] `frontend/src/services/api.js`
#### [NEW] `frontend/src/services/tusClient.js`
#### [NEW] `frontend/src/utils/exifExtractor.js`

### Backend (Node.js/Express)
#### [NEW] `backend/package.json`
#### [NEW] `backend/src/app.js`
#### [NEW] `backend/src/routes/authRoutes.js`
#### [NEW] `backend/src/routes/uploadRoutes.js`
#### [NEW] `backend/src/controllers/authController.js`
#### [NEW] `backend/src/services/tusService.js`
#### [NEW] `backend/src/services/redisService.js`

## Dependencias Necesarias

### Frontend
- **react-router-dom**: Para manejar la redirección del código QR a la vista de subida.
- **tus-js-client**: Cliente oficial de TUS para manejar la subida por fragmentos de manera reanudable y robusta.
- **exifr** (o similar): Para extraer los metadatos originales de las imágenes localmente antes de subirlas.
- **axios**: Para las peticiones convencionales (Guest Auth).

### Backend
- **express**: Framework web principal.
- **@tus/server**: Implementación del protocolo TUS en Node.js que habilita subidas reanudables y prevención de corrupción de archivos.
- **redis**: Base de datos en memoria para gestionar la autenticación temporal rápida (Guest Mode).
- **cors**, **dotenv**: Utilidades generales de configuración.

## Orden de Ejecución

1. **Inicialización y Dependencias**: 
   - Setup de la estructura base en carpetas `frontend` y `backend`.
   - Instalación de las dependencias detalladas.
2. **Backend: Autenticación Guest (Fricción Cero)**: 
   - Implementar el endpoint `POST /api/v1/auth/guest`.
   - Generar un ID de sesión vinculado al evento (QR) y registrarlo temporalmente en Redis.
3. **Backend: Servidor TUS (DAM + Resumable Uploads)**: 
   - Configurar el endpoint `/api/v1/media/upload` utilizando `@tus/server`.
   - Configurar el almacenamiento persistente cuidando de no alterar el archivo y recibir todos los metadatos.
4. **Frontend: Enrutamiento y Sesión**: 
   - Configurar el enrutador para procesar links procedentes del QR (`/:eventSlug/upload`).
   - Llamar al endpoint *Guest* de inmediato para obtener la sesión temporal.
5. **Frontend: UI Selección y EXIF**: 
   - Construir `UploadPage.jsx` con input file asíncrono.
   - Implementar `exifExtractor.js` para retener la metadata e inyectarla durante la subida.
6. **Frontend: Cliente TUS**: 
   - Configurar y orquestar `tus-js-client`.
   - Gestionar el inicio de la carga enviando metadatos.
   - Demostrar la gestión de reanudación automática de conectividad enviando estados de progreso.
