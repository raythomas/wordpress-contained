Welcome to WordPress-Contained!
=============================


The main goal of WordPress-Contained is to get a WordPress blog up and running as quickly as possible. The tool we use to Orchestrate this process is Ansible and the tool we use to "Contain" our blog is Docker.

----------


Prerequisites
------------------

To execute Ansible Playbook it will be **assumed** that you have the following tasks completed:

> **Task to be completed before hand:**

> - A minimal [installation of CentOS 7/ RHEL 7][1] setup and ready to go.
> - A [user account][2] with sudo access and SSH keys configured.
> - Ansible 2.0 or greater installed on Ansible host. I personally prefer [CentOS][3] for the Asible host, but any popular [Linux distros][4] should do.


### Step 1 -- Configure your local playbook
1.) Make sure to put all servers that you want push changes to into the "hosts" file within the playbook. Specify the under the "[RHEL7]" group. I named mine "unicorn"
>- [RHEL7]
>unicorn.mysite.internal

2.)  Within the "group_var/all.yml" file change passwords for the following
> - mysql_root_password
> - wordpress_mysql_root_password

### Step 2 -- Run your Ansible Playbook
1.) cd into the WordPress playbook (there should be a site.yml file present): 
2.) Execute the playbook with a user account that has SUDO access.
>- type: cd wordpress-contained
>- type: ansible-playbook site.yml -u  -K -l RHEL7

### Step 3 -- Verify that you can log into your WordPress and PHPMyAdmin sites.

>- 1.) For WordPress point browser to:
>http://unicorn.mysite.internal:8080

>- 2.) For PHPMyAdmin point browser to:
>http://unicorn.mysite.internal:8181



#Authors
---
This was created by Ray Thomas (ray.thomas@gmail.com).



  [1]: http://www.tecmint.com/centos-7-installation/
  [2]: https://www.digitalocean.com/community/tutorials/initial-server-setup-with-centos-7
  [3]: https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-ansible-on-centos-7
  [4]: http://docs.ansible.com/ansible/intro_installation.html#installing-the-control-machine
