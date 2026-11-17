<!--
EXEMPLO · PRD v2 núcleo (trilha M) + tabela de decisão · modelos/PRD.md v2.0 · 17/11/2026. Substitui a v1 (16/11/2026); fatos, chaves e [A CONFIRMAR] mantidos.
Destino: docs/prd/ do repositório do Konsig [A CONFIRMAR qual, DS-175/DS-495].
Fontes: gdp_16-11.csv e upstream_16-11.csv (16/11/2026 9h51); downstream_16-11.csv e epicos_downstream_16-11.csv (16/11/2026 10h26); previsao-entregas-2026-v02.txt (06/11/2026); contexto-mestre.md §10 e insumos/quitacao-estado-e-faseamento.md (16/11/2026).
Limite: o Documento de Requisitos V04 (26/10/2026) não foi recebido; seus códigos aparecem como "V04 <código>". DS-500, DS-501, DS-503 e DS-505 chegaram truncados.
-->

# Executar o motor de validação da quitação em modo sombra

**Use este exemplo quando** a demanda for M e decidir dinheiro: núcleo + tabela de decisão + ADR + corte no Plano. **Não use quando** for PP/P sem dinheiro (CARD.md ou núcleo sem tabela) ou G/GG (falta apetite e seções 8–15).

**Trilha:** M, 8 cards (`D1-pool/pool-2027-plano.xlsx`; régua proposta, sem decisão). **Gatilhos:** dinheiro (DS-415), dado pessoal (DS-507/DS-509), migração planilha → sombra → efeito real (DS-500). **Ligados:** [Plano DS-500](DS-500_plano-quitacao-fase-2.md) · [ADR-0001 PagAuto + API BB](ADR-0001_GDP-76_pagamento-quitacao-pagauto-api-bb.md) · [ADR-0002 ordem das fases](ADR-0002_GDP-76_ordem-das-fases-quitacao.md).

## 1. Cabeçalho

| Sistema | Chave Jira | Natureza | Status |
|---|---|---|---|
| **Konsig** | GDP-76 (Medium, EM DOWNSTREAM) · US-69 (CONCLUÍDO UPSTREAM, 26/10/2026) · DS-500 (épico na Sprint 19, `downstream_16-11.csv`; 8 cards filhos em BACKLOG, sem sprint, `epicos_downstream_16-11.csv`; 16/11/2026 10h26) | Nova funcionalidade (DS-500, `downstream_16-11.csv`, 16/11/2026 10h26) | Rascunho · v0.2 |

Ganho: Eficiência operacional (Previsão V02, célula G17, 06/11/2026), realizado só com os efeitos; nesta fase, sem ganho de tempo (§4).

Risco: [A CONFIRMAR, sem classificação]. PDTI: [A CONFIRMAR, o PDTI 2026–2028 não cita a Quitação].

**Dados e regulação** ([checklist](../../modelos/CHECKLIST-DADOS-E-REGULACAO.md), Parte A):
- **A1** Sim: CPF e dados da proposta (grupo, convênio, consignatária, valor, vencimento), sem terceiro. Perfis com acesso [A CONFIRMAR]; retenção [A CONFIRMAR com o DPO].
- **A2** Sim, aciona o DPO: exportação com CPF leva dado para fora do sistema (DS-509). Onde o arquivo fica e por quanto tempo [A CONFIRMAR].
- **A3** Sim: registro de cada avaliação (RN05, DS-504); retenção [A CONFIRMAR].
- **A4** Não: a API do BB é da Fase 4. **A5–A7** Não se aplica.

## 2. Problema e por que agora

O Financeiro faz a quitação "de maneira manual através de um EXCEL", com "Risco financeiro e de ratreamento" [sic] (US-69), num processo "predominantemente manual (Konsig + planilhas + WhatsApp + portais bancários)" (DS-418). A decisão de pagar sai das fórmulas da planilha (DS-501, DS-503; códigos D01 e D02 [A CONFIRMAR]). A Fase 1 (DS-418) só cadastra regras: nenhuma roda sobre proposta real (`contexto-mestre.md` §10). Volume diário e valor: [A CONFIRMAR com o Financeiro].

**Por que agora:** pagar automaticamente (Fase 4) exige provar antes, sem efeito, que o motor decide como a planilha (ADR-0002).

## 3. Objetivo e métrica

| Objetivo | Métrica | Linha de base | Meta |
|---|---|---|---|
| Rodar as regras sobre propostas reais sem alterá-las | Propostas alteradas após execução | Motor não roda | Zero (DS-508) |
| Comparar motor × planilha | Concordâncias ÷ avaliadas **[ALÉM DA FONTE — decisão do usuário]** | Não existe | [A CONFIRMAR: "critério de avanço da Fase 2", DS-507] |

## 4. Não objetivos e fora do escopo

Não objetivos: reduzir o tempo do Financeiro nesta fase; automatizar o pagamento (PagAuto + API BB, decidido em 09/11/2026; fica por último, `contexto-mestre.md` §10; Fase 4 pela numeração recomendada na §3.1 do insumo e no ADR-0002).

| Fora do escopo | Onde será tratado |
|---|---|
| Efeitos: mudar situação/status, e-mail, lote (V04 RF23, RF24, RF2, RF5) e tela de envio ao aprovador | Fase 3, pela numeração da §3.1 de `insumos/quitacao-estado-e-faseamento.md` (recomendação do insumo, marcada lá como além da fonte); o DS-500 corta em "ficam para a Fase" sem o número [A CONFIRMAR] |
| Pagamento PagAuto + API BB | Fase 4 |
| Ajustes do teste de 09/11/2026 na tela da Fase 1 | DS-418, sem card |
| Outras esteiras e situações | Não previsto |

## 5. Regras de negócio (EARS)

| RN | Regra | Origem |
|---|---|---|
| RN01 | O motor DEVE avaliar só propostas da esteira Cartão Consignado Compra em AND - AGUARD QUITACAO. | DS-501 |
| RN02 | ENQUANTO em modo sombra, o Konsig NÃO DEVE alterar situação ou status, enviar e-mail ou montar lote. | DS-500, descrição (card criado em 09/11/2026; data da definição não informada; não consta nas decisões do contexto-mestre) |
| RN03 | QUANDO avaliar uma proposta, o motor DEVE decidir PAGAR, NAO_PAGAR, PAGAR_PARCIAL ou ANALISE_MANUAL, aplicando por validador as regras ativas e vigentes, pela prioridade, sobre o grupo comercial normalizado. | DS-415; DS-503 (V04 RF19.3). Normalização do grupo comercial antes das regras, e o valor normalizado é o usado nas condições (DS-503; V04 ES 3, PC-02; exemplo do card: "KOOPERA MATRIZ" → KOOPERA ASSOCIADOS). Tabela completa e dono [A CONFIRMAR]; combinação dos validadores, V04 §11 [A CONFIRMAR]. Os indicadores do DS-505 não batem com estes 4 resultados (§7) |
| RN04 | SE a regra estiver inativa, fora da vigência ou com alterações pendentes, ENTÃO o motor DEVE usar a última versão ativada. | DS-503 |
| RN05 | QUANDO avaliar, o Konsig DEVE gravar registro auditável por proposta e execução (data e hora, valores, resultado por validador, regra e versão, decisão, motivo), sem sobrescrever, sem mudar com a edição da regra, sem edição ou exclusão pela interface. | DS-504 (V04 RF12, RF19.6, RNF 1) |
| RN06 | SE faltar CPF, valor, consignatária ou boleto, ENTÃO o motor NÃO DEVE aplicar regras e DEVE registrar "Dados ausentes" como motivo da avaliação. | DS-501 (o resto do critério está truncado [A CONFIRMAR]); "Dados ausentes": indicador do DS-505 |
| RN07 | QUANDO chegar o horário agendado ou o Financeiro acionar "Reavaliar", o motor DEVE executar. | DS-501 (V04 PC-05); horário [A CONFIRMAR] |
| RN08 | ONDE o perfil não permitir ver o CPF, a tela e a exportação .xlsx DEVEM mascará-lo. | DS-507, DS-509 (V04 RNF 3); perfis e máscara [A CONFIRMAR] |

Sem fonte: tempo máximo da execução [A CONFIRMAR]; V04 RNF 4, citado no DS-500 e no DS-505 [A CONFIRMAR].

## 6. Critérios de aceite

Gatilho de dinheiro: um cenário por linha da tabela de decisão (§12). Os identificadores T1–T9 e E1–E4 são definidos aqui e devem ser os mesmos do roteiro do DS-508 **[ALÉM DA FONTE — decisão do usuário]**.

```gherkin
Cenário: T1 proposta elegível avaliada sem efeito (linha 1, RN01, RN02, RN05)
  Dado uma proposta Cartão Consignado Compra em AND - AGUARD QUITACAO e regras vigentes
  Quando o motor executa
  Então o registro tem a decisão final e a situação da proposta não muda

Cenário: T2 proposta fora da esteira ou da situação (linha 2, RN01)
  Dado uma proposta de outra esteira, ou da esteira Cartão Consignado Compra em outra situação
  Quando o motor executa
  Então nenhuma avaliação é registrada para ela

Cenário: T3 linha 3 da tabela de decisão [A CONFIRMAR, V04 §11]
  Dado [A CONFIRMAR, V04 §11]
  Quando o motor executa
  Então [A CONFIRMAR, V04 §11]

Cenário: T4 linha 4 da tabela de decisão [A CONFIRMAR, V04 §11]
  Dado [A CONFIRMAR, V04 §11]
  Quando o motor executa
  Então [A CONFIRMAR, V04 §11]

Cenário: T5 regra inativa (linha 5, RN04)
  Dado uma proposta elegível e a regra do validador inativa, com uma versão anterior ativada
  Quando o motor executa
  Então o motor aplica a última versão ativada e o registro mostra essa versão

Cenário: T6 regra fora da vigência (linha 6, RN04)
  Dado uma proposta elegível e a regra do validador fora da vigência na data e hora da avaliação
  Quando o motor executa
  Então o motor aplica a última versão ativada e o registro mostra essa versão

Cenário: T7 regra com alterações pendentes (linha 7, RN04)
  Dado uma proposta elegível e a regra do validador com "alterações pendentes"
  Quando o motor executa
  Então o motor aplica a última versão ativada e o registro mostra essa versão

Cenário: T8–T9 duas regras no mesmo validador (linhas 8–9, RN03)
  Dado uma proposta elegível e duas regras vigentes no mesmo validador, com prioridades diferentes
  Quando o motor executa
  Então vence a regra de maior prioridade e o registro mostra a regra e a versão aplicadas

Cenário: E1 a E4 exemplos do Anexo I [A CONFIRMAR, V04 Anexo I]
  Dado o exemplo En do Anexo I do V04 (um cenário por exemplo)
  Quando o motor executa
  Então a decisão é a do Anexo I [A CONFIRMAR]

Cenário: reavaliação não sobrescreve (RN05)
  Dado uma proposta já avaliada
  Quando o Financeiro aciona "Reavaliar"
  Então há um segundo registro e o primeiro continua igual

Cenário: proposta sem boleto (RN06)
  Dado uma proposta elegível sem boleto
  Quando o motor executa
  Então as regras não são aplicadas e o registro mostra o motivo "Dados ausentes"
```

## 7. Perguntas em aberto e aprovação

| Pendência | Quem | Até | Bloqueia? |
|---|---|---|---|
| V04 anexado ao DS-500 (PC-02, PC-05, RNF 4, D01, D02, tabela §11, Anexo I) | Analista de requisitos | [A CONFIRMAR] | **Sim** |
| Fase 1 concluída (DS-415 em CODE REVIEW, DS-416 EM DESENVOLVIMENTO) e cards dos ajustes de 09/11/2026 | PO, tech lead | [A CONFIRMAR] | **Sim** |
| Critério de avanço da Fase 2 (DS-507): é o critério de corte do sombra | PO com Financeiro | Antes dos efeitos | Não |
| Horário do PC-05 (DS-501) | PO | Refinamento | Não |
| Duas exportações (DS-507, DS-509; esta "não consta no Documento de Requisitos V04"). Proposta: manter DS-507 **[ALÉM DA FONTE — decisão do usuário]** | PO | [A CONFIRMAR] | Não |
| Numeração divergente: na Previsão V02 (06/11/2026, C32–C34) o motor é a Fase 3, o pagamento BB a Fase 2 e a tela do aprovador a Fase 4. Este PRD segue a numeração de `insumos/quitacao-estado-e-faseamento.md` §3.1 (motor = 2, efeitos/tela = 3, pagamento = 4) | PO | [A CONFIRMAR] | Não |
| DS-501 pede "quantas tiveram alteração de status", o que a RN02 proíbe; "Reavaliar" está no DS-501, o botão no DS-505 | PO, tech lead | Refinamento | Não |
| GDP-76 sem vínculo com US-69, DS-418 e DS-500 | PO | Antes da sprint | Não |
| Medium no GDP-76, embora prioridade da empresa (`contexto-mestre.md` §10) | PO, ao comitê | — | Não |
| Corte (go/no-go, tempo máximo, rollback por passo) no Plano DS-500 e ADR do modo sombra: obrigatórios pelo gatilho de dinheiro/migração do kit v2 (`modelos/PRD.md`). O Plano DS-500 ainda não tem seção Corte | Tech lead | Antes da primeira execução em produção | **Sim, antes da primeira execução em produção** |
| Decisões do DS-505 (Devolução, Dados ausentes, Avaliação manual × Análise manual) divergem dos 4 resultados do DS-415 (PAGAR, NAO_PAGAR, PAGAR_PARCIAL, ANALISE_MANUAL); Devolução (retorno para AGUARDANDO ABERTURA DE CONTA) conflita com a RN02 | PO, tech lead | Refinamento | Sim, para o DS-505 |
| BPMN TO-BE e protótipo "Quitação · Avaliação do motor" (DS-505) | Analista de requisitos | [A CONFIRMAR] | Não |

| Versão | Data | Mudança | Aprovação |
|---|---|---|---|
| 0.1 | 16/11/2026 | Elaboração (DS-500, DS-501, DS-503 a DS-509) | — |
| 0.2 | 17/11/2026 | Formato v2 | Pendente: Financeiro, PO, tech lead, DPO |

## 12. Tabela de decisão

O DS-508 testa "um caso por linha da tabela de decisão" (1 a 9), os exemplos 1 a 4 do Anexo I, o Validador Boleto, casos de borda das regras e a "confirmação de que nenhuma proposta foi alterada após as execuções". Só o que as fontes dizem:

| Linha | Condição | Resultado | Precedência · vigência | Teste |
|---|---|---|---|---|
| 1 | Esteira e situação elegíveis | Avalia e registra | RN01 | T1 |
| 2 | Fora da esteira ou situação | Não avalia | RN01 | T2 |
| 3–4 | [A CONFIRMAR, V04 §11] | Decisão do V04 | [A CONFIRMAR] | T3, T4 |
| 5 | Regra inativa | Última versão ativada | RN04 | T5 |
| 6 | Regra fora da vigência | Idem | RN04 | T6 |
| 7 | Alterações pendentes | Idem; registro mostra a versão | RN04 | T7 |
| 8–9 | Duas regras no mesmo validador | Vence a de maior prioridade | RN03 | T8–T9 |
| — | Validador Boleto e casos de borda (DS-508): vencimento vazio, vencido, no dia; código de barras com valor igual, diferente e zerado; dois boletos com um pago; condição com campo vazio; validador sem regra | [A CONFIRMAR, regra do V04 que define o resultado esperado] | [A CONFIRMAR] | Um teste por caso (B1–B9) **[ALÉM DA FONTE — decisão do usuário: identificadores]** |

Faixas de linhas: DS-501 (linhas 1 e 2) e DS-503 (linhas 5 a 9), `downstream_16-11.csv` 16/11/2026 10h26. A condição de cada linha dentro da faixa é inferência **[ALÉM DA FONTE — decisão do usuário]** até o V04 §11. Exemplos E1–E4: um teste cada (§6). Imutabilidade (RN05) fora do DS-508 [A CONFIRMAR]; cenários de DS-505, DS-507 e DS-509 não escritos [A CONFIRMAR].

