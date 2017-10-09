# vagrant-templates
Templates for building vagrant boxes for 


## Table of Contents

1. [Overview] (#overview)
2. [Pre-Install] (#pre-install)
3. [Usage] (#usage)


#### Overview

Provides templates for building the follwoing vagrant boxes

    - mysql

#### Pre-Installaiton Setup

To run the vagrant installer you will need Virtualbox, vagrant, and the 
vagrant plugin vagrant-r10k.  If you're on a Mac the easiest way to install everything you'll need is with homebrew.  The following steps will install homebrew and 
everything you need to get vagrant running

    $ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
    $ brew cask install virtualbox
    $ brew cask install vagrant
    $ brew cask install vagrant-manager
    $ vagrant plugin install vagrant-r10k


#### Usage

Clone vagrant templates, checkout the branch you want to build and
then vagrant up. i.e. To build vagrant-mysql do the following,

    $ git clone https://gitlab.com/flannon/vagrant-templates vagrant-mysql
    $ cd vagrant-mysql
    $ git checkout mysql
    $ vagrant up


To connect to your vagrant box you can,

    $ vagrant ssh



Notes

The fedora 3.7.1 installer jar file is available at
  http://central.maven.org/maven2/org/fcrepo/fcrepo-installer/3.7.1/fcrepo-installer-3.7.1.jar


