###### _Deploy the example app_

```bash
oc apply -f ../examples
oc get pods
```

###### _Output_
```bash
NAME                     READY   STATUS          
httpd-xxxxxx             0/1     ErrImagePull 
```

###### _Investigation_ 
```bash
oc get events
oc get events --sort-by='.metadata.creationTimestamp'
alias events="oc get events --sort-by='.metadata.creationTimestamp'"
```

###### _Output_
```bash
LAST SEEN   TYPE      REASON              OBJECT                        MESSAGE
7m21s       Normal    Scheduled           pod/httpd-xxxxxx              Successfully assigned tommer-test/httpd-xxxxxx to ip-10-0-231-179.us-east-2.compute.internal
7m21s       Normal    SuccessfulCreate    replicaset/httpd-xxxxxx       Created pod: httpd-xxxxxx
7m21s       Normal    ScalingReplicaSet   deployment/httpd              Scaled up replica set httpd-7ddc5799d5 to 1
7m20s       Normal    AddedInterface      pod/httpd-xxxxxx              Add eth0 [10.131.0.85/23] from openshift-sdn
5m49s       Warning   Failed              pod/httpd-xxxxxx              Failed to pull image "registry.access.redhat.com/ubi9/httpd-24:lastest": rpc error: code = Unknown desc = reading manifest lastest in registry.access.redhat.com/ubi9/httpd-24: StatusCode: 404, Not found
5m49s       Warning   Failed              pod/httpd-xxxxxx              Error: ErrImagePull
5m50s       Normal    Pulling             pod/httpd-xxxxxx              Pulling image "registry.access.redhat.com/ubi9/httpd-24:lastest"
2m12s       Normal    BackOff             pod/httpd-xxxxxx              Back-off pulling image "registry.access.redhat.com/ubi9/httpd-24:lastest"
5m39s       Warning   Failed              pod/httpd-xxxxxx              Error: ImagePullBackOff
```

###### _Test Locally_
```bash
podman pull registry.access.redhat.com/ubi9/httpd-24:lastest
```

Go to the [RedHat Imgaes Catalog](https://catalog.redhat.com/software/containers/rhel8/httpd-24/5ba0addbbed8bd6ee819856a?container-tabs=gti) and make sure you downloaded the right image

```bash
podman pull registry.redhat.io/rhel8/httpd-24@sha256:4ac6f9969a15369f42bf6816a02eefaeef08b1c9331fc240d0262b897faba168
```
