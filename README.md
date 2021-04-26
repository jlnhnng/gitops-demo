# GitOps DKP Demo

This branch was created to roll-out the truck efficiency demo. It is meant to show how easy it is to use DKP.

## Prerequirements

* Create a [Kommander Project](https://docs.d2iq.com/dkp/kommander/1.4/projects/)
* Install [Platform Services](https://docs.d2iq.com/dkp/kommander/1.4/projects/platform-services/)
  * Zookeeper (ID: zookeeper)
  * Install Kafka (ID: kafka)
  * Install Cassandra (ID: cassandra)
* Create a [ConfigMap](https://docs.d2iq.com/dkp/kommander/1.4/projects/project-configmaps/) with the following key value pair and replace ***ProjectNamespace*** with your Project Namespace:
  * Kafka=kafka-kafka-0.kafka-svc.***ProjectNamespace***.svc.cluster.local:9093
  * Cassandra=cassandra-node-0.cassandra-svc.***ProjectNamespace***.svc.cluster.local:9042

## Installation

To create the resources needed like the api's, a frontend and the data generator we will simply use [Kommander Project Deployments](https://docs.d2iq.com/dkp/kommander/1.3/projects/project-deployments/). You will find all the Kubernetes Manifests in this repository. As this repo is Public you won't need a Git Secret. You just need to specify a name, the Repository URL and a branch. That's all? **Yes**.

What will be installed?

* Node API
* Python API
* Angular UI
* Data Generator

If you want to check the changes in the namespace you can use:

``` bash
watch kubectl get po -n ProjectNamespace
```

*Please replace ***ProjectNamespace*** with your Project Namespace.*

## Usage

As soon as everything is up, please use:

``` bash
watch kubectl get svc truck-demo-ui-svc -n ProjectNamespace
```

*Please replace ***ProjectNamespace*** with your Project Namespace.*

You will find a Loadbalancer Address. Please visit <https://LoadBalancerAddress.us-west-2.elb.amazonaws.com/> and use your LoadBalancer address instead of ***LoadBalancerAddress***.

### Create more trucks

One truck is one pod. The pod will restart after the truck finished (or had to stop unplanned) the drive. If you want to create more please scale the deployment:

``` bash
watch kubectl scale --replicas=5 deploy/truck-data-generator -n ProjectNamespace
```

### Advanced

If you want to play around and would like to see GitOps in action, please feel free to fork this repository, adjust your GitOps Source, change a value in the repository and see the changes getting rolled out to you Project Namespace automatically.
