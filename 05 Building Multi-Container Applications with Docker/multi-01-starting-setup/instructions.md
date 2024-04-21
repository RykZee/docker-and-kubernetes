# Instructions for mongo database, backend server and frontend server

For MongoDB:
`docker run --name mongodb -d --rm -v data:/data/db --network goals-net -e MONGO_INITDB_ROOT_USERNAME=sebastian -e MONGO_INITDB_ROOT_PASSWORD=secret mongo`
It's a named container which has a named volume mapping to `/data/db` where mongo stores its data so it'll persist between starts and stops. It also uses the goals-net network which means we can use it by name from our backend server.
The mongo DB is also initialized with a username and password

For backend:
`docker run --name goals-backend -v "$(pwd):/app" -v "$(pwd)/logs:/app/logs" -v /app/node_modules -e MONGODB_USERNAME=sebastian -e MONGODB_PASSWORD=secret --rm -d -p 80:80 --network goals-net goals-node`
The docker run command mounts 3 volumes, first for the whole app source code, second for logs and thirdly for node_modules which is required after npm install. Environment variables are also passed in to set username and password and port 80 is required in order for frontend to be able to communicate through localhost via http requests.

For frontend:
`docker run --name goals-frontend --rm -d -v "$(pwd)/src:/app/src" -p 3000:3000 goals-react`
The src directory is bound so that we can rewrite code and see the changes without needing to rebuild everything. Port 3000 is used since the frontend application is running in the browser.
