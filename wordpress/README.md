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
