# serverless-nestjs

Fork from [rdlabo-team](https://github.com/rdlabo-team/serverless-nestjs)

This is an example of creating a function that runs as nestjs using the serverless framework.
Sample publish. https://mmjdx4zxmc.execute-api.ap-northeast-1.amazonaws.com/dev/

## How to use

### Prepare

```
$ npm install @nestjs/cli serverless -g
$ git clone git@github.com:rdlabo/serverless-nestjs.git 【projectName】
$ cd 【projectName】
$ npm install
$ npm start
```

### Development

#### use NestCLI

```
$ npm start
```

```
$ npm start
> serverless-nestjs@0.0.0 start /Users/sakakibara/dev/serverless-nestjs
> nest start

[Nest] 3905   - 11/29/2019, 4:40:49 PM   [NestFactory] Starting Nest application...
[Nest] 3905   - 11/29/2019, 4:40:49 PM   [InstanceLoader] AppModule dependencies initialized +20ms
[Nest] 3905   - 11/29/2019, 4:40:49 PM   [RoutesResolver] AppController {/}: +6ms
[Nest] 3905   - 11/29/2019, 4:40:49 PM   [RouterExplorer] Mapped {/, GET} route +3ms
[Nest] 3905   - 11/29/2019, 4:40:49 PM   [NestApplication] Nest application successfully started +4ms
```

Then browse http://localhost:3000

#### use serverless-offline

**after also doing an: `npm run build`**

```powershell
$ serverless offline
```

```
$ serverless offline
Serverless: Starting Offline: dev/us-east-1.

Serverless: Routes for index:
Serverless: ANY /
Serverless: ANY /{proxy*}

Serverless: Offline listening on http://localhost:3000
```

Then browse http://localhost:3000

## How to Deploy

```
$ npm run build && serverless deploy
```

## Options

### Hot start

See : https://serverless.com/blog/keep-your-lambdas-warm/

These behavior can be fixed with the plugin serverless-plugin-warmup

1 Install the plugin

```
$ npm install serverless-plugin-warmup --save-dev
```

2 Enable the plugin

```
plugins:
  - '@hewmen/serverless-plugin-typescript'
  - serverless-plugin-optimize
  - serverless-offline
  - serverless-plugin-warmup

custom:
  # Enable warmup on all functions (only for production and staging)
  warmup:
      - production
      - staging
```

### Use Swagger for development

Browse http://localhost:3000/document
