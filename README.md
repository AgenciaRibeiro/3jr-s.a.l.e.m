# S.A.L.E.M. — 3 J R Agência Digital

**Sistema de Arquitetura, Ligações, Estratégia e Memória**

> Governança, conhecimento e rastreabilidade para uma agência digital orientada por automações e assistentes virtuais.

## 🚨 Regra obrigatória para novas conversas

**Antes de qualquer trabalho, leia `AGENTS.md` e siga a REGRA 001 — CONTINUIDADE OBRIGATÓRIA.** Leia o estado atual, o registro de missões, o plano de execução e os componentes relevantes. Não recomece do zero nem peça ao gestor para repetir informações já documentadas.

- [Regra 001 — AGENTS.md](AGENTS.md)
- [Protocolo de retomada](docs/CONTINUIDADE_DE_CONTEXTO.md)
- [Estado atual e ponto de parada](docs/ESTADO_ATUAL.md)
- [Registro cronológico de missões](docs/REGISTRO_DE_MISSOES.md)

**Para iniciar uma nova conversa, basta enviar o link do repositório e dizer:** "Acesse o repositório e vamos continuar". O assistente deve efetivamente abrir e ler os arquivos acima; o link sozinho não transfere o histórico nem concede acesso automático.

## Objetivo

O S.A.L.E.M. é a arquitetura do **Cérebro Corporativo 3 J R**. Seu propósito é organizar os registros empresariais e conectar informações sobre assistentes virtuais (ASVs), clientes, integrações, infraestrutura e repositórios, sem duplicar as fontes oficiais de cada sistema.

**Status:** arquitetura e governança documentadas; componentes operacionais são mantidos em suas plataformas próprias. Consulte o [estado atual](docs/ESTADO_ATUAL.md) antes de presumir qualquer implantação.

## Núcleos

| Código | Núcleo | Responsabilidade |
|---|---|---|
| 00 | Central de Controle | Índices, rastreabilidade, auditoria e governança |
| 01 | Workspace 3JR | Setores internos, clientes, projetos e conteúdos |
| 02 | Workspace ASV | Identidade, documentação, memória e evolução de agentes |
| 03 | Workspace Conexões e APIs | Catálogo de integrações, provedores e dependências |
| 04 | Workspace VPS | Inventário de servidores, ambientes e aplicações |
| 05 | Workspace GitHub | Repositórios, experimentos, componentes e licenças |

## Princípios

1. **Fonte única por domínio:** código no GitHub; documentação corporativa no Drive; workflows no n8n; bancos e serviços nas suas plataformas.
2. **Relacionamento por identificadores e referências:** um recurso pode ser utilizado em vários sistemas sem ser copiado.
3. **Segurança desde o início:** sem senhas, tokens, chaves, dados pessoais ou dados de clientes no repositório.
4. **Governança por evidências:** distinguir planejado, preparado, implementado, testado e homologado.
5. **Migração controlada:** não mover ou excluir documentos legados sem inventário, validação das dependências e autorização.
6. **Continuidade obrigatória:** toda missão relevante atualiza estado, histórico, evidências e próxima ação.

## Documentação

- [Arquitetura mestra v1.0](docs/ARQUITETURA_MESTRA_V1.md)
- [Regras de governança e segurança](docs/GOVERNANCA_E_SEGURANCA.md)
- [Modelo de entidades e relacionamentos](docs/MODELO_DE_DADOS.md)
- [Plano de execução](docs/PLANO_DE_EXECUCAO.md)
- [Registro de decisão arquitetural](docs/decisoes/ADR-0001-FONTES_OFICIAIS.md)
- [Schemas de referência](schemas/)
- [Documentação do ESDRAS](agents/esdras/README.md)

## Fontes oficiais e implantação

GitHub mantém código, arquitetura e histórico. Google Drive mantém documentos corporativos sob permissões apropriadas. Sheets mantém índices. n8n mantém workflows e estado de execução. Cofres próprios guardam credenciais. **O conteúdo deste repositório não garante que serviços externos permaneçam ativos:** conferir as fontes oficiais na retomada.

---

**3 J R Agência Digital** · *Pense. Transforme. Evolua.*
