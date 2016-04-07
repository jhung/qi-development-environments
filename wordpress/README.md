# Wordpress development environment

Configure ``provisioning/vars.yml`` with the following variables:

  * project_name - Short-name identifier for the project (default: wordpress)
  * project_directory - Where this directory will be mounted within the virtual machine (default: /home/vagrant/sync)

The Wordpress installation will be in directory $project_directory/$project_name (e.g. /home/vagrant/sync/wordpress)

If you do not want Wordpress to be automatically downloaded and extracted, set the following variable to 'no':

  * wordpress_install - Defines whether Wordpress should be downloaded and extracted automatically (default: yes)

## Start new VM

    vagrant up

You can then access Wordpress at [http://localhost:10080](http://localhost:10080) and follow the configuration wizard.

## Reprovision Wordpress

If you want to start from scratch you can destroy the VM and start it again:

    vagrant destroy
    vagrant up

Optionally, you can just delete the $project_name directory local to this repository (e.g. wordpress) and provision the VM:

    rm -rf project_name
    vagrant provision

This will download and extract Wordpress again.

## Sample output

$ vagrant up
Bringing machine 'default' up with 'virtualbox' provider...
==> default: Importing base box 'inclusivedesign/centos7'...
==> default: Matching MAC address for NAT networking...
==> default: Checking if box 'inclusivedesign/centos7' is up to date...
==> default: Setting the name of the VM: wordpress_default_1460051959970_61039
==> default: Clearing any previously set network interfaces...
==> default: Preparing network interfaces based on configuration...
    default: Adapter 1: nat
==> default: Forwarding ports...
    default: 80 (guest) => 10080 (host) (adapter 1)
    default: 3306 (guest) => 13306 (host) (adapter 1)
    default: 19531 (guest) => 19531 (host) (adapter 1)
    default: 22 (guest) => 2222 (host) (adapter 1)
==> default: Running 'pre-boot' VM customizations...
==> default: Booting VM...
==> default: Waiting for machine to boot. This may take a few minutes...
    default: SSH address: 127.0.0.1:2222
    default: SSH username: vagrant
    default: SSH auth method: private key
    default: Warning: Connection timeout. Retrying...
    default: Warning: Remote connection disconnect. Retrying...
    default: 
    default: Vagrant insecure key detected. Vagrant will automatically replace
    default: this with a newly generated keypair for better security.
    default: 
    default: Inserting generated public key within guest...
    default: Removing insecure key from the guest if it's present...
    default: Key inserted! Disconnecting and reconnecting using new SSH key...
==> default: Machine booted and ready!
==> default: Checking for guest additions in VM...
==> default: Setting hostname...
==> default: Mounting shared folders...
    default: /home/vagrant/sync => /home/user/qi-development-environments/wordpress
==> default: Running provisioner: shell...
    default: Running: inline script
==> default: 
==> default: PLAY [Deploy Wordpress server on CentOS 7] ************************************ 
==> default: 
==> default: GATHERING FACTS *************************************************************** 
==> default: ok: [localhost]
==> default: 
==> default: TASK: [Fix vagrant home dir] ************************************************** 
==> default: changed: [localhost]
==> default: 
==> default: TASK: [Create Wordpress installation directories] ***************************** 
==> default: changed: [localhost] => (item=/home/vagrant/sync/wordpress)
==> default: changed: [localhost] => (item=/home/vagrant/sync/wordpress/tmp)
==> default: 
==> default: TASK: [Copy .gitignore (in case version control is used; optional)] *********** 
==> default: changed: [localhost]
==> default: 
==> default: TASK: [Install packages] ****************************************************** 
==> default: changed: [localhost] => (item=nginx,php-fpm,php-gd,php-mysql,php-pgsql,php-mbstring,mariadb,mariadb-server,MySQL-python)
==> default: 
==> default: TASK: [Configure PHP] ********************************************************* 
==> default: changed: [localhost]
==> default: 
==> default: TASK: [Configure php-fpm] ***************************************************** 
==> default: changed: [localhost]
==> default: 
==> default: TASK: [Configure nginx] ******************************************************* 
==> default: changed: [localhost]
==> default: 
==> default: TASK: [Enable and restart services] ******************************************* 
==> default: changed: [localhost] => (item=mariadb)
==> default: changed: [localhost] => (item=php-fpm)
==> default: changed: [localhost] => (item=nginx)
==> default: 
==> default: TASK: [Create database] ******************************************************* 
==> default: changed: [localhost]
==> default: 
==> default: TASK: [Create database user] ************************************************** 
==> default: changed: [localhost]
==> default: 
==> default: TASK: [Download Wordpress] **************************************************** 
==> default: changed: [localhost]
==> default: 
==> default: TASK: [Extract Wordpress] ***************************************************** 
==> default: changed: [localhost]
==> default: 
==> default: PLAY RECAP ******************************************************************** 
==> default: localhost                  : ok=13   changed=12   unreachable=0    failed=0   
==> default: Running provisioner: shell...
    default: Running: inline script

