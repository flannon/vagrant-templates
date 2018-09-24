# vagrant-templates
Templates for building vagrant boxes


## Table of Contents

1. [Quick Setup](#quick-setup)
1. [Overview](#overview)
2. [Pre-Install](#pre-install)
3. [Usage](#usage)
4. [tl;dr](#tl:dr)


#### Quick Setup

  Set HOST_NAME in the Vagrantfile to the service you wnat to boot, load the puppet config and then `vagrant up`.
    - HOST_NAME = 'archivesspace'
    - cd puppetlabs
    - make
    - vagrant up

#### Overview

Provides templates for building the following vagrant boxes

    - archivesspace
    - archivesspace-devenv
    - lamp
    - loris
    - nfs-client
    - nfs-server
    - nginx
    - rpmfactory
    - templates (just a base box with no services)

#### Pre-Installation Setup

To run the vagrant installer you will need Virtualbox, vagrant and r10k installed on your system.
If you're on a Mac the easiest way to install everything you'll need is with homebrew.  The following steps will install homebrew and 
everything you need to get vagrant running

    $ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
    $ brew cask install virtualbox
    $ brew cask install vagrant
    $ brew install r10k

r10k comes packaged as a gem, so to install it you can run,

    $ gem install r10k

#### Plugins

vagrant-templates uses several vagrant plugins, depending on which system you are booting.  If not already present on your system the following plugins will be installed when you run vagrant up,

    - vagrant-vbguest
    - vagrant-puppet-install 
    - vagrant-r10k
    - vagrant-scp
    - vagrant-share

#### Usage

Clone the latest release of this repo, change the value of HOST_NAME in the Vagrantfile to the name of the system/(puppet role) you want to boot, run r10k and then `vagrant up`. Cloning from 'master' may produce inconsistent results, check the [releases](https://github.com/flannon/vagrant-templates/releases) page to find the latest release of this repo.

i.e. To build the nginx from the v0.0.1 release of the vagant-templates repo you can do the following, 

    $ git clone -b v0.0.1 --single-branch --depth 1 https://github.com/flannon/vagrant-templates.git vagrant-nginx
    $ cd vagrant-nginx

    Edit the Vagrantfile ( HOST_NAME = "nginx")

    $ cd puppetlabs
    $ make
    $ vagrant up


To connect to your vagrant box you can,

    $ vagrant ssh

#### tl;dr

The puppetlabs directory is a plain vanilla deployement of Puppet 4 that uses r10k to deploy dynamic environment.  You can easily swap in your puppet environments by running r10k agains your r10k.yaml file. 
