# S.A.L.E.M. — 3 J R Agência Digital

**Sistema de Arquitetura, Ligações, Estratégia e Memória**

> Governança, conhecimento e rastreabilidade para uma agência digital orientada por automações e assistentes virtuais.

## Objetivo

O S.A.L.E.M. é a arquitetura do **Cérebro Corporativo 3 J R**. Seu propósito é organizar os registros empresariais e conectar informações sobre assistentes virtuais (ASVs), clientes, integrações, infraestrutura e repositórios, sem duplicar as fontes oficiais de cada sistema.

**Status:** fundação documental inicial. Não é um aplicativo implantado, uma integração ativa ou um banco de dados operacional.

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
4. **Governança por evidências:** distinguir planejado, preparado, implementado e homologado.
5. **Migração controlada:** não mover ou excluir documentos legados sem inventário, validação das dependências e autorização.

## Documentação

- [Arquitetura mestra v1.0](docs/ARQUITETURA_MESTRA_V1.md)
- [Regras de governança e segurança](docs/GOVERNANCA_E_SEGURANCA.md)
- [Modelo de entidades e relacionamentos](docs/MODELO_DE_DADOS.md)
- [Plano de execução](docs/PLANO_DE_EXECUCAO.md)
- [Registro de decisão arquitetural](docs/decisoes/ADR-0001-FONTES_OFICIAIS.md)
- [Schemas de referência](schemas/)

## Estado de implantação

A criação de pastas e planilhas no Google Drive pode existir independentemente deste repositório; **nenhuma conexão automática está implementada aqui**. Não presumir que servidores, APIs, fluxos ou aplicações estejam integrados só porque aparecem na documentação.

---

**3 J R Agência Digital** · *Pense. Transforme. Evolua.*
