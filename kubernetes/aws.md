## AWS EKS
Amazon EKS es un servicio de administración de Kubernetes que facilita la implementación, la administración y el escalamiento de aplicaciones contenerizadas en AWS. Amazon EKS reduce la complejidad de la implementación de Kubernetes, lo que permite que los desarrolladores se centren en la construcción de aplicaciones innovadoras y los operadores en la administración de Kubernetes en AWS sin tener que preocuparse por la infraestructura subyacente.

### eksctl

eksctl es una herramienta de linea de comando para crear y manejar clusters de Kubernetes en AWS. 

### Instalar eksctl

#### Linux

```shell
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
sudo mv /tmp/eksctl /usr/local/bin
```

#### MacOS

```shell
brew tap weaveworks/tap
brew install weaveworks/tap/eksctl
```

### Vamos a crear nuestro primer cluster

Antes de crearlo debemos asegurarnos que tenemos configurado nuestro usuario de AWS con las credenciales correctas.

```shell
aws configure
```

Vamos a crear un cluster y para ellos debemos crear un archivo yaml con la configuración del cluster.

```shell
eksctl create cluster --name demo --version 1.25 --region us-east-1 --nodegroup-name workers --node-type t3.small --nodes 1 --nodes-min 1 --nodes-max 2 --managed
```

Una vez creado nuestro cluster vamos a crear los mismos recursos que creamos en el cluster local. Pero antes modifiquemos el tipo de servicio que vamos a crear a LoadBalancer, de esta forma eks expondra nuestro servicio a internet a través de un LoadBalancer de AWS.


```shell
kubectl apply -f nginx.yaml
```

Una vez creado veamos si nuestro servicio esta expuesto a internet.

```shell
kubectl get svc
```

Al final recuerda eliminar el cluster.

```shell
eksctl delete cluster --name demo
```
