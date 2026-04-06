Frontend: React (Vite) + Tailwind CSS + Workbox (para capacidades PWA y Background Sync)
.
Backend: Node.js (Express) o Python (FastAPI), optimizado para manejo de streams de archivos.
Base de Datos: PostgreSQL (metadatos y estados) y Redis (gestión de sesiones temporales y colas rápidas).
Almacenamiento (DAM): AWS S3 o Google Cloud Storage para preservar la calidad original de fotos/videos
.
Protocolo de Subida: TUS Protocol (indispensable para la funcionalidad de resumable uploads)
.
Infraestructura: Docker + Nginx.