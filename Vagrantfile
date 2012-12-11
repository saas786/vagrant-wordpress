Vagrant::Config.run do |config|
  config.vm.define :wpvm do |wp_config|

    # Box
    wp_config.vm.box = "precise32"

    # Box URL
    wp_config.vm.box_url = "http://files.vagrantup.com/precise32.box"

    # Shared folder
    wp_config.vm.share_folder "v-data", "www", "data", :owner => "www-data", :group => "www-data"

    # Ports
    wp_config.vm.forward_port 80, 8080

    # Chef solo
    wp_config.vm.provision :chef_solo do |chef|
      chef.cookbooks_path = "./cookbooks"
      chef.add_recipe "apt"
      chef.add_recipe "build-essential"
      chef.add_recipe "git"
      chef.add_recipe "subversion"
      chef.add_recipe "vim"
      chef.add_recipe "apache2"
      chef.add_recipe "mysql::server"
      chef.add_recipe "php"
      chef.add_recipe "openssl"
      chef.add_recipe "wordpress"

      chef.json = {
        "mysql" => {
          "server_root_password" => "vagrant",
          "server_repl_password" => "vagrant",
          "server_debian_password" => "vagrant"
        },
        "wordpress" => {
          "dir" => "/home/vagrant/www"
        }
      }

    end

  end
end