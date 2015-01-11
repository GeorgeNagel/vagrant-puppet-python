# Base Vagrant box with Puppet privisioning and Python
## Clone the repo
```
$ git clone https://github.com/GeorgeNagel/vagrant-puppet-python.git
$ cd vagrant-puppet-python
```
## Install the submodules
This project uses [git submodules](http://git-scm.com/book/en/v2/Git-Tools-Submodules) to
install the puppet provisioning modules.
[puppet-python](https://github.com/stankevich/puppet-python.git) is used to install
python and requires [stdlib](https://github.com/puppetlabs/puppetlabs-stdlib).
```
$ git submodule init
$ git submodule update
```
## Setup the host machine
This installs [fabric](http://www.fabfile.org/) on the host machine so that you
can run commands on the vagrant box without having to use ssh every time.
```
# Create the host python virtual environment
$ virtualenv hostenv
# Install the python requirements
$ hostenv/bin/pip install -r requirements_host.txt
```
## Setup the vagrant box
```
$ vagrant up
```
## Create the python virtual environment and install dependencies
[nose](https://nose.readthedocs.org/en/latest/) is installed by default.
To install additional python dependencies, update requirements.txt.
```
$ hostenv/bin/fab reset_virtualenv
```
