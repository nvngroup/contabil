# Configuração de Workflows - Guia do Administrador

Este documento descreve como configurar e manter os workflows de automação de issues do repositório.

## 📋 Visão Geral

O repositório possui três workflows principais:

1. **issue-management.yml** - Gerenciamento automático de issues
2. **issue-validation.yml** - Validação de qualidade de issues
3. **forward-issues.yml** - Envio automático para repositório privado

## 🔐 Configuração Obrigatória: Personal Access Token

### Por que é necessário?

O workflow `forward-issues.yml` replica automaticamente todas as issues criadas neste repositório público para o repositório **privado** `brunocgc/contabil`. O token padrão do GitHub Actions (`GITHUB_TOKEN`) não tem permissões para acessar repositórios externos, especialmente privados.

### Criando o Personal Access Token (PAT)

1. **Acesse a página de tokens:**
   - https://github.com/settings/tokens
   - OU: GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic)

2. **Gere um novo token:**
   - Clique em "Generate new token (classic)"
   - **Nome:** `Contabil Issues Sync`
   - **Expiration:** Recomendado: 90 dias (configure renovação automática)
   - **Scopes necessários:**
     - ✅ `repo` - Full control of private repositories
       - Isso inclui: repo:status, repo_deployment, public_repo, repo:invite, security_events
   
3. **Copie o token:**
   - ⚠️ **IMPORTANTE:** Copie o token imediatamente após a criação
   - Você não poderá visualizá-lo novamente

### Adicionando o Token aos Secrets

1. **Navegue até o repositório nvngroup/contabil:**
   - https://github.com/nvngroup/contabil/settings/secrets/actions

2. **Adicione o secret:**
   - Clique em "New repository secret"
   - **Name:** `CONTABIL_PAT` (exatamente este nome, o workflow espera este nome)
   - **Secret:** Cole o token copiado
   - Clique em "Add secret"

### Verificando a Configuração

1. **Teste o workflow:**
   - Crie uma issue de teste no repositório nvngroup/contabil
   - Verifique se a issue é criada automaticamente em brunocgc/contabil
   - Verifique se um comentário com o link é adicionado na issue original

2. **Em caso de erro:**
   - Vá para "Actions" no repositório
   - Clique no workflow "Enviar Issues para brunocgc/contabil" que falhou
   - Verifique os logs para identificar o problema
   - Erros comuns:
     - "Resource not accessible by integration" → PAT não configurado ou inválido
     - "Not Found" → Repositório de destino não existe ou sem permissão
     - "Bad credentials" → PAT expirado ou inválido

## 🔄 Manutenção do Token

### Renovação Periódica

Os PATs podem expirar. Quando isso acontecer:

1. Gere um novo token seguindo os passos acima
2. Atualize o secret `CONTABIL_PAT` com o novo valor
3. Não delete o secret anterior antes de adicionar o novo

### Rotação de Segurança

Recomenda-se rotar o PAT a cada 90 dias:

1. Gere um novo PAT
2. Atualize o secret
3. Revogue o PAT antigo em https://github.com/settings/tokens

## 📊 Monitoramento

### Verificar Execuções do Workflow

1. Acesse: https://github.com/nvngroup/contabil/actions
2. Filtre por workflow "Enviar Issues para brunocgc/contabil"
3. Verifique execuções recentes:
   - ✅ Verde = Sucesso
   - ❌ Vermelho = Falha (requer atenção)

### Logs e Debugging

Para investigar problemas:

1. Clique na execução do workflow
2. Clique no job "Replicar Issue para brunocgc/contabil"
3. Expanda o step "Criar issue no repositório brunocgc/contabil"
4. Analise os logs de console

## 🔒 Segurança

### Boas Práticas

1. **Princípio do Menor Privilégio:**
   - Use apenas os scopes necessários (`repo`)
   - Não adicione permissões extras

2. **Proteção do Token:**
   - Nunca compartilhe o PAT
   - Nunca comite o PAT no código
   - Use apenas Secrets do GitHub Actions

3. **Auditoria:**
   - Monitore o uso do token em: https://github.com/settings/tokens
   - Revogue tokens suspeitos imediatamente

4. **Usuário do Token:**
   - Idealmente, use um token de uma conta de serviço (bot account)
   - Se usar conta pessoal, documente quem é o responsável

## 🎯 Permissões Necessárias

### No Repositório Origem (nvngroup/contabil):

- Admin access para configurar secrets
- Workflow permissions habilitadas

### No Repositório Destino (brunocgc/contabil):

O usuário dono do PAT precisa de:
- Write access ou superior
- Issues: Write permission

## 📝 Troubleshooting

### Problema: Workflow não está executando

**Possíveis causas:**
- Workflows desabilitados no repositório
- Branch protection rules impedindo execução
- Arquivo de workflow com erro de sintaxe

**Solução:**
1. Verifique Settings → Actions → General → Actions permissions
2. Valide o YAML do workflow

### Problema: Issue não é criada no repositório privado

**Possíveis causas:**
- PAT não configurado
- PAT expirado
- Sem permissão no repositório de destino
- Repositório de destino não existe

**Solução:**
1. Verifique se o secret `CONTABIL_PAT` existe
2. Gere e configure um novo PAT
3. Verifique permissões no repositório brunocgc/contabil

### Problema: "Resource not accessible by integration"

**Causa:** GITHUB_TOKEN padrão sendo usado em vez do PAT

**Solução:**
1. Verifique que o workflow usa `${{ secrets.CONTABIL_PAT }}`
2. Configure o PAT seguindo as instruções acima

## 📞 Suporte

Para problemas com os workflows:

1. Verifique os logs em Actions
2. Consulte a documentação do GitHub Actions
3. Abra uma issue descrevendo o problema com logs anexados
