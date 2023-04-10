# Testing env variables with Astro + Vercel Edge

When deploying Astro with Vercel Edge, environment variables only work when they are prefixed with `PUBLIC_`.

You can see that in `src/pages/index.astro`.

To test this yourself:

- Fork this repo
- Create a new project on Vercel using this repo
- Add two environment variables to the Vercel project:
  - `MY_ENV_VAR`
  - `PUBLIC_MY_ENV_VAR`

After deploying, on the homepage you should see the `MY_ENV_VAR` variable is not working, but the `PUBLIC_` one is.

Because Edge Functions are not client-side, it seems like this is a bug. You should be able to access things like database credentials inside an Edge function, without prefixing it with `PUBLIC_`.
