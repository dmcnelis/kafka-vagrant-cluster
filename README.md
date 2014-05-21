# kafka-vagrant-cluster
=====================

An example of getting a multi-node Apache Kafka/Zookeeper cluster running in a local vagrant setup.  The recipes to do this are written for Chef
and intended at the moment to be run in a Vagrant environment.  It would be fairly easy to adapt this recipe to do something like deploying
a cluster to AWS.

## What is Kafka
=====================

[Kafka](http://kafka.apache.org/) is a distributed commit log that functions as a kind of PubSub system.  Originally created by 
the nice folks at LinkedIn, and helps facilitate a better way of doing ETL and accomplishing Stream Processing.  Its kind of awesome.

## Dependencies
=====================

Vagrant

	- Plugins 

		- Berkshelf
		- Omnibus

## How to use this
=====================

First, make sure that you have the "precise64" vagrant box referenced:

```
vagrant box add precise64 http://files.vagrantup.com/precise64.box
```

Make sure you have berkshelf and omnibus installed.

```
gem install berkshelf
vagrant plugin install vagrant-berkshelf 
vagrant plugin install vagrant-omnibus
```

Next spin it up:
```
vagrant up
```

You should now have a cluster opertating at 192.168.1.10, 192.168.1.11, 192.168.1.12 and be able to start testing
the cluster in whatever ways you need, i.e. testing replication behavior, leader election, ect.


