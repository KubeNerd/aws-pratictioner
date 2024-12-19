# Anotações com nomes e explicações de serviços

### Amazon IAM

**IAM user groups:** Embora os grupos de usuários IAM sejam úteis para organizar e gerenciar conjuntos de usuários com permissões semelhantes, eles podem exigir ajustes frequentes conforme os funcionários mudam de equipe. Se um usuário mudar de equipe, seria necessário removê-lo de um grupo e adicioná-lo a outro, o que pode resultar em uma sobrecarga operacional significativa, especialmente em organizações com mudanças frequentes de equipe.

**IAM instance profiles:** IAM instance profiles são usados para atribuir permissões a instâncias EC2, não a usuários. Eles não são apropriados para gerenciar permissões de funcionários que mudam de equipe, pois não oferecem flexibilidade para atribuir permissões baseadas em funções de usuário.

**IAM policies for individual users:** Criar políticas de IAM para usuários individuais pode ser uma abordagem detalhada e demorada, especialmente em organizações com mudanças frequentes de equipe. Além disso, pode resultar em uma gestão complexa e propensa a erros conforme os funcionários mudam de equipe, aumentando a sobrecarga operacional.

---
### Armazenamento na AWS  

### Amazon S3

**S3 Standard:** <br/>
Características: Essa classe de armazenamento é projetada para dados acessados com frequência. Oferece baixa latência e alta taxa de transferência, mas o custo por gigabyte é mais alto em comparação com outras classes.

**S3 Glacier Flexible Retrieval:** <br/>
Ideal para dados que não são acessados com frequência e que podem ser recuperados dentro de um tempo de até 12 horas, oferecendo um custo de armazenamento por gigabyte muito baixo em comparação com outras classes de armazenamento. É a opção mais econômica para os dados que a empresa acessa raramente e que não requerem recuperação imediata.

**S3 One Zone-Infrequent Access (S3 One Zone-IA):** <br/>
Características -  Essa classe é destinada a dados acessados com menos frequência, mas é armazenada em uma única zona de disponibilidade. É uma opção econômica, mas com menor durabilidade, já que os dados não são replicados em várias zonas de disponibilidade.

**S3 Standard-Infrequent Access (S3 Standard-IA):** <br/>
Características: Projetada para dados acessados com menos frequência, mas que precisam estar disponíveis rapidamente quando solicitados. Oferece um bom equilíbrio entre custo e desempenho, com um custo menor que o S3 Standard.

#### Criptografia no S3
**Server-side encryption with Amazon S3 managed encryption keys (SSE-S3):** <br/> Neste método, o Amazon S3 gerencia as chaves de criptografia. Cada objeto é criptografado com uma chave de criptografia única, e a chave em si é criptografada com uma chave mestra regularmente rotacionada pelo AWS.

**Server-side encryption with AWS KMS managed keys (SSE-KMS):** Neste caso, as chaves de criptografia são gerenciadas pelo AWS Key Management Service (KMS). O KMS gera, criptografa e descarta as chaves de criptografia de forma segura. Você pode usar chaves gerenciadas pela AWS ou criar suas próprias chaves gerenciadas pelo cliente.

Segurança no S3: [Proteção e criptografia de arquivos no S3](https://repost.aws/pt/knowledge-center/secure-s3-resources)


<hm/>

### Amazon FSx for Windows File Server

O Amazon FSx for Windows File Server é um serviço totalmente gerenciado que fornece servidores de arquivos Windows totalmente compatíveis com o protocolo SMB. Ele é ideal para cargas de trabalho que exigem acesso nativo ao SMB, como aplicativos Windows e compartilhamentos de arquivos. O Amazon FSx oferece alta confiabilidade, escalabilidade e desempenho, tornando-o a melhor escolha para a empresa em questão. <br/>

### Amazon Elastic File System
Serviço de armazenamento em nuvem fornecido pela Amazon Web Services (AWS) projetado para fornecer armazenamento de arquivos escalável , elástico , simultâneo com algumas restrições, e criptografado para uso com serviços de nuvem da AWS e recursos locais


### Amazon EBS
Serviço de armazenamento de bloco. Não um sistema de arquivos.

---
## Modelos de contrato de EC2

**Reserved Instances:** Oferecem um desconto significativo em relação ao modelo On-Demand, mas não chegam a 90%. O desconto típico é de 30-60% dependendo do termo de compromisso.

**On-Demand:** Este é o modelo de preço padrão sem descontos.

**Dedicated Hosts:** Permite arrendar servidores físicos dedicados, mas não oferece descontos tão altos quanto as Spot Instances.

**Cobrança por execução:** No Amazon EC2, as instâncias sob demanda são cobradas por hora de uso, com o tempo de cobrança sendo arredondado para cima até a hora seguinte. Isso significa que, mesmo que a instância seja executada por apenas alguns minutos ou segundos além de uma hora completa, será cobrada como se tivesse sido executada por toda a próxima hora.

Neste caso específico, como a instância foi executada por 3 horas, 5 minutos e 6 segundos, isso ultrapassou a marca de 3 horas completas. Portanto, o cliente será cobrado pelo tempo exato de 3 horas, 5 minutos e 6 segundos, e não pelo arredondamento para 4 horas completas.


---
**AWS IoT Core:** <br/>
O AWS IoT Core é um serviço de nuvem gerenciado da Amazon Web Services que permite que você conecte e gerencie com segurança bilhões de dispositivos de Internet das Coisas (IoT), permitindo que eles enviem e recebam dados de forma confiável de e para aplicativos de nuvem e outros dispositivos, tudo isso sem precisar gerenciar a infraestrutura subjacente você mesmo; atuando essencialmente como um hub central para comunicação entre seus dispositivos de IoT e a nuvem AWS

---
**AWS Snowball Edge:** <br/> 
É um tipo de dispositivo Snowball com armazenamento integrado e poder de computação para recursos selecionados da AWS. O Snowball Edge pode processar dados localmente, executar cargas de trabalho de edge computing e transferir dados de ou para a Nuvem AWS.

Cada dispositivo Snowball Edge pode transportar dados em velocidades mais rápidas do que a internet. Esse transporte é feito enviando os dados nos dispositivos por meio de uma transportadora regional. Os aparelhos são robustos, completos com etiquetas de envio E Ink.

---
**Aws Storage Gateway:** <br/>
Serviço de armazenamento em nuvem híbrida que permite o acesso a armazenamento na nuvem da AWS a partir de ambientes locais. Ele integra a infraestrutura local existente à AWS, permitindo que os usuários armazenem e recuperem dados da nuvem e executem aplicativos em um ambiente híbrido.

---
**AWS LigthSail:** <br/> 
Interface simplificada do console AWS, para usuários sem conhecimento em cloud.

---
**AWS CloudFormation:** <br/>
Permite provisionar recursos da AWS, mas você precisa definir a infraestrutura usando modelos JSON ou YAML, e não linguagens de programação comuns. Portanto, essa não é a melhor opção para a pergunta.

---
**AWS CodePipeline:** <br/>
É um serviço de entrega contínua que ajuda a automatizar o processo de implantação de aplicativos. Ele não é usado diretamente para modelar e provisionar recursos da AWS usando linguagens de programação. Portanto, essa opção não é a resposta correta.

---
**AWS Systems Manager:** <br/> 
É uma coleção de recursos projetados para ajudar na gerência e operação de infraestruturas na AWS. Ele não é usado para modelar e provisionar recursos usando linguagens de programação. Portanto, essa opção também não é a resposta correta.

---
**AWS Knowledge Center**: <br/>
É o principal recurso para revisar as respostas às perguntas frequentes (FAQs) sobre segurança na nuvem da AWS. Ele oferece uma ampla gama de artigos, tutoriais e documentações que abrangem diversos tópicos de segurança

---
**Amazon EC2 Auto Scaling:** <br/>
Serviço da AWS que permite dimensionar automaticamente a capacidade de computação para aplicações baseadas em instâncias do Amazon EC2. Ele monitora o uso dos recursos e ajusta automaticamente a capacidade para manter o desempenho ideal, adicionando ou removendo instâncias do EC2 conforme necessário.

---
**AWS KMS:** <br/>
Serviço que permite a criptografia de dados em repouso para o Amazon Elastic Block Store (Amazon EBS). Ele fornece chaves criptográficas para criptografar seus dados EBS e gerencia o ciclo de vida dessas chaves.

---
**AWS Compute Optimizer:** <br/>
Ferramanta que analisa o uso de recursos de computação na nuvem da AWS e fornece recomendações para otimizar o desempenho e reduzir os custos. O conceito de nuvem demonstrado pelo AWS Compute Optimizer é principalmente Redimensionamento.

Ele ajuda a ajustar os recursos de computação, como instâncias EC2 e grupos de Auto Scaling, de acordo com a demanda atual, garantindo que você tenha os recursos certos na quantidade certa no momento certo. Isso é essencial para otimizar a utilização de recursos na nuvem, garantindo que você não pague por capacidade não utilizada e que possa lidar com flutuações na demanda de maneira eficiente.


---
**Amazon OpenSearch Service:** <br/>
Serviço que facilita a implantação, operação e escalabilidade de um cluster do OpenSearch (anteriormente conhecido como Elasticsearch) na AWS.

---
**AWS Control Tower** <br/>
Serviço que facilita a configuração e governança de múltiplas contas da AWS.

---

## Sistema de arquivos na Amazon

**Amazon FSx:**
Acesse: [Documentação Fsx](https://aws.amazon.com/pt/fsx/)


---
#### AWS Migration Evaluator**
Serviço gratuito oferecido pela Amazon Web Services que ajuda as organizações a avaliar seu ambiente de TI atual e a criar um caso de negócios baseado em dados para migrar suas cargas de trabalho para a nuvem AWS, fornecendo estimativas detalhadas de custos e desempenhos de projeção com base em suas necessidades. uso da infraestrutura local, permitindo-lhes tomar decisões informadas sobre a migração para a nuvem antes de se comprometerem com uma mudança completa. 

**Pontos principais sobre o AWS Migration Evaluator**: <br/>
**Função:**
Analisa servidores e aplicativos locais existentes para estimar possíveis economias de custos e melhorias de desempenho após a migração para a AWS. 

**Benefícios:** <br/>
Cria um caso de negócios direcional para migração para a nuvem 
Identifica tamanhos ideais de instâncias da AWS para cargas de trabalho 
Fornece comparações de custos entre locais e AWS 
Ajuda a avaliar opções de licenciamento para migração de aplicativos

---
**Amazon Detective:** <br/>

---
**AWS Application Composer:** <br/> 
Um serviço de design visual de baixo código que permite criar aplicativos sem servidor com rapidez. Ele fornece uma interface de design visual arrastar e soltar para combinar componentes AWS prontos para uso, como API, bancos de dados, funções, fluxos de trabalho e muito mais.você pode projetar e criar visualmente aplicativos sem servidor completos, desde front-ends até back-ends, sem precisar escrever muito código. Ele abstrai a complexidade das arquiteturas sem servidor subjacentes e permite criar e implantar aplicativos rapidamente.

---
**AWS Resource Access Manager (RAM):** <br/> Permite compartilhar recursos da AWS entre contas da AWS e através de suas organizações. Não é utilizado para adquirir software de terceiros.

---
**AWS Managed Services:** <br/> Fornece serviços gerenciados de monitoramento e automação para recursos na AWS. Não é para aquisição de software.

---
**AWS License Manager:** Ajuda a gerenciar licenças de software de fornecedores terceiros já adquiridas. Não é utilizado para adquirir novas licenças.

---
**AWS Batch:** <br/> 
Serviço gerenciado que permite executar trabalhos em lote de computação em escala na Nuvem AWS. Ele é projetado especificamente para processamento paralelo em larga escala de centenas de milhares ou milhões de trabalhos de computação.

Com o AWS Batch, você pode definir trabalhos computacionais e o serviço dimensiona dinamicamente a capacidade computacional necessária para executá-los, aproveitando os recursos de computação sob demanda da AWS. Ele agenda, inicia, monitora e gerencia os trabalhos de computação em sua conta, otimizando o uso de recursos e reduzindo custos.


---
**AWS Step Functions:** <br/>
Serviço de orquestração de aplicativos serverless, mas não é projetado para executar trabalhos de computação em larga escala.

---
**AWS Service Catalog:** <br/> 
Serviço para gerenciar catálogos de produtos de TI aprovados para implantação, mas não é um serviço de execução de trabalhos de computação.

---
**Amazon Simple Queue Service (SQS):** <br/> 
Serviço de filas de mensagens, não projetado para execução de trabalhos de computação em larga escala.


---
**Amazon Aurora Serverless:** <br/> 
Este serviço oferece escalabilidade automática e capacidade de dimensionamento sob demanda, o que significa que você paga apenas pelos recursos utilizados durante o tempo em que o banco de dados está ativo. Isso elimina a necessidade de provisionar e gerenciar instâncias de banco de dados, proporcionando uma solução mais simples e econômica para a migração do banco de dados PostgreSQL para a AWS.


---
**Amazon SQS:** <br/> 
Serviço de filas de mensagens que permite enviar, armazenar e receber mensagens entre componentes do aplicativo. Ele oferece suporte ao processamento FIFO, o que garante que as mensagens sejam processadas na ordem em que foram enviadas. Isso é crucial para aplicativos que exigem processamento de mensagens em sequência, como sistemas de pagamento ou logs de auditoria.

---

**AWS Elastic Beanstalk:** <br/> 
Serviço de implantação e dimensionamento de aplicativos que facilita o processo de implantação de aplicativos e serviços web na infraestrutura da AWS. Ele abstrai a complexidade da configuração de recursos como instâncias EC2, balanceadores de carga, grupos de Auto Scaling, entre outros.

---
**AWS CloudShell:** <br/> 
Serviço pré-autenticado baseado em navegador que permite executar comandos da AWS CLI diretamente no Console de Gerenciamento da AWS. Isso significa que você não precisa configurar nenhuma credencial de acesso para usar o CloudShell, o que o torna ideal para usuários que precisam acessar os serviços da AWS rapidamente e sem precisar instalar nenhuma ferramenta adicional.

---
**AWS Partner Network (APN):** <br/> 
Programa de parceiros da AWS que conecta empresas com consultores terceirizados e parceiros de serviços aprovados pela AWS. Esses parceiros são qualificados para fornecer serviços especializados em soluções e produtos da AWS.

Ao procurar consultores terceirizados para manter e dar suporte ao ambiente AWS e às necessidades de negócios, o APN é o recurso adequado. Ele permite encontrar parceiros com expertise comprovada em vários serviços e soluções da AWS, como migração, gerenciamento de gastos, arquitetura de soluções, entre outros.

---
**AWS Partner Solutions Finder:** <br/>  seja útil para encontrar parceiros da AWS que ofereçam soluções e serviços, é mais voltado para identificar parceiros que possam auxiliar na implementação, consultoria ou suporte especializado. Não é o local ideal para adquirir diretamente o software de segurança.

---
**AWS Support Center:** <br/>  é um recurso para obter suporte técnico, documentação e recursos de aprendizado sobre os serviços da AWS. No entanto, não é o lugar apropriado para adquirir software de terceiros, como o software de segurança fornecido pelo parceiro.

---
**AWS Management Console:** <br/>  É a interface gráfica de usuário para acessar e gerenciar os serviços da AWS. Embora seja o local onde os usuários interagem com os serviços, não é o lugar para adquirir software de terceiros como um serviço de segurança.

----
### Planos de suporte
**Suporte Básico:** <br/> geralmente é o nível mais baixo de suporte oferecido. Ele normalmente inclui apenas suporte limitado através de canais online como fóruns, bases de conhecimento e talvez email. Não oferece acesso direto a técnicos de suporte ou um concierge dedicado. É insuficiente para obter o alto nível de suporte fornecido por um concierge.

**Suporte ao Desenvolvedor:** <br/> como o nome sugere, é focado em fornecer suporte técnico e recursos para desenvolvedores de software que estão criando aplicativos usando as APIs, SDKs ou plataformas da empresa. Embora possa incluir alguns canais de suporte prioritários, geralmente não inclui um concierge de suporte para lidar com problemas operacionais ou suporte ao usuário final.

**Apoio Empresarial:** <br/>  é um nível abaixo do Suporte Empresarial premium. Pode incluir SLAs mais rígidos, canais prioritários, mas ainda não fornece um concierge ou gerente de suporte dedicado para ajudar com tarefas e solicitações personalizadas em tempo real.
https://aws.amazon.com/pt/premiumsupport/plans/


---
**VPC endpoint** <br/>  
Permite que as instâncias do EC2 se comuniquem com serviços da AWS, como o Amazon S3, sem precisar de um gateway de internet. No entanto, ele não permite que as instâncias do EC2 acessem a internet pública.

---
**Amazon PrivateLink:** <br/>  
Permite que as instâncias do EC2 se comuniquem com outros recursos da AWS e com redes VPC de outras contas da AWS sem precisar de um gateway de internet. No entanto, ele não permite que as instâncias do EC2 acessem a internet pública.

---
**VPC peering:** <br/>  permite conectar duas VPCs na mesma região da AWS, mas não permite que as instâncias do EC2 acessem a internet pública.

---
**NAT gateway** <br/>  permite que instâncias em uma sub-rede privada se conectem à Internet ou a outros serviços da AWS, enquanto oculta a infraestrutura na sub-rede privada dos usuários da Internet. Isso é alcançado através da tradução de endereços IP da instância privada para um endereço IP público atribuído ao NAT gateway ao se comunicar com a Internet. Isso permite que a instância obtenha atualizações do sistema operacional da Internet, mas impede que o tráfego da Internet acesse diretamente a instância do EC2 na sub-rede privada.

---
**AWS Cost and Usage Report** <br/>  
Fornece informações detalhadas sobre seus custos e uso da AWS, incluindo dados de faturamento. Com esses relatórios, você pode criar painéis no Amazon QuickSight para visualizar e analisar seus gastos e tendências ao longo do tempo.


---
**AWS Personal Health Dashboard:** <br/>  Este serviço fornece uma visão geral personalizada do estado de saúde dos serviços e recursos da AWS que você está utilizando. Ele exibe quaisquer eventos relevantes para seus recursos específicos, como problemas de serviço, agendamento de manutenção programada ou mudanças de status operacional. Isso ajuda a monitorar a integridade dos recursos da AWS que a empresa está usando para hospedar seu aplicativo.

---
**AWS Service Health Dashboard:** <br/>  Este serviço exibe o status atual de todos os serviços da AWS em diferentes regiões. Ele fornece informações sobre qualquer problema de serviço ou evento operacional que esteja afetando os serviços da AWS. Isso permite que a empresa verifique se a infraestrutura geral da AWS está operando normalmente.


---
**Amazon Transcribe:** <br/>  
Converte áudio em texto, não texto em voz.

---
**Amazon Rekognition:** <br/>  
Reconhece e analisa objetos em imagens e vídeos, não lida com texto para voz.

---
**Amazon Textract:** <br/>  
Extrai texto de imagens e documentos, não converte texto em fala.