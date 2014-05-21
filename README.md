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

Now you can create a topic and start producing/consuming from it (You can do this from your host machine if you have kafka extracted locally)
```
KAFKA_INSTALL_DIR/bin/kafka-topics.sh --zookeeper 192.168.1.10:2181 --create --topic myTestTopic --partitions 3 --replication-factor 2

KAFKA_INSTALL_DIR/bin/kafka-topics.sh --zookeeper 192.168.1.10:2181 --describe
```

Note:  This is a BSD 3-Clause license.  Have fun with it

Please let me know any issues you have with getting the initial cluster running.  If you have better clarifications on the instructions feel free to add a pull request.

