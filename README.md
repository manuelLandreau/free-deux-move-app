# Test technique Free2move
## Front app (Vue js)

**Temps: 2h15 (+ api 2h15)**

### Axe d'amélioration 

- css-purge pour un bundle css plus petit
- Vuex pour séparation vues/appels api et logique
- Clique vers profil super héro pour plus de détail
- Typescript pourquoi pas
- Tests

## Lancer avec docker

```
docker build . -t test-tech/free2move-app
docker run -p 8080:80 -d test-tech/free2move-app
```

-> localhost:8080

## installation sans docker
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

### Run your end-to-end tests
```
npm run test:e2e
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
