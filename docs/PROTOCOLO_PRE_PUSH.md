# REGRA 002 — Auditoria obrigatória antes de commit, push ou publicação no GitHub

**Aplica-se a todo envio de alterações feito por IDEs e ASVs no S.A.L.E.M.** Pode ser reutilizada em outros projetos da 3 J R ao adicionar a regra ao `AGENTS.md` de cada repositório. A ordem é: **inspecionar → corrigir → testar → confirmar destino → publicar → verificar**.

> Quando o gestor disser simplesmente **"Suba para o GitHub"**, **"Atualize o repositório"**, **"Faça commit e push"**, ou equivalente, a IDE deve executar o protocolo abaixo automaticamente. Não é necessário que o gestor memorize comandos técnicos.

## 1. Pré-voo de Git e destino

1. Identificar o diretório do projeto, repositório correto e URL do `origin`; conferir se há autorização para alterar esse destino.
2. Inspecionar `git status`, arquivos modificados, staged, untracked, removidos e conflitos; selecionar somente alterações legítimas da missão.
3. Conferir `git branch`, branch atual, branch padrão do remoto e existência de `main`. **Não criar nem substituir `main` cegamente**; se a branch padrão não for `main`, esclarecer a divergência.
4. Consultar remoto com `git fetch` (sem alterar o working tree) e verificar se há commits locais/remotos divergentes, merge ou rebase pendente.
5. Não sobrescrever commits alheios, não fazer `push --force`, não alterar `origin` e não remover mudanças do usuário por conta própria. Reconciliar conflitos de modo supervisionado.
6. Se o projeto usa PR, proteção de branch ou checks obrigatórios, respeitar o fluxo de PR e não fazer push direto na `main` sem permissão.

## 2. Segurança e proteção de informações

1. Verificar o `.gitignore` efetivo, arquivos rastreados e arquivos prestes a entrar no commit. **`.gitignore` NÃO protege arquivos já versionados**.
2. Inspecionar o diff de staged e os arquivos novos contra senhas, tokens, API keys, arquivos `.env` reais, credenciais JSON, chaves privadas, certificados, cookies, sessões, backups, dumps de banco, logs e dados pessoais/confidenciais.
3. Procurar segredos no histórico de commits **que serão enviados ao remoto**, não só no diff atual. Se um segredo foi incluído em commit anterior, tratar como incidente e evitar o push até corrigir e rotacionar a credencial afetada.
4. Executar detector automático de segredos (por exemplo, Gitleaks ou equivalente) **quando instalado e configurado**. Complementar com revisão humana/lógica; resultado limpo não garante ausência de credenciais.
5. Conferir links e endpoints expostos, configurações de produção, dados de clientes, identificadores privados, comentários de debug e arquivos de configuração que não devem ser públicos.
6. Revisar dependências, bibliotecas e alertas de vulnerabilidade por ferramentas compatíveis com a stack (`npm audit`, `pip-audit`, `cargo audit` ou equivalentes, se disponíveis). Avaliar severidade; não aplicar atualizações quebrando o projeto automaticamente.
7. Não enviar pastas como `node_modules/`, caches, arquivos temporários, binários gerados, `dist/`, bancos locais ou arquivos grandes indevidos — exceto artefatos intencionalmente versionados e justificados.

**Bloqueio absoluto:** não efetuar push se segredos reais ou dados sensíveis indevidos estiverem incluídos no conteúdo enviado, mesmo se o gestor pedir para ignorar testes. Corrigir e proteger antes.

## 3. Qualidade técnica conforme a stack

Identificar a tecnologia e os scripts reais no projeto. **Não executar comandos aleatórios, nem criar resultados de testes fictícios.**

- Conferir sintaxe, configuração, lockfile, versões, imports, tipos e referências quebradas.
- Executar formatação/check, lint e análise estática quando suportados.
- Executar testes unitários, integração, API e fluxos críticos existentes na medida em que forem executáveis sem afetar produção.
- Validar TypeScript/`typecheck` quando aplicável; compilar/`build` e verificar se o build termina com **código de saída 0**.
- Para frontend: verificar rotas, assets, imports, variáveis de ambiente esperadas e erros básicos de inicialização.
- Para backend: validar configuração de API, schema/migrations, contratos e inicialização segura — sem migrar dados reais sem autorização.
- Para infraestrutura/n8n: validar sintaxe de configurações/manifests e consistência de nós/conexões, sem ativar fluxos ou deploy.
- Para repositório **somente documental**: conferir links relativos, referências de caminhos, nomenclatura, Markdown, datas e coerência dos estados; testes de aplicativo devem ser marcados **não aplicáveis**, não "aprovados".
- Para alteração relevante, conferir README, changelog/relatório, `AGENTS.md`, `docs/ESTADO_ATUAL.md` e documentação relacionada.

Quando houver falha, **corrigir e repetir** o teste impactado antes de enviar.

## 4. Revisão do commit e autorização

1. Revisar diff final: não apagar arquivos, alterar escopo, inserir dependências ou refatorar partes não solicitadas sem justificativa/autorização.
2. Checar erros de whitespace, arquivos corrompidos, conflitos (`<<<<<<<`, `=======`, `>>>>>>>`), artefatos e metadados indesejados.
3. Criar commit objetivo somente com arquivos revisados; não usar `git add .` de forma cega.
4. Se houve falha de teste **não crítica**, indisponibilidade de serviço ou verificação não executável, explicar o impedimento e aguardar decisão do gestor antes de publicar. Falhas de segurança não podem ser liberadas.
5. Fazer o push **somente** se a solicitação atual autorizar o envio e o pré-voo estiver aprovado. Não confundir autorização para commit com autorização para deploy.

## 5. Pós-envio obrigatório

1. Confirmar que o push realmente concluiu e que o commit/branch estão presentes no repositório remoto correto.
2. Conferir checks do GitHub Actions/CI e PR quando existirem; se ainda estiverem em execução, registrar **pendente**, nunca **aprovado**.
3. Registrar SHA ou link do commit, branch, verificações executadas, resultado e itens não aplicáveis/pendentes no histórico da missão sem segredos.
4. Se houver erro pós-envio, informar e propor correção; não fazer force-push, rollback ou deploy unilateral.
5. Atualizar registros de continuidade conforme a **REGRA 001**.

## Semáforo de envio

| Condição | Ação |
|---|---|
| Checks aplicáveis aprovados, diff revisado, destino correto, autorização concedida | **APTO PARA PUSH** |
| Testes falharam, branch divergiu, conflitos, escopo duvidoso, CI pendente com proteção obrigatória | **BLOQUEADO / EXIGE CORREÇÃO OU DECISÃO** |
| Segredo ou dado sensível indevido detectado | **BLOQUEADO POR SEGURANÇA** |
| Teste não aplicável ao tipo de projeto | **NÃO APLICÁVEL**, com justificativa — não é falha |

### Resposta esperada da IDE ao gestor

Ser curta, por exemplo:

- **Antes do envio:** `✅ Pré-push aprovado: Git, segurança, testes e build verificados. Enviando para a branch autorizada.`
- **Após o envio:** `✅ Publicado no GitHub. Branch: ... | Commit: ... | Testes: ...`
- **Se falhar:** `⛔ Push bloqueado: [motivo objetivo]. Próxima correção: ...`

**Importante:** esta regra é uma política operacional para a IDE/agente que lê o repositório. Ela não instala automaticamente um hook local nem transforma o GitHub em um bloqueio técnico. Para proteção automatizada adicional, configurar `pre-commit`/`pre-push`, scanners e checks obrigatórios de branch em cada projeto e validar seu funcionamento. Mesmo com tudo aprovado, não existe garantia absoluta de ausência de defeitos.
