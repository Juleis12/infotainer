# Infotainer

A Vue-powered directory of informative YouTube channels.

## Development

```bash
npm install
npm run dev
```

## Production build

```bash
npm run build
npm run preview
```

## Lint

```bash
npm run lint
```

## Deploy

The production build can be published to the `pages` branch with:

```bash
npm run build
npm run deploy
```

The deployment script publishes `dist` to the `pages` branch and configures the `infotainer.tchh.in` CNAME.
