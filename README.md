# Escopo e objetivo

_Executar "Hello World" através de uma página html hospedada em um kubernet por meio de um deploy no Azure Devops _.


## Iniciando...

- `git clone https://github.com/kyriosdata/exemplo`
- `cd exemplo`

Agora você poderá executar os vários comandos abaixo.

## Pré-requisitos

- Conta AWS
- Cluster do Amazon EKS com função de instância de nó para extrair conteúdo do ECR
- Conta de usuário do IAM com acesso ao cluster do Amazon EKS
- Conta do Azure DevOps
- AWS Toolkit for Azure DevOps instalado no Azure DevOps ou em um servidor Azure DevOps local
- Aplicativo a ser implantado (webapp fornecido no repositório)

## Etapas de execução 

- Modelo principal - main_template.yaml
  Inicializar variavies e validar recursos AWS

- Modelo de trabalho de CI - ci_template.yaml
  Criar img docker
  Push img docker
  Build do helm chart
  push do helm chart

- Modelo de trabalho de CD - cd_template.yaml
  Após conlusão das etapas anteriores estando ok iniciará a implantação do helm chart e a saída geral da implantação

Essa é a estrutura geral do código e execução da implantação:
```
pipeline_templates/
├─ jobs_templates/
│  ├─ ci_template.yaml
│  ├─ cd_template.yaml
├─ main_template.yaml
```

## Limitações

- É necessário um self-host Azure para execução da pipeline, o mesmo pode ser solicitado em 
