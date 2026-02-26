1. 
Rolling out changes (updating a deployment)

- to apply changes to a deployment (eg: update an image or configuration), use the

kubectl set image deployment/<deployment-name> <container-name>=<new-image>

example:
kubectl set image deployment/my-app my-app-container=my-app:v2 

<!-- 
updating nginx image from 1.19.0 to 20 -> kubectl set image deployment/nginx-deployment nginx=nginx:20
 -->

- to view the rollout status of the deployment:
kubectl rollout status deployment/<deployment-name>

example:
kubectl rollout status deployment/nginx-deployment

2. 
checking rollout history:
- to see the revision history of the deployment:
kubectl rollout history deployment/<deployment-name>

example:
kubectl rollout history deployment/nginx-deployment

- to view more details about a specific revision:
kubectl rollout history deployment/<deployment-name> --revision=<revision-number>

example:
kubectl rollout history deployment/nginx-deployemnt --revision=2

3. 
- rolling back changes:
kubectl rollout undo deployment/<deployment-name>

example:
kubectl rollout undo deployment/nginx-deployment

- to rollback a specific version:
kubectl rollout undo deployment/<deployment-name> --to-revision=<revision-number>

example:
kubectl rollout undo deployment/nginx-deployment --to-revision=1


4. 
- pause and resume a rollout
to pause a rollout(useful if you want to stop an automatic deployment in the middle)

kubectl rollout pause deployment/<deployment-name>

example:
kubectl rollout pause deployment/nginx-deployment

- to resume a deployment:
kubectl rollout resume deployment/<deployment-name>

example:
kubectl rollout resume deployment/nginx-deployment

- check status:
kubectl rollout status deployment/nginx-deployment

5. 
Verifying Deployment Rollout
- view the details of your deployments
kubectl get deployment

6. 
Scaling the deployments:
- scaling up or down a deployment can also be part of the rollout process:
kubectl scale deployment/<deployment-name> --replicas=<number-of-replicas>
