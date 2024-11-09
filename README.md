# template-typescript

A simple code template for TypeScript developing.

use:

1. [`tsup`](https://tsup.egoist.dev/) for file compiling.
2. [`tsx`](https://tsx.is/) for file execution and content change monitoring.
3. [`ESLint`](https://eslint.org/) for code formatting and linting. And also use my personal [`eslint-config`](https://github.com/tinywaves/eslint-config) for linting rules.

## Install TypeScript and @types/node.

TS uses the browser environment by default, so you need to install this library to type annotate various properties and methods of node.

```bash
pnpm add typescript @types/node -D
```

## Install tsup and tsx

Use `tsup` to implement ts file compiling, use `tsx` to implement ts file execution and content change monitoring.

```bash
pnpm add tsup tsx -D
```

## configs

`package.json`:

```json
{
  "scripts": {
    "build": "tsup",
    "build:dev": "tsup --watch",
    "dev": "tsx watch --clear-screen=false src/index.ts"
  },
  "devDependencies": {
    "@types/node": "^20.12.12",
    "tsx": "^4.16.2",
    "tsup": "^8.0.2",
    "typescript": "^5.4.5"
  }
}
```

`tsup.config.ts`:

```ts
import { defineConfig } from 'tsup';

export default defineConfig({
  entry: ['src/index.ts'],
  outDir: 'dist',
  shims: true,
  format: ['cjs', 'esm'],
  clean: true,
  dts: true,
  minify: true,
});
```

`tsconfig.json`:

```json
{
  "compilerOptions": {
    "target": "ESNext",
    "lib": ["ESNext"],
    "module": "ESNext",
    "moduleResolution": "Bundler",
    "resolveJsonModule": true,
    "strict": true,
    "strictNullChecks": true,
    "esModuleInterop": true,
    "skipDefaultLibCheck": true,
    "skipLibCheck": true
  }
}
```

## test

```ts
// src/index.ts
console.log('test');
console.log('test');
```

![](https://tinywaves.oss-cn-hangzhou.aliyuncs.com/Pasted%20image%2020240523125424.png)

![](https://tinywaves.oss-cn-hangzhou.aliyuncs.com/CleanShot_2024-07-07_03.31.51-2x-bea35c1e4c3300f759ce63e4d15abee2-1720294385-5194ae.png)
