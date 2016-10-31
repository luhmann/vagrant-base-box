# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # config.vm.box = "parallels/ubuntu-14.04"
  config.vm.box = "puphpet/ubuntu1404-x64"
  config.vm.network :private_network, ip: "192.168.50.50"
  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "vv"
    ansible.playbook = "provisioning/173.yml"
    ansible.inventory_path = "provisioning/vagrant-inventory"
    ansible.host_key_checking = "false"
    ansible.limit = "all"
  end

  config.vm.provider "parallels" do |v|
      v.update_guest_tools = true
      v.optimize_power_consumption = false
      v.memory = 1024
      v.cpus = 2
  end

  config.vm.synced_folder ".", "/srv/www/einssiebendrei", owner:"www-data", group:"www-data"
end
