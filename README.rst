Introduction
============

This is the buildout for the repodono project, a suite of repository
related software built on top of Plone 5.

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
based system, these packages must be installed.

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

Installation
------------

To install this project onto your system, simply clone this project,
initialize a virtualenv, install zc.buildout then invoke buildout.  The
commands that should be invoked in the shell follows::

    $ git clone https://github.com/repodono/repodono.buildout.git
    $ cd repodono.buildout
    $ virtualenv .
    $ bin/pip install -U zc.buildout  # install updated deps
    $ bin/buildout

Wait as buildout downloads and installs the framework and application
onto your system.  Once this process completes simply start the
zeoserver and run the instance in the foreground like so::

    $ bin/zeoserver start
    $ bin/instance fg

Connect to the server address output in the console with a web browser
and follow the instructions there.

This basic installation is nearly identical to the instance found in
deployment, with the only differences being some extra packages that do
not readily benefit a local instance for demonstration.  If the
deployment profiles are desired please make use of the ``deploy-*``
configuration files.

Development
-----------

This will require some knowledge on mr.developer, but to get started,
simply invoke ``bin/buildout`` with the developer configuration::

    $ bin/buildout -c develop.cfg

This should result in the activation and the checkout all development
packages, and should be done for general development of extensions to
this project.

Coding standards
~~~~~~~~~~~~~~~~

Please refer to ``CONTRIBUTE.rst``
