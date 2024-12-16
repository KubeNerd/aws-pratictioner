## Introdução ao Amazon EC2

O **Amazon Elastic Compute Cloud (EC2)** é um dos serviços mais populares da **AWS**, projetado para fornecer capacidade de computação escalável na nuvem. Ele permite que você inicie instâncias virtuais (servidores) de forma rápida, com diferentes configurações de hardware, sistemas operacionais e aplicações, adaptando-se às necessidades específicas de processamento e carga.

### Principais características do EC2:
- **Flexibilidade**: Escolha tipos de instâncias, sistemas operacionais e configurações de rede.
- **Escalabilidade**: Aumente ou diminua a capacidade conforme a demanda.
- **Pagamentos por uso**: Você paga apenas pelo tempo de uso das instâncias, o que reduz custos.
- **Integração**: Funciona em conjunto com outros serviços da AWS, como S3, RDS e ELB.

O EC2 é usado para diversas finalidades, como hospedar sites, processar dados em tempo real, rodar aplicações críticas ou até mesmo criar ambientes de desenvolvimento e teste.

---

## O que é o EC2 Metadata?

O **Amazon EC2 Metadata** é um serviço interno das instâncias EC2 que oferece acesso a informações sobre a própria instância e o ambiente em que ela está sendo executada. Essas informações são chamadas de "metadados" e podem ser acessadas por scripts ou aplicações diretamente da instância.

Os metadados são fornecidos por meio de um endpoint específico, sem necessidade de autenticação externa, permitindo que instâncias configurem automaticamente aplicações ou ambientes.

---

### **Por que usar o EC2 Metadata?**

O EC2 Metadata é útil porque:
- Fornece informações essenciais sobre a instância, como o ID, tipo, endereço IP e mais.
- Permite obter credenciais temporárias de acesso para integrar a instância com outros serviços da AWS de forma segura, usando IAM Roles.
- Ajuda na configuração dinâmica e na automação do ambiente.

---

### **Como funciona o EC2 Metadata?**

As informações de metadados são acessíveis através do seguinte endpoint local:



#### Exemplos de Metadados Disponíveis:

1. **Identificação da instância**:
   - ID da instância, tipo, região, zona de disponibilidade.
   - Comando:  
     ```bash
     curl http://169.254.169.254/latest/meta-data/instance-id
     ```

2. **Informações de rede**:
   - Endereço IP público e privado, configuração de sub-rede, VPC.
   - Comando:  
     ```bash
     curl http://169.254.169.254/latest/meta-data/public-ipv4
     ```

3. **User Data**:
   - Scripts ou informações fornecidas durante a inicialização da instância.
   - Comando:  
     ```bash
     curl http://169.254.169.254/latest/user-data
     ```

4. **Credenciais temporárias do IAM Role**:
   - Se a instância estiver associada a um IAM Role, você pode obter credenciais temporárias.
   - Exemplo:
     ```bash
     curl http://169.254.169.254/latest/meta-data/iam/security-credentials/<RoleName>
     ```

Esses dados permitem que a instância EC2 saiba "quem ela é", onde está e o que pode acessar na infraestrutura AWS.

---

### **Instance Metadata Service v2 (IMDSv2)**

A AWS introduziu a **versão 2 do EC2 Metadata Service (IMDSv2)** para adicionar segurança contra vulnerabilidades como **SSRF (Server-Side Request Forgery)**. A principal diferença é que o IMDSv2 exige que seja feita uma solicitação autenticada com um token para acessar os metadados.

#### Por que usar IMDSv2?
- Protege contra ataques que exploram vulnerabilidades no servidor de aplicação.
- Oferece controle mais rigoroso sobre o acesso aos metadados.

Exemplo de uso com token:
```bash
TOKEN=$(curl -X PUT "http://169.254.169.254/latest/api/token" -H "X-aws-ec2-metadata-token-ttl-seconds: 21600")
curl -H "X-aws-ec2-metadata-token: $TOKEN" "http://169.254.169.254/latest/meta-data/"
