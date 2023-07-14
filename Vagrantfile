Vagrant.configure("2") do |config|
  (1..1).each do |i|
    config.vm.define "master-#{i}" do |k8s|
      k8s.vm.box = "ubuntu/bionic64"  # Define a box a ser usada para criar a máquina virtual (ubuntu/bionic64).
      k8s.vm.hostname = "master-#{i}"  # Define o nome do hostname da máquina virtual ("master-1").

      k8s.vm.network "private_network", ip: "172.89.0.1#{i}"  # Configura uma rede privada e atribui um endereço IP para a máquina virtual.

      k8s.ssh.insert_key = false  # Desabilita a inserção da chave SSH.
      k8s.ssh.private_key_path = ['~/.vagrant.d/insecure_private_key', '~/.ssh/id_rsa']  # Define o caminho para a chave SSH privada a ser usada.
      k8s.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/authorized_keys"  # Provisão do arquivo de chave pública SSH.

      k8s.vm.provider "virtualbox" do |vb|  # Configura o provedor de virtualização (VirtualBox).
        vb.gui = false  # Define se a interface gráfica do VirtualBox será exibida (false).
        vb.cpus = 2  # Define o número de CPUs atribuídas à máquina virtual (2).
        vb.memory = "2048"  # Define a quantidade de memória RAM atribuída à máquina virtual (2048 MB).
      end
    end
  end

  (1..2).each do |i|
    config.vm.define "worker-#{i}" do |k8s|
      k8s.vm.box = "ubuntu/bionic64"  # Define a box a ser usada para criar a máquina virtual (ubuntu/bionic64).
      k8s.vm.hostname = "worker-#{i}"  # Define o nome do hostname da máquina virtual ("worker-1" ou "worker-2").

      k8s.vm.network "private_network", ip: "172.89.0.2#{i}"  # Configura uma rede privada e atribui um endereço IP para a máquina virtual.

      k8s.ssh.insert_key = false  # Desabilita a inserção da chave SSH.
      k8s.ssh.private_key_path = ['~/.vagrant.d/insecure_private_key', '~/.ssh/id_rsa']  # Define o caminho para a chave SSH privada a ser usada.
      k8s.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/authorized_keys"  # Provisão do arquivo de chave pública SSH.

      k8s.vm.provider "virtualbox" do |vb|  # Configura o provedor de virtualização (VirtualBox).
        vb.gui = false  # Define se a interface gráfica do VirtualBox será exibida (false).
        vb.cpus = 1  # Define o número de CPUs atribuídas à máquina virtual (1).
        vb.memory = "2048"  # Define a quantidade de memória RAM atribuída à máquina virtual (2048 MB).
      end
    end
  end
end
