Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"

  config.vm.provider "virtualbox" do |v|
    v.memory = 4096
    v.cpus = 2
  end

  config.vm.define "host1"

  config.vm.synced_folder "/mnt/data", "/data"

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/deploy.yml"
    ansible.groups = {
      "matic" => ["host1"],
    }
  end
end
