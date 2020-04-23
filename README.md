# k8s for beginners

## Step 1: Install kubernetes (locally)

* OSX ( https://www.docker.com/products/docker-desktop ):
  * within docker-desktop: go to Menu / Preferences / Kubernetes / Enable Kubernetes

* Linux (minikube):
```
   curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-OS_DISTRIBUTION-amd64 && chmod +x minikube && sudo mv minikube /usr/local/bin/
   minikube start
   curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/OS_DISTRIBUTION/amd64/kubectl
   chmod +x ./kubectl
   sudo mv ./kubectl /usr/local/bin/kubectl
```

based on https://docs.bitnami.com/kubernetes/get-started-kubernetes/

## Step 2: Install Dashboard

* Linux (minikube):
  
```
   minikube dashboard
```


## Step 3: Install Helm

* OSX
```
   brew install helm
```

* Linux
```
   curl https://raw.githubusercontent.com/kubernetes/helm/master/scripts/get-helm-3 > get_helm.sh
   chmod 700 get_helm.sh
   ./get_helm.sh
```


# Using helm

## Step 1: Check if helm is working

```
   helm version --short
```

## Step 2: Add chart repo to helm

Search Helm Hub for charts

```
   helm search hub openfaass
```

Add chart repo to helm

```
   helm repo add openfaas https://openfaas.github.io/faas-netes
```

## Step 3: Inspect chart

```
   helm show chart openfaas/openfaas
```

## Step 4: Create a installation target

```
   kubectl create namespace openfaas-fn
```

## Step 5: Install Helm chart

```
   helm install my-openfaas openfaas/openfaas --namespace openfaas-fn
```

## Step 6: Check installation

``` 
   kubectl -n openfaas-fn get deployments -l "release=my-openfaas, app=openfaas"
```

## Step 7: Check status

```
   helm ls
```

