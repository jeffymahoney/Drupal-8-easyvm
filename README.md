Drupal-8-easyvm
================

Virtual Machine for Drupal 8 development (VirtualBox 4.3). This is **NOT** a secure configuration and should **NOT** be used for a production machine.

After ```vagrant up``` and waiting (there is lot to download and install) you should have a fresh Drupal 8 virtual machine with Drupal 8 installed and ready to go. You can access it straight away on the url ```127.0.0.1:8080``` in your web browser and/or by adding an entry to your hosts file ```192.168.9.10 drupal8.dev``` and accessing 

This project was based on Drupal vm project at https://drupal.org/project/vm
Originally generated from a configuration from https://puphpet.com/

Aiming to add some variations, so far:

* Added .gitattributes to ensure shell file line endings remain LF
* Raised the VM memory from 512 to 1024MB (may bump this back down again)
* Fixed the Puppet version updated to 3.4.3 otherwise the Puphpet base install fails with later versions
* Added a shell script to exec-once to perform the clone and install of Drupal 8
* Added install of php-apc to the exec-once script until I can discover why the puphpet.com setup fails to install APC via PECL on ubuntu correctly.
* Configured the default vhost to serve up Drupal on 127.0.0.1:8080
* Removed sharing of the folder www for Windows host machines
* Added a text file that can removed and or moved to allow NFS sharing to be attempted by Vagrant for Linux and OSX host machines.

Still to do:
* Add a Samba share that can be used by Windows host machines.
* Flatten and remove the configuration for puphpet for other guest OSes
* etc. etc.

**Note:** The current configuration does not use an NFS mount for the shared www directory on Linux and OSX which will probably make things rather slow. There is a file in the project directory called NFS_block.txt if this is removed or renamed then the share should be set up using NFS.

#### Minimum requirements
* Git (only if you want to clone the code, see 1. below)
* VirtualBox 4.3.x
* Vagrant 1.5.x

#### How to install

1.- Get the code

You can either clone the code with git as follows:
```bash
$ git clone https://github.com/chris-hall-hu/Drupal-8-easyvm.git drupal8.dev
```  
**_OR_**  
download a zip file from [https://github.com/chris-hall-hu/Drupal-8-easyvm/archive/master.zip](https://github.com/chris-hall-hu/Drupal-8-easyvm/archive/master.zip) and unpack into a drupal8.dev directory.

2.- Start you VM with Vagrant

Enter your drupal8.dev directory on the command line and type:

```
vagrant up
```
This will take a while first time around as there is a lot that is automatically downloaded and installed.

3.- Enjoy Drupal 8

The admin account is set up with

**name**: admin  
**pass**: admin

#### Tools on vm
* composer
* drush for drupal 8
* xdebug
* vim

#### Database Credentials
* Name: drupal
* User: drupal
* Pass: drupal


