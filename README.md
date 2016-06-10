# LaraDock Fork

## Building

Run `docker-compose build` within the repo.

## Running

Run `docker-compose up -d` with the `docker-compose.yaml` present in PWD to start all containers in order.

If you do not need the MongoDB container, if you are using an external DB container, only run
`docker-compose up -d nginx`, which will ensure all containers start apart from `mongodb` and `data`.

## Upstream

[LaraDock](https://github.com/LaraDock/laradock)
