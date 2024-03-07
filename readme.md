This is what I did so far.

Create a new app

    npm create vite@latest

I chose (vanilla+typescript)

    npm install --save-dev vite-plugin-typescript-transform
  
Well it did not complain.
Then create a vite.config.ts with the sample from github


    import ts from 'typescript';
    import { defineConfig } from 'vite';
    import { vitePluginTypescriptTransform } from 'vite-plugin-typescript-transform';
  
    export default defineConfig({
      // ...your vite configuration
      plugins: [
        vitePluginTypescriptTransform({
          enforce: 'pre',
          filter: {
            files: {
              include: /\.ts$/,
            },
          },
          tsconfig: {
            override: {
              target: ts.ScriptTarget.ES2021,
            },
          },
        }),
      ],
    });

npm run dev still works.

npm run build also works.

Nothing is broken

But how do I implement a transformer?



