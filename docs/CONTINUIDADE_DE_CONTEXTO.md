# Protocolo de retomada de contexto — S.A.L.E.M.

## Objetivo

Garantir continuidade entre conversas, assistentes e IDEs, sem o gestor precisar recontar o histórico inteiro. A frase **"Acesse este repositório e vamos continuar"** é suficiente para **solicitar a leitura**, desde que a nova conversa disponha de acesso ao GitHub.

> Um link isolado não transmite automaticamente conteúdo a qualquer chat. O assistente precisa realmente abrir e ler os arquivos, com as ferramentas/permissões disponíveis. Este protocolo descreve o que ele deve fazer **após acessar** o repositório.

## Ordem de leitura e verificação

```text
AGENTS.md (regra fundamental)
    ↓
README.md (visão geral e mapa)
    ↓
docs/CONTINUIDADE_DE_CONTEXTO.md (protocolo)
    ↓
docs/ESTADO_ATUAL.md (ponto exato de parada)
    ↓
docs/REGISTRO_DE_MISSOES.md (linha do tempo)
    ↓
docs/PLANO_DE_EXECUCAO.md (roadmap)
    ↓
agents/**, docs/**, docs/decisoes/**, schemas/** e arquivos adicionados
    ↓
Conferência das fontes operacionais autorizadas
    ↓
Resumo objetivo + continuidade da missão
```

**Não pular a inspeção dos novos arquivos**: este índice é orientador e pode ficar incompleto quando outras pastas forem adicionadas.

## O resumo de retomada precisa responder

1. **O que é o projeto?** S.A.L.E.M. = Sistema de Arquitetura, Ligações, Estratégia e Memória da 3 J R Agência Digital.
2. **Quais sistemas compõem o projeto?** Drive, planilhas de controle, GitHub, n8n, serviços e ASVs catalogados.
3. **O que já foi implantado e testado?** Somente aquilo que evidências recentes confirmam.
4. **O que ainda é simulação, proposta, rascunho ou pendência?**
5. **Qual foi a última alteração verificada?** Conferir o estado atual e os commits recentes.
6. **Qual é o próximo passo coerente?** Seguir o roadmap e a solicitação atual, sem reabrir decisões fechadas.
7. **Existe risco operacional ou necessidade de autorização?** Expor antes da ação.

## Governança de documentação

Cada missão deve produzir uma *trilha de continuidade* com:

| Campo | Descrição |
|---|---|
| Data e referência | Data/hora com fuso, nome da missão e executor |
| Objetivo | Por que foi executada |
| Artefatos | Documentos, workflows e sistemas envolvidos |
| Mudanças | O que efetivamente foi alterado |
| Evidências | Testes, resultados, versões e commits verificáveis |
| Estado | Planejado, configurado, simulado, testado real, publicado ou homologado |
| Pendências | Bugs, riscos, limitações e validações faltantes |
| Próxima ação | Passo específico para a continuidade |
| Autorização | O que foi permitido e quais ações permanecem restritas |

**Padrão recomendado:** documentação curta e objetiva; não armazenar conversa bruta, segredos, dados particulares ou conteúdos corporativos restritos no GitHub público.

## Texto reutilizável para iniciar uma nova conversa

```text
Acesse este repositório da 3 J R: https://github.com/AgenciaRibeiro/3jr-s.a.l.e.m

Vamos dar continuidade ao projeto. Antes de fazer qualquer alteração,
siga a REGRA 001 do arquivo AGENTS.md: leia o repositório, o estado atual,
o histórico de missões, os componentes e as pendências. Confirme onde o
projeto parou e prossiga a partir das decisões já registradas.
Não recomece do zero e não faça deploy ou alterações operacionais
não autorizadas.
```

## Fluxo quando o repositório estiver inacessível

- Informar **qual arquivo ou recurso** falhou.
- Utilizar o que estiver disponível, identificando lacunas.
- Solicitar acesso ou o arquivo de continuidade, **somente quando indispensável**.
- Nunca responder como se o projeto inteiro tivesse sido lido quando isso não ocorreu.
