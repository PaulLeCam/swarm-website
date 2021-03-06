# Test site

Test [Docusaurus](https://docusaurus.io/en/) deployment to [Swarm](https://swarm.ethereum.org/) using the [Erebos CLI](https://erebos.js.org/docs/cli).

## Prerequisites

- [Node.js](https://nodejs.org/en/) v10+
- [Yarn](https://yarnpkg.com/lang/en/)

## Setup

- Run `yarn install` in the root and `website` folders to install dependencies.
- Run `yarn setup` to create a new website deployment. It will create a new private key.
- Set the generated key as environment variable `KEY=<the key>`.
- Replace the `--hash=` flag value by the generated hash in the `scripts.upload` command in the `package.json`.
- Replace the hash of the `baseUrl` value in `website/siteConfig.js` using the generated hash.

## Building and deploying

- Run `yarn build` to generate the static assets locally.
- Run `yarn upload` to upload the static assets to Swarm (this requires the `KEY` environment variable to be set).
- Run `yarn deploy` as a shortcut to `yarn build` + `yarn upload`.

## Changes from default Docusaurus config

Changes to apply to the `website/siteConfig.js` file.

### Gateway URLs

- `url` is set to `https://swarm-gateways.net`
- `baseUrl` must be changed to `/bzz:/<website hash>/`

### Pages paths

Swarm doesn't default to resolving `index.html` files when accessing a folder, so the following changes are applied:

- Replaced `{ blog: true, label: 'Blog' }` by `{ page: 'blog/index', label: 'Blog' }`
- Set `cleanUrl` to `false`

Thats all 🎉
