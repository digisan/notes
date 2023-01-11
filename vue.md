## quick vue

0. install node from [node download page](https://nodejs.org/en/download/)
1. `npm init vue@3`
2. `cd /proj`
3. `npm install`
4. `npm run dev` or `npm run build`

### auto-imports

> npm install -D unplugin-auto-import

1. "*vite.config.ts*", add `import AutoImport from 'unplugin-auto-import/vite'`; "**defineConfig**" -> "**plugins**", add `AutoImport({ imports: ["vue"] })`.

2. "*tsconfig.json*", "**include**" add `"auto-imports.d.ts"`.

3. restart vscode project.

4. remove `import { ... } from "vue"`.
