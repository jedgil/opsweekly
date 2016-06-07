# -*- mode: ruby -*-
# vi: set ft=ruby :

  Vagrant.configure(2) do |config|

  config.vm.box = "jedgil/opsweekly" # if atlas is behaving properly
  # config.vm.box = "opsweekly-tiny.box" # if working from local .box file
  # config.vm.box_check_update = false

  config.vm.network :forwarded_port, guest: 80, host: 4567
  config.vm.network :forwarded_port, guest: 80, host: 3306 # for mysql

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "private_network", ip: "192.168.33.10"
  config.vm.hostname = "opsweekly.local"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  config.vm.synced_folder ".", "/home/vagrant/vagrantshare", :mount_options => ["dmode=777", "fmode=666"]

  config.vm.provider "virtualbox" do |vb|
    # Display the VirtualBox GUI when booting the machine
    vb.gui = false

    # Customize the amount of memory on the VM:
    vb.memory = "4096"

    # disable USB
    vb.customize ["modifyvm", :id, "--usb", "off"]
    vb.customize ["modifyvm", :id, "--usbehci", "off"]

  end

end
