# Job Creation/apply, Logs check, job deletion, pod-lifecycle state

Example
```
➜  vim job.yml
➜  kubectl apply -f job.yml 
job.batch/nginx-job created
➜  kubectl get job -n nginx
NAME        STATUS    COMPLETIONS   DURATION   AGE
nginx-job   Running   0/1           25s        25s
➜  kubectl get pods -n nginx
NAME                               READY   STATUS    RESTARTS   AGE
nginx-deployment-f58b5c699-54ztl   1/1     Running   0          3d18h
nginx-deployment-f58b5c699-xmpnm   1/1     Running   0          3d18h
nginx-job-m9n2b                    0/1     Error     0          5s
nginx-job-qhf7b                    0/1     Error     0          31s
nginx-job-xkbs4                    0/1     Error     0          49s
➜  vim job.yml 
➜  kubectl delete -f job.yml 
job.batch "nginx-job" deleted
➜  nginx kubectl apply -f job.yml 
job.batch/nginx-job created
➜  kubectl get job -n nginx
NAME        STATUS    COMPLETIONS   DURATION   AGE
nginx-job   Running   0/1           13s        13s
➜  kubectl get pods -n nginx
NAME                               READY   STATUS      RESTARTS   AGE
nginx-deployment-f58b5c699-54ztl   1/1     Running     0          3d18h
nginx-deployment-f58b5c699-xmpnm   1/1     Running     0          3d18h
nginx-job-jbq8n                    0/1     Completed   0          22s
➜  kubectl logs pod/nginx-job-jbq8n -n nginx
Hello This is onetime JOB
➜  
```
