Vagrant.configure("2") do |config|
    config.vm.box = "generic/ubuntu2004"
    
    # forward ssh port
    config.vm.network "forwarded_port", guest: 22, host: 22

    # forward grafana port
    config.vm.network "forwarded_port", guest: 3000, host: 3000

    # forward prometheus port
    config.vm.network "forwarded_port", guest: 9090, host: 9090  


    # Installing Node-Exporter on current VM using Ansible.
    config.vm.provision "ansible" do |ansible|
        ansible.playbook = "./ansible/install_node_exporter.yml"
    end  

    # Installing Docker using Ansible.
    config.vm.provision "ansible" do |ansible|
        ansible.playbook = "./ansible/install_docker.yml"
    end
    
    # Installing Prometheus and Grafana using Ansible.
    config.vm.provision "ansible" do |ansible|
        ansible.playbook = "./ansible/install_prometheus_grafana.yml"     
    end

end

