# fastapi_semana_7-sarai_gonzalez-3147253
API Biblioteca Municipal – Semana 
Nombre: Gonzalez Vargas Sarai Johanna
Ficha: 3147253
Asignación: Biblioteca Municipal – Tipo C (Libros, préstamos de usuario)

Descripción

Este proyecto implementa una API con FastAPI y Redis que gestiona datos de una biblioteca municipal.
Incluye todas las prácticas solicitadas en la Semana 7:

Redis Caching → almacenamiento en caché de libros y préstamos.

Optimización de DB → consultas simuladas con cacheo y expiración.

Middleware Rate Limiting → límite de 10 peticiones por minuto por usuario.

Monitoring & Performance → métricas de uso, tiempo de respuesta y origen de los datos.

Requisitos

Python 3.9+

Redis
 instalado y corriendo (redis-server)

Librerías necesarias:

pip install fastapi uvicorn redis

Ejecución

Asegúrate de que Redis está en ejecución:

redis-server


Inicia la API con:

uvicorn main:app --reload


Accede en tu navegador:

Docs (Swagger): http://127.0.0.1:8000/docs

Red de prueba rápida:

/libro/1 → Devuelve datos de libro (primero desde DB, luego cache).

/usuario/101/prestamos → Devuelve préstamos de usuario.

/metrics → Estadísticas de uso (hits DB, cache, tiempos).

Endpoints principales

GET / → Bienvenida

GET /libro/{id} → Datos de un libro

GET /usuario/{id}/prestamos → Préstamos activos del usuario

GET /metrics → Métricas de rendimiento

Rate limiting: máximo 10 peticiones por minuto por cliente

Ejemplo de Respuesta
Petición:
GET /libro/1

Primera vez:
{
  "source": "db",
  "data": "Libro 1: Don Quijote de la Mancha"
}

Segunda vez (usando caché):
{
  "source": "cache",
  "data": "Libro 1: Don Quijote de la Mancha"
}

Los datos de libros y préstamos son simulados, pero cumplen el esquema de caching y optimización solicitado.

Redis elimina automáticamente datos después del tiempo de expiración definido.

El middleware evita abusos de peticiones.
Conclusión

Este proyecto cumple con los requerimientos de la Semana 7, integrando Redis, optimización de consultas, rate limiting y métricas en un solo servicio.
