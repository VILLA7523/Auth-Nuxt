# Nuxt with Local Auth

Simple password based starter made with:
- Nuxt goodies
- Built-in session
- Storage layer
- Composables.

This project uses [Nuxt Extend Layers](https://nuxt.com/docs/getting-started/layers) feature to implement local auth in [`auth`](./auth) directory with a modular approach. This way you can share and reuse your authentication implementation across projects and keep the code clean.

Default database is using built-in key-value storage. You can rewrite it with a custom database by updating [`./auth/server/utils/db.ts`](./auth/server/utils/db.ts)

Look at the [Nuxt 3 documentation](https://nuxt.com/docs/getting-started/introduction) to learn more about Nuxt.

https://nuxt.com/docs/examples/features/data-fetching

Copy `.env.example` to `.env` and provide a secure string for session password.
