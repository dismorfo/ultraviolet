Vagrant.configure("2") do |config|
  config.vm.box = "bento/centos-8"

  # Enable GUI
  config.vm.provider "virtualbox" do |v|
    v.memory = 4096
    v.cpus = 2
  end
  if Vagrant.has_plugin?("vagrant-vbguest")
    config.vbguest.auto_update = false
  end

  # Create a synced folder
  config.vm.synced_folder ".", "/home/vagrant/ultraviolet", owner: 'vagrant'

  $python_install = <<-SCRIPT
    yum -y install epel-release
    yum -y install git gcc zlib-devel bzip2-devel readline-devel sqlite-devel openssl-devel
    curl https://pyenv.run | bash
    echo 'export PATH="$HOME/.pyenv/bin:$PATH"' >> ~/.bashrc
    echo 'eval "$(pyenv init -)"' >> ~/.bashrc
    echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.bashrc
    source ~/.bashrc
    pyenv update
    pyenv install 3.7.9
    pyenv global 3.7.9
    pip install --upgrade pip
    python -m pip install invenio-cli
  SCRIPT

  $docker_install = <<-SCRIPT
    sudo curl -L "https://github.com/docker/compose/releases/download/1.29.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
    sudo chmod +x /usr/local/bin/docker-compose
  SCRIPT

  config.vm.provision :shell, privileged: true, inline: $python_install
  config.vm.provision :shell, privileged: true, inline: $docker_install
end
