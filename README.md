# GetPlan: Zero-Cost, Serverless Multi-Framework Deployment

## Overview

GetPlan demonstrates how to deploy a multi-framework application under a single domain using Vercel. The repository includes:

- Static HTML for the main domain: [https://getplan.vercel.app/](https://getplan.vercel.app/)
- Nuxt 3 App at: [https://getplan.vercel.app/create](https://getplan.vercel.app/create)
- Ghost/Gatsby Blog at: [https://getplan.vercel.app/blog/](https://getplan.vercel.app/blog/)

Custom domain deployment: [pitch.co.il](https://pitch.co.il/)

## Technology Stack

- **Main website**: Static HTML
- **/create path**: Nuxt3
- **/blog path**: Ghost & Gatsby (depployted through [fly.io](https://fly.io/))
  - Learn how to set it up: [How to Host a Ghost Blog on Fly.io](https://blixtdev.com/how-to-host-a-ghost-blog-for-free-on-fly-io/)
  - Template: [Gatsby-Starter-Ghost](https://github.com/TryGhost/gatsby-starter-ghost)
  
All components are deployed through Vercel.

## Git Submodules

The repo utilizes Git submodules to manage these different parts of the project. This allows each section to exist in its separate repository while being deployed under a single, unified domain.

```git
[submodule "website"]
    path = website
    url = https://github.com/danielunited/getplan-website.git
[submodule "app"]
    path = app
    url = https://github.com/danielunited/business-plan.git
[submodule "blog"]
    path = blog
    url = https://github.com/danielunited/getplan-blog.git
```


## Submodule-Specific Configurations

In the Nuxt 3 app's `nuxt.config.ts`:

```
export default defineNuxtConfig({
  ...
  baseURL: '/create/',
});
```

In the Ghost/Gatsby blog's `gatsby-config.js`:

```
module.exports = {
  ...
  pathPrefix: `/blog`,
};
