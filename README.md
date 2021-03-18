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

As soon as everything is up, please visit e.g. https://abcc6d03017104680b6bc699174eb48d-691815500.us-west-2.elb.amazonaws.com/demo/ui, depending on your LoadBalancer Address. 