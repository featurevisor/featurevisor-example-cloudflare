# featurevisor-example-cloudflare

Example Featurevisor project utilizing [Cloudflare Pages](https://developers.cloudflare.com/pages).

For more documentation, visit https://featurevisor.com.

## Installation

Since this example app lives outside the Featurevisor [monorepo](https://github.com/fahad19/featurevisor), you are recommended to make sure [`package.json`](./package.json) has the latest version of [`@featurevisor/cli`](https://www.npmjs.com/package/@featurevisor/cli) package.

```
$ npm ci
```

## Usage

### Lint YAMLs

```
$ npm run lint
```

### Build datafiles

```
$ npm run build
```

### Test features

```
$ npm test
```

### Start local server

Generates and serves [status site](https://featurevisor.com/docs/site/):

```
$ npm start
```

## GitHub Actions

This example project is configured to run its CI/CD pipeline with [GitHub Actions](https://github.com/features/actions).

You are free to choose any other CI/CD provider of your choice.

### Workflows

You can find the GHA workflow files in [`.github/workflows`](./.github/workflows) directory.

- `checks` workflow: runs against non-`master` (non-`main`) branches
- `publish` workflow: runs against `master` (`main`) branch

## Cloudflare

For this example, we are going to be uploading to and serving our datafiles from [Cloudflare Pages](https://developers.cloudflare.com/pages).
