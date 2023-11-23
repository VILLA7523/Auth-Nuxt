## SERVER
El directorio server/ se utiliza para registrar API y controladores de servidor en la aplicación.

 - Cada archivo debe exportar una función predeterminada definida con defineEventHandler() o eventHandler() (alias).
 - El controlador puede devolver directamente datos JSON, una Promesa o usar event.node.res.end() para enviar una respuesta.
