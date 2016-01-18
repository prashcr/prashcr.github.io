---
layout:     post
title:      Running Node.js in the cloud
date:       2016-01-18 12:31:19
summary:    Getting a Node.js environment up and running in the cloud in just a few keystrokes
categories: devops
---

Over the weekend, I put together a 3-piece starter kit to get a Node.js environment up and running in an Ubuntu 14.04 server on DigitalOcean, in just a few keystrokes.

All the code is available [as a Gist](https://gist.github.com/prashcr/01d0ee571c3ae8a606ad){:target="_blank"}

### To use this kit
* Download the Gist to a folder on your computer
* Add a timezone to `provision.sh`
* Configure your provider settings in the `Vagrantfile`, as described [here](https://github.com/smdahlen/vagrant-digitalocean)
* Get an API token from DigitalOcean and export it as an environment variable on your computer like this: `export DIGITAL_OCEAN_TOKEN=xxxxxxxxxx`
* Run `bash up` in your terminal

I realized I was doing a lot of repetitive work, mostly installations, as I kept spinning servers up and down while trying out different configurations for practice. So, I wrote the bash script to set up my environment for me. You'll notice that some steps are longer than they should be, where a simple `apt-get install` would've sufficed. However, the package versions on the default `apt` repos are woefully out of date. Therefore, I visited the website of each package and included the Ubuntu commands to install the latest stable version of every package. To use this script, add your timezone as specified, or you could also use "UTC".

I use [nvm](https://github.com/creationix/nvm){:target="_blank"} because it makes installing and managing node versions a breeze. I install git, which makes it easy to bring in existing projects by cloning them. Then there's [nginx](http://nginx.org/en/){:target="_blank"} which is an invaluable reverse proxy for Node.js applications. As fast as Node.js is, nginx will still run circles around it when it comes to things like caching. Moreover, it lets you have multiple Node.js applications running and accepting connections from the outside world, on a single server. It also makes it possible to set up load balancing if needed in the future. Lastly we have [MongoDB](https://www.mongodb.com/mongodb-3.2?jmp=dotorg-form){:target="_blank"}, which is the most popular DB used with Node.js.

Afterwards, I was playing around with [Vagrant](https://docs.vagrantup.com/v2/getting-started/){:target="_blank"}, and found the [DigitalOcean plugin](https://github.com/smdahlen/vagrant-digitalocean){:target="_blank"} for Vagrant. I thought it would be a great idea to not only automate the server setup but also the launching of servers. I built upon the example Vagrantfile provided in the repo.

After a bunch of tinkering and experimentation, I finally got my perfect starter kit together. One major caveat was that DigitalOcean doesn't respect the `privileged: false` setting in `config.vm.provision` line, and remains a root user while provisioning during the `up` phase. This breaks nvm and requires you to run Node.js with sudo at all times (thus, trusting npm packages with root privileges over your computer). To remedy this, I had to write a 2 line bash script that calls Vagrant for us, calling `up` without provisioning then provisioning afterwards to make sure the provisioning script is run as a non-root user.

#### Summary
Our Vagrantfile spins up a virtual Ubuntu server on DigitalOcean, our provisioning script configures basic things like swapfile, timezone and installing our required software, and there's a little helper script that calls Vagrant for us to ensure that provisioning occurs correctly
