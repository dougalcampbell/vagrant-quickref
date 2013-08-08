# VAGRANT CLI QUICKREF

## Terminology

* **Boxes** are base images which are used to initialize new Vagrant _environments_.
* **Machines** or **environments** are virtual machines which you run under a _provider_.
* **Providers** are virtual machine hosts, such as VirtualBox, VMWare, or AWS EC2.
* **Provisioners** are customization scripts applied to a _box_ when the _machine_ is brought up.
* **Packages** are `.box` files, created for a particular _provider_.

## COMMANDS

(arranged roughly by order/frequency of use?)

**vagrant box add** [--provider _PROVIDER_ [--insecure]] _NAME_ _URL_

**vagrant box list**

**vagrant box remove** _NAME_ [_PROVIDER_]

**vagrant box repackage** _NAME_ _PROVIDER_

**vagrant init** [_NAME_ [_URL_]]

**vagrant up**

**vagrant ssh-config** [--host _NAME_]

**vagrant ssh** [-c _COMMAND_ | --command _COMMAND_ [-p | --plain [-- _SSH_OPTIONS_]]]

**vagrant suspend**

**vagrant resume**

**vagrant reload** [--no-provision | --provision-with _PROV1_,_PROV2_,_..._]

**vagrant halt** [-f | --force]

**vagrant status**

**vagrant provision** _NAME_ [--provision-with _PROV1_,_PROV2_,_..._]

**vagrant package** [--base _NAME_ [--output _NAME_ [--include _FILE1_,_FILE2_,_..._ [--vagrantfile _FILE_]]]]
> Create a re-usable box image from the current environment.

**vagrant plugin install** _NAME_

**vagrant plugin license** _NAME_ _FILE_

**vagrant plugin** list

**vagrant plugin uninstall** _NAME_

**vagrant destroy** [-f | --force]
> Destroys the current environment, as if it had never been created.

## Typical Workflow
    mkdir myproject
    cd myproject
    vagrant init
    vagrant provision
    vagrant up
    vagrant ssh
    # work, work, work
    vagrant suspend
    # do other stuff
    vagrant resume

