# Mongoku on Wodby

A web interface for the MongoDB service of the environment, from the upstream Mongoku image.

## Link and login

- The required `db` link points to one MongoDB service and sets `MONGOKU_DEFAULT_HOST` to a connection URL that includes the credentials of the environment's database user. Mongoku opens that server without asking for database credentials, with that user's access.
- The interface itself is protected with HTTP basic authentication (`MONGOKU_AUTH_BASIC`): user `admin` and a password generated once per environment (token `admin_password`).
- The interface listens on port `3100`. `MONGOKU_SERVER_ORIGIN` is set to the service's primary URL, so the interface is meant to be opened at that URL.

## Configuration

- Setting `read_only` (`MONGOKU_READ_ONLY_MODE`): prevents write operations from the interface. Off by default.
- `MONGOKU_EXCLUDE_DATABASES` hides the `admin`, `config` and `local` databases.

The service has no volume.
