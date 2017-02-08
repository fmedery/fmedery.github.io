# My journey to activate ≈ authentication on our MongoDB clusters

At [ssense](https:/www/ssense.com) we embrace micro service and I fell in love with Kubernetes in the process but that is another story.

With micro services come the idea of independent data store. With that in mind, software like Cassandra, Elasticsearch and MongoDB appeared on my team's radar.

Another trend with these softwares is the absence of (even little) security by design (and with Elasticsearch, security is a premium feature). Back to Mongodb


## Our MongoDB setup

Simple setup :
* 1 master
* 1 slave
* 1 arbiter

With the arrival of MongoDB ransomware I decided, as a personal project, to enable authentication on our clusters.

After days of reading documentation, posts and frustration I was finally able to merge all the info in an actual procedure.

Probably not the perfect one but I was not able to find it all

##  Gathering all the information needed
first surprise there is no cookbook for my very simple setup.  I needed to read and understand each how-to documentation :
* One to understand how to  for the 3 nodes clusters without any security.
* Another to understand the authentication mechanism with and without a cluster (probably the worst part of my research).
*

So I was suppose to :
* create my cluster without authentication
* create an admin user
* create and key file, set the correct permission and copy it on each server.
* stop the cluster
* activate auth in the configuration
* start the cluster
* create other users

As a lazy <*insert the latest buzz ops position here*> I was surprise that the official procedure was not automation friendly at all! So after yet some hours of research I found that we can use JS script to do most of the work.
