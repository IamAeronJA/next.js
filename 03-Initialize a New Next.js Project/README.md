Bootstrapping a new project with Next.js is easy, thanks to `npx`. Just run `npx create-next-app` to initialize a new project directory.

https://nextjs.org/blog/create-next-app

```
npx create-next-app --use-npm baconeater
```

Once you've created the project, you can immediately run it with fast refresh support, using `npm run dev`.
If port 3000 is taken by another application already, you can override it with `-p <port>` in the `dev` script.

If you make a change to your project, it will automatically recompile the project, and you'll see the changes in the browser.

## Learning Points

* The `./pages` directory contains the static pages on your site, in the root of the directory
* The `./pages/api` directory contains API endpoints
* `package.json` contains only a few dependencies for base projects
* The `public` directory contains static assets (raster images, SVG, GLTF, CSS, JavaScript, etc.)

Join the [CBT Nuggets Slack community](http://learn.gg/lc-ts)!
