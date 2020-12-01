# Quick setup Tailwind CSS and Next.js

## Create a Next.js project


```bash
npx create-next-app
# or
yarn create next-app
```


## Install dependencies

Use for for conditionally joining `classNames` together.

```bash
npm install --save classnames
# or
yarn add classnames
```

## Install dev dependencies

We now need to install some dependencies which are used for compiling CSS, including Tailwind itself.

```bash
npm install --save-dev tailwindcss postcss-preset-env autoprefixer postcss @fullhuman/postcss-purgecss postcss-import
# or
yarn add --dev tailwindcss postcss-preset-env autoprefixer postcss @fullhuman/postcss-purgecss postcss-import
```


## Configure and integrate Tailwind

```bash
npx tailwindcss init
# or
yarn tailwindcss init
```

By default this will create a file called `tailwind.config.js` in your project root that looks a little like:


```js
module.exports = {
  purge: [],
  darkMode: false, // or 'media' or 'class'
  theme: {
    extend: {},
  },
  variants: {
    extend: {},
  },
  plugins: [],
}
```

## Configure Tailwind to remove unused styles in production

In your tailwind.config.js file, configure the purge option with the paths to all of your pages and components so Tailwind can tree-shake unused styles in production builds:

```js
  module.exports = {
    purge: [
      './pages/**/*.js', 
      './components/**/*.js', 
      './features/**/*.js'
    ],
    darkMode: false, // or 'media' or 'class'
    theme: {
      extend: {}
    },
    variants: {},
    plugins: []
  }
```

### Done with setup. That’s it! 🎉

# Using Tailwind

## Import Tailwind into your CSS

If you are planning to write some custom CSS in your project, use the @tailwind directive to include Tailwind's `base`, `components`, and `utilities` styles inside your main CSS file `styles/global.css`.

```css
@tailwind base;
/* Write your own custom base styles here */

@tailwind components;
/* Write your own custom component styles here */

@tailwind utilities;
/* Your own custom utilities */

```

## Import your CSS with Next.js

Finally, ensure your CSS file is being imported in your `pages/_app.js` component:

```js
import '../styles/globals.css'

export default function MyApp({ Component, pageProps }) {
  return <Component {...pageProps} />
}

```


# Links

- [Get up and running with Tailwind CSS and Next.js](https://dev.to/notrab/get-up-and-running-with-tailwind-css-and-next-js-3a73)
- [Next.js](https://github.com/zeit/next.js)
- [Tailwind CSS](https://tailwindcss.com/)




