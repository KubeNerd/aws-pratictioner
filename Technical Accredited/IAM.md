O IAM (Identity and Access Management) da AWS é o serviço que gerencia usuários, grupos, permissões e políticas de segurança. Ele controla quem pode acessar recursos da AWS e o que pode ser feito com esses recursos<br/>

## Componentes principais:
**Usuários**:   
Representam pessoas ou aplicações com acesso à AWS.<br/>
Cada usuário pode ter credenciais de acesso (chave de API ou senha).<br/>

**Grupos**:
Conjunto de usuários com permissões compartilhadas.<br/>
Simplifica o gerenciamento de acessos.<br/>

**Políticas**:
Definem permissões em JSON (ex.: permitir ou negar ações em recursos).<br/>
Podem ser anexadas a usuários, grupos ou roles.<br/>

**Roles (Funções)**:
Usadas por serviços ou aplicações para assumir permissões temporárias.<br/>
Muito usado em instâncias EC2, Lambda ou contas cross-account.<br/>

**Policies Managed vs Inline**:
**Managed**: Criadas e reutilizáveis.<br/>
**Inline**: Vinculadas diretamente a um recurso (menos flexíveis).<br/>

**MFA (Multi-Factor Authentication)**:
Segurança adicional, exigindo algo que o usuário "sabe" (senha) + algo que "tem" (token). <br/>

**Boas práticas**:
Use políticas de menor privilégio (Least Privilege).<br/>
Habilite MFA para contas críticas.<br/>
Não use a conta root no dia a dia.<br/>
Monitore acessos com logs no CloudTrail.<br/>
Utilize Roles em vez de chaves de API embutidas no código.<br/>

Link best pratices: [Acesse](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html)