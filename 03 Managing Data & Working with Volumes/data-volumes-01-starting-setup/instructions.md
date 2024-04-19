# Instructions for this section
To create an image first run `docker build -t feedback-node:something .` when standing in the root directory at the same level as the Dockerfile

To run the image, run this command:
`docker run -d --rm -p 3000:80 --name feedback-app -v "$(pwd)/feedback:/app/feedback" -v "$(pwd):/app:ro" -v /app/node_modules -v /app/temp feedback-node:volumes`

This command will run the container in detached mode, removing it when it has stopped, it will publish port 3000 on your local machine to port 80 on the container.
It will also have everything in current directory available in the container in read-only mode, except "feedback" directory and "temp" directory in the container.
It will also add `/app/node_modules` as available in the container but not visible in your local machine, since it is create by npm install from the Dockerfile instructions 

you can build with different arguments using `docker build -t feedback-node:dev --build-arg DEFAULT_PORT=8000`
