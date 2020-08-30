vm_list = [
  "ansible",
  "webserver1"
]

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.hostmanager.enabled = true

  # 必要に応じてホストOSの方へゲストOSの情報を追加
  # config.hostmanager.manage_host = true

  vm_list.each_with_index do |vm_name,i|
    config.vm.define vm_name do |vm_conf|
      vm_conf.vm.network "private_network", ip: "192.168.33.#{10+i}"
      vm_conf.vm.hostname = vm_name
    end
  end
end
