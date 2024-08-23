# vagrant

<!-- ${toc} -->

## install

- [doc](https://developer.hashicorp.com/vagrant/install)

```sh
wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install vagrant
```

## commands

<!-- cmd | desc.
-|-
vagrant init | init
vagrant up | start a vm
vagrant halt | shut down a vm
vagrant destroy | set a vm to its initial state by cleaning all data
vagrant ssh <vm target> | connect to a running instance
vagrant box update | Update the os
vagrant box list | List all local boxes -->

### Creating a VM
- `vagrant init`           -- Initialize Vagrant with a Vagrantfile and ./.vagrant directory, using no specified base image. Before you can do vagrant up, you'll need to specify a base image in the Vagrantfile.
- `vagrant init <boxpath>` -- Initialize Vagrant with a specific box. To find a box, go to the [public Vagrant box catalog](https://app.vagrantup.com/boxes/search). When you find one you like, just replace it's name with boxpath. For example, `vagrant init ubuntu/trusty64`.

### Starting a VM
- `vagrant up`                  -- starts vagrant environment (also provisions only on the FIRST vagrant up)
- `vagrant resume`              -- resume a suspended machine (vagrant up works just fine for this as well)
- `vagrant provision`           -- forces reprovisioning of the vagrant machine
- `vagrant reload`              -- restarts vagrant machine, loads new Vagrantfile configuration
- `vagrant reload --provision`  -- restart the virtual machine and force provisioning

### Getting into a VM
- `vagrant ssh`           -- connects to machine via SSH
- `vagrant ssh <boxname>` -- If you give your box a name in your Vagrantfile, you can ssh into it with boxname. Works from any directory.

### Stopping a VM
- `vagrant halt`        -- stops the vagrant machine
- `vagrant suspend`     -- suspends a virtual machine (remembers state)

### Cleaning Up a VM
- `vagrant destroy`     -- stops and deletes all traces of the vagrant machine
- `vagrant destroy -f`   -- same as above, without confirmation

### Boxes
- `vagrant box list`              -- see a list of all installed boxes on your computer
- `vagrant box add <name> <url>`  -- download a box image to your computer
- `vagrant box outdated`          -- check for updates vagrant box update
- `vagrant box remove <name>`   -- deletes a box from the machine
- `vagrant package`               -- packages a running virtualbox env in a reusable box

### Saving Progress
-`vagrant snapshot save [options] [vm-name] <name>` -- vm-name is often `default`. Allows us to save so that we can rollback at a later time

### Tips
- `vagrant -v`                    -- get the vagrant version
- `vagrant status`                -- outputs status of the vagrant machine
- `vagrant global-status`         -- outputs status of all vagrant machines
- `vagrant global-status --prune` -- same as above, but prunes invalid entries
- `vagrant provision --debug`     -- use the debug flag to increase the verbosity of the output
- `vagrant push`                  -- yes, vagrant can be configured to [deploy code](http://docs.vagrantup.com/v2/push/index.html)!
- `vagrant up --provision | tee provision.log`  -- Runs `vagrant up`, forces provisioning and logs all output to a file

## Plugins
- [vagrant-hostsupdater](https://github.com/cogitatio/vagrant-hostsupdater) : `$ vagrant plugin install vagrant-hostsupdater` to update your `/etc/hosts` file automatically each time you start/stop your vagrant box.

<!-- - If you are using [VVV](https://github.com/varying-vagrant-vagrants/vvv/), you can enable xdebug by running `vagrant ssh` and then `xdebug_on` from the virtual machine's CLI. -->

## configuration file

vagrant file

```ruby
# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  
  config.ssh.insert_key = false
  
  config.vm.synced_folder ".", "/vagrant", disabled: true

  config.vm.provider :virtualbox do |v|
    v.memory = 256
    v.linked_clone = true
  end
  
  # app server 1
  config.vm.define "app1" do |app|
    app.vm.hostname = "orc-app1.test"
    app.vm.network :private_network, ip: "192.168.56.1"
  end

end
```

## Multi machines

https://developer.hashicorp.com/vagrant/docs/multi-machine