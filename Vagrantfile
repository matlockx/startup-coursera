require File.expand_path(File.join('~', '.matlockx', 'aws'))
aws_config = Aws::Config.new
Vagrant.configure("2") do |config|
  config.vm.define :web do |web_config|
        web_config.vm.box = "dummy"
        web_config.vm.box_url = "https://github.com/mitchellh/vagrant-aws/raw/master/dummy.box"

        web_config.vm.provider :aws do |aws,override|
          aws.access_key_id = aws_config.access_key
          aws.secret_access_key = aws_config.secret_key
          aws.keypair_name = "matlockx"
          override.ssh.username = "ubuntu"
          override.ssh.private_key_path = "~/.ssh/matlockx-aws.pem"

          aws.ami = "ami-640a0610"
          aws.region = "eu-west-1"
          aws.instance_type = "t1.micro"
        end
    end

    config.vm.define :local do |local_config|
        local_config.vm.box = "ubuntu_12_04_64"
        local_config.vm.box_url="http://puppet-vagrant-boxes.puppetlabs.com/ubuntu-server-12042-x64-vbox4210.box"

        local_config.vm.provider :virtualbox  do |vb|

        end     
    end
  config.vm.provision :shell, :path => "setup.sh"
end