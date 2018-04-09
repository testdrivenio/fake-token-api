# Fake Token API

Fake Node/Express API used to test token-based authentication.

## Project Setup

1. Fork/Clone
1. Install Dependencies - `npm install`
1. Run - `npm start`

## Endpoints

1. GET http://localhost:1337/ping
1. POST http://localhost:1337/register
1. POST http://localhost:1337/login
1. GET http://localhost:1337/status

## Requests

### Register

Success:

```sh
$ curl http://localhost:1337/register \
  -H "Content-Type: application/json" \
  -X POST \
  -d '{"email":"test@test.com", "password": "test"}'

{
  "status": "success",
  "token": "1234567"
}
```

Failure:

```sh
$ curl http://localhost:1337/register \
  -H "Content-Type: application/json" \
  -X POST \
  -d '{"email":"not@right.com", "password": "test"}'

{
  "status": "error"
}
```

### Login

Success:

```sh
$ curl http://localhost:1337/login \
  -H "Content-Type: application/json" \
  -X POST \
  -d '{"email":"test@test.com", "password": "test"}'

{
  "status": "success",
  "token": "1234567"
}
```

Failure:

```sh
$ curl http://localhost:1337/login \
  -H "Content-Type: application/json" \
  -X POST \
  -d '{"email":"bad@email.com", "password": "test"}'

{
  "status": "error"
}
```

### Status

Success:

```sh
$ curl http://localhost:1337/status \
  -H "Content-Type: application/json" \
  -H "Authorization: Token 1234567"

{
  "status": "success"
}
```

Failure:

```sh
$ curl http://localhost:1337/status \
  -H "Content-Type: application/json" \
  -H "Authorization: Token incorrect"

{
  "status": "error"
}
```
