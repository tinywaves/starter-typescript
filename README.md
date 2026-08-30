# starter-typescript

A minimal, opinionated starter for building and publishing TypeScript libraries.

## Features

- Build ESM and CommonJS bundles with [tsdown](https://tsdown.dev/)
- Generate TypeScript declaration files
- Run TypeScript directly with [tsx](https://tsx.is/)
- Test with [Vitest](https://vitest.dev/) and V8 coverage
- Lint and format with [ESLint](https://eslint.org/) and [`@dhzh/eslint-config`](https://github.com/tinywaves/eslint-config)
- Enforce conventional commits with Commitlint and [prek](https://prek.j178.dev/)
- Manage releases with [bumpp](https://github.com/antfu-collective/bumpp)
- Generate GitHub releases from tags with GitHub Actions

## Requirements

- Node.js `^24.18.0`
- pnpm `^11.22.0`

## Getting Started

Use this repository as a template, then install the dependencies:

```bash
pnpm install
```

Start the development watcher:

```bash
pnpm dev
```

The package entry point is `src/index.ts`, and tests live in the `test` directory.

## Scripts

| Command | Description |
| --- | --- |
| `pnpm dev` | Run `src/index.ts` and restart on changes |
| `pnpm build` | Build ESM, CommonJS, and declaration files into `dist` |
| `pnpm build:dev` | Rebuild the package in watch mode |
| `pnpm test` | Run the test suite once |
| `pnpm test:dev` | Run tests in watch mode |
| `pnpm test:coverage` | Run tests and generate a coverage report |
| `pnpm lint` | Check the project with ESLint |
| `pnpm lint-fix` | Fix lint and formatting issues |
| `pnpm version:update` | Check and update dependency versions |
| `pnpm release` | Select and create a new package version and Git tag |
| `pnpm release:publish` | Create a release and publish the package to npm |

## Package Output

Running `pnpm build` generates:

```text
dist/
├── index.cjs
├── index.d.cts
├── index.d.mts
└── index.mjs
```

The package exposes both ESM and CommonJS entry points through the `exports` field in `package.json`.

## Usage

Before you start coding with this template:

1. Update `README.md` for your project.
2. Update the `name`, `version`, `description`, `author`, `license`, `homepage`, `keywords`, and `repository` fields in `package.json`.
3. Update the license information in `LICENSE`.
4. Remove the `.github` directory if you do not want to use the included GitHub workflows.
5. Replace the example code in `src` and `test` with your implementation and tests.
6. If you want to publish the package to npm, add a `prepack` script to build the package before publishing:

```json
{
  "scripts": {
    "prepack": "pnpm build"
  }
}
```

## Publishing

The default release workflow creates a GitHub release whenever a tag matching `v*` is pushed.

An npm publishing workflow is provided as `.github/workflows/publish.yml.template`. Rename it to `publish.yml` to enable it, then configure npm trusted publishing for your GitHub repository.

Only `dist` is included in the published package, so make sure the package is built before publishing.

## License

[MIT](LICENSE)
