# terraform-eks-aws

Módulo Terraform para criar e gerenciar um cluster **Amazon EKS** na AWS com node groups gerenciados e configuração flexível.

## 🌟 Visão Geral

Este projeto do Terraform automatiza a criação de um cluster EKS completo:

- Cluster Kubernetes (control plane + networking)
- Node groups (EC2 Managed Node Groups)
- Configuração de IAM, VPC, sub-redes e Security Groups
- Integração com addons como `aws-ebs-csi-driver`, `coredns`, `vpc-cni`, entre outros

---

## 📋 Pré-requisitos

Antes de usar o módulo, você precisará:

- [Terraform ≥ 1.0](https://www.terraform.io/)
- Provider AWS (ex. `aws ≧ 5.0`)
- AWS CLI configurada (credenciais + região)
- Kubectl para testar o acesso ao cluster


