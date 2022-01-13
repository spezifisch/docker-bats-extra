# docker-bats-extra

Docker image for BATS with extra libraries

## Usage

In your BATS setup function use `$TEST_HELPER` as prefix for the included libraries:

```shell
setup() {
    load "${TEST_HELPER}/bats-support/load.bash"
    load "${TEST_HELPER}/bats-assert/load.bash"
    load "${TEST_HELPER}/bats-file/load.bash"
}
```

### docker-compose

Example `docker-compose.yaml` if your BATS tests are in the subdirectory `./tests/bats`:

```yaml
services:
  # test runner
  test:
    image: ghcr.io/spezifisch/docker-bats-extra:latest
    volumes:
      # bats test scripts
      - ./tests/bats:/code/tests:ro
    command: "/code/tests"
```

Run tests with:

```console
$ docker-compose run --rm test
```

### Github Action

For a further usage example look at https://github.com/spezifisch/mettmail which uses this image in a Github Action.

## Description

This docker image includes the official [BATS image](https://hub.docker.com/r/bats/bats) along with the following [libraries](https://bats-core.readthedocs.io/en/stable/writing-tests.html#libraries-and-add-ons):

* https://github.com/bats-core/bats-assert
* https://github.com/bats-core/bats-support
* https://github.com/bats-core/bats-file
