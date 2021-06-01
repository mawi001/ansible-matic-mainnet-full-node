Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"

  config.vm.provider "virtualbox" do |v|
    v.memory = 8072
    v.cpus = 4
  end

  config.vm.define "host1"

  config.vm.synced_folder "/mnt/data", "/data"

  $script = <<-SCRIPT
  echo I am provisioning...
  # enable ansible localhost in order to run ansible-playbook inside vagrant
  sed -i "s/.*PasswordAuthentication.*/PasswordAuthentication yes/g" /etc/ssh/sshd_config
  service ssh restart
  SCRIPT

  config.vm.provision "shell",  inline: $script

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/deploy.yml"
    ansible.groups = {
      "matic" => ["host1"],
    }
  end
end
