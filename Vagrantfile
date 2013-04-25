# -*- mode: ruby -*-
# # vi: ft=ruby

Vagrant.configure('2') do |config|
  config.vm.box = 'ubuntu1204'
  config.vm.box_url = 'http://f.willianfernandes.com.br/vagrant-boxes/UbuntuServer12.04amd64.box'
  config.vm.hostname = 'redmine-box'

  config.vm.provider :virtualbox do |vb|
    # Disable GUI, use headless mode
    vb.gui = false

    # Use VBoxManage to customize the VM. For example to change memory:
    vb.customize ['modifyvm', :id, '--memory', '1024']
  end

  if ENV['VAGRANT_ENV'] == 'test'
    config.vm.provision :chef_solo do |chef|
      chef.cookbooks_path = ['cookbooks', 'site-cookbooks']
      chef.roles_path = 'roles'

      chef.add_role 'redmine'
    end
  end
end
