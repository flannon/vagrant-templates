# vagrant-templates
Templates for building vagrant boxes


## Table of Contents

1. [Overview] (#overview)
2. [Pre-Install] (#pre-install)
3. [Usage] (#usage)
4. [tl;dr] (#tl:dr)


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
    $ brew install r10k

#### Plugins

vagrant-templates uses several vagrant plugins, depending on which system you are booting.  If not already present on your system the follwoign plugins will be installed when you run vagrant up,

    - vagrant-vbguest
    - vagrant-puppet-install 
    - vagrant-r10k
    - vagrant-scp
    - vagrant-share

#### Usage

Clone vagrant-templates, change the value of HOST_NAME in the Vagrantfile to the name of the system you want to boot, update submodule references and then vagrant up.

i.e. To build vagrant-mysql do the following,

    $ git clone https://gitlab.com/flannon/vagrant-templates vagrant-mysql
    $ cd vagrant-mysql
    Update the Vagrantfile ( HOST_NAME = "mysql")
    $ git submodule update --init --recursive
    $ cd puppetlabs
    $ r10k deploy environment development -p -v -c r10k/r10k-puglic.yaml
    $ vagrant up


To connect to your vagrant box you can,

    $ vagrant ssh

#### tl;dr

The puppetlabs directory is a plain vanilla deployement of puppet 4 that uses r10k to deploy dynamic environment.  You can easily swap in your own puppetlabs directoryand run r10k on your own control repo.  You'll just need to set MANIFEST in the Vagrantfile to the name of your systems manifest file.
