# cs3219-TaskA2

### Instructions:
Clone the Github Repository on your local machine.

```
git clone https://github.com/candyhy/cs3219-TaskA2.git
```

Navigate to the project directory.

```
cd cs3219-TaskA2
```
Deploy deployment component

```
kubectl apply -f deployment.yaml 
```
Deploy service commponent
```
kubectl apply -f service.yaml 
```
View pod status to affirm it is running
```
kubectl get pods -l app=taska1
```
View services deployed
```
kubectl exec <podname> — printenv | grep SERVICE
```
Our service will not be deployed as we need to create the Service before the replica. 
First scale the replicas to 0:
```
kubectl scale deployment taska1 --replicas=0 
```
Then scale the replicas back up to 2:
```
kubectl scale deployment taska1 --replicas=2 
```
View pod status to affirm it is running
```
kubectl get pods -l app=taska1
```
Now check that the service has been deployed:
```
kubectl exec <podname> -- printenv | grep SERVICE
```
Variables TASKA1_SERVICE_PORT and TASKA1_SERVICE_HOST should be found under the list of services deployed