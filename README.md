# puppet_docker_repo

Puppet Repository to demonstrate using kitchen-puppet with Docker.

The tests are stored in the repository rather than separately in /test/integration (as is the chef format)

This demonstrates using test-kitchen, puppet and kitchen-verifier-serverspec to build and verify a server.


## Workstation Software Installation

The first thing you need to do is install the test-kitchen environment on your workstation.
A useful link is: http://misheska.com/blog/2013/12/26/set-up-a-sane-ruby-cookbook-authoring-environment-for-chef/

The follow instructions are for Windows PC (it will be similar for Mac):

1. Download and install virtualbox from https://www.virtualbox.org/wiki/Downloads.
2. Download and install Docker
3. Download and install the Windows RubyInstaller for latest 64 bit Ruby 2.x from http://rubyinstaller.org/downloads.
   * Check the option to add ruby to your path.
   * Install the devkit
4. Then install the following gems
  * gem install librarian-puppet
  * gem install test-kitchen
  * gem install kitchen-puppet
  * gem install kitchen-docker
  * gem install kitchen-verifier-serverspec
5. git clone the repository https://github.com/neillturner/puppet_docker_repo

## Check everything installed

In a Docker CLI window in the puppet_docker_repo directory run command
```
kitchen list
```
NOTE: I used Windows Kitematic and select Docker CLI from the bottom of the screen to get a Docker CLI POwershell Windpws
This will return a list if everyting is correctly installed.

## Create Servers in Virtual Box on your Workstation.
```
kitchen create base-centos-7 -l debug
```

## Build the server.
```
kitchen converge base-centos-7 -l debug
```

## Verify the server.
```
kitchen verify base-centos-7 -l debug
```

## Shutdown the server.
```
kitchen destroy base-centos-7 -l debug
```

## References

https://michaelheap.com/test-kitchen-docker-and-centos-7/