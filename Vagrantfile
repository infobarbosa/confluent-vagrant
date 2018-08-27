# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  #configuracao da instancia 1 do zookeeper
  config.vm.define "zookeeper1" do |zookeeper1|
    zookeeper1.vm.box = "ubuntu/xenial64"

    zookeeper1.vm.network "private_network", ip: "192.168.56.71"
    zookeeper1.vm.hostname = "zookeeper1"
    zookeeper1.vm.provider "virtualbox" do |v|
      v.memory = 1024
      v.cpus = 1
      v.name = "zk1"
    end

    zookeeper1.vm.provision "file", source: "zookeeper.service", destination: "zookeeper.service"
    zookeeper1.vm.provision "file", source: "hosts", destination: "hosts"
    zookeeper1.vm.provision "shell", inline: <<-SHELL
      sudo add-apt-repository ppa:openjdk-r/ppa
      sudo apt-get -y update && sudo apt-get install -y openjdk-8-jdk
      wget -qO - https://packages.confluent.io/deb/5.0/archive.key | apt-key add -
      sudo add-apt-repository "deb [arch=amd64] https://packages.confluent.io/deb/5.0 stable main"
      sudo apt-get -y update && sudo apt-get install -y confluent-platform-2.11

      sudo ufw allow 2181/tcp

      sudo cat hosts >> /etc/hosts

      sudo cp zookeeper.service /etc/systemd/system/zookeeper.service
      chown root:root /etc/systemd/system/zookeeper.service
      sudo systemctl enable zookeeper
      sudo systemctl start zookeeper

    SHELL
  end

  #configuracao da instancia 1 do kafka
  config.vm.define "kafka1" do |kafka1|
    kafka1.vm.box = "ubuntu/xenial64"

    kafka1.vm.network "private_network", ip: "192.168.56.81"
    kafka1.vm.hostname = "kafka1"
    kafka1.vm.provider "virtualbox" do |v|
      v.memory = 1536
      v.cpus = 1
      v.name = "k1"
    end

    kafka1.vm.provision "file", source: "kafka.service", destination: "kafka.service"
    kafka1.vm.provision "file", source: "server1.properties", destination: "server.properties"
    kafka1.vm.provision "file", source: "hosts", destination: "hosts"
    kafka1.vm.provision "shell", inline: <<-SHELL
      sudo add-apt-repository ppa:openjdk-r/ppa
      sudo apt-get -y update && sudo apt-get install -y openjdk-8-jdk
      wget -qO - https://packages.confluent.io/deb/5.0/archive.key | apt-key add -
      sudo add-apt-repository "deb [arch=amd64] https://packages.confluent.io/deb/5.0 stable main"
      sudo apt-get -y update && sudo apt-get install -y confluent-platform-2.11

      sudo ufw allow 9092/tcp
      sudo ufw allow 9999/tcp

      sudo cat hosts >> /etc/hosts
      sudo mv server.properties /etc/kafka/server.properties

      sudo cp kafka.service /etc/systemd/system/kafka.service
      sudo chown root:root /etc/systemd/system/kafka.service
      sudo systemctl enable kafka
      sudo systemctl start kafka
    SHELL
  end

  #configuracao da instancia 2 do kafka
  config.vm.define "kafka2" do |kafka2|
    kafka2.vm.box = "ubuntu/xenial64"

    kafka2.vm.network "private_network", ip: "192.168.56.82"
    kafka2.vm.hostname = "kafka2"
    kafka2.vm.provider "virtualbox" do |v|
      v.memory = 1536
      v.cpus = 1
      v.name = "k2"
    end

    kafka2.vm.provision "file", source: "kafka.service", destination: "kafka.service"
    kafka2.vm.provision "file", source: "server2.properties", destination: "server.properties"
    kafka2.vm.provision "file", source: "hosts", destination: "hosts"
    kafka2.vm.provision "shell", inline: <<-SHELL
      sudo add-apt-repository ppa:openjdk-r/ppa
      sudo apt-get -y update && sudo apt-get install -y openjdk-8-jdk
      wget -qO - https://packages.confluent.io/deb/5.0/archive.key | apt-key add -
      sudo add-apt-repository "deb [arch=amd64] https://packages.confluent.io/deb/5.0 stable main"
      sudo apt-get -y update && sudo apt-get install -y confluent-platform-2.11

      sudo ufw allow 9092/tcp
      sudo ufw allow 9999/tcp

      sudo cat hosts >> /etc/hosts
      sudo mv server.properties /etc/kafka/server.properties

      sudo cp kafka.service /etc/systemd/system/kafka.service
      sudo chown root:root /etc/systemd/system/kafka.service
      sudo systemctl enable kafka
      sudo systemctl start kafka
    SHELL
  end

  #configuracao da instancia 3 do kafka
  config.vm.define "kafka3" do |kafka3|
    kafka3.vm.box = "ubuntu/xenial64"

    kafka3.vm.network "private_network", ip: "192.168.56.83"
    kafka3.vm.hostname = "kafka3"
    kafka3.vm.provider "virtualbox" do |v|
      v.memory = 1536
      v.cpus = 1
      v.name = "k3"
    end

    kafka3.vm.provision "file", source: "kafka.service", destination: "kafka.service"
    kafka3.vm.provision "file", source: "server3.properties", destination: "server.properties"
    kafka3.vm.provision "file", source: "hosts", destination: "hosts"
    kafka3.vm.provision "shell", inline: <<-SHELL
      sudo add-apt-repository ppa:openjdk-r/ppa
      sudo apt-get -y update && sudo apt-get install -y openjdk-8-jdk
      wget -qO - https://packages.confluent.io/deb/5.0/archive.key | apt-key add -
      sudo add-apt-repository "deb [arch=amd64] https://packages.confluent.io/deb/5.0 stable main"
      sudo apt-get -y update && sudo apt-get install -y confluent-platform-2.11

      sudo ufw allow 9092/tcp
      sudo ufw allow 9999/tcp

      sudo cat hosts >> /etc/hosts
      sudo mv server.properties /etc/kafka/server.properties

      sudo cp kafka.service /etc/systemd/system/kafka.service
      sudo chown root:root /etc/systemd/system/kafka.service
      sudo systemctl enable kafka
      sudo systemctl start kafka
    SHELL
  end

  #####KSQL#####
  #configuracao da instancia do control center
  config.vm.define "ksql1" do |ksql1|
    ksql1.vm.box = "ubuntu/xenial64"

    ksql1.vm.network "private_network", ip: "192.168.56.87"
    ksql1.vm.hostname = "ksql1"
    ksql1.vm.provider "virtualbox" do |v|
      v.memory = 2048
      v.cpus = 1
      v.name = "ksql1"
    end

    ksql1.vm.provision "file", source: "ksql.service", destination: "ksql.service"
    ksql1.vm.provision "file", source: "ksql-server.properties", destination: "ksql-server.properties"
    ksql1.vm.provision "file", source: "hosts", destination: "hosts"
    ksql1.vm.provision "shell", inline: <<-SHELL
      sudo add-apt-repository ppa:openjdk-r/ppa
      sudo apt-get -y update && sudo apt-get install -y openjdk-8-jdk
      wget -qO - https://packages.confluent.io/deb/5.0/archive.key | apt-key add -
      sudo add-apt-repository "deb [arch=amd64] https://packages.confluent.io/deb/5.0 stable main"
      sudo apt-get -y update && sudo apt-get install -y confluent-platform-2.11

      sudo ufw allow 8088/tcp
      sudo mkdir -p /usr/logs/ksql-cli
      #isso aqui provavelmente voce nao vai querer fazer em producao
      sudo chmod 777 /usr/logs/ksql-cli

      sudo cat hosts >> /etc/hosts
      sudo mv ksql-server.properties /etc/ksql/ksql-server.properties

      sudo cp ksql.service /etc/systemd/system/ksql.service
      sudo chown root:root /etc/systemd/system/ksql.service
      sudo systemctl enable ksql
      sudo systemctl start ksql
    SHELL
  end

  #configuracao da instancia do control center
  config.vm.define "confluenttools" do |confluenttools|
    confluenttools.vm.box = "ubuntu/xenial64"

    confluenttools.vm.network "private_network", ip: "192.168.56.84"
    confluenttools.vm.hostname = "confluent-tools"
    confluenttools.vm.provider "virtualbox" do |v|
      v.memory = 2048
      v.cpus = 1
      v.name = "confluent-kafka-tools"
    end

    confluenttools.vm.provision "file", source: "control-center.service", destination: "control-center.service"
    confluenttools.vm.provision "file", source: "control-center.properties", destination: "control-center.properties"
    confluenttools.vm.provision "file", source: "hosts", destination: "hosts"
    confluenttools.vm.provision "shell", inline: <<-SHELL
      sudo add-apt-repository ppa:openjdk-r/ppa
      sudo apt-get -y update && sudo apt-get install -y openjdk-8-jdk
      wget -qO - https://packages.confluent.io/deb/5.0/archive.key | apt-key add -
      sudo add-apt-repository "deb [arch=amd64] https://packages.confluent.io/deb/5.0 stable main"
      sudo apt-get -y update && sudo apt-get install -y confluent-platform-2.11

      sudo ufw allow 9021/tcp

      sudo cat hosts >> /etc/hosts
      sudo mv control-center.properties /etc/confluent-control-center/control-center.properties

      sudo cp control-center.service /etc/systemd/system/control-center.service
      sudo chown root:root /etc/systemd/system/control-center.service
      sudo systemctl enable control-center
      sudo systemctl start control-center
    SHELL
  end
end
