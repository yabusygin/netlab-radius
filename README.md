FRADIUS Service for Networking Labs
===================================

A simple RADIUS service for networking labs. The service uses [FreeRADIUS][FreeRADIUS].

[FreeRADIUS]: https://freeradius.org/documentation/

Basic Usage
-----------

Specify settings in the [`clients.conf`][ClientsManual] and
[`authorize`][UsersManual] files.

[ClientsManual]: https://freeradius.org/radiusd/man/clients.conf.html
[UsersManual]: https://freeradius.org/radiusd/man/users.html

Start the service:

```sh
docker compose up --detach
```

Print logs:

```sh
docker compose logs
```

Stop the service:

```sh
docker compose down
```

Testing
-------

Add the following settings to the `snmptrapd.conf` file:

```
client any {
    ipaddr = 0.0.0.0/0
    secret = test-client-password
}
```

Send a test request:

```sh
radtest alice alice-password localhost 0 test-client-password 0 127.0.0.1
```
