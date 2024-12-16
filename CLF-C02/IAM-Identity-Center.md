# Comparação: IAM vs IAM Identity Center

## O que é IAM?
**IAM (Identity and Access Management)** é o serviço da AWS para gerenciamento de identidades e acessos em nível de recursos. Ele permite:
- Controle de acesso granular para recursos da AWS.
- Criação de **usuários**, **grupos**, **funções** e **políticas** de permissões.
- Integração com autenticação baseada em credenciais e chaves de acesso.

**Casos de uso do IAM**:
- Conceder permissões específicas para usuários individuais ou aplicações.
- Gerenciar permissões baseadas em funções para instâncias EC2, Lambda, etc.
- Controlar acessos usando políticas JSON personalizadas.

---

## O que é o IAM Identity Center?
**IAM Identity Center (anteriormente AWS Single Sign-On)** é uma solução para:
- Gerenciar acesso a contas AWS e aplicativos de terceiros.
- Oferecer login centralizado (SSO) para usuários.
- Integração com diretórios externos, como **AD** ou **Azure AD**.

**Casos de uso do IAM Identity Center**:
- Implementar Single Sign-On para múltiplas contas ou aplicações na AWS.
- Facilitar o gerenciamento de usuários em organizações grandes.
- Configurar permissões usando grupos e atribuições centralizadas.

---

## Comparação: IAM vs IAM Identity Center

| Aspecto                      | **IAM**                                      | **IAM Identity Center**                       |
|------------------------------|----------------------------------------------|----------------------------------------------|
| **Escopo**                   | Gerenciamento direto de recursos da AWS.    | Acesso centralizado a contas e aplicações.   |
| **Usuários e Grupos**        | Criados diretamente no IAM.                 | Sincronizados de diretórios externos ou criados no serviço. |
| **Autenticação**             | Credenciais individuais ou chaves de acesso.| Login centralizado com Single Sign-On.       |
| **Gerenciamento de Permissões** | Políticas JSON específicas por usuário/role.| Baseado em grupos e atribuições centralizadas. |
| **Melhor para**              | Configuração granular em recursos AWS.      | Organizações com múltiplas contas ou aplicações externas. |

---

## Quando usar cada um?

- **Use IAM**:
  - Para acessos granulares a serviços AWS.
  - Quando você precisa de controle específico sobre usuários e políticas.

- **Use IAM Identity Center**:
  - Para gerenciar usuários e acessos em uma **estrutura organizacional grande**.
  - Para fornecer uma experiência de login única e simplificada.
