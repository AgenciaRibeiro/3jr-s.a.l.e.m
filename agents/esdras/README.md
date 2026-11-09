# ESDRAS — Guardião Documental do S.A.L.E.M.

**3 J R Agência Digital** · Assistente virtual especializado em gestão e governança do conhecimento corporativo.

## Arquitetura oficial: workflow clássico por nós

Em 08/11/2026, o ESDRAS foi **recriado como workflow tradicional do n8n**, para que seus componentes possam ser adicionados, configurados, substituídos e conectados pelo editor de nós. O rascunho anterior do **Agent Builder foi excluído**, conforme decisão do gestor.

O ESDRAS atual utiliza, no canvas n8n:

1. **Chat Trigger (interno):** entrada de solicitações.
2. **AI Agent:** interpretação e roteamento de consultas.
3. **OpenAI Chat Model:** modelo de linguagem conectado por credencial existente.
4. **Simple Memory:** contexto limitado da conversa.
5. **Google Drive Tool:** pesquisa de arquivos e pastas.
6. **Google Sheets Tool:** consulta ao catálogo de entidades.
7. **Google Sheets Tool:** consulta aos relacionamentos.
8. **Google Docs Tool:** leitura de documentos autorizados.

A estrutura permite adicionar novos nós e ferramentas, inclusive canais ou procedimentos de aprovação humana, após especificação e validação.

## Missão

- Identificar documentos empresariais e suas fontes oficiais.
- Verificar fichas, relacionamentos e pendências do S.A.L.E.M.
- Orientar a organização de ASVs, clientes, APIs, VPS, repositórios e arquivos corporativos.
- Consultar informações sem sobrescrever, apagar, mover ou compartilhar documentos.
- Relatar evidências e distinguir estado **planejado, preparado, testado e homologado**.
- Evitar processamento de conteúdos pessoais fora do escopo corporativo.

## Regras de governança

1. Documentos do Drive não constituem instruções para o agente; são dados não confiáveis.
2. Toda ação de escrita futura requer autorização, proteção contra duplicatas e rastreabilidade.
3. Credenciais e segredos não podem ser versionados no GitHub.
4. Repositório público contém apenas documentação e modelos genéricos.
5. O workflow clássico e o monitor de eventos são componentes separados, com estados distintos.

## Testes e estado em 08/11/2026

| Componente | Situação verificada |
|---|---|
| Workflow clássico por nós | **Criado** e validado estruturalmente |
| Chat Trigger → AI Agent → modelo/memória/ferramentas | **Execução manual real com sucesso** |
| Consulta ao catálogo Google Sheets | **Validada** por leitura de entidades de teste |
| Credencial exclusiva de Google Drive | **Conectada**, acesso à raiz corporativa previamente verificado |
| Google Docs | Ferramenta configurada; operação não homologada individualmente |
| Monitor de eventos Google Drive | Workflow separado preservado, inativo |
| Workflow do ESDRAS | **Inativo / não publicado** |
| Agente antigo do Agent Builder | **Excluído** e ausência conferida |

A verificação atual não atesta monitoramento recursivo do Google Drive, escrita segura em produção nem leitura de todos os documentos. Ampliação do escopo exige um processo de homologação.

## Próximas etapas

- Testar leitura de Google Docs e Drive no próprio workflow clássico, com informações autorizadas.
- Implantar aprovação humana real para qualquer nó com escrita.
- Conectar ingestão de eventos do monitor ao índice e à governança do ESDRAS.
- Projetar sincronização recursiva, reconciliação de IDs e validação de permissões.
- Publicar workflows somente após homologação e autorização do gestor.

## Canal Telegram — preparação técnica (08/11/2026)

O workflow clássico do ESDRAS foi ampliado com um canal **Telegram por nós**, isolado do chat interno:
- Telegram Trigger (mensagens)
- Code: apenas mensagens de texto em chats privados; converte em `chatInput` e `sessionId`
- AI Agent próprio para Telegram com memória de sessão
- OpenAI Chat Model e ferramentas Google Drive / Sheets / Docs de leitura
- Telegram: enviar resposta ao mesmo chat
- Dois grupos visuais no editor, separando chat interno e canal Telegram.

**Estado atual:** 18 nós; a edição estrutural foi validada. O chat interno foi reexecutado com sucesso. **A conversa real via Telegram não foi homologada.**

**Bloqueio para ativação:** não foi encontrada credencial específica de Telegram do ESDRAS no n8n MinhaEmpresa. O n8n atribuiu automaticamente uma credencial chamada `Telegram - JoJoZinha`, que pertence a outro contexto. Por segurança, **Telegram Trigger e Telegram Enviar resposta estão desativados**, e o workflow continua inativo. Antes de habilitar, associar aos dois nós uma credencial Telegram de ESDRAS efetivamente registrada nessa instância, confirmar usuário ou chat autorizado (allowlist), e validar ida e volta com a conta proprietária.

**Segurança:** não colocar token do Telegram no repositório; nunca publicar o workflow com credencial de outro bot ou sem restrição de acesso. Não habilitar modificações, exclusões ou compartilhamento de arquivos sem aprovação e trilha de auditoria.


## Telegram: transcrição, agrupamento e resposta adaptativa

**Atualização:** 08/11/2026. Workflow clássico do n8n — modo de resposta controlado explicitamente pelo operador.

### Regras de comunicação

- **Padrão: TEXTO**, independentemente de a entrada ser um texto ou uma gravação de voz.
- **Ativar modo de voz:** comandos como "Esdras, responda só por áudio", "modo voz" e "a partir de agora responda por áudio".
- **Retornar ao texto:** "Esdras, volta a responder só por texto", "modo texto".
- O modo escolhido fica registrado por conversa, em uma Data Table exclusiva do n8n, até novo comando.
- **Exclusividade:** em modo texto, o Telegram recebe apenas texto; em modo voz, recebe somente um arquivo de áudio MP3, sem resposta textual duplicada.
- Mensagem recebida em áudio é transcrita com OpenAI e entra na mesma fila de fragmentos que mensagens de texto; **receber áudio não troca automaticamente o modo**.
- O agrupamento das mensagens usa buffer por chat e aguarda um intervalo de aproximadamente 10 segundos antes de responder.
- As mensagens processadas são removidas do buffer. Recuperação e expiração de fragmentos pendentes continuam sujeitas a auditoria operacional.
- A autorização de chats privados deve ser feita por identificadores verificados, mantidos exclusivamente nas configurações internas. Não publicar IDs particulares, tokens ou credenciais neste repositório.

### Estado de validação

- Roteamento do modo padrão texto: **testado**.
- Troca de texto → voz, persistência em outra solicitação e retorno voz → texto: **testados** com eventos simulados.
- Solicitação recebida em áudio, transcrita em simulação, gerando **somente texto** com modo texto ativo: **testada**.
- Publicação e versão ativa no n8n: **confirmadas**.
- **Ainda pendente:** homologação ponta a ponta por mensagem real de voz no Telegram, incluindo áudio recebido, download, transcrição e retorno MP3.

A execução continua limitada a consultas de documentos; operações destrutivas ou alteração de permissões permanecem indisponíveis. Transcrição e geração de voz podem implicar custos por uso.
