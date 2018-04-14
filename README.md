# ansible-aws-kubernetes

### First to provision Kubernetes on AWS

1. Create CentOS VM with vagrant
2. yum update
3. sudo yum install epel-release
4. sudo yum install ansible git
5. Run ansible playbook to setup localhost
6. Switch to aws_user (defined in group_vars)
7. git clone https://github.com/jfeddern/ansible-aws-kubernetes.git
8. aws configure
9. Run site.yml
12. Get admin password with ´kops get secrets kube --type secret -oplaintext´
13. Get Token of admin-user ´kubectl -n kube-system describe secret $(kubectl -n kube-system get secret | grep admin-user | awk '{print $1}')´
14. Login to api ´api.devopscluster.de/ui´

### Deploy Hello World Application

Run ´ansible-playbook playbooks/deploy_app.yml --ask-vault-pass´

### Update OS

Run ´ansible-playbook -i inventory/development/hosts.ini playbooks/update_vm.yml´