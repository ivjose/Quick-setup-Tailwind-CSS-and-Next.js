# CMS Prismic setup

Go to Root directory

## Install dependencies

Use for for conditionally joining `classNames` together.

```bash
npm install --save prismic-javascript prismic-reactjs
# or
yarn add prismic-javascript prismic-reactjs
```

## Create `./lib/prismicClient.js`

```js
import PrismicAPI from 'prismic-javascript';

export const apiEndpoint = process.env.NEXT_PUBLIC_PRISMIC_URL;
export const accessToken = process.env.NEXT_PUBLIC_PRISMIC_TOKEN;

// Client method to query documents from the Prismic repo
export const Client = (req = null) =>
PrismicAPI.client(apiEndpoint, createClientOptions(req, accessToken));

const createClientOptions = (req = null, prismicAccessToken = null) => {
  const reqOption = req ? { req } : {};
  const accessTokenOption = prismicAccessToken
    ? { accessToken: prismicAccessToken }
    : {};
  return {
    ...reqOption,
    ...accessTokenOption,
  };
};

export const Prismic = PrismicAPI;
```
