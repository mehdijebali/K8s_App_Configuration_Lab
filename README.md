# Manage Application Configuration with K8s Lab
In this tutorial, we will show how to manage application configuration (configmap, secret) using K8s with different manners. 
K8s allows user to pass dynamic conﬁguration values to application at Runtime. These dynamic Conﬁguration helps user to control the application flow. Indeed, we prevent hardcoding conﬁguration data to Pod speciﬁcations.
## ConfigMap
Configmap is a K8s object that is used to keep Non-Sensitive Data in Key-Value format, which can be passed to Container Application. ConﬁgMaps allow to separate conﬁgurations from Pods and components. We use Configmaps in order to make configurations easier to change and manage.
## Secret
Secret is a K8s object that is used to keep Non-Sensitive Data Key-Value format, which can be passed to Container Application. We can store encrypted secrets. We make then secrets easier to change and manage.

User can pass Secrets and Conﬁg Map to Container using 
## Environment Variables
In this case, Data will be available in container as environment variables.
```
spec:
containers:
- ...
env:
- name: SPECIAL_LEVEL_KEY
    valueFrom:
        conﬁgMapKeyRef:
            name: special-conﬁg
            key: special.how
```
## Mount Volume
Using this Conﬁg Data will be available in Files to Container File System.
```
volumes:
    - name: conﬁg-volume
      conﬁgMap:
        name: special-conﬁg
```