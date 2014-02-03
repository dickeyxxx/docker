Vagrant.configure("2") do |config|
  config.ssh.private_key_path = "~/.ssh/id_rsa"
  config.ssh.forward_agent = true

  config.vm.define "ubuntu", primary: true do |c|
    c.vm.box = "ubuntu-vagrant"
    c.vm.box_url = "https://oss-binaries.phusionpassenger.com/vagrant/boxes/ubuntu-12.04.3-amd64-vbox.box"
    c.vm.hostname = "ubuntu"
    c.vm.network :private_network, ip: "192.168.65.2"

    if Dir.glob("#{File.dirname(__FILE__)}/.vagrant/machines/default/*/id").empty?
      # Install Docker
      pkg_cmd = "wget -q -O - https://get.docker.io/gpg | apt-key add -;" \
        "echo deb http://get.docker.io/ubuntu docker main > /etc/apt/sources.list.d/docker.list;" \
        "apt-get update -qq; apt-get install -q -y --force-yes lxc-docker; "
      # Add vagrant user to the docker group
      pkg_cmd << "usermod -a -G docker vagrant; "
      config.vm.provision :shell, :inline => pkg_cmd
    end
  end

  config.vm.define "core" do |c|
    c.vm.box = "coreos"
    c.vm.box_url = "http://storage.core-os.net/coreos/amd64-generic/dev-channel/coreos_production_vagrant.box"
    c.vm.hostname = "core"
    c.vm.network :private_network, ip: "192.168.65.3"
  end

  config.vm.define "centos" do |c|
    c.vm.box = "centos65-x86_64"
    c.vm.box_url = "https://github.com/2creatives/vagrant-centos/releases/download/v6.5.1/centos65-x86_64-20131205.box"
    c.vm.hostname = "centos"
    c.vm.network :private_network, ip: "192.168.65.4"
  end
end
