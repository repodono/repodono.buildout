Introduction
============

This is the buildout for the repodono project.

Usage
=====

To ease maintenance, the buildout configuration is split up into
separate files for specific tasks, such as development, staging or
deployment.  Please refer to the specific configuration file for further
configuration options.


Prerequisite 
------------

Before this buildout will build correctly, a number of packages and
dependencies must be provided.  If this is to be done on a Debian/Ubuntu
based system, these packages must be installed:

* python-setuptools
* python-virtualenv
* python-dev
* build-essential
* libssl-dev
* libxml2-dev
* libxslt1-dev
* libbz2-dev
* libjpeg62-dev
* libz-dev

Develop
-------

To get the standard development site set up, just clone this repoistory
then run the following::

    virtualenv .
    ./bin/pip install zc.buildout
    ./bin/buildout 
