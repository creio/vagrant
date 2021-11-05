# ENV["LC_ALL"] = "en_US.UTF-8"

Vagrant.configure("2") do |config|
  # config.vagrant.plugins = ["vagrant-vbguest", "vagrant-share", "vagrant-libvirt"]

  #config.vm.box = "base"
  # config.vm.box = "archlinux/archlinux"

  # config.vm.box_check_update = false
  # config.vm.network "forwarded_port", guest: 80, host: 8080
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
  # config.vm.network "private_network", ip: "192.168.33.10"
  # config.vm.network "public_network"

  config.vm.synced_folder "./data", "/vagrant_data"
  config.vm.provision "shell", inline: <<-SHELL
    pacman -Syy --noconfirm htop
  SHELL

  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL

  config.vm.define "vbox" do |vbox|
    vbox.vm.box = "archlinux/archlinux"
    vbox.vm.hostname = "vbox"

    vbox.vm.provider :virtualbox do |vb|
      vb.memory = 2048
      vb.cpus = 2
      # vb.gui = true
      # config.vagrant.plugins = "vagrant-disksize"
      # config.disksize.size = "30GB"
    end
  end

  (1..2).each do |i|
    config.vm.define "vbox#{i}" do |node|
      node.vm.box = "archlinux/archlinux"
      node.vm.hostname = "vbox#{i}"

      node.vm.provider :virtualbox do |vb|
        vb.memory = 1024
        vb.cpus = 2
      end
    end
  end

  # config.vm.define "mysql" do |mysql|
  #   mysql.vm.box = "archlinux/archlinux"
  #   mysql.vm.hostname = "mysql"
  # end

  # ## export VAGRANT_DEFAULT_PROVIDER=libvirt
  # ## Resize the disk image file: $ vagrant halt
  # ## sudo qemu-img resize /var/lib/libvirt/images/arch_default.img +10G
  # ## sudo qemu-img resize --shrink /var/lib/libvirt/images/arch_default.img -10G
  # config.vm.define "libvirt" do |libvirt|
  #   libvirt.vm.box = "archlinux/archlinux"
  #   libvirt.vm.hostname = "libvirt"

  #   libvirt.vm.provider :libvirt do |lv|
  #     lv.driver = "kvm"
  #     lv.memory = 2048
  #     lv.cpus = 2
  #     # lv.connect_via_ssh = false
  #     # lv.username = "root"
  #     # lv.password = "secret"
  #     lv.storage_pool_name = "default"
  #     #lv.default_prefix = ''
  #     lv.storage :file, :size => "5G"
  #   end
  # end

end
