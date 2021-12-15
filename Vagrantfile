MASTER_NUM = 1
MASTER_CPU = 1
MASTER_MEM = 2048

NODE_NUM = 2
NODE_CPU = 2
NODE_MEM = 2048

IP_BASE = "192.168.56."


Vagrant.configure("2") do |config|
    config.vm.define "k3sMaster" do |master|
        master.vm.box = "hashicorp/bionic64"
        master.vm.network "private_network", ip: "192.168.56.11"
        master.vm.hostname = "k3sMaster"
        master.vm.provider "virtualbox" do |v|
            v.memory = MASTER_MEM
            v.cpus = MASTER_CPU
        end
    end

    (1..NODE_NUM).each do |j|
        config.vm.define "k3sNode#{j}" do |node|
            node.vm.box = "hashicorp/bionic64"
            node.vm.network "private_network", ip: "#{IP_BASE}#{j + 10 + MASTER_NUM}"
            node.vm.hostname = "k3sNode#{j}"
            node.vm.provider "virtualbox" do |v|
                v.memory = NODE_MEM
                v.cpus = NODE_CPU
            end
        end
    end
end
