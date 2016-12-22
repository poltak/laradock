# LaraDock Fork

## WhichTeam MongoDB image

Note that now our MongoDB image, used as a container within the WhichTeam App cluster,
is not managed by mupx, but by this Laradock fork. The main purpose of this docker cluster is
to manage images used for running the WhichTeam CMS, but now the database is also included,
since it doesn't really belong anywhere else.

## Building

___(You can skip this step if you're just trying to run the containers).___

Run `docker-compose build` within the repo root.


## Running

Run `docker-compose up -d` within the repo root to start all containers in order in the background.

If you do not need the MongoDB container, if you are using an external DB container, only run
`docker-compose up -d nginx`, which will ensure all containers start apart from `mongodb` and `data`.

## Setting up running MongoDB container with WhichTeam app

__NOTE__: This is the first step in getting WhichTeam app running; this needs to be
done before `mup deploy`.

Make sure you have already run `docker-compose up -d`, as doc'd in the previous step.

Follow the steps to enable a 1-node replication set, so we can use MongoDB oplog:

1. Add the line `replSet=meteor` to the mapped `mongodb.conf` on the docker host; should be in `/opt/mongodb/`
2. Restart the MongoDB container: `docker restart mongodb`
3. Open mongo shell in the MongoDB container: `docker exec -it mongodb mongo`
4. Paste in the following code to start the replication set: `rs.initiate({_id: 'meteor', members: [{ _id: 0, host: '127.0.0.1:27017' }]})`

Now, the MongoDB will be set up permanently and you can `mup deploy` from dev to deploy the
docker container holding the WhichTeam App server.

## Upstream

__NOTE__: master is not kept up-to-date with upstream changes.

[LaraDock](https://github.com/LaraDock/laradock)

