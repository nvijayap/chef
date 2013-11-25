chef - Quick Start
==================

Install Vagrant from http://www.vagrantup.com/

Pick up chef-repo from https://github.com/opscode/chef-repo

&gt; mkdir mychefrepo ; cd mychefrepo

&gt; git clone https://github.com/opscode/chef-repo.git

Create Vagrantfile -

&gt; vagrant init

Add Vagrant Box -

&gt; vagrant box add precise64 http://files.vagrantup.com/precise64.box

Add this chef recipe (mysql) to Vagrantfile -

<pre>
  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = "cookbooks"
    chef.roles_path = "roles"
    chef.data_bags_path = "data_bags"
    chef.add_recipe "mysql"
    chef.json = { :mysql_password => "foo321bar" }
  end
</pre>

Bring up the VM -

&gt; vagrant up

Login into the VM -

&gt; vagrant ssh

Start using the VM

NOTE:
chef_solo is shown above for demo purpose.
You will most likely be using Chef client/server in your setup.
For more elaborate details, look into https://learnchef.opscode.com/

