##  Desafio DIO – Automatizando Workflows com AWS Step Functions

###  Descrição

Este projeto faz parte do desafio da **Digital Innovation One (DIO)** e tem como objetivo consolidar conhecimentos sobre **AWS Step Functions**, criando um **workflow automatizado** que processa arquivos no S3, analisa logs, armazena métricas e gera relatórios diários.

---

### Objetivo

Explorar na prática o funcionamento do **AWS Step Functions** como orquestrador de serviços, integrando:

* **S3** para armazenamento de logs,
* **CloudWatch** para métricas,
* **DynamoDB** para persistência de dados, e
* **Lambda** para processamento e geração de relatórios.

---

###  Estrutura do Workflow

O fluxo implementado segue as seguintes etapas:

1. **ProcessLogsUnderPrefix (Map State)**
   Percorre os objetos em um bucket S3 (`<S3_INPUT_BUCKET>`) e inicia o processamento de cada log.

2. **AnalyzeLogData (Pass State)**
   Analisa os dados do log recebido, preparando as informações para coleta de métricas.

3. **StoreMetrics (CloudWatch: PutMetricData)**
   Registra métricas no **Amazon CloudWatch** para acompanhamento e monitoramento de performance.

4. **StoreSummary (DynamoDB: PutItem)**
   Persiste os resultados resumidos no **Amazon DynamoDB**.

5. **Export Results (<S3_RESULT_BUCKET>)**
   Armazena os dados processados em um bucket de saída no **S3**.

6. **GenerateDailySummary (Lambda: Invoke)**
   Invoca uma função **Lambda** responsável por consolidar os resultados diários e gerar o relatório final.

---

###  Diagrama do Workflow

Abaixo está a representação visual do fluxo construído:

images/AWS-Step-Functions-Workflow.PNG
---

###  Insights e Aprendizados

* **Step Functions** facilita a criação de workflows complexos com integração entre múltiplos serviços da AWS.
* O uso de **Map State** permite processar diversos arquivos de forma paralela.
* A integração com **CloudWatch** e **DynamoDB** simplifica a coleta e o armazenamento de dados de forma escalável.
* É possível obter **observabilidade completa** sobre cada execução, status e tempo de processamento.

---

###  Tecnologias Utilizadas

* **AWS Step Functions**
* **AWS Lambda**
* **Amazon S3**
* **Amazon CloudWatch**
* **Amazon DynamoDB**



### 🏁 Conclusão

Este laboratório permitiu compreender como **automatizar workflows serverless** usando AWS Step Functions, aplicando conceitos de **orquestração, mensageria, monitoramento e persistência de dados**.
O resultado é um fluxo robusto, escalável e de fácil manutenção — pronto para ser aplicado em cenários reais de processamento de logs e geração de relatórios.

---

