POST /api/v1/auth/guest: Crea una sesión temporal vinculada al QR del evento.
HEAD /api/v1/media/verify/{hash}: Verifica si el archivo ya existe para evitar duplicados
.
POST /api/v1/media/upload: Endpoint compatible con TUS para subidas fragmentadas y resumibles
.
GET /api/v1/event/{slug}/timeline: Obtiene la lista de medios ya sincronizados para la vista cronológica
.