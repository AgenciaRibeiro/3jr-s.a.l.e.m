# Plano de execução S.A.L.E.M.

| Fase | Entrega | Critério de aceite | Situação documentada |
|---|---|---|---|
| 00 | Arquitetura v1.0 | Árvore e princípios documentados | Documentado |
| 01 | Estrutura Google Drive | Núcleos e áreas padronizados e conferidos | Estrutura inicial criada; validar estado e abrangência na fonte oficial |
| 02 | Inventário e Central de Controle | Fontes, duplicatas, relacionamentos e pendências registrados | Trabalho parcial; conciliação e validação pendentes |
| 03 | Conciliação de cadastros | IDs estáveis, responsáveis e fontes oficiais reconciliados | Pendente |
| 04 | Segurança | Política de acesso, cofre, classificação e validações | Política documentada; auditoria operacional pendente |
| 05 | Integrações | Drive, Sheets, GitHub, n8n e outras APIs conectados com testes | Parcial; verificar cada conexão na plataforma |
| 06 | Painel | Pesquisa, fichas e visualização dos relacionamentos | Planejado |
| 07 | Auditoria e homologação | Testes de integridade, autorização e recuperação | Em andamento por componente |

## Frente prioritária: ESDRAS

1. Homologar entrada e transcrição de áudio real no Telegram.
2. Homologar saída MP3 real quando o gestor ativar modo de voz.
3. Testar fragmentação, concorrência, duplicidade e recuperação de mensagens.
4. Testar individualmente Google Drive e Google Docs em leitura autorizada.
5. Auditar monitor de eventos do Drive, recursividade, idempotência e reconciliação.
6. Integrar eventos ao índice somente após aprovação e testes de segurança.

O ponto de parada e as evidências estão em [ESTADO_ATUAL.md](ESTADO_ATUAL.md); o histórico está em [REGISTRO_DE_MISSOES.md](REGISTRO_DE_MISSOES.md).

## Próxima ação recomendada

Não recriar componentes existentes. Conferir o workflow clássico do ESDRAS na instância n8n, realizar testes ponta a ponta autorizados de voz e fragmentação, registrar evidências e então continuar a conciliação dos índices corporativos.

## Limites

O repositório contém documentação e modelos. Não há backend, frontend ou painel implantado por estes commits. A existência de um workflow documentado não substitui a conferência de seu estado real na plataforma n8n.

## Governança

- Uma etapa por vez com critérios de aceite.
- Não alterar produção sem autorização e plano de rollback.
- Não tratar **implementado** como **homologado**.
- Ao concluir missão relevante, atualizar estado, registro cronológico, documentação do componente e próximo passo.
