# Intro

# Sanity Test for working OCP envrionment
- [x] https://openshift.tips/troubleshooting/
- [x] https://cloud.redhat.com/blog/the-openshift-troubleshooting-workshop
- [ ] https://start.learning.redhat.com/
- [x] https://towardsdatascience.com/troubleshooting-openshift-clusters-and-workloads-382664018935

~~https://blog.clairvoyantsoft.com/openshift-troubleshooting-aa7cc67b0334~~

~~https://github.com/redhat-cop/openshift-migration-best-practices/blob/main/05-troubleshooting.md~~

- [ ] https://access.redhat.com/documentation/en-us/openshift_container_platform/4.7/html/support/troubleshooting
- [ ] https://www.youtube.com/watch?v=NdpAli78o0A
- [ ] https://www.youtube.com/watch?v=-YLVTvJ67Jw
- [ ] https://www.youtube.com/watch?v=EF9_Ab5U8U4
- [ ] https://examples.openshift.pub/deploy/

* ImageStream Bug
* Registry no access
* no pull secret
* icsp bug
* trigger bug
* service points to wrong label
* pv of important component full
* DNS forwarder bug
* pv pending - wrong type
* SCC & RBAC restriction
* Quota & LimitRanges 

```bash
oc adm top nodes
oc adm top node/<NODE>
oc adm top nodes -l node-role.kubernetes.io/worker
```

```bash
oc debug nodes/node-name
sh # chroot /host
sh # bash
[node]# crictl ps
[node]# systemctl status kubelet.service
```

```bash
oc get clusterversion,nodes,clusteroperators,mcp
oc describe clusterversion

oc status
```

```bash
oc get pods -A -o wide | grep -v -E 'Completed|Running'
```
# Break the enrvionment

```bash
oc logs -f pod/<POD> -n <NS
oc exec -it POD -c <Container_NAME> -- bash
oc rsh <POD> -c <Container_NAME>
oc cp podname:/logs/messages.log messages.log
```

```bash
oc rsh pod
sh# bash
[Node]# curl other_svc.NS.cluster.svc.local
[node]# nslookup <IP>

oc get svc
oc get endpoints => no endpoints (fuked selector)
```

```bash
oc get pod podname -o yaml | oc adm policy scc-subject-review -f -
oc adm policy scc-subject-review -z builder
```

```bash
oc get events -n <NS> --sort-by='.metadata.creationTimestamp'
```
![image](https://user-images.githubusercontent.com/60185557/173819028-51204f01-fc87-4551-a151-685f594f0c3d.png)
![image](https://user-images.githubusercontent.com/60185557/173819103-a3e2d696-de63-4fb8-a5e4-6e3673d9600d.png)
