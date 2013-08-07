**VAGRANT CLI QUICKREF**
====================
(verbose version)

BOX
---
**vagrant box add** [--provider _PROVIDER_] _NAME_ _URL_
> Adds the given _URL_ (or file) to Vagrant and stores it under the logical name _NAME_. _PROVIDER_, if given, will verify the box is for the given provider (virtual machine, e.g., VirtualBox, VMWare).By default, Vagrant automatically detects the proper provider to use.

**vagrant box list**
> Lists all the boxes that are installed into Vagrant.

**vagrant box remove** _NAME_ [_PROVIDER_]
> Removes a box from Vagrant that matches the given name and provider.

**vagrant box repackage** _NAME_ _PROVIDER_
> Repackages the given box and puts it in the current directory so you can redistribute it.

> When you add a box, Vagrant unpacks it and stores it internally. The original *.box file is not preserved. This command is useful for reclaiming a *.box file from an installed Vagrant box.

DESTROY
-------
**vagrant destroy** [-f | --force]
> Stops the running machine Vagrant is managing and destroys all resources that were created during the machine creation process. After running this command, your computer should be left at a clean state, as if you never created the guest machine in the first place.

> This command usually asks for confirmation before destroying. This confirmation can be skipped by passing in the -f or --force flag.

HALT
----
**vagrant halt** [-f | --force]
> Shuts down the running machine Vagrant is managing.>Vagrant will first attempt to gracefully shut down the machine by running the guest OS shutdown mechanism. If this fails, or if the --force flag is specified, Vagrant will effectively just shut off power to the machine.

INIT
----
**vagrant init** [_NAME_ [_URL_]]
> Initializes the current directory to be a Vagrant environment by creating an initial Vagrantfile if one doesn't already exist. If arguments are given, it will prepopulate the config.vm.box and config.vm.box_url settings in the created Vagrantfile.

PACKAGE
-------
**vagrant package** [--base _NAME_ --output _NAME_ --include _FILE1_,_FILE2_,_..._ --vagrantfile _FILE_]
> Packages a currently running VirtualBox environment into a re-usable box. This command cannot be used with any other provider. 

> --base _NAME_ - Instead of packaging a VirtualBox machine that Vagrant manages, this will package a VirtualBox machine that VirtualBox manages. NAME should be the name or UUID of the machine from the VirtualBox GUI.

> --output _NAME_ - The resulting package will be saved as NAME, default = 'package.box'.

> --include _FILE1_,_FILE2_,_..._ - Additional files to be packaged with the box

> --vagrantfile _FILE_ - Packages a Vagrantfile with the box, that is loaded as part of the Vagrantfile load order when the resulting box is used.

> A common misconception is that the --vagrantfile option will package a Vagrantfile that is used when vagrant init is used with this box. This is not the case. Instead, a Vagrantfile is loaded and read as part of the Vagrant load process when the box is used. For more information, read about the Vagrantfile load order.

PLUGIN
------
**vagrant plugin install** _NAME_
> Installs a plugin with the given name or file path. If the name is not a path to a file, then the plugin is installed from remote repositories, usually RubyGems.

**vagrant plugin license** _NAME_ _FILE_
> Installs a license for a proprietary Vagrant plugin, such as the VMware Fusion provider.

**vagrant plugin** list
> Lists all installed plugins and their respective versions.

**vagrant plugin uninstall** _NAME_
> Uninstalls the plugin with the given name. Any dependencies of the plugin will also be uninstalled assuming no other plugin needs them.

PROVISION
---------
**vagrant provision** [--provision-with _PROV1_,_PROV2_,_..._]
> Runs any configured provisioners against the running Vagrant managed machine.

> --provision-with _PROV1_,_PROV2_,_..._ - This will only run the given provisioners. For example, if you have a :shell and :chef_solo provisioner and run vagrant provision --provision-with shell, only the shell provisioner will be run.

RELOAD
------
**vagrant reload** [--no-provision | --provision-with _PROV1_,_PROV2_,_..._]
> The equivalent of running a halt followed by an up. Often done to make changes to the Vagrantfile take effect.
> 
> --no-provision - The provisioners will not run.

> --provision-with _PROV1_,_PROV2_,_..._ - This will only run the given provisioners. For example, if you have a :shell and :chef_solo provisioner and run vagrant provision --provision-with shell, only the shell provisioner will be run.

RESUME
------
**vagrant resume**
> Resumes a Vagrant managed machine that was previously suspended..

SSH
---
**vagrant ssh** [-c _COMMAND_ | --command _COMMAND_ [-p | --plain [-- _SSH_OPTIONS_]]]
> SSH into a running Vagrant machine and give you access to a shell.

> If a -- (two hyphens) are found on the command line, any arguments after this are passed directly into the ssh executable. This allows you to pass any abitrary commands to do things such as reverse tunneling down into the ssh program.

> -c _COMMAND_ or --command _COMMAND_ - This executes a single SSH command, prints out the stdout and stderr, and exits.

> -p or --plain - This does an SSH without authentication, leaving authentication up to the user.

SSH CONFIG
----------
**vagrant ssh-config** [--host _NAME_]
> Output valid configuration for an SSH config file to SSH into the running Vagrant machine from ssh directly (instead of using vagrant ssh).

> --host _NAME_ - Name of the host for the outputted configuration.

STATUS
------
**vagrant status**
> Report the state of the machines Vagrant is managing.

SUSPEND
-------
**vagrant suspend**
> Suspends the guest machine Vagrant is managing, rather than fully shutting it down or destroying it. Saves the guest machine's state to disk, and exits, allowing it to be resumed later in the exact same state as before suspension.

UP
--
**vagrant up**
> Creates and configures guest machines according to your Vagrantfile.

