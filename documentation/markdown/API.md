---
title: E-Commerce User & Order Management API v1.0.0
language_tabs:
  - shell: cURL
  - javascript: JavaScript
  - java: Java
language_clients:
  - shell: ""
  - javascript: ""
  - java: ""
toc_footers: []
includes: []
search: true
highlight_theme: darkula
headingLevel: 2

---

<!-- Generator: Widdershins v4.0.1 -->

<h1 id="e-commerce-user-and-order-management-api">E-Commerce User & Order Management API v1.0.0</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

Eine professionelle Demo-API zur Verwaltung von Benutzern, Bestellungen, Produkten und Metriken im Rahmen des API-First Workflow-Designs.

Base URLs:

* <a href="http://127.0.0.1:4010">http://127.0.0.1:4010</a>

* <a href="http://api-staging.example.com/v1">http://api-staging.example.com/v1</a>

* <a href="http://api.example.com/v1">http://api.example.com/v1</a>

Email: <a href="mailto:api-support@example.com">API Support Team</a> Web: <a href="https://developer.example.com">API Support Team</a> 
License: <a href="https://opensource.org/licenses/MIT">MIT</a>

<h1 id="e-commerce-user-and-order-management-api-users">Users</h1>

Endpunkte zur Verwaltung von Benutzerkonten und Profilen

## Liste aller Benutzer abrufen

<a id="opIdgetUsers"></a>

> Code samples

```shell
# You can also use wget
curl -X GET http://127.0.0.1:4010/users \
  -H 'Accept: application/json'

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('http://127.0.0.1:4010/users',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```java
URL obj = new URL("http://127.0.0.1:4010/users");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

`GET /users`

Gibt eine paginierte Liste registrierter Benutzer zurück.

<h3 id="liste-aller-benutzer-abrufen-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|limit|query|integer|false|Anzahl der zurückzugebenden Elemente (Standard: 20)|
|offset|query|integer|false|Versatz für Paginierung|

> Example responses

> 200 Response

```json
[
  {
    "id": "a0eebc99-9c0b-4ef8-bb6d-6bb9bd380a11",
    "username": "johndoe",
    "email": "john.doe@example.com",
    "firstName": "John",
    "lastName": "Doe",
    "createdAt": "2026-08-13T08:30:00Z"
  }
]
```

<h3 id="liste-aller-benutzer-abrufen-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Liste der Benutzer erfolgreich abgerufen|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Ungültige Anfrage / Parameter|[ApiError](#schemaapierror)|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Unerwarteter Serverfehler|[ApiError](#schemaapierror)|

<h3 id="liste-aller-benutzer-abrufen-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[User](#schemauser)]|false|none|none|
|» id|string(uuid)|true|none|none|
|» username|string|true|none|none|
|» email|string(email)|true|none|none|
|» firstName|string|false|none|none|
|» lastName|string|false|none|none|
|» createdAt|string(date-time)|true|none|none|

<aside class="success">
This operation does not require authentication
</aside>

## Neuen Benutzer anlegen

<a id="opIdcreateUser"></a>

> Code samples

```shell
# You can also use wget
curl -X POST http://127.0.0.1:4010/users \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```javascript
const inputBody = '{
  "username": "johndoe",
  "email": "john.doe@example.com",
  "firstName": "John",
  "lastName": "Doe"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('http://127.0.0.1:4010/users',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```java
URL obj = new URL("http://127.0.0.1:4010/users");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

`POST /users`

Erstellt ein neues Benutzerkonto im System.

> Body parameter

```json
{
  "username": "johndoe",
  "email": "john.doe@example.com",
  "firstName": "John",
  "lastName": "Doe"
}
```

<h3 id="neuen-benutzer-anlegen-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[UserCreate](#schemausercreate)|true|none|

> Example responses

> Benutzer erfolgreich erstellt

```json
{
  "id": "a0eebc99-9c0b-4ef8-bb6d-6bb9bd380a11",
  "username": "johndoe",
  "email": "john.doe@example.com",
  "firstName": "John",
  "lastName": "Doe",
  "createdAt": "2026-08-13T08:30:00Z"
}
```

> 400 Response

```json
{
  "type": "https://api.example.com/errors/not-found",
  "title": "Resource Not Found",
  "status": 404,
  "detail": "Die angeforderte Ressource konnte nicht gefunden werden.",
  "instance": "/users/a0eebc99-9c0b-4ef8-bb6d-6bb9bd380a11"
}
```

<h3 id="neuen-benutzer-anlegen-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Benutzer erfolgreich erstellt|[User](#schemauser)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Ungültige Anfrage / Parameter|[ApiError](#schemaapierror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validierungsfehler in den Request-Daten|[ApiError](#schemaapierror)|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|201|Location|string||URI des neu erstellten Benutzers|

<aside class="success">
This operation does not require authentication
</aside>

## Benutzer nach ID abrufen

<a id="opIdgetUserById"></a>

> Code samples

```shell
# You can also use wget
curl -X GET http://127.0.0.1:4010/users/{userId} \
  -H 'Accept: application/json'

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('http://127.0.0.1:4010/users/{userId}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```java
URL obj = new URL("http://127.0.0.1:4010/users/{userId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

`GET /users/{userId}`

Liefert die Details eines spezifischen Benutzers anhand seiner UUID.

<h3 id="benutzer-nach-id-abrufen-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|string(uuid)|true|Eindeutige UUID des Benutzers|

> Example responses

> 200 Response

```json
{
  "id": "a0eebc99-9c0b-4ef8-bb6d-6bb9bd380a11",
  "username": "johndoe",
  "email": "john.doe@example.com",
  "firstName": "John",
  "lastName": "Doe",
  "createdAt": "2026-08-13T08:30:00Z"
}
```

<h3 id="benutzer-nach-id-abrufen-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Benutzer gefunden|[User](#schemauser)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Ungültige Anfrage / Parameter|[ApiError](#schemaapierror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Die angeforderte Ressource wurde nicht gefunden|[ApiError](#schemaapierror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validierungsfehler in den Request-Daten|[ApiError](#schemaapierror)|

<aside class="success">
This operation does not require authentication
</aside>

## Benutzer vollständig aktualisieren

<a id="opIdupdateUser"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT http://127.0.0.1:4010/users/{userId} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```javascript
const inputBody = '{
  "username": "johndoe_updated",
  "email": "john.doe.updated@example.com",
  "firstName": "John",
  "lastName": "Doe"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('http://127.0.0.1:4010/users/{userId}',
{
  method: 'PUT',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```java
URL obj = new URL("http://127.0.0.1:4010/users/{userId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PUT");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

`PUT /users/{userId}`

Ersetzt die Stammdaten eines bestehenden Benutzers.

> Body parameter

```json
{
  "username": "johndoe_updated",
  "email": "john.doe.updated@example.com",
  "firstName": "John",
  "lastName": "Doe"
}
```

<h3 id="benutzer-vollständig-aktualisieren-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|string(uuid)|true|none|
|body|body|[UserCreate](#schemausercreate)|true|none|

> Example responses

> 200 Response

```json
{
  "id": "a0eebc99-9c0b-4ef8-bb6d-6bb9bd380a11",
  "username": "johndoe",
  "email": "john.doe@example.com",
  "firstName": "John",
  "lastName": "Doe",
  "createdAt": "2026-08-13T08:30:00Z"
}
```

<h3 id="benutzer-vollständig-aktualisieren-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Benutzer erfolgreich aktualisiert|[User](#schemauser)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Ungültige Anfrage / Parameter|[ApiError](#schemaapierror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Die angeforderte Ressource wurde nicht gefunden|[ApiError](#schemaapierror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validierungsfehler in den Request-Daten|[ApiError](#schemaapierror)|

<aside class="success">
This operation does not require authentication
</aside>

## Benutzer löschen

<a id="opIddeleteUser"></a>

> Code samples

```shell
# You can also use wget
curl -X DELETE http://127.0.0.1:4010/users/{userId} \
  -H 'Accept: application/json'

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('http://127.0.0.1:4010/users/{userId}',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```java
URL obj = new URL("http://127.0.0.1:4010/users/{userId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

`DELETE /users/{userId}`

Entfernt einen Benutzer dauerhaft aus dem System.

<h3 id="benutzer-löschen-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|string(uuid)|true|none|

> Example responses

> 400 Response

```json
{
  "type": "https://api.example.com/errors/not-found",
  "title": "Resource Not Found",
  "status": 404,
  "detail": "Die angeforderte Ressource konnte nicht gefunden werden.",
  "instance": "/users/a0eebc99-9c0b-4ef8-bb6d-6bb9bd380a11"
}
```

<h3 id="benutzer-löschen-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Benutzer erfolgreich gelöscht|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Ungültige Anfrage / Parameter|[ApiError](#schemaapierror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Die angeforderte Ressource wurde nicht gefunden|[ApiError](#schemaapierror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validierungsfehler in den Request-Daten|[ApiError](#schemaapierror)|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="e-commerce-user-and-order-management-api-products">Products</h1>

Endpunkte für den Produktkatalog und Inventarabfragen

## Produktkatalog durchsuchen

<a id="opIdgetProducts"></a>

> Code samples

```shell
# You can also use wget
curl -X GET http://127.0.0.1:4010/products \
  -H 'Accept: application/json'

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('http://127.0.0.1:4010/products',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```java
URL obj = new URL("http://127.0.0.1:4010/products");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

`GET /products`

Ruft alle verfügbaren Produkte im Katalog ab.

<h3 id="produktkatalog-durchsuchen-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|category|query|string|false|none|

> Example responses

> 200 Response

```json
[
  {
    "id": "b5c1a8d0-1234-5678-90ab-cdef12345678",
    "title": "Ergonomische Tastatur",
    "description": "Kabellose Tastatur mit geteiltem Tastenfeld.",
    "price": 129.99,
    "currency": "EUR",
    "sku": "KB-ERG-01"
  }
]
```

<h3 id="produktkatalog-durchsuchen-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Erfolgreiche Produktabfrage|Inline|

<h3 id="produktkatalog-durchsuchen-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[Product](#schemaproduct)]|false|none|none|
|» id|string(uuid)|true|none|none|
|» title|string|true|none|none|
|» description|string|false|none|none|
|» price|number(float)|true|none|none|
|» currency|string|true|none|none|
|» sku|string|true|none|none|

<aside class="success">
This operation does not require authentication
</aside>

## Einzelnes Produkt abrufen

<a id="opIdgetProductById"></a>

> Code samples

```shell
# You can also use wget
curl -X GET http://127.0.0.1:4010/products/{productId} \
  -H 'Accept: application/json'

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('http://127.0.0.1:4010/products/{productId}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```java
URL obj = new URL("http://127.0.0.1:4010/products/{productId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

`GET /products/{productId}`

Liefert die Einzelheiten eines spezifischen Produkts.

<h3 id="einzelnes-produkt-abrufen-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|productId|path|string(uuid)|true|none|

> Example responses

> 200 Response

```json
{
  "id": "b5c1a8d0-1234-5678-90ab-cdef12345678",
  "title": "Ergonomische Tastatur",
  "description": "Kabellose Tastatur mit geteiltem Tastenfeld.",
  "price": 129.99,
  "currency": "EUR",
  "sku": "KB-ERG-01"
}
```

<h3 id="einzelnes-produkt-abrufen-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Produkt gefunden|[Product](#schemaproduct)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Ungültige Anfrage / Parameter|[ApiError](#schemaapierror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Die angeforderte Ressource wurde nicht gefunden|[ApiError](#schemaapierror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validierungsfehler in den Request-Daten|[ApiError](#schemaapierror)|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="e-commerce-user-and-order-management-api-orders">Orders</h1>

Endpunkte zur Erstellung und Verfolgung von Kundenbestellungen

## Bestellungen auflisten

<a id="opIdgetOrders"></a>

> Code samples

```shell
# You can also use wget
curl -X GET http://127.0.0.1:4010/orders \
  -H 'Accept: application/json'

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('http://127.0.0.1:4010/orders',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```java
URL obj = new URL("http://127.0.0.1:4010/orders");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

`GET /orders`

Ruft alle Bestellungen ab (gefiltert nach Status oder Kunde).

<h3 id="bestellungen-auflisten-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|status|query|string|false|none|

#### Enumerated Values

|Parameter|Value|
|---|---|
|status|pending|
|status|processing|
|status|shipped|
|status|delivered|
|status|cancelled|

> Example responses

> 200 Response

```json
[
  {
    "id": "c9f8a7b6-5432-10fe-dcba-9876543210fe",
    "userId": "a0eebc99-9c0b-4ef8-bb6d-6bb9bd380a11",
    "items": [
      {
        "productId": "b5c1a8d0-1234-5678-90ab-cdef12345678",
        "quantity": 2,
        "unitPrice": 129.99
      }
    ],
    "totalAmount": 259.98,
    "status": "processing",
    "createdAt": "2026-08-13T08:45:00Z"
  }
]
```

<h3 id="bestellungen-auflisten-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Bestellungsübersicht erfolgreich abgerufen|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Ungültige Anfrage / Parameter|[ApiError](#schemaapierror)|

<h3 id="bestellungen-auflisten-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[Order](#schemaorder)]|false|none|none|
|» id|string(uuid)|true|none|none|
|» userId|string(uuid)|true|none|none|
|» items|[[OrderItem](#schemaorderitem)]|true|none|none|
|»» productId|string(uuid)|true|none|none|
|»» quantity|integer|true|none|none|
|»» unitPrice|number(float)|true|none|none|
|» totalAmount|number(float)|true|none|none|
|» status|string|true|none|none|
|» createdAt|string(date-time)|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|status|pending|
|status|processing|
|status|shipped|
|status|delivered|
|status|cancelled|

<aside class="success">
This operation does not require authentication
</aside>

## Neue Bestellung aufgeben

<a id="opIdcreateOrder"></a>

> Code samples

```shell
# You can also use wget
curl -X POST http://127.0.0.1:4010/orders \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```javascript
const inputBody = '{
  "userId": "a0eebc99-9c0b-4ef8-bb6d-6bb9bd380a11",
  "items": [
    {
      "productId": "b5c1a8d0-1234-5678-90ab-cdef12345678",
      "quantity": 2,
      "unitPrice": 129.99
    }
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('http://127.0.0.1:4010/orders',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```java
URL obj = new URL("http://127.0.0.1:4010/orders");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

`POST /orders`

Erstellt eine neue Bestellung im System.

> Body parameter

```json
{
  "userId": "a0eebc99-9c0b-4ef8-bb6d-6bb9bd380a11",
  "items": [
    {
      "productId": "b5c1a8d0-1234-5678-90ab-cdef12345678",
      "quantity": 2,
      "unitPrice": 129.99
    }
  ]
}
```

<h3 id="neue-bestellung-aufgeben-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[OrderCreate](#schemaordercreate)|true|none|

> Example responses

> 201 Response

```json
{
  "id": "c9f8a7b6-5432-10fe-dcba-9876543210fe",
  "userId": "a0eebc99-9c0b-4ef8-bb6d-6bb9bd380a11",
  "items": [
    {
      "productId": "b5c1a8d0-1234-5678-90ab-cdef12345678",
      "quantity": 2,
      "unitPrice": 129.99
    }
  ],
  "totalAmount": 259.98,
  "status": "processing",
  "createdAt": "2026-08-13T08:45:00Z"
}
```

<h3 id="neue-bestellung-aufgeben-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Bestellung erfolgreich aufgegeben|[Order](#schemaorder)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Ungültige Anfrage / Parameter|[ApiError](#schemaapierror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validierungsfehler in den Request-Daten|[ApiError](#schemaapierror)|

<aside class="success">
This operation does not require authentication
</aside>

## Bestellungsdetails abrufen

<a id="opIdgetOrderById"></a>

> Code samples

```shell
# You can also use wget
curl -X GET http://127.0.0.1:4010/orders/{orderId} \
  -H 'Accept: application/json'

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('http://127.0.0.1:4010/orders/{orderId}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```java
URL obj = new URL("http://127.0.0.1:4010/orders/{orderId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

`GET /orders/{orderId}`

Gibt Details zu einer konkreten Bestellung zurück.

<h3 id="bestellungsdetails-abrufen-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|orderId|path|string(uuid)|true|none|

> Example responses

> 200 Response

```json
{
  "id": "c9f8a7b6-5432-10fe-dcba-9876543210fe",
  "userId": "a0eebc99-9c0b-4ef8-bb6d-6bb9bd380a11",
  "items": [
    {
      "productId": "b5c1a8d0-1234-5678-90ab-cdef12345678",
      "quantity": 2,
      "unitPrice": 129.99
    }
  ],
  "totalAmount": 259.98,
  "status": "processing",
  "createdAt": "2026-08-13T08:45:00Z"
}
```

<h3 id="bestellungsdetails-abrufen-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Bestellung gefunden|[Order](#schemaorder)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Ungültige Anfrage / Parameter|[ApiError](#schemaapierror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Die angeforderte Ressource wurde nicht gefunden|[ApiError](#schemaapierror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validierungsfehler in den Request-Daten|[ApiError](#schemaapierror)|

<aside class="success">
This operation does not require authentication
</aside>

# Schemas

<h2 id="tocS_User">User</h2>
<!-- backwards compatibility -->
<a id="schemauser"></a>
<a id="schema_User"></a>
<a id="tocSuser"></a>
<a id="tocsuser"></a>

```json
{
  "id": "a0eebc99-9c0b-4ef8-bb6d-6bb9bd380a11",
  "username": "johndoe",
  "email": "john.doe@example.com",
  "firstName": "John",
  "lastName": "Doe",
  "createdAt": "2026-08-13T08:30:00Z"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string(uuid)|true|none|none|
|username|string|true|none|none|
|email|string(email)|true|none|none|
|firstName|string|false|none|none|
|lastName|string|false|none|none|
|createdAt|string(date-time)|true|none|none|

<h2 id="tocS_UserCreate">UserCreate</h2>
<!-- backwards compatibility -->
<a id="schemausercreate"></a>
<a id="schema_UserCreate"></a>
<a id="tocSusercreate"></a>
<a id="tocsusercreate"></a>

```json
{
  "username": "johndoe",
  "email": "john.doe@example.com",
  "firstName": "John",
  "lastName": "Doe"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|username|string|true|none|none|
|email|string(email)|true|none|none|
|firstName|string|false|none|none|
|lastName|string|false|none|none|

<h2 id="tocS_Product">Product</h2>
<!-- backwards compatibility -->
<a id="schemaproduct"></a>
<a id="schema_Product"></a>
<a id="tocSproduct"></a>
<a id="tocsproduct"></a>

```json
{
  "id": "b5c1a8d0-1234-5678-90ab-cdef12345678",
  "title": "Ergonomische Tastatur",
  "description": "Kabellose Tastatur mit geteiltem Tastenfeld.",
  "price": 129.99,
  "currency": "EUR",
  "sku": "KB-ERG-01"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string(uuid)|true|none|none|
|title|string|true|none|none|
|description|string|false|none|none|
|price|number(float)|true|none|none|
|currency|string|true|none|none|
|sku|string|true|none|none|

<h2 id="tocS_Order">Order</h2>
<!-- backwards compatibility -->
<a id="schemaorder"></a>
<a id="schema_Order"></a>
<a id="tocSorder"></a>
<a id="tocsorder"></a>

```json
{
  "id": "c9f8a7b6-5432-10fe-dcba-9876543210fe",
  "userId": "a0eebc99-9c0b-4ef8-bb6d-6bb9bd380a11",
  "items": [
    {
      "productId": "b5c1a8d0-1234-5678-90ab-cdef12345678",
      "quantity": 2,
      "unitPrice": 129.99
    }
  ],
  "totalAmount": 259.98,
  "status": "processing",
  "createdAt": "2026-08-13T08:45:00Z"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string(uuid)|true|none|none|
|userId|string(uuid)|true|none|none|
|items|[[OrderItem](#schemaorderitem)]|true|none|none|
|totalAmount|number(float)|true|none|none|
|status|string|true|none|none|
|createdAt|string(date-time)|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|status|pending|
|status|processing|
|status|shipped|
|status|delivered|
|status|cancelled|

<h2 id="tocS_OrderItem">OrderItem</h2>
<!-- backwards compatibility -->
<a id="schemaorderitem"></a>
<a id="schema_OrderItem"></a>
<a id="tocSorderitem"></a>
<a id="tocsorderitem"></a>

```json
{
  "productId": "b5c1a8d0-1234-5678-90ab-cdef12345678",
  "quantity": 2,
  "unitPrice": 129.99
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|productId|string(uuid)|true|none|none|
|quantity|integer|true|none|none|
|unitPrice|number(float)|true|none|none|

<h2 id="tocS_OrderCreate">OrderCreate</h2>
<!-- backwards compatibility -->
<a id="schemaordercreate"></a>
<a id="schema_OrderCreate"></a>
<a id="tocSordercreate"></a>
<a id="tocsordercreate"></a>

```json
{
  "userId": "a0eebc99-9c0b-4ef8-bb6d-6bb9bd380a11",
  "items": [
    {
      "productId": "b5c1a8d0-1234-5678-90ab-cdef12345678",
      "quantity": 2,
      "unitPrice": 129.99
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|userId|string(uuid)|true|none|none|
|items|[[OrderItem](#schemaorderitem)]|true|none|none|

<h2 id="tocS_ApiError">ApiError</h2>
<!-- backwards compatibility -->
<a id="schemaapierror"></a>
<a id="schema_ApiError"></a>
<a id="tocSapierror"></a>
<a id="tocsapierror"></a>

```json
{
  "type": "https://api.example.com/errors/not-found",
  "title": "Resource Not Found",
  "status": 404,
  "detail": "Die angeforderte Ressource konnte nicht gefunden werden.",
  "instance": "/users/a0eebc99-9c0b-4ef8-bb6d-6bb9bd380a11"
}

```

Standardisiertes Fehlerformat angelehnt an RFC 7807 (Problem Details).

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|type|string(uri)|true|none|none|
|title|string|true|none|none|
|status|integer|true|none|none|
|detail|string|true|none|none|
|instance|string(uri-reference)|false|none|none|

