# Learn Terraform - Provision an EKS Cluster

This repo is a companion repo to the [Provision an EKS Cluster tutorial](https://developer.hashicorp.com/terraform/tutorials/kubernetes/eks), containing
Terraform configuration files to provision an EKS cluster on AWS.

aws iam attach-role-policy \
--role-name node-group-1-eks-node-group-20240601183535049400000002 \
--policy-arn arn:aws:iam::aws:policy/CloudWatchAgentServerPolicy

aws iam attach-role-policy \
--role-name node-group-2-eks-node-group-20240601183535049200000001 \
--policy-arn arn:aws:iam::aws:policy/CloudWatchAgentServerPolicy


terraform apply

aws eks --region $(terraform output -raw region) update-kubeconfig \
    --name $(terraform output -raw cluster_name)

kubectl cluster-info

kubectl get nodes

terraform destroy