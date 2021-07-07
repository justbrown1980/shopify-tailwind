# Shopify Theme Tailwind CSS

This repository contains a starting point for Shopify Online Store 2.0 Theme
development using Tailwind CSS and the default Dawn theme.

> :bulb: On june 29, Shopify introduced a new git-based workflow. To learn more,
> visit the
> [create a theme guide](https://shopify.dev/themes/getting-started/create) or
> visit [shopify.dev](https://shopify.dev).

## Workflow

A short description of this workflow:

- Edit theme locally using the Shopify CLI and Tailwind
- Commit changes to feature branch
- Merge feature branch with main branch once feature is implemented
- Automatically publish build to dist branch using Github Actions
- Sync Shopify store with dist branch

### Technologies used

- Tailwind CSS
  - The main css file is located in `src/index.css`
  - This file will be built to `assets/index.css`
- Shopify CLI
- Github Actions to deploy the theme to the dist branch on push to the main
  branch

You can copy the Lighthouse Github Action from the original
[Dawn theme](https://github.com/Shopify/dawn) repository to track the
performance of your theme on every push.

## Prerequisites

- The
  [shopify CLI](https://shopify.dev/themes/getting-started/create#step-1-install-shopify-cli)
  is installed on your machine.

## Installation

Run the following commands:

```bash
git clone git@github.com:wesselvanree/shopify-theme-tailwind.git
cd shopify-theme-tailwind
npm install
```

Make sure the `assets/index.css` output file is included in the
`layout/theme.liquid` file. Add this line of code under the base.css stylesheet
tag.

```liquid
<!-- line 98 -->
{{ 'index.css' | asset_url | stylesheet_tag }}
```

Once you've made your first commit, a dist branch will be created on Github. Use
the Shopify Github integration to sync your theme with the dist branch by going
to `your admin dashboard` > `Online Store` > `Themes` > `Add Theme` >
`Connect from Github`.

## Usage

### Development

First, log in to your store if you was not logged in already.

```bash
shopify login --store your-store-name.myshopify.com
```

Run `npm start`. This command will watch your files, build on change and update
the Shopify theme preview.

### Production

This repository contains a Github Action that uses
[JamesIves/github-pages-deploy-action@4.1.4](https://github.com/JamesIves/github-pages-deploy-action).
This action does not activate Github Pages in your repository but just commits
the build to another branch. Currently, the action is configured to deploy the
build to the dist branch. You can easily customize this by editing
`.github/workflows/deploy.yml`.

Alternatively, you can create the build manually. Run `npm run build` to build
for production. You can use the
[Shopify Github integration](https://shopify.dev/themes/getting-started/create#step-6-install-the-shopify-github-integration-and-connect-your-branch-to-your-store)
to track a branch in your Github repository.

## Final notes

### Useful links

- [shopify.dev](https://shopify.dev)
- [Tools for building Shopfy themes](https://shopify.dev/themes/tools)
- [Version control for Shopify themes best practices](https://shopify.dev/themes/best-practices/version-control)

### Things to keep in mind

Using the built-in Shopify code editor would not be effective when using file
transformations like this. The changes made by your merchant in the code editor
would be overridden when you push new changes.

### Suggestions

If you have any suggestions to improve this repository, please open an issue. I
would be happy to hear from you.
