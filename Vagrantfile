Vagrant::Config.run do  | config |
	config.vm.box = "hurly"
 	config.vm.box_url = "./hurly.box" ## "https://dl.dropbox.com/u/98660990/hurly.box"
	
	config.vm.network :hostonly, "33.33.33.33"
	config.vm.share_folder "webroot" , "/var/www/", "./webroot/", :owner => "www-data" 
 
   config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = ["cookbooks"]
    #chef.add_recipe "apt"
    chef.add_recipe "build-essential"
    chef.add_recipe "percona::package_repo"
   #chef.add_recipe "mysql::ruby"
    chef.add_recipe "percona::server"
    chef.add_recipe "percona::client"
    chef.add_recipe "nginx"
    chef.add_recipe "php"
    chef.add_recipe "php::module_apc"
    chef.add_recipe "php::module_curl"
    chef.add_recipe "php::module_gd"
    chef.add_recipe "php::module_mysql"		
    #chef.add_recipe "php"
    chef.add_recipe "php-fpm"
    #chef.add_recipe "database::mysql"
    chef.json = {
          "mysql" => {
                "server_root_password" => "iloverandompasswordsbutthiswilldo",
                "server_repl_password" => "iloverandompasswordsbutthiswilldo",
                "server_debian_password" => "iloverandompasswordsbutthiswilldo",
                "server" => {
                     "packages" => ["percona-server-server"]
                                         },
                "client" => {
                    "packages" => ["percona-server-client", "libmysqlclient-dev"]
                          }
                          }
                        }
  end
end
