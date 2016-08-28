## Prerequisites:

Ansible
Boto

Separately following environment variables should be set:
AWS_SECRET_ACCESS_KEY=
AWS_ACCESS_KEY_ID=
EC2_INI_PATH=/etc/ansible/ec2.ini
ANSIBLE_HOSTS=/etc/ansible/ec2.py

## Configuration: 

All configuration is done through group-vars/all file:

```python

# repos
#ambari_repo : http://public-repo-1.hortonworks.com/ambari/centos6/2.x/updates/2.1.0
#hdp_repo : http://public-repo-1.hortonworks.com/HDP/centos6/2.x/updates/2.2.6.0
#hdp_util_repo : http://public-repo-1.hortonworks.com/HDP-UTILS-1.1.0.20/repos/centos6

ambari_repo : http://public-repo-1.hortonworks.com/ambari/centos7/2.x/updates/2.2.2.0
hdp_repo : http://public-repo-1.hortonworks.com/HDP/centos7/2.x/updates/2.4.2.0
hdp_util_repo : http://public-repo-1.hortonworks.com/HDP-UTILS-1.1.0.20/repos/centos7

# Stack info
hdp_stack: 2.4
hdp_utils: 1.1.0.20

os: centos7

cluster_name : hdfs-ha

blueprint : ha.json.j2

instance_type : m4.large

remote_user : centos

image : ami-d2c924b2

region : us-west-2

keypair : ansible2

security_group : CentOS 7 -x86_64- - with Updates HVM-1602-AutogenByAWSMP-

```