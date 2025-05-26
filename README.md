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


### Variáveis importantes

| Nome                       | Descrição                                              |
|---------------------------|--------------------------------------------------------|
| `cluster_name`            | Nome do seu cluster EKS                                |
| `cluster_version`         | Versão Kubernetes (ex: `1.29`)                         |
| `vpc_id` / `subnet_ids`   | VPC e sub-redes onde o cluster será criado            |
| `eks_managed_node_groups` | Mapa para definir node groups gerenciados             |
| `cluster_addons`          | Permite instalar addons do EKS, ativados com `most_recent = true` |



## 🧪 Testes e Validação

Após aplicar (`terraform apply`), configure seu `kubectl`:

```bash
aws eks --region $(terraform output -raw aws_region) \
  update-kubeconfig --name $(terraform output -raw cluster_name)

kubectl get nodes
```