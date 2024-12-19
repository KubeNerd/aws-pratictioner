# Comparação: Assumed-Role vs Access Key ID e Secret Access Key

## 1. Conceito: Assumed-Role vs Access Key ID e Secret Access Key

### **Access Key ID e Secret Access Key**
- **O que é?**
  - São credenciais estáticas geradas no **AWS IAM** (Identity and Access Management) para autenticação de usuários ou aplicações.
  - O **Access Key ID** identifica o usuário/aplicação.
  - O **Secret Access Key** é a chave secreta usada para assinar as requisições.
- **Desafios:**
  - **Segurança:** Se vazadas, podem ser usadas indevidamente.
  - **Gerenciamento:** São estáticas e precisam ser rotacionadas manualmente.
  - **Melhores práticas:** Nunca armazene essas chaves no código ou em sistemas inseguros.

### **Assumed-Role**
- **O que é?**
  - Utiliza a funcionalidade do **AWS STS (Security Token Service)** para assumir uma **role** temporariamente, ao invés de usar credenciais estáticas.
  - Uma **role** define permissões específicas e pode ser assumida por serviços ou entidades (como uma EC2).
  - Permissões temporárias são fornecidas (via tokens temporários) e expiram automaticamente.
- **Vantagens:**
  - **Segurança:** Credenciais temporárias reduzem a superfície de ataque.
  - **Flexibilidade:** Pode ser configurada para aplicações e serviços assumirem a role quando necessário.
  - **Gerenciamento:** Elimina a necessidade de gerenciar chaves estáticas.

| Aspecto                 | Access Key ID / Secret Key           | Assumed-Role                       |
|-------------------------|-------------------------------------|------------------------------------|
| **Tipo de credencial**  | Estática e de longo prazo           | Temporária e gerada dinamicamente  |
| **Gerenciamento**       | Manual (rotação periódica)          | Automático via STS                 |
| **Segurança**           | Maior risco em caso de vazamento    | Menor risco (token temporário)     |
| **Uso ideal**           | Aplicações legadas, scripts locais  | Aplicações em nuvem (como EC2)     |

---

## 2. Configurando Permissões de Leitura no S3 via Assumed-Role

### **Passo 1: Criar uma Role no IAM**
1. Acesse o **IAM** no console AWS.
2. Vá para **Roles** > **Create Role**.
3. Escolha **AWS Service** como o tipo de entidade confiável.
4. Selecione **EC2** como serviço.
   - Isso permite que a instância EC2 assuma essa role.
5. Clique em **Next: Permissions**.

### **Passo 2: Adicionar Permissão de Somente Leitura no S3**
1. Em **Attach Policies**, procure pela policy gerenciada do S3:
   - **AmazonS3ReadOnlyAccess**
2. Esta policy permite somente leitura de objetos e buckets no S3.

**Exemplo de Policy JSON (caso queira customizar):**
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:GetObject",
                "s3:ListBucket"
            ],
            "Resource": [
                "arn:aws:s3:::nome-do-bucket",
                "arn:aws:s3:::nome-do-bucket/*"
            ]
        }
    ]
}
```

---

### **Passo 3: Associar a Role à Instância EC2**

#### **Durante o lançamento da EC2**:
   - Ao criar uma nova instância EC2, no passo **Configure Instance**, vá até a seção **IAM Role**.
   - Selecione a role que você criou anteriormente (com permissões de leitura no S3).

#### **Para uma instância EC2 existente**:
   1. Acesse o **EC2 Dashboard** no console AWS.
   2. Selecione a instância que deseja associar à role.
   3. Clique em **Actions** > **Security** > **Modify IAM Role**.
   4. Escolha a role criada anteriormente.
   5. Confirme as alterações.

---

### **Passo 4: Testar o Acesso ao S3 via EC2**
Para confirmar que a EC2 assumiu a role corretamente e possui acesso ao S3:

1. Acesse a instância EC2 via SSH.
2. Use o comando **AWS CLI** para listar o bucket S3:
   ```bash
   aws s3 ls s3://nome-do-bucket
   ```
   > **Nota:** A AWS CLI precisa estar configurada, mas **não requer credenciais estáticas** quando a EC2 assume a role.

3. Para verificar que as credenciais temporárias estão sendo usadas pela EC2, execute:
   ```bash
   curl http://169.254.169.254/latest/meta-data/iam/security-credentials/
   ```
   Isso retornará o nome da role associada à EC2. Em seguida, execute:
   ```bash
   curl http://169.254.169.254/latest/meta-data/iam/security-credentials/<nome-da-role>
   ```
   Você verá as credenciais temporárias geradas pelo **AWS STS**.

---

## Benefícios da Abordagem
1. **Elimina credenciais estáticas**: A role associada à EC2 gera tokens temporários automaticamente.
2. **Segurança aprimorada**: Credenciais temporárias são difíceis de serem reutilizadas em caso de vazamento.
3. **Gestão simplificada**: Não há necessidade de gerenciar ou rotacionar manualmente as chaves.
