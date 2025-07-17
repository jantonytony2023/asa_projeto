# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "debian/bookworm64"
  config.ssh.insert_key = false

 # config.trigger.after :up, type: :action do |trigger|
  #  trigger.name = "Parar DHCP do VirtualBox"
   # trigger.run = {inline: "VBoxManage dhcpserver stop --interface vboxnet0"}
 # end

  #config.trigger.after :"Vagrant::Action::Builtin::WaitForCommunicator", type: :"Vagrant::Action::Builtin::WaitForCommunicator" do
   # run = {inline: "vboxmanage dhcpserver stop --interface vboxnet0"}
  #end
  config.vm.provider "virtualbox" do |vb|
    vb.linked_clone = true
    vb.memory = "512"
    vb.check_guest_additions = false
    config.vbguest.auto_update = false
  end

  config.vm.define "arq" do |arq|
    arq.vm.hostname = "arq.jantony.jonatas.devops"
    arq.vm.network "private_network", ip: "192.168.56.124"
    (1..3).each do |x|
      arq.vm.disk :disk, size: "10GB", name: "arq_disk_#{x}"
    end
    arq.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
    end
    arq.vm.provision "ansible" do |ansible|
      ansible.compatibility_mode = "2.0"
      ansible.playbook = "ansible/arq_playbook.yml"
      ansible.inventory_path = "ansible/hosts"
    end 
   end

  config.vm.define "db" do |db|
    db.vm.hostname = "db.jantony.jonatas.devops"
    db.vm.network "private_network", type: "dhcp"
    db.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
    end
    db.vm.provision "ansible" do |ansible|
      ansible.compatibility_mode = "2.0"
      ansible.playbook = "ansible/db_playbook.yml"
      ansible.inventory_path = "ansible/hosts"
    end 
  end

  config.vm.define "app" do |app|
    app.vm.hostname = "app.jantony.jonatas.devops"
    app.vm.network "private_network", type: "dhcp"
    app.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
    end
    app.vm.provision "ansible" do |ansible|
      ansible.compatibility_mode = "2.0"
      ansible.playbook = "ansible/app_playbook.yml"
      ansible.inventory_path = "ansible/hosts"
    end
  end

  config.vm.define "cli" do |cli|
    cli.vm.hostname = "cli.jantony.jonatas.devops"
    cli.vm.network "private_network", type: "dhcp"
    cli.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
    end
    cli.vm.provision "ansible" do |ansible|
      ansible.compatibility_mode = "2.0"
      ansible.playbook = "ansible/cli_playbook.yml"
      ansible.playbook = "ansible/common_config.yml"
      ansible.inventory_path = "ansible/hosts"
    end
 end
end

