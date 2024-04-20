## Instructions for Networking with docker.

instead of localhost will be `host.docker.internal` to communicate with internal ports etc

To create a network
`docker network create <NAME_OF_NETWORK>`

Then to run a container using that network:
`docker run --name <SOME_NAME> -d --network <NAME_OF_NETWORK> mongo`
