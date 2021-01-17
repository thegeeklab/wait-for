# wait-for

Poor-mans docker service synchronizer

[![Build Status](https://img.shields.io/drone/build/thegeeklab/wait-for?logo=drone&server=https%3A%2F%2Fdrone.thegeeklab.de)](https://drone.thegeeklab.de/thegeeklab/wait-for)
[![Docker Hub](https://img.shields.io/badge/dockerhub-latest-blue.svg?logo=docker&logoColor=white)](https://hub.docker.com/r/thegeeklab/wait-for)
[![Quay.io](https://img.shields.io/badge/quay-latest-blue.svg?logo=docker&logoColor=white)](https://quay.io/repository/thegeeklab/wait-for)
[![GitHub contributors](https://img.shields.io/github/contributors/thegeeklab/wait-for)](https://github.com/thegeeklab/wait-for/graphs/contributors)
[![Source: GitHub](https://img.shields.io/badge/source-github-blue.svg?logo=github&logoColor=white)](https://github.com/thegeeklab/wait-for)
[![License: MIT](https://img.shields.io/github/license/thegeeklab/wait-for)](https://github.com/thegeeklab/wait-for/blob/master/LICENSE)

wait-for is a script designed to synchronize services like docker containers. It is [sh](https://en.wikipedia.org/wiki/Bourne_shell) and [alpine](https://alpinelinux.org/) compatible and was forked from [eficode/wait-for](https://github.com/eficode/wait-for).

When using this tool, you only need to pick the `wait-for` file as part of your project.

## Usage

```Shell
$ wait-for --help
usage: wait-for host:port [-t timeout] [-- command args]

Synchronize services like docker containers and wait for readiness.

optional arguments:
  -q | --quiet                              Do not output any status messages
  -t WAITFOR_TIMEOUT | --timeout=timeout    Timeout in seconds, zero for no timeout
  -- COMMAND ARGS                           Execute command with args after the test finishes
```

## Dependencies

- Installed Netcat

## Examples

To check if [google.com](https://google.com) is available:

```Shell
$ ./wait-for google.com:80 -- echo "Google site is up"

Google site is up
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

## Contributors

Special thanks goes to all [contributors](https://github.com/thegeeklab/wait-for/graphs/contributors). If you would like to contribute,
please see the [instructions](https://github.com/thegeeklab/wait-for/blob/master/CONTRIBUTING.md).

## License

This project is licensed under the MIT License - see the [LICENSE](https://github.com/thegeeklab/wait-for/blob/master/LICENSE) file for details.
