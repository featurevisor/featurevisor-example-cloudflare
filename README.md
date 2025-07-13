# featurevisor-example-cloudflare

Example Featurevisor project utilizing [Cloudflare Pages](https://developers.cloudflare.com/pages).

For more documentation, visit https://featurevisor.com.

## Accessing datafiles

The generated datafiles from this repository is accessible via these URLs:

- `production`: https://featurevisor-example-cloudflare.pages.dev/production/featurevisor-tag-all.json
- `staging`: https://featurevisor-example-cloudflare.pages.dev/staging/featurevisor-tag-all.json

### Usage with Featurevisor SDK

Install the SDK in your application:

```
$ npm install --save @featurevisor/sdk
```

Then use it in your application:

```js
import { createInstance } from "@featurevisor/sdk";

const DATAFILE_URL =
  "https://featurevisor-example-cloudflare.pages.dev/production/featurevisor-tag-all.json";

const datafileContent = await fetch(DATAFILE_URL).then((res) => res.json());

const sdk = createInstance({
  datafile: datafileContent,
});
```

Learn more about [SDK usage here](https://featurevisor.com/docs/sdks/javascript/).

## Installation

Since this example app lives outside of the Featurevisor [monorepo](https://github.com/featurevisor/featurevisor), you are recommended to make sure [`package.json`](./package.json) has the latest version of [`@featurevisor/cli`](https://www.npmjs.com/package/@featurevisor/cli) package.

```
$ npm ci
```

## Usage

### Lint YAMLs

```
$ npx featurevisor lint
```

### Build datafiles

```
$ npx featurevisor build
```

Checkout output in `datafiles` directory.

### Test features

```
$ npx featurevisor test
```

## Cloudflare

For this example, we are going to be uploading to and serving our datafiles from [Cloudflare Pages](https://pages.cloudflare.com/).

Make sure you already have a Cloudflare Pages project set up, and then use it in the [`publish`](./.github/workflows/publish.yml) workflow.

## GitHub Actions

This example project is configured to run its CI/CD pipeline with [GitHub Actions](https://github.com/features/actions).

You are free to choose any other CI/CD provider of your choice.

### Settings

Make sure you have `Read and write permissions` enabled in your GitHub repository's `Settings > Actions > General > Workflow permissions` section.

### Workflows

You can find the GHA workflow files in [`.github/workflows`](./.github/workflows) directory.

- `checks` workflow: runs against non-`master` (non-`main`) branches
- `publish` workflow: runs against `master` (`main`) branch

### Secrets

Follow the guide [here](https://developers.cloudflare.com/pages/how-to/use-direct-upload-with-continuous-integration/), and set up these two secrets in your GitHub repository's `Settings > Secrects and variables > Actions` section:

- `CLOUDFLARE_ACCOUNT_ID`
- `CLOUDFLARE_API_TOKEN`

## License

MIT © [Fahad Heylaal](https://fahad19.com)
