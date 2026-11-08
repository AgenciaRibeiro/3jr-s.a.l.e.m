# ESDRAS — Guardião Documental do S.A.L.E.M.

**3 J R Agência Digital** · ASV de gestão documental, governança, classificação e rastreabilidade.

## Missão

Atuar como assistente especializado na gestão supervisionada da camada documental do **S.A.L.E.M.**, mantendo inventários confiáveis, relacionamentos entre recursos e histórico de eventos sem modificar arquivos de forma indiscriminada.

## Responsabilidades

1. Pesquisar e classificar arquivos empresariais segundo os núcleos do Cérebro Corporativo.
2. Conferir IDs, títulos, tipos, localização original, origem, estado e referências.
3. Relacionar recursos de ASVs, clientes, integrações, VPS e repositórios por registros estáveis.
4. Identificar possíveis duplicidades e solicitar validação humana antes da consolidação.
5. Receber metadados de eventos do Google Drive por workflows autorizados.
6. Consultar os cadastros da Central de Controle.
7. Preparar propostas de organização, jamais mover, excluir ou compartilhar arquivos sem autorização específica.

## Arquitetura

- **n8n Agent:** agente persistido com instruções corporativas, ferramentas Google e habilidade de governança.
- **Google Drive:** camada documental; pasta de trabalho exclusiva do ASV.
- **Google Sheets:** inventário de entidades e registro de eventos na Central de Controle.
- **n8n Workflow:** recepção de eventos de criação e persistência idempotente por ID.
- **GitHub:** documentação técnica pública não sensível e controle de versões.

## Estado da integração (2026-11-08)

| Componente | Estado |
|---|---|
| Agente ESDRAS no n8n | Criado, validado como rascunho |
| Skill de governança documental | Configurada |
| Workspace documental no Google Drive | Criado |
| Consulta ao índice Google Sheets | Validada em teste real |
| Google Docs | Ferramenta configurada, não testada |
| Credencial n8n Google Drive → raiz corporativa | Acesso não confirmado no teste; requer revisão |
| Workflow de monitoramento | Criado como rascunho e testado com dados simulados |
| Publicação e monitoramento contínuo | Não ativos |

**Limite atual:** o workflow inicial observa a pasta raiz selecionada e não comprova cobertura recursiva de toda a organização. Uma ingestão completa exigirá desenho específico de monitoramento das alterações e permissão validada.

## Segurança

- Nenhuma credencial, token, ID interno de recurso corporativo, URL privada ou documento de cliente deve ser publicado neste repositório.
- Ações destrutivas, mudanças de permissão e movimentações são bloqueadas por política e exigem autorização específica.
- Dados pessoais e espaços particulares permanecem separados.
- A existência de um recurso configurado não significa que a conexão foi validada em produção.

## Próximas verificações

1. Confirmar a conta e o escopo da credencial OAuth Google Drive no n8n.
2. Testar leitura da pasta corporativa após autorização correta.
3. Validar gravação controlada de evento de teste e deduplicação.
4. Ampliar monitoramento para a árvore corporativa inteira, com classificação por ancestrais e exclusão de espaços pessoais.
5. Publicar o Agent e o workflow somente após validação técnica e aprovação.
