# Elastic Compute Cloud

## EC2 - Elastic Compute Cloud
O Amazon EC2 (Elastic Compute Cloud) é um serviço da AWS que fornece máquinas virtuais (instâncias) na nuvem. Ele é escalável, flexível e pode ser usado para hospedar aplicações, sites, bancos de dados e mais. Você escolhe o tipo de instância, sistema operacional, e recursos como CPU, memória e armazenamento. Paga apenas pelo uso (pay-as-you-go). Ideal para workloads variados, de testes a produção.<br/>

No Amazon EC2, existem diferentes tipos de contratos para controlar custos e adequar ao uso:

**On-Demand**:
Paga pelo uso por hora ou segundo, sem compromisso de longo prazo.<br/>
Ideal para cargas variáveis ou testes.<br/>

**Savings Plans**:
Contrato flexível de 1 ou 3 anos, com descontos baseados no gasto comprometido ($/hora).<br/>
Aplica-se a instâncias EC2 e outros serviços (como AWS Lambda).<br/>
Oferece economia sem fixar tipo ou região de instância.<br/>


**Spot Instances**:
Usa capacidade ociosa da AWS com desconto de até 90%.<br/>
Preços variáveis; pode ser interrompido pela AWS.<br/>
Bom para workloads tolerantes a interrupções, como processamento em lote.<br/>

**Reserved Instances**:
Contrato de 1 ou 3 anos para instâncias específicas (tipo, região, AZ).<br/>
Oferece descontos significativos (até 75%), mas menos flexível.<br/>
Ideal para cargas constantes e previsíveis.<br/>


**Dedicated Hosts**:
Servidores físicos exclusivos, com controle total para compliance ou licenciamento.<br/>
Mais caro, usado em cenários específicos.<br/>

---
## Serverless
É um modelo de computação em que você não gerencia servidores diretamente. A infraestrutura é totalmente abstraída, e você paga apenas pelo uso (tempo de execução ou quantidade de requisições).<br/>

**Exemplos**: 
AWS Lambda, Fargate, DynamoDB.<br/>

#### Vantagens:
Escalabilidade automática.<br/>
Custo reduzido (paga pelo uso).<br/>
Foco no código, não na infraestrutura.<br/>
AWS Lambda
Serviço serverless para executar funções sob demanda em resposta a eventos.<br/>

**Execução baseada em eventos**: HTTP (API Gateway), S3, DynamoDB, CloudWatch, entre outros.
Limites: Até 15 minutos por execução, 10GB de memória, e limitações de armazenamento temporário.<br/>

**Caso de uso**: 
APIs sem servidor, automação, processamento em tempo real, etc.<br/>

---

## AWS Fargate
Modelo serverless para executar containers (ECS/EKS). Você gerencia apenas as tarefas e não a infraestrutura.<br/>

**Uso**: Para rodar containers Docker sem precisar configurar servidores ou clusters EC2.<br/>

**Casos de uso**: Aplicações escaláveis, microsserviços e processamento em lote.<br/>
Diferença de Lambda: Ideal para workloads longas ou complexas que precisam de um ambiente de container.<br/>

**Diferenças práticas**:
Característica	Lambda	Fargate
Tipo de Execução	Funções/eventos	Containers
Duração	Máx. 15 min por execução	Sem limite de duração
Uso	Tarefas pequenas e rápidas	Workloads complexos e persistentes
Gerenciamento 100% serverless (foco no código)	

### Containers sob demanda
Resumo: Use Lambda para tarefas simples/eventos e Fargate para workloads baseados em containers. Ambos são serverless, mas atendem necessidades diferentes.<br/>