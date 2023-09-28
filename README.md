# Deploying a multi-framework app using Vercel

## Overview

This demo demonstrates how to deploy a multi-framework app on a single domain using Vercel. It has:

- [Main Site](https://getplan.vercel.app/): Static HTML 
- [/create](https://getplan.vercel.app/create): Nuxt3 
- [/blog](https://getplan.vercel.app/blog/): Ghost & Gatsby  (deployed on [fly.io](https://fly.io/) micro-VMs)
  - [Tutorial](https://blixtdev.com/how-to-host-a-ghost-blog-for-free-on-fly-io/)
  - [Template](https://github.com/TryGhost/gatsby-starter-ghost)

It also works on a [custom domain](https://pitch.co.il/)

## Git Submodules

The repo utilizes Git submodules to manage these different parts of the project. This allows each section to exist in its separate repository while being deployed under a single, unified domain.

```git
[submodule "website"]
    url = https://github.com/danielunited/getplan-website.git
[submodule "app"]
    url = https://github.com/danielunited/business-plan.git
[submodule "blog"]
    url = https://github.com/danielunited/getplan-blog.git
```

## Pulling from Submodules

For pulling the latest changes specifically for all the submodules, use:

```bash
git submodule update --recursive --remote
```

This will fetch and update the submodules to their latest commits in their respective remote repositories. Make sure you're in the root directory of your main repository when running this command.

## Configs

`nuxt.config.ts` sets the Nuxt app at `[Domain]/create`.
```ts
export default defineNuxtConfig({ baseURL: '/create/' });
```

`gatsby-config.js` makes the blog accessible at `[Domain]/blog`.
```js
module.exports = { pathPrefix: `/blog` };
```

These settings route traffic to the correct app sections.
