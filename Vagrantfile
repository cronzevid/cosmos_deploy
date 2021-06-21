Vagrant.configure("2") do |config|
  config.vm.provider :virtualbox do |vb|
      vb.name = "test-box"
      vb.memory = 2048
  end
  config.vm.define "test-box"
  config.vm.hostname = "test-box"
  config.vm.box = "ubuntu/focal64"
  config.vm.provision "file", 
    source: "~/.ssh/id_rsa.pub", 
    destination: "/tmp/authorized_keys"
  config.vm.provision "shell",
    inline: "sudo mv /tmp/authorized_keys /root/.ssh/authorized_keys && chown -R root:root /root/.ssh && chmod 600 /root/.ssh/authorized_keys && chmod 700 /root/.ssh/"
  config.vm.network "forwarded_port", guest: 1317, host: 13170
end
