## Proposed Svelte Tech Stack (SPA)

| Purpose       | React Library          | Svelte Equivalent                |
| ------------- | ---------------------- | -------------------------------- |
| UI Framework  | React                  | Svelte                           |
| TypeScript    | TypeScript             | TypeScript                       |
| Backend       | Supabase               | Supabase                         |
| Styling       | Tailwind CSS           | Tailwind CSS                     |
| Data Fetching | Axios + TanStack Query | fetch/Axios + Svelte Query       |
| Routing       | TanStack Router        | svelte-spa-router, routify       |
| UI Components | shadcn/ui              | Skeleton UI / Svelte Headless UI |
| Forms         | react-hook-form        | Felte / svelte-forms-lib         |
| Code Hygiene  | Knip                   | Knip                             |

### Notes

- **Supabase**: Use the official JS client, just as in React.
- **Tailwind CSS**: Integrates seamlessly with Svelte and Vite.
- **Data Fetching**: You can use either the native `fetch` API or Axios. For caching and async state, use [Svelte Query](https://github.com/SvelteStack/svelte-query).
- **Routing**: [svelte-spa-router](https://github.com/ItalyPaleAle/svelte-spa-router) is the most popular SPA router for Svelte.
- **UI Components**: [Skeleton UI](https://www.skeleton.dev/) is Tailwind-based and similar in spirit to shadcn/ui. [Svelte Headless UI](https://github.com/rgossiaux/svelte-headlessui) is another good option.
- **Forms**: [Felte](https://felte.dev/) is ergonomic and similar to react-hook-form. [svelte-forms-lib](https://github.com/tjinauyeung/svelte-forms-lib) is another alternative.
- **Knip**: Can be used for code hygiene in Svelte projects as well.

### Recommended VSCode Extensions

- [Svelte for VS Code](https://marketplace.visualstudio.com/items?itemName=svelte.svelte-vscode)
- [Tailwind CSS IntelliSense](https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss)
- [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
- [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
