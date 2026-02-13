# Política de Segurança

Esta política descreve como mantemos a segurança do projeto Contabil e como você pode reportar vulnerabilidades.

## 🛡️ Versões Suportadas

Atualmente, oferecemos suporte de segurança apenas para a versão estável mais recente (main branch) e versões de release identificadas.

| Versão            | Status           |
| :---------------- | :--------------- |
| **Latest Stable** | ✅ Suportado     |
| **Dev Branch**    | ⚠️ Experimental  |
| < 0.11.0           | ❌ Não suportado |

## 🚨 Como Reportar uma Vulnerabilidade

Levamos a segurança a sério. Se você descobrir uma vulnerabilidade de segurança, por favor, **NÃO** abra uma Issue pública imediatamente.

### Processo de Report

1. **Envie um e-mail** para os mantenedores (consulte o perfil do GitHub do proprietário ou use o e-mail de contato do projeto).
2. **Inclua detalhes**:
   - Tipo de vulnerabilidade (ex: XSS, SQL Injection, RLS Bypass).
   - Passos para reproduzir.
   - Impacto potencial.
3. **Aguarde a confirmação**: Tentaremos responder em até 48 horas.

Faremos o possível para corrigir a vulnerabilidade rapidamente e coordenar a divulgação pública.

## 🔐 Medidas de Segurança Implementadas

O projeto utiliza diversas camadas de segurança para proteger dados e usuários:

### 1. Autenticação e Autorização

- **Supabase Auth**: Gerenciamento robusto de sessões e usuários via JWT.
- **Row Level Security (RLS)**: Isolamento estrito de dados no banco de dados PostgreSQL.
  - Cada requisição é autenticada e o acesso aos dados é restrito pelo `user_id` e `tenant_id`.
  - Políticas de "Deny by Default".

### 2. Segurança de API e Rotas

- **Middleware**: Proteção de rotas no Next.js (`middleware.ts`).
- **Validação de Dados**: Uso intensivo de **Zod** para validar todas as entradas de API, prevenindo injeção de dados maliciosos.
- **Server Actions**: Execução segura no servidor, sem expor lógica sensível ao cliente.

### 3. Cabeçalhos HTTP (Security Headers)

Configurados no `next.config.js` para mitigar ataques comuns:

- **Strict-Transport-Security (HSTS)**: Força HTTPS.
- **X-Frame-Options**: `SAMEORIGIN` (previne Clickjacking).
- **X-Content-Type-Options**: `nosniff` (previne MIME Sniffing).
- **X-XSS-Protection**: `1; mode=block` (proteção contra XSS).
- **Referrer-Policy**: `origin-when-cross-origin`.

### 4. Proteção de Dados

- **Criptografia**: Dados sensíveis criptografados em repouso (Supabase) e em trânsito (HTTPS/TLS).
- **Variáveis de Ambiente**: Segredos gerenciados via `.env.local` e nunca commitados no repositório.

## 🛠️ Diretrizes para Desenvolvimento Seguro

Ao contribuir com código, siga estas práticas:

- **Nunca commite chaves de API ou segredos**.
- **Use parâmetros em queries SQL** (ou deixe o ORM/Supabase client lidar com isso) para evitar SQL Injection.
- **Valide todos os inputs** usando os schemas Zod já definidos.
- **Sanitize outputs** no frontend (React já faz isso por padrão para XSS, mas tenha cuidado com `dangerouslySetInnerHTML`).
- **Mantenha dependências atualizadas**: Execute `pnpm audit` regularmente.

## 📄 License

Este projeto é licenciado sob a licença MIT. Consulte o arquivo `LICENSE` para mais detalhes.
