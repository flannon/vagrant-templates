# vagrant-templates
Templates for building vagrant boxes


## Table of Contents

1. [Overview] (#overview)
2. [Pre-Install] (#pre-install)
3. [Usage] (#usage)


#### Overview

Provides templates for building the follwoing vagrant boxes

    - archivesspace
    - jenkins
    - mysql
    - nexus
    - nginx
    - solr
    - rpmfactory

#### Pre-Installation Setup

To run the vagrant installer you will need Virtualbox, and  vagrant installed on your system.
If you're on a Mac the easiest way to install everything you'll need is with homebrew.  The following steps will install homebrew and 
everything you need to get vagrant running

    $ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
    $ brew cask install virtualbox
    $ brew cask install vagrant

#### Plugins

vagrant-templates uses several vagrant plugins, depending on which system you are booting.  If not already present on your system the follwoign plugins will be installed when you run vagrant up,

    - vagrant-vbguest
    - vagrant-puppet-install 
    - vagrant-r10k
    - vagrant-scp
    - vagrant-share

#### Usage

Clone vagrant-templates, change the value of HOST_NAME in the Vagrantfile to the name of the system you want to boot, and then vagrant up
then vagrant up. i.e. To build vagrant-mysql do the following,

    $ git clone https://gitlab.com/flannon/vagrant-templates vagrant-mysql
    $ cd vagrant-mysql
    $ HOST_NAME = "mysql"
    $ vagrant up


To connect to your vagrant box you can,

    $ vagrant ssh

