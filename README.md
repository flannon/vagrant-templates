# vagrant-templates
Templates for building vagrant boxes


## Table of Contents

1. [Overview] (#overview)
2. [Pre-Install] (#pre-install)
3. [Usage] (#usage)
4. [tl;dr] (#tl:dr)


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

r10k comes packaged as a gem, so to install it run,

    $ gem install r10k

#### Plugins

vagrant-templates uses several vagrant plugins, depending on which system you are booting.  If not already present on your system the following plugins will be installed when you run vagrant up,

    - vagrant-vbguest
    - vagrant-puppet-install 
    - vagrant-r10k
    - vagrant-scp
    - vagrant-share

#### Usage

Clone vagrant-templates, change the value of HOST_NAME in the Vagrantfile to the name of the system you want to boot, update the submodule references and then `vagrant up`.

i.e. To build the nginx template you can do the following,

    $ git clone https://gitlab.com/flannon/vagrant-templates vagrant-nginx
    $ cd vagrant-nginx

    Edit the Vagrantfile ( HOST_NAME = "nginx")

    $ git submodule update --init --recursive
    $ cd puppetlabs
    $ r10k deploy environment development -p -v -c r10k/r10k-public.yaml
    $ vagrant up


To connect to your vagrant box you can,

    $ vagrant ssh

#### tl;dr

The puppetlabs directory is a plain vanilla deployement of Puppet 4 that uses r10k to deploy dynamic environment.  You can easily swap in your own puppetlabs directory and run r10k on your own control repo.  You'll just need to set MANIFEST in the Vagrantfile to the name of your systems manifest file.
