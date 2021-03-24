# Heroku Mono Repo Tutorial

## Prettier

- Let op: installeer `yarn add husky@4.3` (ipv nieuwe versie 5) om problemen te vermijden

## Project klaarmaken

- Zorg dat je een Procfile hebt in beide projecten (leeg bij app, ingevuld bij api)
- Zorg bij je API eventueel dat je via package.json de Node versie meegeeft (`engines`)
- Zorg bij de API dat je `process.env.PORT` gebruikt zodat Heroku dit kan wijzigen

## Heroku

### App

Maak 2 verschillende applicaties aan op Heroku. Kies voor Europa ipv USA.

### Git

Voeg bij beide applicaties toegang tot je Github project toe.

### Buildpacks

Voeg bij instellingen volgende buildpacks toe (in deze volgorde!):

- https://github.com/lstoll/heroku-buildpack-monorepo
- https://buildpack-registry.s3.amazonaws.com/buildpacks/heroku-community/multi-procfile.tgz
- API
  - heroku/nodejs
- APP
  - https://buildpack-registry.s3.amazonaws.com/buildpacks/mars/create-react-app.tgz

### ENV

Voeg bij instellingen volgende Config Vars toe

- API

  | Var      |    Value     |
  | -------- | :----------: |
  | APP_BASE |     api/     |
  | PROCFILE | api/Procfile |

  **Vergeet ook je eigen variabelen niet (degene die je in `.env` had)**

- APP

  | Var      |    Value     |
  | -------- | :----------: |
  | APP_BASE |     app/     |
  | PROCFILE | app/Procfile |

  **Vergeet ook je eigen variabelen niet (degene die je in `.env.development.local` had)**

### Deploy

Deploy de app en kijk
