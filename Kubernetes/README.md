# Kubernetes

### How to setup kubernetes on Mac System

For this we have to first check about the chip of mac System. If it is intel based then follow this steps (amd64)

```bash
# To install minikube
brew install minikube

# To start the minikube
minikube start --driver=docker

# To verify whether the minikube is running or not
kubectl cluster-info

```

To stop and delete minikube cluster

```bash
minikube stop
minikube delete
```

If System is mac's own chip that is m1, then follow the below steps (darwin)

```bash
# Downloads the Minikube binary from the URL and saves it to the current directory with the name minikube-darwin-arm64
curl -LO https://github.com/kubernetes/minikube/releases/download/v1.32.0/minikube-darwin-arm64

# makes the binary executable and moves it to the /usr/local/bin
sudo install minikube-darwin-arm64 /usr/local/bin/minikube

# To start the minikube
minikube start --driver=docker

# To verify whether the minikube is running or not
kubectl cluster-info

```

### Few commands that is used in kubernetes

- To set image of deployment lets say deployment name is frontend

```bash
kubectl set image deployment/deployment_name container_name=image_name
# or
kubectl edit deploy and deploy_name
```

- For managing and monitoring resources in Kubernetes.

```bash
kubectl get all
```

### Deployment vs ReplicaSet

In Kubernetes, a Deployment is an object that provides declarative updates for Pods and ReplicaSets. A Deployment is used to manage the deployment and scaling of a set of replicas of your application.

A Deployment provides several benefits over a ReplicaSet:

1. Rolling updates: Deployments allow you to perform rolling updates, meaning that you can update a replica set with a new version of your application without downtime.

2. Rollback: Deployments also provide an easy way to roll back to a previous version of your application if there are issues with the updated version.

3. Scaling: You can easily scale your application, either manually or automatically, by changing the number of replicas in a Deployment. This will create or delete new Pods as required to match the desired state.

4. Automated recovery: If a Pod in a Deployment fails or is terminated, the Deployment controller automatically replaces the Pod with a new one.

- In summary, Deployments provide additional features and functionality over ReplicaSets, such as rolling updates, rollbacks, and automated scaling. While ReplicaSets are responsible for creating and managing a set of replica Pods, Deployments provide a higher level of abstraction that makes it easier to manage and update your application deployments with less downtime and greater reliability.

### Rollout & Versioning

Whenever you create a new deployment or upgrade the images in an existing deployment it triggers a Rollout. A rollout is the process of gradually deploying or upgrading your application containers.

Here is the few commands that is used mostly in rollout and versioning

```bash
# To Check the deployment status of myapp-deployment
kubectl rollout status deployment/myapp-deployment
# To check the rollout history of the deployment
kubectl rollout history deployment/myapp-deployment
```

Whenever we upgrade our application then to deploy the same application we have two deployment strategy

1. Recreate
2. RollingUpdate

In Recreate, suppose if we have 5 replicas of an application then we destroy all of them and recreate the same again. This is not a default deployment strategy.

In RollingUpdate, we destroy one pod at a time and recreate new one. In this strategy our application will be available all times meaning it will available during pod destroy and recreate time also. This is the default deployment strategy provided by Kubernetes.

```bash
# To apply the changes in deployment
kubectl apply –f deployment-definition.yml

```

When a new deployment is created, say to deploy 5 replicas, it first creates a Replicaset automatically, which in turn creates the number of PODs required to meet the number of replicas. When you upgrade your application as we saw in the previous slide, the kubernetes deployment object creates a NEW replicaset under the hoods and starts deploying the containers there. At the same time taking down the PODs in the old replica-set following a RollingUpdate strategy.

Say for instance once you upgrade your application, you realize something isn’t very right. Something’s wrong with the new version of build you used to upgrade. So you would like to rollback your update. Kubernetes deployments allow you to rollback to a previous revision. To undo a change run the command kubectl rollout undo followed by the name of the deployment. The deployment will then destroy the PODs in the new replicaset and bring the older ones up in the old replicaset. And your application is back to its older format.

```bash
# To rollback to the previous deployment version
kubectl rollout undo deployment/myapp-deployment
```

```bash
kubectl run nginx --image=nginx
```

The kubectl run nginx --image=nginx command not only create pod, but under hood it create a deployment name nginx and due to deployment replicaset will automtically created and thus pod will be.
