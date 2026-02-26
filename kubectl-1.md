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


