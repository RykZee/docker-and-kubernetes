# Utility Containers
Utility containers can take extra arguments which override its entrypoint. So in the Node image for instance, instead of starting a node repl, you could instead run _npm init_

After first building the image, you can run
`docker run -it --rm -v "$(pwd):/tools" <IMAGE_NAME> init`
You will then get the prompt and after get a package.json file in your local file system. You could run it again using:
`docker run -it --rm -v "$(pwd):/tools" <IMAGE_NAME> install`
Which would also give you a package-lock.json file

## Docker Compose
With the Docker compose, instead of up command you use the run command, like this:
`docker-compose run --rm npm init`
Note the rm option, because run doesn't remove immediately after creation, like up does.
