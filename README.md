# Ansible Playbooks

I'm teaching myself Ansible using the free tier of AWS. I'll be keeping my playbooks here.

Before I could begin, I had to configure an Ansible server running in my AWS VPC. I started with a RHEL 7 instance because I was already familiar with Red Hat. I also wanted to use the dynamic inventory I saw described in an AWS blog post. There was a sequence of prerequisites I needed to satisfy.

1. Download EPEL RPM from [EPEL wiki](https://fedoraproject.org/wiki/EPEL#How_can_I_use_these_extra_packages.3F)
1. Install Boto from EPEL
1. Install pip from EPEL
1. Install AWS CLI using pip
1. Create IAM role with read-only access
1. Launch an instance with the new IAM role
1. Download EC2 scripts from [Ansible GitHub repo](https://github.com/ansible/ansible)
1. Configure command line environment according to instructions in blog post (and export `ANSIBLE_HOSTS` in `~/.bash_profile`)
1. Edit `ec2.ini` to make AWS CLI use private DNS names and IPs

The time I spent configuring these prerequisites turned out to be worthwhile. A dynamic inventory allows me to refer to groups of AWS instances by their tags. I can also automatically apply my playbooks to new instances launched since the last time I ran Ansible.

**References**

* [Dynamic Inventory - Ansible Documentation](http://docs.ansible.com/ansible/intro_dynamic_inventory.html#example-aws-ec2-external-inventory-script)
* [Getting Started with Ansible and Amazon EC2 Dynamic Inventory Management](https://aws.amazon.com/blogs/apn/getting-started-with-ansible-and-dynamic-amazon-ec2-inventory-management/)
