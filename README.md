# In this stack

* SvelteKit (Vite)
* Vitest
* Tailwind CSS
* i18n

## Developing

Checkout the `package.json / scripts` for full list of commands. Example:

```bash
# run dev server & watch
pnpm dev

# run test and watch changes
pnpm test

# run test with UI
pnpm test -- --ui
```

Note: You can replace `pnpm` by `yarn` in this document, the command parameters stays the same.

## Building

To create a production version of your app:

```bash
pnpm build
```

You can preview the production build with `pnpm preview`.

> To deploy your app, you may need to install an [adapter](https://kit.svelte.dev/docs/adapters) for your target environment.
