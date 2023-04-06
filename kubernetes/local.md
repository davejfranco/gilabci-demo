# Intro a Kubernetes

Antes de empezar a trabajar con Kubernetes, es necesario tener instalado Docker.

Lo que haremos a continuación es crear un cluster local de Kubernetes con Minikube pero antes también instalaremos kubectl, una herramienta de línea de comandos para ejecutar comandos contra un clúster de Kubernetes.

Vamos a dar nuestros primeros pasos con Kubernetes, veremos como crear un cluster local, como crear pods, deployments, servicios y como escalarlos. También veremos como ver los logs de los pods y como ejecutar comandos dentro de los pods. Los comandos básicos para que pueda empezar a trabajar con Kubernetes.

A pesar que en el proyecto final van a trabajar con un proyecto más en el frontend sino me equivoco. Como equipo DevOps es importante también conocer esta herramienta porque es muy utilizada en la industria. 


## Instalar kubectl

Documentacion para instalar [aquí](https://kubernetes.io/docs/tasks/tools/)

### Linux
```shell
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"

sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
```
### MacOS
```shell
brew install kubectl
```
### Windows
```shell
choco install kubernetes-cli
```

## Minikube

### Linux
```shell
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```	

### MacOS
```shell
brew install minikube
```

### Iniciar cluster
```shell
minikube start
```

## Herramienta adicional
kubectx y kubens [enlace](https://github.com/ahmetb/kubectx)

### Linux
```shell
sudo apt install kubectx
```

### MacOS
```shell
brew install kubectx
```

### Windows
```shell
choco install kubectx
```

## Comandos básicos de kubectl

### ver nodos
```shell
kubectl get nodes
```

### Crear namespace
```shell
kubectl create namespace webserver
```

### Crear un pod
```shell
kubeclt run nginx --image=nginx:alpine
```

### Ver pods
```shell
kubectl get pods
```

### Ver pods en formato yaml
```shell
kubectl get pods -o yaml
```

### Describir un pod
```shell
kubectl describe pod nginx
```

### Ver logs
```shell
kubectl logs nginx
```

### Ver logs en tiempo real
```shell
kubectl logs -f nginx
```

### Ejectuar un comando en un pod
```shell
kubectl exec nginx -- ls -la
```

### Crear un deployment
```shell
kubectl create deployment nginx --image=nginx:alpine
```

### Escalar un deployment
```shell
kubectl scale deployment nginx --replicas=3
```

### Ver deployments
```shell
kubectl get deployments
```

### Crear servicio
```shell
kubectl expose deployment nginx --port=80 --type=NodePort
```

### Ver servicios
```shell
kubectl get services
```

## Vamos a escribir nuestro primer deployment

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:alpine
        ports:
        - containerPort: 80
```

y nuestro primer servicio

```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx
spec:
  type: ClusterIP
  selector:
    app: nginx
  ports:
  - port: 80
    targetPort: 80
```


