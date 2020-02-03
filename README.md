# wait-for

[![Build Status](https://img.shields.io/drone/build/xoxys/wait-for?logo=drone)](https://cloud.drone.io/xoxys/wait-for)
[![License: MIT](https://img.shields.io/github/license/xoxys/wait-for)](LICENSE)

`./wait-for` is a script designed to synchronize services like docker containers. It is [sh](https://en.wikipedia.org/wiki/Bourne_shell) and [alpine](https://alpinelinux.org/) compatible. It was inspired by [vishnubob/wait-for-it](https://github.com/vishnubob/wait-for-it), but the core has been rewritten at [Eficode](http://eficode.com/) by [dsuni](https://github.com/dsuni) and [mrako](https://github.com/mrako).

When using this tool, you only need to pick the `wait-for` file as part of your project.

## Usage

```Shell
$ ./wait-for host:port [-t timeout] [-- command args]
    -q | --quiet                        Do not output any status messages
    -t TIMEOUT | --timeout=timeout      Timeout in seconds, zero for no timeout
    -- COMMAND ARGS                     Execute command with args after the test finishes
```

## Dependencies

* Installed Netcat

## Examples

To check if [eficode.com](https://eficode.com) is available:

```Shell
$ ./wait-for www.eficode.com:80 -- echo "Eficode site is up"

Connection to www.eficode.com port 80 [tcp/http] succeeded!
Eficode site is up
```

To wait for database container to become available:

```Yaml
version: '2'

services:
  db:
    image: postgres:9.4

  backend:
    build: backend
    command: sh -c './wait-for db:5432 -- npm start'
    depends_on:
      - db
```

### License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

### Maintainers and Contributors

[Robert Kaussow](https://github.com/xoxys) &#8226;
[eficode](https://github.com/eficode) &#8226;
[Marko Klemetti](https://github.com/mrako)
