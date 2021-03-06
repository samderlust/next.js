# Reverse Proxy example

## How to use

### Using `create-next-app`

Execute [`create-next-app`](https://github.com/segmentio/create-next-app) with [Yarn](https://yarnpkg.com/lang/en/docs/cli/create/) or [npx](https://github.com/zkat/npx#readme) to bootstrap the example:

```bash
npx create-next-app --example with-custom-reverse-proxy with-custom-reverse-proxy-app
# or
yarn create next-app --example with-custom-reverse-proxy with-custom-reverse-proxy-app
```

### Download manually

Download the example [or clone the repo](https://github.com/zeit/next.js):

```bash
curl https://codeload.github.com/zeit/next.js/tar.gz/master | tar -xz --strip=2 next.js-master/examples/with-custom-reverse-proxy
cd with-custom-reverse-proxy
```

Install it and run:

```bash
npm install
npm run dev
# or
yarn
yarn dev
```

## The idea behind the example

This example applies this gist https://gist.github.com/jamsesso/67fd937b74989dc52e33 to Nextjs and provides:

* Reverse proxy in development mode by add `http-proxy-middleware` to custom server
* NOT a recommended approach to production scale (hence explicit dev flag) as we should scope proxy as outside UI applications and have separate web server taking care of that.

Sorry for the extra packages. I belong to the minority camp of writing ES6 code on Windows developers. Essentially you only need `http-proxy-middleware` on top of bare-bone Nextjs setup to run this example.

## What it does

Take any random query string to the index page and does a GET to `/api/<query string>` which gets routed internally to `https://swapi.co/api/<query string>`, or any API endpoint you wish to configure through the proxy.

## Expectation

/api/people/2 routed to https://swapi.co/api/people/2
Try Reset

```json
{
  "name": "C-3PO",
  "height": "167",
  "mass": "75",
  "hair_color": "n/a",
  "skin_color": "gold",
  "eye_color": "yellow",
  "birth_year": "112BBY",
  "gender": "n/a",
  "homeworld": "https://swapi.co/api/planets/1/",
  "films": [
    "https://swapi.co/api/films/2/",
    "https://swapi.co/api/films/5/",
    "https://swapi.co/api/films/4/",
    "https://swapi.co/api/films/6/",
    "https://swapi.co/api/films/3/",
    "https://swapi.co/api/films/1/"
  ],
  "species": ["https://swapi.co/api/species/2/"],
  "vehicles": [],
  "starships": [],
  "created": "2014-12-10T15:10:51.357000Z",
  "edited": "2014-12-20T21:17:50.309000Z",
  "url": "https://swapi.co/api/people/2/"
}
```
