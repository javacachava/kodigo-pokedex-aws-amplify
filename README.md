# PokeQuery Lab — desplegado en AWS Amplify

Pokédex construida con **Next.js 16 (App Router)**, React Server Components, TypeScript y TanStack Query. Consume la [PokeAPI](https://pokeapi.co/) y muestra un listado con búsqueda y una página de detalle por Pokémon.

## URL pública del despliegue

**https://PENDIENTE.amplifyapp.com** (se reemplaza por la URL real que genera Amplify)

## Ejecutar en local

```bash
cp .env.example .env.local   # opcional: la variable tiene valor por defecto
npm ci
npm run dev                  # http://localhost:3000
npm run build && npm start   # build de producción
```

## Variables de entorno

| Variable | Obligatoria | Descripción |
|---|---|---|
| `NEXT_PUBLIC_POKEAPI_URL` | No | Endpoint de la PokeAPI. Por defecto `https://pokeapi.co/api/v2`. |

El archivo `.env.local` real nunca se sube al repositorio (está en `.gitignore`). En producción la variable se configura directamente en la consola de Amplify.

## Despliegue en AWS Amplify

1. Subir el proyecto a un repositorio público de GitHub y comprobar que `npm run build` compila.
2. En la consola de AWS abrir **AWS Amplify** y elegir **Create new app → Deploy with GitHub**.
3. Autorizar a Amplify, elegir este repositorio y la rama `main`. Amplify detecta Next.js y usa `amplify.yml` (`npm ci` y `npm run build`).
4. En **Environment variables** agregar `NEXT_PUBLIC_POKEAPI_URL` con el valor de `.env.example`.
5. Guardar y desplegar. Al terminar el build el estado es **Deployed** y Amplify muestra la URL pública.
6. Abrir la URL y comprobar el listado, la búsqueda y el detalle de un Pokémon.

Cada `git push` a `main` dispara un nuevo despliegue automáticamente.

## Evidencia

Las capturas del proceso están en [`docs/capturas/`](docs/capturas/).
