# Governança e segurança

## Classificação

- **Público:** conceitos arquiteturais gerais, documentação não sensível e modelos de exemplo.
- **Interno:** procedimentos, inventários e informações operacionais sem exposição pública.
- **Restrito:** dados de clientes, contratos, dados pessoais, topologia e detalhes técnicos sensíveis.
- **Segredo:** tokens, chaves de API, credenciais, certificados privados, senhas e material de autenticação — **jamais versionar**.

## Regras operacionais

1. Nunca publicar tokens, segredos, logs com dados pessoais, backups reais ou exportações completas de clientes no GitHub.
2. Não copiar automaticamente documentos corporativos do Drive para este repositório.
3. Manter IDs internos e referências sensíveis somente no ambiente apropriado.
4. Conceder menor privilégio a pessoas, ASVs e integrações.
5. Separar ambientes de desenvolvimento, teste e produção.
6. Registrar responsável, data, evidência e justificativa de alterações significativas.
7. Não executar migrações, exclusões, compartilhamentos ou deploy sem autorização específica.
8. Antes de consolidar duplicatas, conferir conteúdo, versão, proprietário, dependências e links existentes.
9. Manter informações pessoais de assistentes privados separadas do acervo corporativo.
10. Exigir critérios de aceite e evidência para declarar recurso **homologado**.

## Ciclo de vida

`PROPOSTO → PLANEJADO → EM_EXECUCAO → IMPLEMENTADO → EM_VALIDACAO → HOMOLOGADO`.

Estados especiais: `BLOQUEADO`, `ARQUIVADO`, `DESATIVADO`.

**Aviso:** a existência de uma pasta, modelo, planilha ou referência não implica que o recurso esteja implantado ou ativo.

## Responsabilidades

- GitHub: código-fonte, documentação arquitetural pública e histórico de mudanças.
- Google Drive: documentação corporativa e evidências com acessos apropriados.
- n8n: fluxos operacionais, sujeitos a auditoria e controle de mudanças.
- Cofre de segredos: armazenamento dos valores de credenciais.
- Infraestrutura: execução de workloads, armazenamento operacional e backups supervisionados.

## Política de contribuições

Revisar alterações via branch e pull request quando houver impacto técnico; verificar segredos antes de publicar; usar decisões de arquitetura (ADRs) para escolhas estruturais.


## Verificação de segurança pré-push

Antes de publicar qualquer alteração, obedecer à **REGRA 002**, definida em [PROTOCOLO_PRE_PUSH.md](PROTOCOLO_PRE_PUSH.md): inspeção de diff e histórico, `.gitignore`, credenciais, segredos, dados sensíveis, testes aplicáveis, branch e verificações após o push. Ocorrências de segredo real bloqueiam publicação e exigem proteção/rotação conforme o risco. Uma política textual não substitui hooks e verificações automatizadas de CI.
