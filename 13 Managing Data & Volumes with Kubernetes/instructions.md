# Kubernetes and Volumes
First build the image with your dockerhub name and push it there.
Make sure minikube is up `minikube status` otherwise start it `minikube start --driver=docker`

Run the kubernetes cluster
`kubectl apply -f deploy.yaml -f service.yaml`

