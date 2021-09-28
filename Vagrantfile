vm_list = [
  ["ansible",    "192.168.110.33"],
  ["webserver1", "192.168.110.34"]
]
 
Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  # 必要に応じてホストOSの方へゲストOSの情報を追加
  # config.hostmanager.manage_host = true
   
  vm_list.each do |v|
    config.vm.define v[0] do |vm_conf|
      vm_conf.vm.network "private_network", ip: v[1]
      vm_conf.vm.hostname = v[0]
    end
  end
 
  config.vm.provider "virtualbox" do |vb|
    # 適宜メモリは調整する
    # vb.memory = "1024"
  end
 
  config.vm.provision "shell", inline: <<-SHELL
    sudo timedatectl set-timezone Asia/Tokyo;
    sudo yum -y install git vim wget zip;
    sudo sed -i -e "s/^SELINUX=enforcing$/SELINUX=disabled/" /etc/selinux/config;
    setenforce 0;
  SHELL
end
