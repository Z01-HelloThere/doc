# How to create and launch a VM

<!-- this file is incompatible with Joplin -->

## Requirement

  - Virtualbox
  - Vagrant
  - 


## install

- [doc](https://developer.hashicorp.com/vagrant/install)

=== "ubuntu"

    ```sh
    wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
    echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
    sudo apt update && sudo apt install vagrant
    ```

=== "fedora"

    ```sh
    sudo dnf install -y dnf-plugins-core
    sudo dnf config-manager --add-repo https://rpm.releases.hashicorp.com/fedora/hashicorp.repo
    sudo dnf -y install vagrant
    ```

=== "homebrew"

    ```sh
    brew tap hashicorp/tap
    brew install hashicorp/tap/vagrant
    ```


### test

=== "C"

    ``` c
    #include <stdio.h>

    int main(void) {
      printf("Hello world!\n");
      return 0;
    }
    ```

=== "C++"

    ``` c++
    #include <iostream>

    int main(void) {
      std::cout << "Hello world!" << std::endl;
      return 0;
    }
    ```

## commands (basics)

cmd | desc.
-|-
`vagrant init` | To initate Vagrant
`vagrant up` | To start a vm
`vagrant ssh` | To connect to a running instance
`vagrant halt` | To shut down a vm
`vagrant destroy` | To set a vm to its initial state by cleaning all data
`vagrant ssh <vm target>` | Connect to machine via SSH
`vagrant box update` | To start a vm
`vagrant box list` | List all local boxes
`vagrant box update` | 

## configuration file (Vagrantfile)

  - [Vagrantfile - doc](https://developer.hashicorp.com/vagrant/docs/vagrantfile)

### create the `Vagrantfile`

```ruby
# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/jammy64"

  config.ssh.insert_key = false

  config.vm.synced_folder ".", "/vagrant", disabled: true

  config.vm.provider :virtualbox do |v|
    v.memory = 256
    v.linked_clone = true
  end

  # Run Ansible from the Vagrant Host
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
  end

  # app server
  config.vm.define "app1" do |app|
    app.vm.hostname = "orc-app1.test"
    app.vm.network :private_network, ip: "192.168.56.1"
  end

end
```

## connect to a vm

```sh
vagrant ssh ub01
```

### multi machines

https://developer.hashicorp.com/vagrant/docs/multi-machine

vagrant init ubuntu/jammy64
vagrant up