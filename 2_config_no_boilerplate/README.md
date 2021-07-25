# Setting up Vite + Svelte From Scratch

- Put vite config in `vite.config.js`. It turns out that this is an easy mistake to make after too too much cider
- vite is EASY to setup and you get optional intellisense with an import

```ts
import {defineConfig} from 'vite'

export default defineConfig({
	root: 'src/client'
})
```

That's all you need to get going! There's the svelte config - `@sveltejs/vite-plugin-svelte`.

---

