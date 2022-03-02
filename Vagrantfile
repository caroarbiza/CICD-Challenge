Vagrant.configure("2") do |config|

  config.vm.define "jenkins" do |jenkins|
    jenkins.vm.box = "dmhughes/ubuntu-18.04-desktop-gui"
    jenkins.vm.box_version = "0.0.1"
    jenkins.vm.network "private_network", ip: "192.168.108.200", :name => 'VirtualBox Host-Only Ethernet Adapter', :adapter => 2
    
  end 
  
  config.vm.define "app" do |app|
    app.vm.box = "generic/ubuntu1804"
    app.vm.network "private_network", ip: "192.168.108.210", :name => 'VirtualBox Host-Only Ethernet Adapter', :adapter => 2
    app.vm.network "forwarded_port", guest: 80, host: 3030
  end  

end
