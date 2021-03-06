# openpaas-videoconference-app

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Run your unit tests
```
npm run test:unit
```

### Run your end-to-end tests
```
npm run test:e2e
```

## Docker

### Build

Before building the image for production, you will have to configure it from an environment file. By default, vue-cli (used by `npm run build`) will set the `NODE_ENV` to production on build step. In order to define production environment values, you will have to create a `.env.production.local` file at the root or the repository and set the required values (copy, paste and adapt `.env` file properties). Once done, you can build the image like:

```
docker build -t linagora/openpaas-videoconference-app .
```

### Run

```
docker run -it -p 8888:80 --rm --name openpaas-videoconference-app linagora/openpaas-videoconference-app
```

In order to define the OpenPaaS endpoint to use (override the `VUE_APP_OPENPAAS_URL` variable from `.env*` files), the `public/env/openpaas.js` file has to be updated. In order to do this, a Docker volume is available in the container and the `openpaas.js` file can be redefined by mounting a volume. By using this, the image is generated once, and can be used in multiple application deployments.

```
docker run -it -p 8888:80 --rm --name openpaas-videoconference-app -v $PWD/.config/env:/usr/share/nginx/html/env linagora/openpaas-videoconference-app
```
