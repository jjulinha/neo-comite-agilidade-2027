# Modelo · Contrato de Integração · kit-dev v2 · 17/11/2026 · proposta **[ALÉM DA FONTE — decisão do usuário]**

**Tipo (Diátaxis):** referência. Ficha que se consulta para saber um fato exato sobre uma contraparte. Não explica decisão (isso é ADR) nem ensina a operar (isso é RUNBOOK). Por que existe: há 26 parceiros externos listados em `insumos/sistemas-e-tecnologias.md` §4 (Jira de 16/11/2026), e o PRD do kit v1 (seção 9, Integrações) só tinha uma linha por integração. No PRD v2, a seção 13 (Integrações) aponta para esta ficha.

**Quando usar.** Gatilho de risco do kit, em qualquer tamanho, inclusive PP: integração nova ou alterada por API, SFTP ou fila, com parceiro externo ou entre sistemas (Konsig ↔ NeoKonsig). Um arquivo por contraparte e por sistema Neo, em `docs/integracoes/<parceiro>.md` do repositório do sistema dono; se houver lugar comum aos dois sistemas, use `<parceiro>-<sistema>.md`. A mesma contraparte em dois sistemas gera duas fichas. Enquanto o repositório do Konsig que recebe docs/ estiver [A CONFIRMAR] (DS-175/DS-495), use a pasta provisória definida no README do kit. Se houver rotina agendada ou falha conhecida, abra também um RUNBOOK.md e ligue os dois.

**Quando não usar.** Para registrar por que se escolheu o parceiro ou o protocolo (ADR); para o passo a passo de reprocessar (RUNBOOK); para a visão geral dos parceiros (diagrama C4 nível 1 em SISTEMA.md, que aponta para cada ficha). O catálogo é a pasta de fichas, e o SISTEMA.md só aponta para ela. Os 26 parceiros de `insumos/sistemas-e-tecnologias.md` §4 (Jira de 16/11/2026) não são todos integração sistêmica: Slack e Compupack não se aplicam, e a Mastercard não tem integração direta (chega pela Orbitall).

**Regra.** Campo sem resposta fica `[A CONFIRMAR]` com o card que vai responder; nunca apague o campo. Quem muda a integração atualiza a ficha no mesmo PR.

**Por que não Pact com terceiros.** A página "What is Pact good for?" do Pact desaconselha teste de contrato contra API de terceiro: o provedor precisa rodar a verificação do lado dele, e bancos, bureaus e processadora não rodam. Para esses, exemplos guardados mais teste de fumaça em homologação a cada mudança **[ALÉM DA FONTE — decisão do usuário]**.

## Cópia em branco

```markdown
# Integração · <parceiro ou fila> · <sistema Neo>

| Campo | Valor |
|---|---|
| Finalidade | <uma frase: o que a Neo obtém ou entrega> |
| Sistema Neo (um só) | Konsig · NeoKonsig · outro (nome) [A CONFIRMAR no Inventário de Sistemas] |
| Dono do dado e SSOT | <quem é a fonte única de verdade de cada dado trocado> |
| Protocolo | API REST · SFTP · fila (RabbitMQ) · outro |
| Autenticação | <tipo> · certificado <nome> · vence em dd/mm/aaaa · renovação: card <chave> |
| Ambientes | dev: mock/real · homolog: mock/real · produção: real |
| Contrato | OpenAPI 3.1 / AsyncAPI 3.0.0 em `<caminho>` · senão manual do parceiro v<x>, de dd/mm/aaaa |
| Leiaute de arquivo | <nome> v<x> · campos e tipos em `<caminho>` |
| Horários e janelas | <envio, recebimento, janela de manutenção do parceiro> |
| Timeout e SLA esperado | timeout <n> s · SLA do parceiro <n> · o que o fluxo faz ao estourar |
| Idempotência e reenvio | <chave de idempotência> · nº de tentativas · intervalo · quem reenvia |
| Contingência | <fornecedor alternativo ou modo manual> · critério de troca (ADR-n) |
| Dado pessoal | sim/não · quais campos · CHECKLIST-DADOS-E-REGULACAO.md no PR <link> |
| Contato por papel | suporte do parceiro · dono técnico na Neo (papel) · gestor do contrato (papel) |
| Runbooks ligados | `docs/runbooks/<arquivo>.md` |

## Erros conhecidos e tratamento
| Código ou sintoma | Causa | Tratamento | Card de origem |
|---|---|---|---|

## Aviso de mudança pelo fornecedor
Canal pelo qual o parceiro avisa. Se não avisar: sintoma esperado, quem abre o Expedite, quem fala com o parceiro.

## Exemplos de requisição e resposta
Só massa sintética. Sem CPF, CNPJ, nome, e-mail, telefone ou token reais. Dado de cartão (PAN/CVV) nunca entra.

## Teste de fumaça em homologação
Passos e resultado esperado. Rodar a cada mudança nossa ou do parceiro; registrar data e resultado no PR.
```

## Orientações por campo, com casos reais

Fonte dos casos: `downstream_16-11.csv` (Jira de 16/11/2026, 10h26), salvo indicação.

- **Autenticação e certificado.** Escreva a data de vencimento: hoje a renovação de certificado vira card reativo (DS-237, DS-283, DS-444), e o DS-295, que organiza calendário e procedimentos, está pausado ('temos atuado de forma reativa', downstream_16-11.csv, 16/11/2026 10h26).
- **Aviso de mudança.** JUDIT, DS-272: 401 depois de uma atualização de segurança do fornecedor, sem aviso, tratada como Expedite. A ficha diz quem percebe e o que fazer.
- **Idempotência e reenvio.** Na Quitação Fase 4 (API BB), registre chave de idempotência do pagamento e como se obtém o comprovante: pagamento enviado ao banco não se desfaz por rollback de código (ADR-0001 do exemplo da Quitação). O R16 da Visão v6 (03/11/2026) cita "idempotência, reprocessamento". Caso real de reenvio: NMP, DS-98, 3 tentativas antes das 07h, com notificação no Teams quando falham.
- **Contrato e tipos.** CRM API, DS-544: CPF enviado como número e esperado como string. Escreva o tipo de cada campo, não só o nome.
- **Timeout, SLA e contingência.** CAF no NeoKonsig (KYC, DS-566): retorno de mais de 4 horas em produção. CAF no Konsig (ações judiciais, contingência do JUDIT, GDP-138, `gdp_16-11.csv` 16/11/2026 9h51): ficha própria. A mesma contraparte em dois sistemas gera duas fichas. DS-406 pede observabilidade, quedas e timeouts para Judit, Celcoin, CAF e CRM.
- **Timeout e leiaute.** Cobmais, DS-121: lote reprocessado para evitar timeout do servidor e do banco; planilha de entrada com 2 colunas definidas no card.
- **Horários, SFTP e leiaute.** NMP, DS-98: SFTP com RSA, 3 tentativas antes das 07h, substituição completa da base. Cartão (Orbitall: TRANDIA por SFTP diário, MANCAD, Conta Nova): a ficha atende a primeira mitigação do R16 da Visão v6 (03/11/2026), "Contratos de integração com layouts e versionamento"; monitoramento e reprocessamento ficam no RUNBOOK.
- **Fila entre sistemas.** NeoKonsig → Konsig por RabbitMQ (DS-298; DS-529 e a subtarefa DS-561, exchange corban.created e fila q.corban-created-into-konsig): contrato mínimo da mensagem (canal, esquema, quem publica, quem consome) do lado do Konsig, que segue em 2027 **[ALÉM DA FONTE — decisão do usuário]**.
- **Ambientes.** DS-567 "Tirar mock CAF KYC homolog": marque mock ou real por ambiente, para ninguém homologar contra mock achando que é real.

## Referências de mercado

- OpenAPI 3.1.1: https://spec.openapis.org/oas/v3.1.1
- AsyncAPI 3.0.0: https://www.asyncapi.com/docs/reference/specification/v3.0.0
- Pact, 'What is Pact good for?' (teste de contrato com API pública ou de terceiro): https://docs.pact.io/getting_started/what_is_pact_good_for
- Diátaxis (tipos de documentação): https://diataxis.fr/
