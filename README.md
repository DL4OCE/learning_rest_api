# Tools

## Linting

VS Code plugins:

* **Spectral (online verification against .spectral.yaml)**

default rulesets:
>
>npm install -D @stoplight/spectral-rulesets

.spectral.yaml erweitern:
>extends:
>  - spectral:oas
>  - "@stoplight/spectral-rulesets/rulesets/owasp-api"`
>

local pre-commit linting:
>npm install -D husky lint-staged
>npx husky init

extend package.json:

>{
>  "name": "learning0",
>  "version": "1.0.0",
>  "description": "",
>  "main": "index.js",
>  "scripts": {
>    "test": "echo \"Error: no test specified\" && exit 1",
>    "mock": "prism mock openapi-demo.yaml",
>    "lint": "spectral lint openapi-demo.yaml",
>    "prepare": "husky"
>  },
>  "lint-staged": {
>    "*.{yaml,yml}": [
>      "spectral lint"
>    ]
>  },
>  "keywords": [],
>  "author": "",
>  "license": "ISC",
>  "devDependencies": {
>   "@stoplight/prism-cli": "^5.16.0",
>   "@stoplight/spectral-rulesets": "^1.22.7",
>   "husky": "^9.1.7",
>   "lint-staged": "^17.3.0"
>  }
>}

>npx lint-staged

## generate / preview documentation

#### OpenAPI (preview)
* VS Code
    * **OpenAPI (Swagger) Editor: Preview of SwaggerUI / Redoc; json / yaml; IntelliSense**
    * **Swagger Viewer: Preview of Swagger / OpenAPI**
    * OpenAPI  Designer *(deprecated)*
    * Redocly OpenAPI
    * OpenAPI Editor *(deprecated)*

#### Redoc  
>npm install -D @redocly/cli

>npx redocly build-docs openapi-demo.yaml -o documentation/redoc/API.html

#### swaggerUI
>*(npm install -D swagger-ui-watcher)*

>npm install -D @apidevtools/swagger-cli

>npm install -D js-yaml

>npx node -e 'const f=require("fs"),y=require("js-yaml"),s=y.load(f.readFileSync("openapi-demo.yaml","utf8"));f.writeFileSync("documentation/swaggerUI/API.html",`<!DOCTYPE html><html><head><meta charset="utf-8"/><link rel="stylesheet" href="https://unpkg.com/swagger-ui-dist@5/swagger-ui.css"/></head><body><div id="swagger-ui"></div><script src="https://unpkg.com/swagger-ui-dist@5/swagger-ui-bundle.js"></script><script>window.onload=()=>{SwaggerUIBundle({spec:${JSON.stringify(s)},dom_id:"#swagger-ui"})}</script></body></html>`)'


## mock server

* **Prism**: run mock REST API server from openAPI.yaml, locally 

## Testing

* Schemathesis (py): generates dozens of valid and ivalid test cases from openapi.yaml

>pipx install schemathesis

>st run openapi-demo.yaml --url http://127.0.0.1:4010

test mock server
>st run openapi-demo.yaml --url http://127.0.0.1:4010 --phases examples --checks not_a_server_error

* Dredd: *(deprecated)*

* Pact: test micro services by their REST APIs (overkill!)

## markdown representation

#### widdershins

> npm install -D widdershins
>
>npx widdershins openapi-demo.yaml -o documentation/markdown/API.md

nicer:

>npx widdershins openapi-demo.yaml -o documentation/markdown/API.md --language_tabs 'shell:cURL' 'javascript:JavaScript' 'python:Python' --summary

 without code snippets:
 >npx widdershins openapi-demo.yaml -o documentation/markdown/API.md --summary --language_tabs '' --omitHeader


