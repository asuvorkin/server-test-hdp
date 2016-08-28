## Prerequisites:

Ansible.
Boto.

Separately following environment variables should be set:
```python
AWS_SECRET_ACCESS_KEY=
AWS_ACCESS_KEY_ID=
EC2_INI_PATH=/etc/ansible/ec2.ini
ANSIBLE_HOSTS=/etc/ansible/ec2.py
```

AWS access .pem file should be placed in ~/.ssh folder with "chmod 400" rights.

AWS security group should be set up to allow all internal traffic wihtin the group

## Configuration: 

All configuration is done through group-vars/all file:

```python

# repos

ambari_repo : http://public-repo-1.hortonworks.com/ambari/centos7/2.x/updates/2.2.2.0
hdp_repo : http://public-repo-1.hortonworks.com/HDP/centos7/2.x/updates/2.4.2.0
hdp_util_repo : http://public-repo-1.hortonworks.com/HDP-UTILS-1.1.0.20/repos/centos7

# Stack info
hdp_stack: 2.4
hdp_utils: 1.1.0.20

os: centos7

cluster_name : hdfs-ha

# Name of blueprint file in blueprints folder
blueprint : ha.json.j2

#AWS instance type
instance_type : m4.large

#user to ssh to AWS instances
remote_user : centos

#AWS instance image - Centos 7 
image : ami-d2c924b2

region : us-west-2

#Naem of keypair .pem file in ~/.ssh folder
keypair : ansible2

#AWS security group 
security_group : CentOS 7 -x86_64- - with Updates HVM-1602-AutogenByAWSMP-

```

# Important Note: 
Currently playbook finishes at copying blueprint, host-mapping and shell script file to Master Node - m1, which is Ambari Server as well. 
In order to start cluster deployment it's neccessary to ssh to m1 and run register_launch.sh from /tmp folder.
Alternatively for fully automatic deployment uncomment last steps in roles/cluster-reg/tasks/main.yml
