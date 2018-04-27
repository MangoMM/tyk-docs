---
date: 2017-03-22T15:46:41Z
Title: On Ubuntu
menu:
  main:
    parent: "Installation"
weight: 2
url: "/get-started/with-tyk-on-premise/installation/on-ubuntu"
---

## <a name="ubuntu"></a> Install Tyk API Gateway on Ubuntu

Installing Tyk on Ubuntu is very straightforward, follow the guides and tutorials in this section to have Tyk up and running in no time.

## <a name="prerequisites"></a> Prerequisites

Before installing the Tyk components in the order below, you need to install firstly MongoDb, then Redis.

### Install MongoDb 3.2

First import the public key as required by Ubuntu APT

```{.copyWrapper}
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv EA312927
```

Then create a MongoDb source list file

Ubuntu 14.04
```{.copyWrapper}
echo "deb http://repo.mongodb.org/apt/ubuntu trusty/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list
```

Ubuntu 16.04
```{.copyWrapper}
echo "deb http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list
```

Reload the package database

```{.copyWrapper}
sudo apt-get update
```

Then run the install script.

```{.copyWrapper}
sudo apt-get install -y mongodb-org
```

Finally, start and enable the mongod service - then ensure all is running.

```
# sudo systemctl start mongod

# sudo systemctl enable mongod
Created symlink from /etc/systemd/system/multi-user.target.wants/mongod.service to /lib/systemd/system/mongod.service.

# sudo systemctl status mongod
● mongod.service - High-performance, schema-free document-oriented database
   Loaded: loaded (/lib/systemd/system/mongod.service; enabled; vendor preset: enabled)
   Active: active (running) since Fri 2018-04-27 16:55:59 UTC; 22s ago
     Docs: https://docs.mongodb.org/manual
 Main PID: 2463 (mongod)
   CGroup: /system.slice/mongod.service
           └─2463 /usr/bin/mongod --config /etc/mongod.conf

Apr 27 16:55:59 systemd[1]: Started High-performance, schema-free document-o
lines 1-9/9 (END)
```

### Install Redis

```{.copyWrapper}
sudo apt-get install -y redis-server
```

We then recommend installing Tyk in the following order:

* [Dashboard][2]
* [Pump][1]
* [Gateway][3]

[1]: /docs/get-started/with-tyk-on-premise/installation/on-ubuntu/analytics-pump
[2]: /docs/get-started/with-tyk-on-premise/installation/on-ubuntu/dashboard
[3]: /docs/get-started/with-tyk-on-premise/installation/on-ubuntu/gateway/
