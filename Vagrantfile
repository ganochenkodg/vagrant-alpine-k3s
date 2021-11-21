plugins_dependencies = %w( vagrant-hostmanager)
plugin_status = false
plugins_dependencies.each do |plugin_name|
  unless Vagrant.has_plugin? plugin_name
    system("vagrant plugin install #{plugin_name}")
    plugin_status = true
    puts " #{plugin_name}  Dependencies installed"
  end
end

if plugin_status === true
  exec "vagrant #{ARGV.join' '}"
else
  puts "All Plugin Dependencies already installed"
end

Vagrant.configure("2") do |config|
  config.vm.box = "generic/alpine314"
  config.hostmanager.enabled = true
  config.hostmanager.include_offline = true
  config.hostmanager.manage_host = true
  config.vm.provision :hostmanager

  config.vm.define "alpine-k3s" do |c|
    c.vm.hostname = "alpine-k3s"
    c.vm.network "private_network", ip: "10.168.10.10"
    c.vm.provision "shell", inline: "sudo apk add python3"
    c.vm.provision "ansible", playbook: "ansible/full.yml", run: "always"
    c.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
      vb.cpus = 1
    end
  end
end
