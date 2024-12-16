# Shared Responsibility Model

## O que é?

O **Modelo de Responsabilidade Compartilhada** divide as responsabilidades de segurança e conformidade entre a **AWS** e o **cliente**, garantindo que ambos contribuam para a proteção do ambiente.

---

## Responsabilidades da AWS ("Segurança da Nuvem")

A AWS é responsável por gerenciar:
- **Infraestrutura global**:
  - Hardware físico, rede e datacenters.
  - Serviços de rede, como proteção contra ataques DDoS.
- **Software subjacente**:
  - Sistemas operacionais de hosts e hipervisores.
- **Conformidade**:
  - Certificações globais (ISO 27001, PCI-DSS, etc.).

---

## Responsabilidades do Cliente ("Segurança na Nuvem")

O cliente gerencia:
- **Configuração de Serviços**:
  - Definição de permissões e políticas no **IAM**.
  - Configuração de Security Groups, NACLs e rotas.
- **Gerenciamento de Dados**:
  - Criptografia de dados em repouso e em trânsito.
  - Configuração de backups e políticas de recuperação.
- **Sistemas Operacionais e Aplicações**:
  - Atualizações de patches e segurança de instâncias EC2.
  - Monitoramento e auditoria de logs (**CloudTrail, CloudWatch**).

---

## Exemplos Práticos

### Amazon EC2
- **AWS**: Gerencia hardware, hipervisor e rede do datacenter.
- **Cliente**: Configura e mantém o sistema operacional, firewalls e aplicações.

### Amazon S3
- **AWS**: Garante a alta disponibilidade e replicação (quando habilitada).
- **Cliente**: Define políticas de acesso, criptografia e compliance dos dados.

---

## Boas Práticas
- Sempre habilite **MFA** para usuários e root.
- Use o princípio de **menor privilégio** no IAM.
- Monitore seu ambiente com ferramentas como **CloudTrail** e **VPC Flow Logs**.
- Realize auditorias regulares e configure alarmes.

---

