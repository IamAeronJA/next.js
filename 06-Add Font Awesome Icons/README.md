The Font Awesome library of icons provides pleasant visuals that make it easier for end users to interpret the functions of your application.
While there is a paid, premium version of Font Awesome, there's also a free version with a plethora of essential icons for any application, such as e-mail, phone, coffee, beer, bacon, and many more!

In this module, we'll take a look at how to add [Font Awesome](https://www.npmjs.com/package/@fortawesome/react-fontawesome) to your project and start using the free icons it offers in Next.js!

## Install Font Awesome Modules

First, you'll need to install several modules from NPM.

```
npm i --save @fortawesome/fontawesome-svg-core @fortawesome/react-fontawesome @fortawesome/free-solid-svg-icons  @fortawesome/free-regular-svg-icons
```

## Using Font Awesome Icons

You can import Font Awesome icons into specific components, by importing the `FontAwesomeIcon` component from the `react-fontawesome` module.

```
import { FontAwesomeIcon } from '@fortawesome/react-fontawesome'
import { faCoffee, faBeer } from '@fortawesome/free-solid-svg-icons'
```

Inside your component, you can reference the Font Awesome icon component using the following code:

```
<FontAwesomeIcon icon={faCoffee} />
```

## Build a Font Awesome Icon Library

You might notice that there is a lot of duplicate code by importing Font Awesome into each page. Instead of importing Font Awesome into each page, you can build a library of icon imports in an initialization page.
We'll use the [Custom App](https://nextjs.org/docs/advanced-features/custom-app) functionality from Next.js to accomplish this.

Start by adding a custom app under `pages/_app.js`.

```
function MyApp({ Component, pageProps }) {
  return <Component {...pageProps} />
}

export default MyApp
```

Next, import `FontAwesomeIcon` and any specific icons that you want, same as with individual pages.

```
import { FontAwesomeIcon } from '@fortawesome/react-fontawesome'
import { faCoffee, faBeer } from '@fortawesome/free-solid-svg-icons'
```

Now, the different part here is that we'll build a `library` from `fontawesome-svg-core` in the init page.

```
import { library } from '@fortawesome/fontawesome-svg-core'

library.add(faBeer)
```

Back in your Next.js pages, you still have to import the `FontAwesomeIcon` component, but all your library icons will automatically be accessible.
In this case, you must use the icon's name as a string, without the `fa` prefix.

## Learning Points

* You can easily import Font Awesome icons into your Next.js projects as a React components
* Font Awesome SVGs scale well, as they are vector-based graphics
* Font Awesome version 5 changed from a font-based implementation to an SVG-based implementation

Join the [CBT Nuggets Slack community](http://learn.gg/lc-ts)!
