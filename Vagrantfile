# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # jenkins server
  config.vm.define "jenkins-pipeline" do |jenkins|
    jenkins.vm.box = "debian/buster64"
    jenkins.vm.hostname = "jenkins-pipeline"
    jenkins.vm.box_url = "debian/buster64"
    jenkins.vm.network :private_network, ip: "192.168.5.2"
    jenkins.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
      v.customize ["modifyvm", :id, "--memory", 3072]
      v.customize ["modifyvm", :id, "--name", "jenkins-pipeline"]
      v.customize ["modifyvm", :id, "--cpus", "2"]
    end
    config.vm.provision "shell", inline: <<-SHELL
      sed -i 's/ChallengeResponseAuthentication no/ChallengeResponseAuthentication yes/g' /etc/ssh/sshd_config    
      service ssh restart
    SHELL
    jenkins.vm.provision "shell", path: "install_jenkins.sh"
  end

# serveur dev
  config.vm.define "srvdev-pipeline" do |srvdev|
    srvdev.vm.box = "debian/buster64"
    srvdev.vm.hostname = "srvdev-pipeline"
    srvdev.vm.box_url = "debian/buster64"
    srvdev.vm.network :private_network, ip: "192.168.5.3"
    srvdev.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
      v.customize ["modifyvm", :id, "--memory", 512]
      v.customize ["modifyvm", :id, "--name", "srvdev-pipeline"]
      v.customize ["modifyvm", :id, "--cpus", "1"]
    end
    config.vm.provision "shell", inline: <<-SHELL
      sed -i 's/ChallengeResponseAuthentication no/ChallengeResponseAuthentication yes/g' /etc/ssh/sshd_config
      service ssh restart
    SHELL
  end

  # serveur stage/recette
  config.vm.define "srvstage-pipeline" do |srvstage|
    srvstage.vm.box = "debian/buster64"
    srvstage.vm.hostname = "srvstage-pipeline"
    srvstage.vm.box_url = "debian/buster64"
    srvstage.vm.network :private_network, ip: "192.168.5.7"
    srvstage.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
      v.customize ["modifyvm", :id, "--memory", 512]
      v.customize ["modifyvm", :id, "--name", "srvstage-pipeline"]
      v.customize ["modifyvm", :id, "--cpus", "1"]
    end
    config.vm.provision "shell", inline: <<-SHELL
      sed -i 's/ChallengeResponseAuthentication no/ChallengeResponseAuthentication yes/g' /etc/ssh/sshd_config
      service ssh restart
    SHELL
  end

  # serveur prod
  config.vm.define "srvprod-pipeline" do |srvprod|
    srvprod.vm.box = "debian/buster64"
    srvprod.vm.hostname = "srvprod-pipeline"
    srvprod.vm.box_url = "debian/buster64"
    srvprod.vm.network :private_network, ip: "192.168.5.4"
    srvprod.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
      v.customize ["modifyvm", :id, "--memory", 512]
      v.customize ["modifyvm", :id, "--name", "srvprod-pipeline"]
      v.customize ["modifyvm", :id, "--cpus", "1"]
    end
    config.vm.provision "shell", inline: <<-SHELL
      sed -i 's/ChallengeResponseAuthentication no/ChallengeResponseAuthentication yes/g' /etc/ssh/sshd_config
      service ssh restart
    SHELL
  end

# Serveur bdd 
  config.vm.define "srvbdd-pipeline" do |srvbdd|
    srvbdd.vm.box = "debian/buster64"
    srvbdd.vm.hostname = "srvbdd-pipeline"
    srvbdd.vm.box_url = "debian/buster64"
    srvbdd.vm.network :private_network, ip: "192.168.5.6"
    srvbdd.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
      v.customize ["modifyvm", :id, "--memory", 512]
      v.customize ["modifyvm", :id, "--name", "srvbdd-pipeline"]
      v.customize ["modifyvm", :id, "--cpus", "1"]
    end
    config.vm.provision "shell", inline: <<-SHELL
      sed -i 's/ChallengeResponseAuthentication no/ChallengeResponseAuthentication yes/g' /etc/ssh/sshd_config    
      service ssh restart
    SHELL
    srvbdd.vm.provision "shell", path: "install_srvpostgres.sh"
  end

 # Serveur registry
  config.vm.define "registry-pipeline" do |registry|
    registry.vm.box = "debian/buster64"
    registry.vm.hostname = "registry-pipeline"
    registry.vm.box_url = "debian/buster64"
    registry.vm.network :private_network, ip: "192.168.5.5"
    registry.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
      v.customize ["modifyvm", :id, "--memory", 512]
      v.customize ["modifyvm", :id, "--name", "registry-pipeline"]
      v.customize ["modifyvm", :id, "--cpus", "1"]
    end
    config.vm.provision "shell", inline: <<-SHELL
      sed -i 's/ChallengeResponseAuthentication no/ChallengeResponseAuthentication yes/g' /etc/ssh/sshd_config    
      service ssh restart
    SHELL
    registry.vm.provision "shell", path: "install_registry.sh"
  end

# Serveur gitlab
  config.vm.define "gitlab-pipeline" do |gitlab|
    gitlab.vm.box = "debian/buster64"
    gitlab.vm.hostname = "gitlab-pipeline"
    gitlab.vm.box_url = "debian/buster64"
    gitlab.vm.network :private_network, ip: "192.168.5.10"
    gitlab.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
      v.customize ["modifyvm", :id, "--memory", 2048]
      v.customize ["modifyvm", :id, "--name", "gitlab-pipeline"]
      v.customize ["modifyvm", :id, "--cpus", "1"]
    end
    config.vm.provision "shell", inline: <<-SHELL
      sed -i 's/ChallengeResponseAuthentication no/ChallengeResponseAuthentication yes/g' /etc/ssh/sshd_config
      service ssh restart
    SHELL
    gitlab.vm.provision "shell", path: "install_gitlab.sh"
  end

end

