# Kubernetes with minikube

First build an image and push it to docker hub.
`docker build -t sebastianzee/kub-first-app .`
`docker push sebastianzee/kub-first-app`

Then create a deployment based on that image
`kubectl create deployment first-app --image=sebastianzee/kub-first-app`

in order to update the image then you need to first build and notice that we must add a tag otherwise Kubernetes won't rebuild it.
`docker build -t sebastianzee/kub-first-app:2`

Then docker push
`docker push sebastianzee/kub-first-app:2`

and finally rebuild the image with the following command
`kubectl set image deployment/first-app kub-first-app=sebastianzee/kub-first-app:2`

## Other
Check status of rollouts:
`kubectl rollout status deployment/first-app`

Rollback rollout:
`kubectl rollout undo deployment/first-app`
This will undo the latest deployment

In order to rollout to an older revision. First run 
`kubectl rollout history deployment/first-app`
To see the revision history and to see more details run
`kubectl rollout history deployment/first-app --revision=<REVISION_NUMBER>`
In order to rollback to a specific revision run
`kubectl rollout undo deployment/first-app --to-revision=<REVISION_NUMBER>`

## Declarative commands
After defining yaml files with specification, the file can be applied using
`kubectl apply -f <NAME_OF_FILE.yaml>`

and thereafter deleted using
`kubectl delete -f <NAME_OF_FILE.yaml>`

## minikube
To service the app, meaning making it available in a browser tab.
`minikube service first-app`

To run dashboard:
`minikube dashboard`

## Tips
If you know a command which is long which you want to convert to a yaml file, you can use a shortcut using:
`kubectl create deployment some-app --image=nginx:1.22.1 --port=80 -o yaml > deployment.yaml`

