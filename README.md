# Tools

## Linting

VS Code plugins:

* **Spectral (online verification against .spectral.yaml)**

default rulesets:
>
>npm install -D @stoplight/spectral-rulesets

#### local pre-commit linting
>npm install -D husky lint-staged
>npx husky init

extend package.json:

```
{
  ...
  "scripts": {
    "lint": "spectral lint openapi.yaml",
    "prepare": "husky"
  },
  "lint-staged": {
    "*.{yaml,yml}": [
      "spectral lint"
    ]
  },
  ...
}
```

>npx lint-staged

## documentation generation / preview 

#### OpenAPI (preview)
* VS Code plugins
    * **OpenAPI (Swagger) Editor: Preview of SwaggerUI / Redoc; json / yaml; IntelliSense**
    * **Swagger Viewer: Preview of Swagger / OpenAPI**
    * (OpenAPI  Designer *(deprecated)*)
    * Redocly OpenAPI
    * (OpenAPI Editor *(deprecated)*)

#### Redoc  
```
npm install -D @redocly/cli
npx redocly build-docs openapi.yaml -o documentation/redoc/API.html
```

#### swaggerUI
```
*(npm install -D swagger-ui-watcher)*
npm install -D @apidevtools/swagger-cli
npm install -D js-yaml
npx node -e 'const f=require("fs"),y=require("js-yaml"),s=y.load(f.readFileSync("openapi.yaml","utf8"));f.writeFileSync("documentation/swaggerUI/swaggerUI.html",`<!DOCTYPE html><html><head><meta charset="utf-8"/><link rel="stylesheet" href="https://unpkg.com/swagger-ui-dist@5/swagger-ui.css"/></head><body><div id="swagger-ui"></div><script src="https://unpkg.com/swagger-ui-dist@5/swagger-ui-bundle.js"></script><script>window.onload=()=>{SwaggerUIBundle({spec:${JSON.stringify(s)},dom_id:"#swagger-ui"})}</script></body></html>`)'
```

## mock server

* **Prism**: run mock REST API server from openAPI.yaml, locally 

## Testing

* Schemathesis (py): generates dozens of valid and ivalid test cases from openapi.yaml

```
pipx install schemathesis

# test mock server (contract only, needs examples in your openapi.yaml!!)
st run openapi.yaml --url http://127.0.0.1:4010 --phases examples --checks not_a_server_error
```

* Dredd: *(deprecated)*

* Pact: test micro services by their REST APIs (overkill!)

## markdown representation

#### widdershins

```
npm install -D widdershins
npx widdershins openapi.yaml -o documentation/markdown/API.md --summary --code false --omitHeader
# 
```

```
# nicer
npx widdershins openapi.yaml -o documentation/markdown/API.md --language_tabs 'shell:cURL' 'javascript:JavaScript' 'python:Python' --summary

# without code snippets:
npx widdershins openapi.yaml -o documentation/markdown/API.md --summary --language_tabs '' --omitHeader
```

## CI/CD automation

```
# according to package.json, we can also use pre-defined aliases to perform these tasks

# lint openapi-yaml against .spectral.yaml
npm run lint

# build all dcoumentation files (swagger, redoc, markdown) 
npm run docs:all

# run mock server
npm run mock

# run all tests to verify contract fulfillment
npm run test:contract

```

