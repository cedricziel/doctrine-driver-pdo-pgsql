# doctrine-driver-pdo-pgsql

A doctrine driver for PostgreSQL that supports the unix_socket option

## Why?

When you want to configure the Doctrine DBAL via DSN, you cannot use the
`unix_socket` option. This is a modified driver, which lets you use it.

This is mandatory for services like Google CloudSQL, which primarily relies
on socket connections.

## Installation

```
composer require cedricziel/doctrine-driver-pdo-pgsql
```

## Usage

To use this driver with Symfony, you can add the following to your `doctrine.yaml`
configuration file:

```yaml
doctrine:
    dbal:
        driver_class: App\Doctrine\PgSQLSocketDriver
```

*NOTE:* To enable the driver manager, to select your driver, the DSN supplied via `DATABASE_URL` *must* be schamless.

For example:

```
# previously
DATABASE_URL="postgresql//postgres:postgres@127.0.0.1:5432/postgres?serverVersion=13&charset=utf8"

# afterwards
DATABASE_URL="//postgres:postgres@127.0.0.1:5432/postgres?serverVersion=13&charset=utf8&unix_socket=/path/to/socket"
```

## License

MIT
