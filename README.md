## Introduction

run:

```console
$ pipenv install && pipenv shell
$ npm install --prefix client
$ cd server
$ flask db upgrade
$ python seed.py
```

```console
$ python app.py
```

And you can run React in another terminal with:

```console
$ npm start --prefix client
```

```
"proxy": "http://localhost:5555",
```

The proxy avoids CORS issues and allows the server to set a session cookie to
store the user's login data.

### Sessions

- `Login` is located at `/login`.

  - It has one route, `post()`.
  - `post()` gets a `username` from `request`'s JSON.
  - `post()` retrieves the user by `username` (we made these unique for you).
  - `post()` sets the session's `user_id` value to the user's `id`.
  - `post()` returns the user as JSON with a 200 status code.

- `Logout` is located at `/logout`.

  - It has one route, `delete()`.
  - `delete()` removes the `user_id` value from the session.
  - `delete()` returns no data and a 204 (No Content) status code.

- `CheckSession` is located at `/check_session`.
  - It has one route, `get()`.
  - `get()` retrieves the `user_id` value from the session.
  - If the session has a `user_id`, `get()` returns the user as JSON with a 200
    status code.
  - If the session does not have a `user_id`, `get()` returns no data and a 401
    (Unauthorized) status code.

---
