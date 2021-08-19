# ansible-eks-quickstart
Ansible Role to Deploy EKS Quickstarts

### Python libraries

Install requirements

```bash
pip install --user -r requirements.txt
```

### Export AWS Credentials

1. Clone this repository

2. Make your [AWS account credentials](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) (`AWS_ACCESS_KEY` and `AWS_SECRET_KEY`) available as environment variables (`export`).

```bash
export AWS_ACCESS_KEY='...'
export AWS_SECRET_KEY='...'
```

3 Use the sample create file to create or delete your eks-cluster:
  
  ansible-playbook /root/ansible-eks-quickstart/sample-cf-create.yaml

Notes:

- Add your cluster name and region to the CLUSTER_INFO VARIABLE in sample-cf-create.yaml
- Cloudformation template expects a main cluster for every region as that's what the VPC is tied to and other eks clusters are installed in the same vpc
- By default MAIN_CLUSTER_NAME is eks-cluster-1 you can change it by setting the MAIN_CLUSTER_NAME via the --extra-args option and also set CLUSTER_INFO

e.g
ansible-playbook /root/ansible-eks-quickstart/sample-cf-create.yaml -e MAIN_CLUSTER_NAME=eks-cluster

- To delete a cluster remove it from the CLUSTER_INFO variable
- To delete all clusters set CLUSTER_INFO variable to empty --extra-args CLUSTER_INFO={}
