# Oficina — Infraestrutura de Banco de Dados

Infraestrutura Terraform do banco de dados gerenciado do sistema da oficina.

## Responsabilidades planejadas

- Amazon RDS PostgreSQL;
- DB subnet groups e parameter groups;
- security groups específicos do banco;
- backups, criptografia e proteção contra exclusão;
- gestão ou referência segura às credenciais;
- documentação da modelagem, consistência e performance;
- ambientes isolados de homologação e produção.

## Ambientes e branches

| Branch | Ambiente | Diretório Terraform |
|---|---|---|
| `staging` | Homologação | `terraform/environments/staging` |
| `main` | Produção | `terraform/environments/production` |

Cada ambiente deverá possuir instância e Terraform state independentes. A branch
`main` não deverá receber commits diretos; a promoção ocorrerá por Pull Request.

## Dependências planejadas

Este repositório consumirá identificadores de VPC e subnets publicados pelo
repositório `oficina-infra-kubernetes`, sem assumir a propriedade desses recursos.

## Limites deste repositório

Não pertencem a este repositório:

- migrations Alembic, que acompanharão a aplicação;
- código da API;
- cluster Kubernetes, Kong ou observabilidade;
- código da função serverless de autenticação.

## Estrutura inicial

```text
.
├── .github/workflows/
├── docs/
└── terraform/
    ├── environments/
    │   ├── staging/
    │   └── production/
    └── modules/
        └── postgres/
```

## Status

Estrutura inicial. Terraform, CI/CD e recursos cloud ainda não foram implementados.
