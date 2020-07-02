It's easy to add new pages to your Next.js project. There is a `Pages` directory created when you initialize your project.
Next.js automatically adds a route to your page, based on the file name. For example, the URL `http://localhost/about` will be directed to the default React component exported by the `about.js` file.
This is considered a convention-based approach to extensibility, rather than a configuration-based approach.
You simply create new page files, and the Next.js framework automatically picks up on them and enables routing.


## Learning Points

* Pages can be statically generated or Server-Side Rendered (SSR)
* Data can be injected into static pages at build time via `getStaticProps` and `getStaticPaths`

Join the [CBT Nuggets Slack community](http://learn.gg/lc-ts)!
