# S.A.L.E.M. — Estado atual e ponto de retomada

**Última consolidação documental:** 2026-11-08 (Brasil).  
**Escopo:** estado conhecido a partir de implementações e verificações nesta iniciativa.  
**Atenção:** este documento é um instantâneo, **não um monitor ao vivo**. Na retomada, conferir os sistemas conectados antes de afirmar que permanecem ativos.

## Resumo executivo

O **S.A.L.E.M.** é a arquitetura do Cérebro Corporativo da 3 J R Agência Digital. Integra conceitualmente documentos do Google Drive, índices no Sheets, assistentes virtuais, workflows n8n, integrações, VPS e repositórios. O GitHub versiona a arquitetura e as decisões; não centraliza os dados privados de todos os sistemas.

### Situação geral

| Frente | Situação documentada | O que não presumir |
|---|---|---|
| Arquitetura de informação | Documentada nos arquivos `docs/` | Não é uma aplicação SaaS pronta |
| Estrutura Google Drive | Núcleos de pastas e workspace ASV criados em etapa anterior | Não implica ingestão ou indexação automática de toda a conta |
| Central de Controle Sheets | Cadastro de entidades, relacionamentos e aba de eventos preparados | Cadastro e registro de eventos não significam monitoramento completo |
| ESDRAS (ASV do Drive) | **Workflow clássico por nós do n8n publicado**, consulta e Telegram configurados | Nem todas as ferramentas Google foram homologadas ponta a ponta |
| Entrada Telegram | Identificação e tratamento de textos/áudios configurados; chat privado restrito | Não abrir acesso a chat desconhecido |
| Fragmentos de mensagem | Buffer nativo do n8n, espera de cerca de 10 segundos, agregação por conversa | Precisam de testes reais de concorrência e recuperação |
| Preferência de resposta | **Texto por padrão**; trocar para somente voz por comando; voltar para texto por comando; preferência persistente por chat | A entrada em áudio NÃO muda automaticamente o modo de saída |
| Leitura de áudio | Nós para download e transcrição configurados; rota testada com simulações | Áudio real ainda não homologado integralmente |
| Voz de saída | Nós OpenAI de síntese e Telegram de envio MP3 configurados; seleção de rota testada | Envio de MP3 real e reprodução ainda carecem de teste real |
| Monitor Drive | Workflow separado de detecção de criação preparado e mantido em rascunho/inativo no último exame | Não cobre recursivamente toda a árvore |
| Escrita no Drive | Limitada por regras de segurança | Não conceder autonomia para mover, editar, apagar ou compartilhar arquivos |

## ESDRAS: ponto exato de parada

**Arquitetura vigente:** workflow **clássico do n8n**, **não** o Agent Builder. O Agent Builder anterior do ESDRAS foi excluído a pedido do gestor.

**Última configuração verificada:**

- Workflow clássico com **41 nós**, versão publicada e ativa.
- Chat interno do n8n e canal Telegram no mesmo projeto, com nós editáveis.
- Telegram com credencial exclusiva para ESDRAS.
- Autorização limitada a conversa privada previamente validada (identificador particular **não publicado neste repositório**).
- Google Drive, Google Sheets e Google Docs conectados como ferramentas de leitura.
- Buffer de fragmentos na Data Table do n8n, com consolidação após espera aproximada de 10 segundos.
- Uma Data Table separada guarda `response_mode` por conversa; estados possíveis `text` e `audio`.
- **Comportamento desejado e testado em simulação:**
  - Texto recebido → texto respondido (padrão).
  - Áudio recebido → texto respondido (padrão).
  - Pedido explícito para responder só por áudio → persistir modo `audio` e responder **apenas por áudio**.
  - Pedido para voltar ao texto → persistir modo `text` e responder **apenas por texto**.
- Testes simulados de modo de voz, permanência do modo na solicitação seguinte, retorno ao texto e áudio entrante em modo texto foram bem-sucedidos.
- Estado registrado ao final desses testes: **modo texto**.
- Documentação do componente: [ESDRAS](../agents/esdras/README.md).

**IMPORTANTE:** a configuração foi verificada na ocasião descrita. Na retomada, conferir versão, credenciais por **nome** e execuções no n8n autorizado; não declarar homologação real de voz a partir de simulações.

## Pendências priorizadas

1. **P1 — Teste real de áudio do Telegram:** enviar voz pelo Telegram; conferir download, transcrição, resposta apenas em texto (padrão) e eventualmente resposta só em áudio após comando. Registrar evidências; controlar custos de IA.
2. **P1 — Testes reais de debounce:** enviar várias mensagens em poucos segundos e verificar uma única resposta com conteúdo agrupado, inclusive em situações de concorrência.
3. **P1 — Tratamento de erros:** transcrição indisponível, texto vazio, áudio acima do tamanho suportado, falhas no TTS, indisponibilidade do Sheets/Data Table e mensagens repetidas.
4. **P2 — Leitura Google Docs:** validar acesso real individualmente, em documento corporativo autorizado; conferir permissões.
5. **P2 — Monitor do Google Drive:** revisar escopo, testar event capture controlado, decidir estratégia recursiva, idempotência, reconciliação e trilha de auditoria antes de publicar.
6. **P2 — Integração entre catalogação documental e eventos monitorados:** projetar processo supervisionado, sem mover ou excluir documentos automaticamente.
7. **P3 — Painel e automações avançadas:** somente depois de requisitos, segurança e homologação.

## Fronteiras entre assistentes

- **ESDRAS:** gestão do conhecimento corporativo, catálogo, documentos Drive e relacionamentos.
- **ELEAZAR:** guardião de credenciais, acessos, integrações e seus segredos (projeto separado).

O ESDRAS pode utilizar credenciais **conectadas de forma segura** nos nós permitidos, mas **não** se torna administrador de chaves ou do cofre.

## Próxima ação concreta

**Não recriar o ESDRAS.** Conferir o workflow clássico já publicado, examinar execuções recentes e realizar os testes de voz/mensagens fragmentadas **com entradas reais e autorizadas**. Só depois expandir o controle documental do S.A.L.E.M.

## Política de segurança da retomada

Este repositório é **público** nesta consolidação. Não inserir URLs privadas, identificadores pessoais de usuários, IDs de chat, tokens, chaves, capturas com dados restritos, documentos de clientes, dumps ou logs de conversas. Usar nomes lógicos e consultar identificadores reais **dentro da plataforma conectada autorizada**.
