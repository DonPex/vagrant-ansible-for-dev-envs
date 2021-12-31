Vagrant.configure("2") do |config|

  config.vm.box = "hashicorp/bionic64"
  config.vm.network "public_network", ip: "192.168.1.99"
  #config.vm.network "private_network", ip: "100.93.71.99"
  config.vm.synced_folder "sync/", "/ext/shared"
  
  if Vagrant.has_plugin?("vagrant-timezone")
    config.timezone.value = "UTC"
  end
  
  config.vm.provider "virtualbox" do |vm|
    vm.memory = 4096
    vm.cpus = 2
	vm.name = "dev_machine"
	#vm.gui = true
  end
  
  # trigger that updates datetime (optional) 
  config.trigger.after [:up, :resume] do |trigger|
	trigger.info = "Adjusting time according to Google.com ..."
	trigger.run_remote = {inline: "sudo date -s \"$(wget -qSO- --max-redirect=0 google.com 2>&1 | grep Date: | cut -d' ' -f5-8)Z\""}
  end

  #INSTALL DOCKER + DOCKER COMPOSE
  config.vagrant.plugins = "vagrant-docker-compose"
  config.vm.provision :docker
  config.vm.provision :docker_compose
  
  config.vm.provision "ansible_local" do |ansible|
    ansible.galaxy_role_file = 'requirements.yml'
    ansible.playbook = "playbook.yml"
    ansible.version = "2.9.27"
  end

  
  
end

