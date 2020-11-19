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
npm install --save-dev tailwindcss postcss-preset-env autoprefixer @fullhuman/postcss-purgecss
# or
yarn add --dev tailwindcss postcss-preset-env autoprefixer @fullhuman/postcss-purgecss
```


## Configure and integrate Tailwind

```bash
npx tailwindcss init
# or
yarn tailwindcss init
```

By default this will create a file called `tailwind.config.js` in your project root that looks a little like:


```js
// tailwind.config.js

module.exports = {
  future: {},
  purge: [],
  theme: {
    extend: {},
  },
  variants: {},
  plugins: [],
}
```

## Configure PostCSS with PurgeCSS

Inside your project root, create the file `postcss.config.js` and add the following:
Please make sure to update tests as appropriate.

```js
// postcss.config.js

const purgecss = [
  '@fullhuman/postcss-purgecss',
  {
    content: ['./components/**/*.js', './pages/**/*.js'],
    defaultExtractor: (content) => content.match(/[\w-/:]+(?<!:)/g) || [],
  },
];

module.exports = {
  plugins: [
    'postcss-import',
    'tailwindcss',
    'autoprefixer',
    ...(process.env.NODE_ENV === 'production' ? [purgecss] : []),
  ],
};

```

### Done with setup. That’s it! 🎉

# Using Tailwind

## Import Tailwind into your CSS

Create a CSS file inside your project. I’ve created the directory and file `styles/index.css` and added the following:

```
// styles/index.css

@tailwind base;
/* Write your own custom base styles here */

@tailwind components;
/* Write your own custom component styles here */

@tailwind utilities;
/* Your own custom utilities */

```

## Import your CSS with Next.js

Create a file at pages/_app.js, or if you have one already, this is where you should import the stylesheet we created.

```js
import '../styles/index.css'

export default function MyApp({ Component, pageProps }) {
  return <Component {...pageProps} />
}

```


# Links

- [Get up and running with Tailwind CSS and Next.js](https://dev.to/notrab/get-up-and-running-with-tailwind-css-and-next-js-3a73)
- [Next.js](https://github.com/zeit/next.js)
- [Tailwind CSS](https://tailwindcss.com/)



