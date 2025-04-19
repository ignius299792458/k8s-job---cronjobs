# Cron job Comprehensive Application Flow
-  yml config,
-  apply/create,
-  checking pod lifecycle state at every schedule cron

Example 
```
➜ vim cron_job.yml 

➜ kubectl apply -f cron_job.yml 
cronjob.batch/minute-backup created

➜ kubectl get cronjobs -n nginx
NAME            SCHEDULE    TIMEZONE   SUSPEND   ACTIVE   LAST SCHEDULE   AGE
minute-backup   * * * * *   <none>     False     0        <none>          17s

➜ kubectl get pods -n nginx
NAME                               READY   STATUS      RESTARTS   AGE
nginx-deployment-f58b5c699-54ztl   1/1     Running     0          3d19h
nginx-deployment-f58b5c699-xmpnm   1/1     Running     0          3d19h

➜ kubectl get cronjobs -n nginx
NAME            SCHEDULE    TIMEZONE   SUSPEND   ACTIVE   LAST SCHEDULE   AGE
minute-backup   * * * * *   <none>     False     0        <none>          22s

➜ kubectl get cronjobs -n nginx
NAME            SCHEDULE    TIMEZONE   SUSPEND   ACTIVE   LAST SCHEDULE   AGE
minute-backup   * * * * *   <none>     False     0        <none>          23s

➜ kubectl get cronjobs -n nginx
NAME            SCHEDULE    TIMEZONE   SUSPEND   ACTIVE   LAST SCHEDULE   AGE
minute-backup   * * * * *   <none>     False     0        <none>          25s

➜ kubectl get pods -n nginx
NAME                               READY   STATUS    RESTARTS   AGE
nginx-deployment-f58b5c699-54ztl   1/1     Running   0          3d19h
nginx-deployment-f58b5c699-xmpnm   1/1     Running   0          3d19h

➜ kubectl get cronjobs -n nginx
NAME            SCHEDULE    TIMEZONE   SUSPEND   ACTIVE   LAST SCHEDULE   AGE
minute-backup   * * * * *   <none>     False     0        13s             68s

➜ kubectl get cronjobs -n nginx
NAME            SCHEDULE    TIMEZONE   SUSPEND   ACTIVE   LAST SCHEDULE   AGE
minute-backup   * * * * *   <none>     False     0        18s             73s

➜ kubectl get pods -n nginx
NAME                               READY   STATUS      RESTARTS   AGE
minute-backup-29084535-m9ngz       0/1     Completed   0          37s
nginx-deployment-f58b5c699-54ztl   1/1     Running     0          3d19h
nginx-deployment-f58b5c699-xmpnm   1/1     Running     0          3d19h

➜ kubectl get cronjobs -n nginx
NAME            SCHEDULE    TIMEZONE   SUSPEND   ACTIVE   LAST SCHEDULE   AGE
minute-backup   * * * * *   <none>     False     0        42s             97s

➜ kubectl get cronjobs -n nginx
NAME            SCHEDULE    TIMEZONE   SUSPEND   ACTIVE   LAST SCHEDULE   AGE
minute-backup   * * * * *   <none>     False     0        47s             102s

➜ kubectl get cronjobs -n nginx
NAME            SCHEDULE    TIMEZONE   SUSPEND   ACTIVE   LAST SCHEDULE   AGE
minute-backup   * * * * *   <none>     False     0        58s             113s

➜ kubectl get cronjobs -n nginx
NAME            SCHEDULE    TIMEZONE   SUSPEND   ACTIVE   LAST SCHEDULE   AGE
minute-backup   * * * * *   <none>     False     1        1s              116s

➜ kubectl get cronjobs -n nginx
NAME            SCHEDULE    TIMEZONE   SUSPEND   ACTIVE   LAST SCHEDULE   AGE
minute-backup   * * * * *   <none>     False     0        6s              2m1s

➜ kubectl get pods -n nginx    
NAME                               READY   STATUS      RESTARTS   AGE
minute-backup-29084535-m9ngz       0/1     Completed   0          68s
minute-backup-29084536-j4n8q       0/1     Completed   0          9s
nginx-deployment-f58b5c699-54ztl   1/1     Running     0          3d19h
nginx-deployment-f58b5c699-xmpnm   1/1     Running     0          3d19h

➜ kubectl get pods -n nginx
NAME                               READY   STATUS      RESTARTS   AGE
minute-backup-29084535-m9ngz       0/1     Completed   0          72s
minute-backup-29084536-j4n8q       0/1     Completed   0          13s
nginx-deployment-f58b5c699-54ztl   1/1     Running     0          3d19h
nginx-deployment-f58b5c699-xmpnm   1/1     Running     0          3d19h

➜ kubectl get cronjobs -n nginx
NAME            SCHEDULE    TIMEZONE   SUSPEND   ACTIVE   LAST SCHEDULE   AGE
minute-backup   * * * * *   <none>     False     0        17s             2m12s

➜ kubectl get cronjobs -n nginx
NAME            SCHEDULE    TIMEZONE   SUSPEND   ACTIVE   LAST SCHEDULE   AGE
minute-backup   * * * * *   <none>     False     0        20s             2m15s

➜ kubectl get cronjobs -n nginx
NAME            SCHEDULE    TIMEZONE   SUSPEND   ACTIVE   LAST SCHEDULE   AGE
minute-backup   * * * * *   <none>     False     0        21s             2m16s

➜ kubectl get cronjobs -n nginx
NAME            SCHEDULE    TIMEZONE   SUSPEND   ACTIVE   LAST SCHEDULE   AGE
minute-backup   * * * * *   <none>     False     0        22s             2m17s

➜ kubectl get cronjobs -n nginx
NAME            SCHEDULE    TIMEZONE   SUSPEND   ACTIVE   LAST SCHEDULE   AGE
minute-backup   * * * * *   <none>     False     0        9s              6m4s

➜ kubectl get pods -n nginx    
NAME                               READY   STATUS      RESTARTS   AGE
minute-backup-29084538-j97lh       0/1     Completed   0          2m15s
minute-backup-29084539-2m45n       0/1     Completed   0          75s
minute-backup-29084540-d2jcm       0/1     Completed   0          15s
nginx-deployment-f58b5c699-54ztl   1/1     Running     0          3d19h
nginx-deployment-f58b5c699-xmpnm   1/1     Running     0          3d19h

```
