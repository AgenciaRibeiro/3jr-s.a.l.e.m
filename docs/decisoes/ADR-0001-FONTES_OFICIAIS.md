# ADR-0001 — Fontes oficiais e arquitetura híbrida

**Data:** 2026-11-08  
**Estado:** Proposta inicial documentada.

## Contexto

A agência usa várias ferramentas para documentos, código, automações, APIs e hospedagem. Copiar tudo para um único sistema produziria desatualização e riscos de segurança.

## Decisão proposta

- Google Drive é a camada documental e de conhecimento.
- GitHub é a camada de código, versionamento e revisão técnica.
- n8n integra eventos e serviços somente após autorização e validação.
- Bancos apropriados guardam dados operacionais estruturados.
- Cofres próprios guardam os valores reais de segredos.
- A Central de Controle é um índice de entidades e relacionamentos, não uma cópia de todas as bases.

## Consequências

**Positivas:** rastreabilidade, manutenção modular, evolução e redução de duplicação.  
**Riscos:** referências quebradas, inconsistências entre sistemas e permissões incorretas.  
**Mitigação:** IDs estáveis, auditoria, idempotência, testes, aprovação e recuperação.

A documentação deste ADR não configura qualquer integração real.
