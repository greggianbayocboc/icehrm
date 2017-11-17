acehrm
===========
[![Build Status](https://travis-ci.org/gamonoid/acehrm.svg?branch=master)](https://travis-ci.org/gamonoid/acehrm)

acehrm is a [HRM software](https://acehrm.com) which enable companies of all sizes to [manage HR activities](https://acehrm.com)
properly. 

Useful Links
-------------
 * acehrm Opensource Blog: [http://acehrm.org](http://acehrm.org)
 * acehrm Cloud Hosting: [https://acehrm.com](https://acehrm.com)
 * acehrm Documentation (Opensource and Commercial): [http://blog.acehrm.com](http://blog.acehrm.com)
 * acehrm Blog: [https://acehrm.com/blog](http://acehrm.com/blog)
 * Purchase acehrm Pro: [https://acehrm.com/modules.php](https://acehrm.com/modules.php)
 * Report Issues: [https://github.com/gamonoid/acehrm/issues](https://github.com/gamonoid/acehrm/issues)
 * Feature Requests: [https://bitbucket.org/thilina/acehrm-opensource/issues](https://bitbucket.org/thilina/acehrm-opensource/issues)
 * Community Support: [http://stackoverflow.com/search?q=acehrm](http://stackoverflow.com/search?q=acehrm)

Installation
------------
 * Download the latest release https://github.com/gamonoid/acehrm/releases/latest

 * Copy the downloaded file to the path you want to install iCE Hrm in your server and extract.

 * Create a mysql DB for and user. Grant all on iCE Hrm DB to new DB user.

 * Visit iCE Hrm installation path in your browser.

 * During the installation form, fill in details appropriately.

 * Once the application is installed use the username = admin and password = admin to login to your system.

 Note: Please rename or delete the install folder (<ice hrm root>/app/install) since it could pose a security threat to your iCE Hrm instance.

Manual Installation
-------------------

[](https://thilinah.gitbooks.io/acehrm-guide/content/manual-installation.html)

Upgrade from Previous Versions to Latest Version
------------------------------------------------

Refer: [http://blog.acehrm.com/docs/upgrade/](http://blog.acehrm.com/docs/upgrade/)

Setup acehrm Development Environment
------------------------------------

acehrm development environment is packaged as a Vagrant box. I includes php7, nginx, phpunit and other
software required for running acehrm

Preparing development VM with Vagrant
-------------------------------------

- Clone acehrm from https://github.com/gamonoid/acehrm.git or download the source

- Install Vagrant [https://www.vagrantup.com/downloads.html](https://www.vagrantup.com/downloads.html)

- Install Vagrant host updater plugin [https://github.com/cogitatio/vagrant-hostsupdater](https://github.com/cogitatio/vagrant-hostsupdater)


- Run vagrant up in acehrm root directory (this will download acehrm vagrant image which is  ~1 GB)

```
~ $ vagrant up
```

- Run vagrant ssh to login to the Virtual machine

```
~ $ vagrant ssh
```

- Install ant build in your VM

```
~ $ sudo apt-get install ant
```

- Build acehrm (your acehrm root directory is mapped to /vagrant/ directory in VM)

```
~ $ cd /vagrant
~ $ ant buildlocal
```

- Execute table creation scripts
```
~ $ mysql -udev -pdev dev < /vagrant/core-ext/scripts/acehrmdb.sql
~ $ mysql -udev -pdev dev < /vagrant/core-ext/scripts/acehrm_master_data.sql
~ $ mysql -udev -pdev dev < /vagrant/core-ext/scripts/acehrm_sample_data.sql
```

- Navigate to [](http://clients.app.dev/dev) to load acehrm from VM. (user:admin/pass:admin)

- Unit testing

```
~ $ cd /vagrant
~ $ phpunit
```


