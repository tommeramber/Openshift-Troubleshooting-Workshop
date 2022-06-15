# Intro

# Sanity Test for working OCP envrionment
https://openshift.tips/troubleshooting/

https://cloud.redhat.com/blog/introduction-to-customer-empathy-workshops

https://cloud.redhat.com/blog/the-openshift-troubleshooting-workshop

https://towardsdatascience.com/troubleshooting-openshift-clusters-and-workloads-382664018935

https://blog.clairvoyantsoft.com/openshift-troubleshooting-aa7cc67b0334

https://github.com/redhat-cop/openshift-migration-best-practices/blob/main/05-troubleshooting.md

https://access.redhat.com/documentation/en-us/openshift_container_platform/4.7/html/support/troubleshooting

https://www.youtube.com/watch?v=NdpAli78o0A

https://www.youtube.com/watch?v=-YLVTvJ67Jw

https://www.youtube.com/watch?v=EF9_Ab5U8U4

https://examples.openshift.pub/deploy/

* ImageStream Bug
* Registry no access
* no pull secret
* icsp bug
* trigger bug
* service points to wrong label

```bash
oc get clusterversion,nodes,clusteroperators,mcp
```
```bash
oc get pods -A -o wide | grep -v -E 'Completed|Running'
```
# Break the enrvionment
