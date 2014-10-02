sense-m
=======

Sense-M (sense-market): Parent module for projects related to personal data markets


Getting Started
===============

If using Windows or Mac you might find it easier to run the apps in
Docker. Docker uses Linux Virtual Containers so needs a Linux
environment. On Mac/Windows this is taken care of using a VM. Install
Boot2Docker which includes all you need. Linux users don't need to do
this -- just install Docker.

If using Boot2Docker, fire up the VM:
    $ boot2docker start
    $ export DOCKER_HOST=`boot2docker socket`

Build environment from the Dockerfile:
    $ docker pull hissohathair/openpds

To inspect the environment after the build
    $ docker run -p 8002:8002 -p 8000:8000 hissohathair/openpds



Developers
==========

The Sense-M project uses git submodules:

* [data-market](https://github.com/hissohathair/data-market): Early
  "PDS" demo based on NodeJS

* [openPDS](https://github.com/hissohathair/openPDS), forked [from
  MIT](https://github.com/HumanDynamics/openPDS): MIT's openPDS and
  SafeAnswers system.

To checkout the project:

    $ git clone https://github.com/hissohathair/sense-m.git
    $ cd sense-m
    $ git submodule init
    $ git submodule update

Every time you want to pull down a submodule change you'll need to do
an update first.

    $ git submodule update
    $ git merge origin/master

If another developer commits changes to the superproject (Sense-M) but
without checking in their changes to a subproject you'll get an error
from git ("reference isn't a tree"). To find out who goofed:

    $ git log -l openPDS

More about submodules in [Chapter 6.6](http://git-scm.com/book/en/Git-Tools-Submodules)

To keep up to date with MIT's upstream repository:

    $ git remote add upstream 'https://github.com/HumanDynamics/openPDS.git'   # do once
    $ git remote -v  # to check above
    $ git fetch upstream
    $ git checkout master
    $ git merge upstream/master
