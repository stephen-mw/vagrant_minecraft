# Disposable Minecraft Servers
Minecraft is a game where you run around punching blocks and building stuff with your imagination, basically like legos for boys and girls born in the 21st century. Vagrant is a virtualization service for creating disposable dev environments. Now the two of them are together for running easy, shareable minecraft servers.

![Minecraft Vagrant](https://i.imgur.com/g6mFnta.png?1 "Minecraft running inside Vagrant")

## What does this do
You can run ```vagrant up``` on your windows, linux, or mac machine and have a minecraft server running in a compartmentalized virtual server. When you run ```vagrant destroy``` the virtualize machine is destroyed but your persistent data is kept in ```persistent_data```. You can clone this repo on any mac, windows, or linux machine with Vagrant installed to easily create a minecraft server you and your friends can join.

## Why
Initially I created this vagrant image so I could quickly and easily test mods. Just start the vagrant instance, do whatever you want. If you break something or decide you don't want to use that mod any longer, simply destroy the image and the persistent data and start it again. It will be just like new.

I also bet there's parents out there who want to run minecraft servers for their children. This let's you do this easily from just about any platform without having to configure anything.

## Running the server
First install Vagrant if you haven't already done that.

Next clone the repo:
```
git clone git@github.com:stephendotexe/vagrant_minecraft_auto_launch.git
```

Pop into the vagrant server and run ```vagrant up```
```
cd vagrant_minecraft_auto_launch
vagrant up
```

The server will launch an Ubuntu 12.04 image that will download and install everything you need to run minecraft automatically. It will also start the service and take care of logs. Everything related to your server will be in ```persistent_data``` and that folder will survive the destruction and creation of these vagrant instances.

After the installation completes, you'll be able to connect to your server at your private IP address or loopback address (127.0.0.1).

The instance itself doesn't need to be destroyed between runs. You can also halt it. Either way, when you bring it back online it should be running the server.

## But I want others to play on my server too
Rightly so. By default other's can connect to your server on the _host's_ IP address. What that means is if your desktop that you launch the vagrant image has an ip address of 192.168.0.101, then others (you included) can connect to the server at 192.168.0.101.
