## SERVER
El directorio server/ se utiliza para registrar API y controladores de servidor en la aplicación.

 - Cada archivo debe exportar una función predeterminada definida con defineEventHandler() o eventHandler() (alias).
 - El controlador puede devolver directamente datos JSON, una Promesa o usar event.node.res.end() para enviar una respuesta.

`auth\server\api\auth\session.get.ts`
```javascript
export default eventHandler(async (event) => {
  const session = await useAuthSession(event);
  return session.data;
});
```
`pages\profile.vue`
 - Esta API se puede llamar universalmente en las páginas y componentes , solo se realiza el fetch a la ruta en donde esta la api 
```javascript
<script setup lang="ts">
  useHead({
    title: "User Profile",
  });

  definePageMeta({
    auth: true,
  });
  const { data: session } = await useFetch("/api/auth/session", { headers: useRequestHeaders(['cookie'])});
</script>
```
