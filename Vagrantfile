Vagrant.configure("2") do |config|
  config.vm.base_mac = nil
  #config.ssh.username = "labs"
  #config.ssh.private_key_path = "labs_private"
  config.ssh.forward_agent = true
  config.ssh.insert_key = false

  #config.vm.synced_folder ".", "/vagrant", disabled: true

  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.memory = "1024"
    vb.cpus = 1
    #vb.linked_clone = true
  end

  N = 3
  (1..N).each do |machine_id|
    config.vm.define "nginx-#{machine_id}" do |n|
      #n.vm.hostname = "nginx-#{machine_id}"
      n.vm.network "private_network", ip: "192.168.56.#{20+machine_id}"
      n.vm.network "forwarded_port", guest: 80, host: "#{8080+machine_id}"
      n.vm.network "forwarded_port", guest: 443, host: "#{8442+machine_id}"
      n.vm.box = "test-box"
    end
  end
end
