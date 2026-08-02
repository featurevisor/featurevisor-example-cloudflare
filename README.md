# featurevisor-example-cloudflare

Example Featurevisor project using [Cloudflare Pages](https://developers.cloudflare.com/pages).

For more documentation, visit [featurevisor.com](https://featurevisor.com).

## Accessing datafiles

The generated target datafiles from this repository are available at these URLs:

- `production`: https://featurevisor-example-cloudflare.pages.dev/production/featurevisor-tag-all.json
- `staging`: https://featurevisor-example-cloudflare.pages.dev/staging/featurevisor-tag-all.json

The smaller mobile target is intended for the native iOS and Android examples:

- `production`: https://featurevisor-example-cloudflare.pages.dev/production/featurevisor-mobile.json
- `staging`: https://featurevisor-example-cloudflare.pages.dev/staging/featurevisor-mobile.json

The mobile target contains three focused examples:

- `mobile_theme` demonstrates variations only.
- `mobile_feed` demonstrates variables only.
- `mobile_experience` demonstrates variations and variables together.

### Usage with Featurevisor SDK

Install the SDK in your application:

```sh
npm install @featurevisor/sdk
```

Then use it in your application:

```js
import { createFeaturevisor } from "@featurevisor/sdk";

const DATAFILE_URL =
  "https://featurevisor-example-cloudflare.pages.dev/production/featurevisor-tag-all.json";

const datafileContent = await fetch(DATAFILE_URL).then((res) => res.json());

const sdk = createFeaturevisor({
  datafile: datafileContent,
});
```

Learn more about [SDK usage here](https://featurevisor.com/docs/sdks/javascript/).

## Installation

```sh
npm ci
```

## Usage

### Lint YAMLs

```sh
npx featurevisor lint
```

### Build datafiles

```sh
npx featurevisor build
```

Review the output in the `datafiles` directory.

### Test features

```sh
npx featurevisor test
```

### Explore the Catalog

```sh
npx featurevisor catalog
```

## Cloudflare

For this example, we are going to be uploading to and serving our datafiles from [Cloudflare Pages](https://pages.cloudflare.com/).

Make sure you already have a Cloudflare Pages project set up, and then use it in the [`publish`](./.github/workflows/publish.yml) workflow.

## GitHub Actions

This example project is configured to run its CI/CD pipeline with [GitHub Actions](https://github.com/features/actions).

You can use another CI/CD provider if preferred.

### Settings

Make sure you have `Read and write permissions` enabled in your GitHub repository's `Settings > Actions > General > Workflow permissions` section.

### Workflows

You can find the GHA workflow files in [`.github/workflows`](./.github/workflows) directory.

- `checks` workflow: runs against non-`master` (non-`main`) branches
- `publish` workflow: runs against `master` (`main`) branch

### Secrets

Follow the [Cloudflare guide](https://developers.cloudflare.com/pages/how-to/use-direct-upload-with-continuous-integration/) and add these secrets under `Settings > Secrets and variables > Actions`:

- `CLOUDFLARE_ACCOUNT_ID`
- `CLOUDFLARE_API_TOKEN`

## License

MIT © [Fahad Heylaal](https://fahad19.com)
