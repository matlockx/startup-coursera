startup-coursera
================
Vagrant setup to start an aws instance or a local virtual box instance with installed git, nodejs, python and heroku toolbelt.
Can be used for coursera course 'startup': https://class.coursera.org/startup-001/class/index

#Setup

Create a file with your aws credentials somewhere save on your HD with following content:

	module Aws
		class Config
	  		attr_accessor :access_key   
	  		attr_accessor :secret_key 
	 	 	def initialize()
	    		@access_key = "access_key"  
	  			@secret_key = "z+secret_key"
	  		end
		end
	end

Change first line in vagrant file to point to the aws credential file. Mine is located in ~/.matlockx/aws.rb so first line looks:
	
	require File.expand_path(File.join('~', '.matlockx', 'aws'))

Next you need to change the path to your aws pem file. Mine is located in ~/.ssh:

	override.ssh.private_key_path = "~/.ssh/matlockx-aws.pem" 

#AWS
cd aws
vagrant up --provider=aws web

#Virtualbox
vagrant up local
