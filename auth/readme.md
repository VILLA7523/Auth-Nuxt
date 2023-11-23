## SERVER
El directorio server/ se utiliza para registrar API y controladores de servidor en la aplicación.

 - Cada archivo debe exportar una función predeterminada definida con defineEventHandler() o eventHandler() (alias).
 - El controlador puede devolver directamente datos JSON, una Promesa o usar event.node.res.end() para enviar una respuesta.

``` 
export default eventHandler(async (event) => {
  const session = await useAuthSession(event);
  const { email, password } = await readBody(event);
  const user = await findUserByEmail(email);
  if (!user) {
    throw createError({
      message: "Email not found! Please register.",
      statusCode: 401,
    });
  }
  if (!user.password || user.password !== (await hash(password))) {
    throw createError({
      message: "Incorrect password!",
      statusCode: 401,
    });
  }
  await session.update({
      id: user.id,
      name: user.name,
      email: user.email,
  });
  return session;
});
```
