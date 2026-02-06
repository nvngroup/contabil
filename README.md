# Contabil

Um sistema de contabilidade e gestão financeira desenvolvido para facilitar o controle de finanças pessoais e empresariais.

## 📋 Sobre o Projeto

Contabil é uma solução de contabilidade que visa simplificar a gestão financeira através de ferramentas modernas e intuitivas. O projeto está em desenvolvimento ativo e aceita contribuições da comunidade.

## 🚀 Funcionalidades

- Controle de receitas e despesas
- Gestão de categorias financeiras
- Relatórios e análises
- Integração com diferentes métodos de pagamento
- Histórico de transações

## 📦 Instalação

```bash
# Clone o repositório
git clone https://github.com/nvngroup/contabil.git

# Navegue até o diretório
cd contabil

# Instale as dependências
# (instruções de instalação serão adicionadas conforme o projeto evolui)
```

## 💻 Uso

```bash
# Instruções de uso serão adicionadas conforme o desenvolvimento
```

## 🛠️ Tecnologias

As tecnologias utilizadas serão definidas durante o desenvolvimento do projeto.

## 🤝 Contribuindo

Contribuições são sempre bem-vindas! Para contribuir:

1. Faça um fork do projeto
2. Crie uma branch para sua feature (`git checkout -b feature/MinhaFeature`)
3. Commit suas mudanças (`git commit -m 'Adiciona MinhaFeature'`)
4. Push para a branch (`git push origin feature/MinhaFeature`)
5. Abra um Pull Request

Por favor, certifique-se de:
- Seguir os padrões de código do projeto
- Adicionar testes quando aplicável
- Atualizar a documentação conforme necessário
- Descrever suas mudanças claramente no PR

## 📝 Reportando Issues

Se você encontrar um bug ou tiver uma sugestão de melhoria, por favor:

1. Verifique se já não existe uma issue similar
2. Use os templates de issue disponíveis
3. Forneça o máximo de detalhes possível
4. Inclua exemplos quando aplicável

**Nota:** Todas as issues criadas neste repositório são automaticamente replicadas para o repositório privado `brunocgc/contabil` para gerenciamento interno.

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

Para questões ou sugestões, abra uma issue no repositório.

---

⭐ Se este projeto foi útil para você, considere dar uma estrela!