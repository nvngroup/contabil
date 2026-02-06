# Contabil

🌐 **Site oficial:** [https://contabil.yesalel.tech/](https://contabil.yesalel.tech/)

Um sistema de contabilidade e gestão financeira desenvolvido para facilitar o controle de finanças pessoais e empresariais.

## 📋 Sobre este Repositório

**Este repositório é destinado exclusivamente para receber Issues e Discussions para feedback dos clientes.**

O aplicativo Contabil está disponível em [https://contabil.yesalel.tech/](https://contabil.yesalel.tech/). Este repositório serve como um canal de comunicação com nossos usuários, onde você pode:

- 🐛 Reportar bugs e problemas
- 💡 Sugerir novas funcionalidades
- 💬 Participar de discussões sobre o produto
- 📣 Enviar feedback sobre sua experiência

## 🚀 Principais Funcionalidades do Aplicativo

Acesse [https://contabil.yesalel.tech/](https://contabil.yesalel.tech/) para utilizar as seguintes funcionalidades:

- Controle de receitas e despesas
- Gestão de categorias financeiras
- Relatórios e análises
- Integração com diferentes métodos de pagamento
- Histórico de transações

## 📝 Como Reportar Issues e Enviar Feedback

Se você encontrar um bug ou tiver uma sugestão de melhoria:

1. Acesse a [aba Issues](https://github.com/nvngroup/contabil/issues) deste repositório
2. Verifique se já não existe uma issue similar
3. Clique em "New Issue" e use os templates disponíveis
4. Forneça o máximo de detalhes possível sobre o problema ou sugestão
5. Inclua capturas de tela quando aplicável

**Nota:** Todas as issues criadas neste repositório são automaticamente replicadas para o repositório privado `brunocgc/contabil` para gerenciamento interno.

## 💬 Discussions

Utilize a [aba Discussions](https://github.com/nvngroup/contabil/discussions) para:

- Fazer perguntas sobre o uso do aplicativo
- Compartilhar ideias e sugestões
- Discutir sobre funcionalidades futuras
- Conectar-se com outros usuários

## ⚙️ Configuração do Workflow de Issues

Para que o workflow de envio automático de issues funcione corretamente com o repositório privado `brunocgc/contabil`, é necessário configurar um Personal Access Token (PAT):

### Passos para Configuração:

1. **Criar um Personal Access Token:**
   - Acesse https://github.com/settings/tokens
   - Clique em "Generate new token" > "Generate new token (classic)"
   - Dê um nome descritivo (ex: "Contabil Issues Sync")
   - Selecione os escopos necessários:
     - ✅ `repo` (acesso completo a repositórios privados)
   - Clique em "Generate token"
   - **Copie o token gerado** (você não poderá vê-lo novamente!)

2. **Adicionar o Token como Secret:**
   - Vá para as configurações do repositório nvngroup/contabil
   - Navegue para "Settings" > "Secrets and variables" > "Actions"
   - Clique em "New repository secret"
   - Nome: `CONTABIL_PAT`
   - Valor: Cole o token que você copiou
   - Clique em "Add secret"

3. **Verificar Permissões:**
   - O usuário que criou o PAT deve ter permissão de escrita no repositório `brunocgc/contabil`
   - O repositório `brunocgc/contabil` deve existir e estar acessível

Após a configuração, todas as novas issues criadas serão automaticamente replicadas para o repositório privado.

## 📄 Licença

Este projeto está sob a licença Unlicense. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

## 👥 Autores

Desenvolvido e mantido por [nvngroup](https://github.com/nvngroup)

## 📞 Contato

- **Para usar o aplicativo:** Acesse [https://contabil.yesalel.tech/](https://contabil.yesalel.tech/)
- **Para reportar problemas:** Abra uma [issue](https://github.com/nvngroup/contabil/issues)
- **Para discussões gerais:** Utilize as [discussions](https://github.com/nvngroup/contabil/discussions)

---

⭐ Se este projeto foi útil para você, considere dar uma estrela e compartilhar com outros!