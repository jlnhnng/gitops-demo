# GitOps DKP Demo

This branch was created to roll-out a demo. It should show the ease of using DKP.

Prerequirements (need to be installed in Kommander Project before GitOps Source is added):

* Zookeeper
* Kafka
* Cassandra

What will be installed?

* Node API
* Python API
* Angular UI
* Data Generator

Please keep an eye on the Pods in the project namespace:

``` bash
watch kubectl get po -n <project-ns>
```

As soon as everything is up, please visit https://LoadBalancerAddress/demo. Use your LoadBalancer address instead of "LoadBalancerAddress".