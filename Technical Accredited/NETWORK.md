# VPC (Virtual Private Cloud)
A VPC é um ambiente de rede virtual isolado dentro da AWS, onde você pode executar recursos como EC2, RDS, e ELB com controle total sobre sua rede.<br/>

**Principais Componentes**:
**Subnets**:

**Divisões dentro da VPC. Podem ser**:
**Públicas**: Conectadas à Internet (via Internet Gateway).<br/>
**Privadas**: Não têm acesso direto à Internet, usadas para recursos internos.<br/>
**Route Tables**:

Definem o tráfego permitido entre subnets e outros destinos (Internet Gateway, NAT Gateway, VPC Peering).
**Internet Gateway (IGW)**:

Permite que instâncias na subnet pública acessem a Internet.<br/>

**NAT Gateway**:

Permite que instâncias privadas iniciem conexões de saída para a Internet (atualizações, APIs) sem serem diretamente acessíveis.
**Security Groups**:

Firewalls em nível de instância. Controlam tráfego de entrada/saída com base em regras.<br/>

**Network ACLs (NACLs)**:
Firewalls em nível de subnet. Fornecem controle de tráfego mais amplo, mas menos granular que os Security Groups.<br/>
**VPC Peering**:

Conexão entre duas VPCs para comunicação direta, sem necessidade de Internet.<br/>

**VPN e Direct Connect**:
**VPN**: Conecta a VPC a uma rede on-premises via Internet.

**Direct Connect**: Conexão dedicada de alta performance entre sua empresa e a AWS.<br/>

**Boas Práticas**:
Use múltiplas subnets (públicas e privadas) para isolar cargas de trabalho.<br/>

Restringir acesso usando Security Groups e NACLs.<br/>

Log de tráfego: Ative o VPC Flow Logs para monitorar e depurar problemas de rede.<br/>

Reduza custos ao usar NAT Gateways estrategicamente (uma por AZ ou compartilhada).<br/>

Configure High Availability com múltiplas AZs para redundância.<br/>

**Resumo**:
A VPC oferece controle total sobre a rede, permitindo criar arquiteturas seguras e escaláveis para suas aplicações na nuvem.<br/>