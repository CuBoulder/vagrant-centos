Vagrant.configure("2") do |config|
  config.vm.box = "generic/centos8"
  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  config.vm.network "public_network", bridge: [
    "en1: Wi-Fi (AirPort)",
    "en2: Wi-Fi (AirPort)",
  ]
  config.ssh.insert_key = false
  # Ansible is executed on Vagrant host
  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.extra_vars = "vars.yaml"
    ansible.config_file = "baseline/ansible.cfg"
    ansible.playbook = "baseline/test_playbook.yaml"
  end
  config.vm.provider "virtualbox"
end
