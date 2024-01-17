# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.vm.box = "kalilinux/rolling"
  config.ssh.forward_x11 = true
  config.ssh.forward_agent = true
  config.vm.hostname = "kali"
  config.vm.define :kali do |t|
  end

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine and only allow access
  # via 127.0.0.1 to disable public access
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  config.vm.synced_folder "../Assessments/", "/assessments"
  config.vm.synced_folder "../ctfs/", "/ctfs"

  # Disable the default share of the current code directory. Doing this
  # provides improved isolation between the vagrant box and your host
  # by making sure your Vagrantfile isn't accessable to the vagrant box.
  # If you use this you may want to enable additional shared subfolders as
  # shown above.
  # config.vm.synced_folder ".", "/vagrant", disabled: true

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
   config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
     vb.gui = false
     vb.name = "kali"
  #
  #   # Customize the amount of memory on the VM:
     vb.memory = "4096"
   end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Ansible, Chef, Docker, Puppet and Salt are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # Runs as Super User by default
   config.vm.provision "shell", inline: <<-SHELL
     apt-get update && apt upgrade -y && apt install -y
     #install apt available tools
     apt-get install -y gobuster seclists sublist3r snapd bc build-essentials dkms
     apt install autoremove
     systemctl start snapd.seeded.service
     #install go & nuclei
     snap install go --classic
     /snap/bin/go version
     /snap/bin/go install -v github.com/projectdiscovery/nuclei/v3/cmd/nuclei@latest
     chsh -s /usr/bin/tmux vagrant
   SHELL

   config.vm.provision "shell", privileged: false, inline: <<-SHELL
     #install oh-my-zsh and theme
     sh -c "$(wget https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"
     wget https://raw.githubusercontent.com/coronito1337/pentester-theme/main/pentest.zsh-theme -O ~/.oh-my-zsh/themes/pentest.zsh-theme
     sed -i -e 's/robbyrussell/pentest/g' ~/.zshrc

     #install autocompletion plugins
     git clone https://github.com/zsh-users/zsh-autosuggestions.git ~/.oh-my-zsh/plugins/zsh-autosuggestions
     git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ~/.oh-my-zsh/plugins/zsh-syntax-highlighting
     git clone https://github.com/zdharma-continuum/fast-syntax-highlighting.git ~/.oh-my-zsh/plugins/fast-syntax-highlighting
     git clone https://github.com/zsh-users/zsh-completions.git ~/.oh-my-zsh/plugins/zsh-completions
     sed -i -e 's/plugins=\(git\)/plugins=\(tmux git zsh-autosuggestions zsh-syntax-highlighting fast-syntax-highlighting zsh-completions\)/g' ~/.zshrc
     echo 'set-option -g default-shell "/usr/bin/zsh"' > ~/.tmux.conf
     echo 'set -g mouse on' >> ~/.tmux.conf  
     SHELL
end
