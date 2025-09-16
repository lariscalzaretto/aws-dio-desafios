## Desafio 01
# Explorando Workflows Automatizados com AWS Step Functions

Este repositório é mais do que um simples projeto; é a minha jornada de aprendizado e descoberta no mundo da orquestração de processos na nuvem. Ele foi criado como parte do desafio proposto pela **DIO (Digital Innovation One)**, com o objetivo de ir além da teoria e realmente colocar a mão na massa, consolidando os conhecimentos em AWS Step Functions.

Aqui, você vai encontrar não apenas os conceitos, mas também as anotações, os insights, os pequenos triunfos e até as dificuldades que enfrentei enquanto aprendia a criar workflows automatizados e resilientes na AWS.

---

## 📌 O que aprendi

### O que são Step Functions
AWS Step Functions são responsáveis por **orquestrar serviços da AWS** em forma de **State Machines** (máquinas de estado). Em vez de um código monolítico que controla tudo, você descreve o fluxo em etapas (estados), cada qual com sua função.

### Principais benefícios
- **Organização visual** do processo.  
- **Escalabilidade automática** sem necessidade de gerenciar servidores.  
- **Resiliência a falhas**, com possibilidade de reprocessar etapas.  
- **Flexibilidade**, integrando serviços como Lambda, DynamoDB, S3, API Gateway.  

### Estrutura dos workflows
Os workflows são descritos em **Amazon States Language (JSON)**. Principais tipos de estados:
- **Task** → executa uma ação (geralmente uma função Lambda).  
- **Choice** → permite criar ramificações condicionais.  
- **Parallel** → executa múltiplos caminhos em paralelo.  
- **Wait** → pausa a execução por tempo definido.  
- **Succeed / Fail** → finalizam o fluxo.  

### Experiência prática
Durante a prática, entendi como:
1. Criar e configurar uma **State Machine** no console da AWS.  
2. Definir estados em JSON para executar Lambdas em sequência.  
3. Validar entradas e simular caminhos diferentes com o `Choice`.  
4. Acompanhar a execução visualmente no painel do Step Functions.  

Exemplo simplificado de workflow:

```json
{
  "Comment": "Fluxo de exemplo com Lambda",
  "StartAt": "ValidarEntrada",
  "States": {
    "ValidarEntrada": {
      "Type": "Task",
      "Resource": "arn:aws:lambda:REGION:ACCOUNT_ID:function:validarEntrada",
      "Next": "ProcessarDados"
    },
    "ProcessarDados": {
      "Type": "Task",
      "Resource": "arn:aws:lambda:REGION:ACCOUNT_ID:function:processarDados",
      "End": true
    }
  }
}

```
## Desafio 02
# Implementando minha Primeira Stack com AWS CloudFormation

Repositório criado como parte do desafio da DIO para consolidar conhecimentos em **AWS CloudFormation**.  
O objetivo é registrar práticas e aprendizados ao criar e gerenciar Stacks automatizadas.

---

## 📌 O que aprendi

### O que é o CloudFormation
AWS CloudFormation é um serviço que permite **provisionar e gerenciar recursos de forma automática** usando templates em YAML ou JSON.  
Com ele, conseguimos descrever toda a infraestrutura como código (**IaC – Infrastructure as Code**).

### Benefícios principais
- Padronização e repetibilidade no provisionamento.  
- Facilidade para versionar infraestrutura no GitHub.  
- Automação completa, evitando criação manual de recursos.  
- Possibilidade de atualizar e excluir Stacks de forma controlada.  

### Estrutura de um Template
Um arquivo YAML/JSON de CloudFormation é dividido em seções, como:
- **Parameters** → entradas que tornam o template reutilizável.  
- **Resources** → onde definimos os serviços que serão criados (S3, EC2, DynamoDB etc.).  
- **Outputs** → valores retornados após a criação da stack (ex.: endpoint de uma instância).  

---

## ⚙️ Experiência prática

Durante a prática:
1. Criei meu primeiro **template YAML** para provisionar recursos.  
2. Entendi como enviar e executar esse template no **CloudFormation Console**.  
3. Observei a criação da **Stack**, validando logs e outputs.  
4. Testei atualizações e exclusões de Stacks para compreender o ciclo de vida.  

Exemplo simplificado de template:

```yaml
AWSTemplateFormatVersion: "2010-09-09"
Description: "Exemplo de Stack simples no CloudFormation"

Resources:
  MeuBucketS3:
    Type: AWS::S3::Bucket
    Properties:
      BucketName: "meu-bucket-exemplo-cloudformation"
```

## Desafio 03
# Automatizando Infraestrutura com AWS CloudFormation
Aqui registro minhas anotações, aprendizados e um exemplo prático de template.

---

## 📌 O que aprendi

### O que é CloudFormation
AWS CloudFormation é o serviço da AWS que permite **criar, atualizar e gerenciar recursos de infraestrutura** usando arquivos declarativos em **YAML** ou **JSON**. É um dos pilares de **Infrastructure as Code (IaC)**, permitindo automatizar ambientes sem necessidade de configuração manual.

### Benefícios
- **Automação**: cria recursos sem cliques manuais no console.  
- **Padronização**: mantém ambientes consistentes.  
- **Escalabilidade**: provisiona múltiplos recursos de uma vez.  
- **Versionamento**: templates podem ser versionados no GitHub.  

---

## ⚙️ Estrutura de Templates
Um template em CloudFormation geralmente possui:
- **AWSTemplateFormatVersion** → versão do formato.  
- **Description** → descrição do que o template faz.  
- **Parameters** → valores que podem ser passados dinamicamente.  
- **Resources** → serviços AWS que serão criados.  
- **Outputs** → informações de retorno após a criação da Stack.  

---

## 🛠️ Experiência Prática
Durante a prática do desafio:
1. Entendi como acessar o serviço **CloudFormation** no console.  
2. Criei uma **Stack** usando um template simples em YAML.  
3. Validei logs e eventos durante a criação.  
4. Testei o ciclo de vida completo: criação, atualização e deleção da Stack.  

### Exemplo de Template
Um template simples para provisionar um bucket S3:

```yaml
AWSTemplateFormatVersion: "2010-09-09"
Description: "Exemplo de Stack simples no CloudFormation"

Resources:
  MeuPrimeiroBucket:
    Type: AWS::S3::Bucket
    Properties:
      BucketName: "bucket-exemplo-cloudformation-lari"

```

