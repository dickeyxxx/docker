Vagrant.configure("2") do |config|
  config.vm.define "core", primary: true do |c|
    c.vm.box = "coreos"
    c.vm.box_url = "http://storage.core-os.net/coreos/amd64-generic/dev-channel/coreos_production_vagrant.box"
    c.vm.hostname = "core"
    c.vm.network :private_network, ip: "192.168.65.2"
  end

  config.vm.define "centos" do |c|
    c.vm.box = "centos65-x86_64"
    c.vm.box_url = "https://github.com/2creatives/vagrant-centos/releases/download/v6.5.1/centos65-x86_64-20131205.box"
    c.vm.hostname = "centos"
    c.vm.network :private_network, ip: "192.168.65.3"
  end
end
