This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Steps

1) Follow along to:
[This Article](https://www.freecodecamp.org/news/learn-kubernetes-in-under-3-hours-a-detailed-guide-to-orchestrating-containers-114ff420e882/)

2) Clone this project to local

3) Things to install
    1) Docker
    2) Docker Desktop
    3) kubectl
    4) minikube
    Note: Hypervisor not required because of docker desktop. (It'll give a container to minikube)

4) Make sure docker is running and then run code:
    ```
    minikube start
    eval $(minikube docker-env) #Point terminal shell to docker daemon in minikube
    cd projectDirectoryRoot
    docker build -t reactapp . #Builds the docker image file inside minicube instead of local
    #in deployment file we have given imagePullPolicy to never so that it works with the local image only
    kubectl apply -f Manifests/mydeploymentfile.yml  #Will deploy the image into containers and take care of service discoverability
    kubectl get pods #will show new pods are up and running
    kubectl apply -f Manifests/myservicefile.yml  #Will start a load balancer service which will work on the deployed pods/containers
    minikube service react-frontend-lb created #will generate a temp server to run the loadbalancer. Should show the page at work.
    ```