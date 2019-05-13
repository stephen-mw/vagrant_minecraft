[![Build Status](https://travis-ci.org/stephen-mw/vagrant_minecraft.svg?branch=master)](https://travis-ci.org/stephen-mw/vagrant_minecraft)

# Disposable Minecraft Servers

Vagrant is a virtualization service for creating disposable dev environments. Now the two of them are together for running easy, shareable minecraft servers.


![Minecraft Vagrant](https://i.imgur.com/g6mFnta.png?1 "Minecraft running inside Vagrant")

## What does this do
You can run ```vagrant up``` on your windows, linux, or mac machine and have a minecraft server running in a compartmentalized virtual server. When you run ```vagrant destroy``` the virtualize machine is destroyed but your persistent data is kept in ```persistent_data```. You can clone this repo on any mac, windows, or linux machine with Vagrant installed to easily create a minecraft server you and your friends can join.

## Why
Initially I created this vagrant image so I could quickly and easily test mods. Just start the vagrant instance and do whatever you want. If you break something or decide you don't want to use that mod any longer, simply destroy the image and the persistent data and start it again. It will be just like new.

Backing up and restoring your minecraft server very easy, since all of your data -- including the information necessary for running the server -- is contained in just a few files and folders. You can even copy the entire directory over to a new server and run it there.

Lastly, I bet there are parents out there who want to run minecraft servers for their children. This let's you do this easily from just about any platform without having to configure anything.

## Running the server
First install Vagrant if you haven't already done that.

Next clone the repo:
```
git clone git@github.com:stephen-mw/vagrant_minecraft_auto_launch.git
```

Pop into the vagrant server and run ```vagrant up```
```
cd vagrant_minecraft_auto_launch
vagrant up
```

At this point you can run ```vagrant ssh``` to go into the server. You'll be greated with a MOTD with some helpful information:
```
WELCOME TO MINECRAFT!

To stop, start, restart or check the status of the the minecraft server
process, simply run:

  $ service minecraft <stop|start|restart|status>

The runtime logs are available at /opt/minecraft/logs

To change the min or max server memory values, make the change in:

  /etc/init/minecraft.conf

And then restart the server proces.

Status of minecraft server:

minecraft start/running, process 2344

Have fun!
```

### Under the hood
The server will launch an Ubuntu 12.04 image that will download and install everything you need to run minecraft automatically. It will also start the service and take care of logs. Everything related to your server will be in ```persistent_data``` and that folder will survive the destruction and creation of these vagrant instances.

After the installation completes, you and others will be able to connect to your server at your _host's_ ip address. That means if you launch the vagrant instance on a laptop that has the ip address of 192.168.0.101, then you can connect to the server at the same address (regardless of what your guest ip address is).

The instance itself doesn't need to be destroyed between runs. You can also halt it. Either way, when you bring it back online it should be running the server.
