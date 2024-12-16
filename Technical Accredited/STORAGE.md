# Amazon Storage Services

A **AWS** oferece diferentes soluções de **armazenamento** para atender às mais diversas necessidades, desde armazenamento de objetos até volumes persistentes para aplicações.

---

## Tipos Principais de Storage na AWS

### 1. **Amazon S3 (Simple Storage Service)**
- Armazenamento de objetos escalável e durável.  
- **Usos comuns**: Backup, arquivos estáticos (imagens, vídeos), data lakes.  
- **Características**:  
  - Durabilidade de **99,999999999% (11 9's)**.  
  - Classes de armazenamento para reduzir custos:
    - **S3 Standard**: Alta performance para acessos frequentes.
    - **S3 Infrequent Access (IA)**: Menor custo para acessos ocasionais.
    - **S3 Glacier**: Arquivamento de longo prazo (mais barato).

---

### 2. **EBS (Elastic Block Store)**
- Armazenamento em bloco para instâncias **EC2**.  
- **Usos comuns**: Volumes persistentes para bancos de dados, sistemas de arquivos.  
- **Características**:
  - Tipos de volume:
    - **GP3/GP2 (General Purpose SSD)**: Balanceio de performance e custo.
    - **IOPS SSD**: Alta performance para workloads críticos.
    - **Magnetic (HDD)**: Custos baixos para dados sequenciais.
  - Integrado com snapshots no **S3** para backup.

---

### 3. **EFS (Elastic File System)**
- Armazenamento de arquivos escalável para múltiplas instâncias EC2.  
- **Usos comuns**: Compartilhamento de dados entre containers, aplicações distribuídas.  
- **Características**:  
  - Escalabilidade automática.
  - Suporte ao protocolo **NFS (Network File System)**.
  - Classes para otimizar custos (Standard e Infrequent Access).

---

### 4. **FSx (File Systems Managed)**
- Soluções de **file system gerenciados** para casos específicos:
  - **FSx for Windows**: File system nativo para aplicações Windows.
  - **FSx for Lustre**: Alta performance para HPC (High-Performance Computing).

---

### 5. **Amazon Glacier**
- Armazenamento de **arquivos arquivados de longo prazo**.  
- **Usos comuns**: Retenção de dados para compliance e backup de histórico.  
- **Características**:
  - Custos extremamente baixos.
  - Recuperação de dados em minutos (Glacier Instant Retrieval) ou horas.

---

### 6. **Storage Gateway**
- Conecta ambientes **on-premises** com serviços AWS.  
- **Usos comuns**: Backup em nuvem, extensão de storage local.  
- **Modos**:
  - Gateway de arquivo.
  - Gateway de volume.
  - Gateway de fitas (para substituir sistemas legados de backup em fita).

---

## Resumo Comparativo

| **Serviço**    | **Tipo de Armazenamento** | **Usos Comuns**                  | **Diferencial**                     |
|----------------|---------------------------|-----------------------------------|-------------------------------------|
| **S3**         | Objeto                    | Backups, Data Lakes, arquivos     | Durabilidade e classes econômicas  |
| **EBS**        | Bloco                     | Bancos de dados, VMs, sistemas    | Alta performance, persistente      |
| **EFS**        | Arquivo                   | Aplicações compartilhadas         | Escalabilidade automática           |
| **FSx**        | Arquivo gerenciado        | Windows ou HPC                    | File system nativo específico       |
| **Glacier**    | Arquivamento              | Longo prazo, compliance           | Custo muito baixo                   |
| **Storage GW** | Híbrido                   | Backup on-premises, migrações     | Integração com sistemas locais      |

---

## Boas Práticas
1. Escolha o tipo de storage com base no uso (frequente, backup, etc.).
2. Use **lifecycle policies** no S3 para mover dados entre classes automaticamente.
3. Ative criptografia para dados sensíveis (**SSE-S3**, **SSE-KMS**, ou BYOK).
4. Monitore o uso com **AWS CloudWatch** para otimização de custos.
