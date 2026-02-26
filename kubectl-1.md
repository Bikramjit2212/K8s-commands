Here are some commonly used kubectl commands in K8s

1. 
Create a Pod:
kubectl run <pod-name> --image=<image-name>

Example:
kubectl run nginx --image=nginx

2.
Create a configmap:
- From literal values:
kubectl create configmap <configmap-name> --from-literal=<key>=<value>

Example:
kubectl create configmap website --from-literal=name=bikram
describe -> kubectl describe configmap website

3. 
Insert a file in configmap
kubectl create configmap <config-name> --from-file=<file-path>

example:
kubectl create configmap exams --from-file=bikram.txt
<!-- 
create a file bikram.txt -> vim bikram.txt
close vim -> "ESC" + ":" + "w" + "q" + "!"
-->
describe -> kubectl describe configmap exams

3. 
Create a secret:
From literal values:
kubectl create secret generic <secret-name> --from-literal=<key>=<value>

example:
kubectl create secret generic website --from-literal=username=admin --from-literal=password=secret

<!-- 
kubectl get secret website -O yaml
decode -> echo <encoded-code> | base64 --decode
encode -> echo <decoded-code> | base64 --encode 
-->
From a file:
kubectl create secret generic <secret-name> --from-file=<file-path>
Example:
kubectl create secret generic exams --from-file=bikram.txt

4. 
create a deployment:
kubectl create deployment <deployment-name> --image=<image-name>

Example:
kubectl create deployment nginx-deployment --image=nginx

5. 
Scale a deployment:
kubectl scale deployment <deployment-name> --replicas=<nuber-of-replicas>

example:
kubectl scale deployment nginx-deployment --replicas=3

6. 
Expose a Deployment as a service:
kubectl expose deployment <deployment-name> --port=<port> --target-port=<target-port> --type=<service-type>

example:
kubectl expose deployment nginx-deployment --port=80 --target-port=80 --type=ClusterIP

check service -> kubectl get svc 

check pods ip -> kubectl get pods -o wide


7. 
Update an image in a deployment:
kubectl set image deployment/<deployment-name> <container-name>=<new-image>

example:
kubectl set image deployment/nginx-deployment nginx=nginx:1.19.0

8. 
delete a resource:
kubectl delete <resource-type> <resource-name>

example:
kubectl delete pod nginx-deployment-7c7cd64c48-4vpkj

9. 
Get resource details:
kubectl get <resource-type>

example:
kubectl get pods

kubectl get configmaps -> for configmaps

kubectl get secrets -> for secrets

10. 
Describe a resource:
kubectl describe <resource-type> <resource-name>

example:
kubectl describe pod nginx

11. 
apply a configuration from a file:
kubectl apply -f <file-path>

example:
kubectl apply -f d1.yml
-> k8s is going to d1.yml and then read the yml file
<!-- 
create deployment in dry run -> kubectl create deployment d1 --image=nginx --dry-run=client

create deployment in dry run in yaml format and store it in a yml file -> kubectl create deployment d1 --image=nginx --dry-run=client -o yaml
 -->

12. 
create a namespace:
kubectl create namespace <namespace-name>

example:
kubectl create namespace dev

<!--
- Create a namespace a
Kubectl create namespace a 

- Deploying in the group namespace-a: 
kubectl create deployment team-a-deployment --image=nginx --namespace a 

- To see the deployment in namespace a
kubectl get deployment --namespace a

and whenever dont specify anything it goes into the default
-->

13. 
Set a context for a namespace:
kubectl config set-context --current --namespace=<namespace-name>

example:
kubectl config set-context --current --namespace=dev



