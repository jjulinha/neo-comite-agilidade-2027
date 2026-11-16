# Projeto Quitação · Estado e faseamento

| Item | Valor |
|---|---|
| Documento | Insumo para o Pool de projetos priorizados 2027 (Solicitação 1 da gestora, reunião de 12/11/2026) |
| Sistema | **Konsig (legado)**. Não se trata do NeoKonsig. |
| Data de referência | 16/11/2026 (Sprint 19 em andamento, de 09/11 a 20/11/2026) |
| Fontes | Seção 9 deste documento |

---

## 1. Objetivo e sistema

O Projeto Quitação automatiza, no **Konsig legado**, a etapa de quitação de dívida e de pagamento residual que o Financeiro executa hoje de forma manual.

- Situação atual descrita pela demanda: "o time realiza a etapa de quitação de maneira manual através de um EXCEL"; consequência registrada: "Risco financeiro e de ratreamento" [sic] (US-69, upstream_16-11.csv, extração 16/11/2026 9h51).
- O épico da Fase 1 descreve o processo atual como executado "de forma predominantemente manual (Konsig + planilhas + WhatsApp + portais bancários)" (DS-418, downstream_16-11.csv, extração 16/11/2026 10h26).
- O motor avalia as propostas da esteira **Cartão Consignado Compra** na situação **AND - AGUARD QUITACAO**, e nenhuma outra (DS-501, critério de aceite; downstream_16-11.csv, 16/11/2026 10h26).
- O projeto é classificado como prioridade da empresa (contexto-mestre.md, seção 10, 16/11/2026).

## 2. Decisões consolidadas

| Data | Decisão | Fonte |
|---|---|---|
| 09/11/2026 | O pagamento será feito via **PagAuto com a API do Banco do Brasil**. | contexto-mestre.md, seção 10 (16/11/2026) |
| 09/11/2026 | Inclusão da exportação da avaliação do motor para Excel, que não consta no Documento de Requisitos V04 ("decisão da equipe em 09/11/2026"). | DS-509, descrição (downstream_16-11.csv, 16/11/2026 10h26) |
| Vigente | Ordem das fases: tela de parametrização (entregue, apenas cadastral) → motor de validação com tela de visualização (Fase 2) → integração bancária **por último**. | contexto-mestre.md, seção 10 (16/11/2026) |
| 13/11/2026 | No pool de 2027, projeto = épico; um projeto tem vários cards. | contexto-mestre.md, seção 6 |

**Escopo especificado no épico (registro em card, não decisão consolidada).** A Fase 2 roda em **modo sombra**: o motor calcula e registra a avaliação, mas não altera situação ou status, não envia e-mail e não monta lote. Fonte: registrado no DS-500 (criado em 09/11/2026), descrição (downstream_16-11.csv, extração 16/11/2026 10h26). A descrição não informa a data dessa definição, e o modo sombra não consta nas decisões consolidadas do contexto-mestre (seções 6 e 10).

## 3. Fases: escopo, estado no Jira e sprint planejada

### 3.1 Numeração adotada neste documento

Este documento adota a sequência do contexto-mestre (seção 10) e do épico DS-500, por serem posteriores à Previsão V02 e por refletirem a decisão de 09/11/2026. A divergência com a Previsão V02 está descrita na seção 4.1.

| Fase | Escopo | Épico no Downstream |
|---|---|---|
| 1 | Área administrativa: cadastro, consulta, alteração, ativação/inativação e simulação das regras dos validadores; bloqueio da linha digitável de boleto já quitado | DS-418 |
| 2 | Motor de validação em modo sombra, registro auditável da avaliação e tela de visualização (lista, detalhe e exportação) | DS-500 |
| 3 | Efeitos do motor (RF23, RF24, RF2, RF5 do Documento de Requisitos V04, citados em DS-500) e tela no Konsig de envio ao aprovador e de controle (descrita como "Fase 4" na Previsão V02) | Não existe |
| 4 | Pagamento via PagAuto com a API do Banco do Brasil | Não existe |

A atribuição das Fases 3 e 4 acima é recomendação deste documento: a descrição do DS-500 na extração termina em "Os efeitos (RF23, RF24, RF2, RF5) ficam para a Fase", sem o número. **[ALÉM DA FONTE — decisão do usuário]**

### 3.2 Fase 1 · Área administrativa (DS-418)

**Escopo.** Área administrativa no Konsig para manutenção das regras do motor de validação da esteira de Compra, com identificador, nome, validador (V01 a V06), resultado (PAGAR, NAO_PAGAR, PAGAR_PARCIAL, ANALISE_MANUAL), grupo comercial, condição, tipo (geral ou exceção), vigência, situação, justificativa e auditoria; e bloqueio da linha digitável de boleto com pagamento confirmado, inclusive no pagamento residual (RF17). Fontes: US-88 e US-89 (upstream_16-11.csv, 16/11/2026 9h51); DS-415 e DS-416 (downstream_16-11.csv, 16/11/2026 10h26).

**Estado no Jira** (downstream_16-11.csv, extração 16/11/2026 10h26; epicos_downstream_16-11.csv, 16/11/2026 10h26):

| Chave | Tipo | Resumo | Status | Sprints |
|---|---|---|---|---|
| DS-418 | Épico | [KON] MÓDULO DE QUITAÇÃO - FASE 1 | EM DESENVOLVIMENTO | Sprint 18, Sprint 19 |
| DS-415 | História | [KON] QUITAÇÃO - AREA ADMINISTRATIVA | CODE REVIEW | Sprint 18, Sprint 19 |
| DS-416 | História | [KON] QUITAÇÃO - BLOQUEIO DA LINHA DIGITÁVEL | EM DESENVOLVIMENTO | Sprint 18, Sprint 19 |

- Cards do épico: 2 no total, 0 concluídos, 2 abertos (1 em CODE REVIEW, 1 em EM DESENVOLVIMENTO) (epicos_downstream_16-11.csv, 16/11/2026 10h26).
- Correspondência no Upstream: US-69 (pai, CONCLUÍDO UPSTREAM em 26/10/2026), com as subtarefas US-88 (área administrativa) e US-89 (bloqueio da linha digitável), ambas CONCLUÍDO UPSTREAM em 26/10/2026 (upstream_16-11.csv, 16/11/2026 9h51). Os títulos coincidem com DS-415 e DS-416, mas não há vínculo formal entre os itens.
- O DS-500 registra como pré-requisito da Fase 2 a tela de Administração de Quitação "com os ajustes apontados no teste de 09/11/2026". Nenhum card desses ajustes consta no épico DS-418 na extração.
- O DS-418, o DS-415 e o DS-416 estão sem o campo Categorias; o DS-418 está ainda sem PO e sem item associado (downstream_16-11.csv, 16/11/2026 10h26). Pela regra 3 do experimento vigente desde a Sprint 19, o card só vai para Concluído com Categorias, Descrição, Classe de serviço e Tipo preenchidos (contexto-mestre.md, seção 4).

**Sprint planejada.** Sprint 18 a Sprint 19, status "Desenvolvimento", estimativa 15, ganho "Fase 1 - Sem ganho" (previsao-entregas-2026-v02.txt, linha 16 da planilha, células A16:J16, modificada 06/11/2026). A fonte não informa a unidade da estimativa. A Review da Sprint 18, slide 17, registra "Quitação · Fase 1 · Desenvolvimento · Sem ganho na fase 1" (review-sprint-18.txt, extração 06/11/2026 16h46).

### 3.3 Fase 2 · Motor de validação e tela de visualização (DS-500)

**Escopo.** Aplicar às propostas reais as regras cadastradas na Fase 1 e permitir ao Financeiro visualizar o resultado de cada avaliação, sem alterar proposta (modo sombra). Origem declarada: Documento de Requisitos V04 (26/10/2026), ES 1, ES 2, ES 3, RF1, RF10, RF12, RF19.3 a RF19.6, RF22, RNF 1, RNF 3, RNF 4, Anexo I e seção 11 (tabela de decisão) (DS-500, downstream_16-11.csv, 16/11/2026 10h26).

**Estado no Jira** (downstream_16-11.csv e epicos_downstream_16-11.csv, extração 16/11/2026 10h26):

| Chave | Tipo | Resumo | Status |
|---|---|---|---|
| DS-500 | Épico | [KON] QUITAÇÃO · Fase 2 · Motor de validação e tela de visualização | BACKLOG (Sprint 19) |
| DS-501 | História | Capturar as propostas em AND - AGUARD QUITACAO e executar o motor | BACKLOG |
| DS-503 | História | Aplicar as regras parametrizadas por prioridade e definir a decisão final | BACKLOG |
| DS-504 | História | Registrar cada avaliação de forma auditável | BACKLOG |
| DS-505 | História | Tela de visualização: lista de propostas avaliadas | BACKLOG |
| DS-506 | História | Tela de visualização: detalhe da avaliação da proposta | BACKLOG |
| DS-507 | História | Exportar a avaliação para comparação com a planilha | BACKLOG |
| DS-509 | História | Exportar a avaliação do motor para Excel | BACKLOG |
| DS-508 | Tarefa | Testar o motor com a tabela de decisão e os exemplos do Anexo I | BACKLOG |

- Cards do épico: 8 no total, 0 concluídos, 8 abertos, todos em BACKLOG (epicos_downstream_16-11.csv, 16/11/2026 10h26).
- Todos os cards foram criados em 09/11/2026. O épico está na Sprint 19; nenhum dos 8 cards tem sprint atribuída.
- A chave DS-502 não consta na extração do Downstream (475 itens, project = DS, extração completa segundo o LEIA-ME.md).

**Sprint planejada.** Sprint 19 a Sprint 19, status "Backlog downstream", sem estimativa, ganho "Eficiência operacional" (previsao-entregas-2026-v02.txt, linha 17 da planilha, células A17:J17, modificada 06/11/2026). Atenção: na Previsão V02, a "Fase 2" é o pagamento BB (seção 4.1).

### 3.4 Fase 3 · Efeitos do motor, envio ao aprovador e tela de controle

**Escopo conhecido.** O DS-500 transfere para uma fase posterior os efeitos RF23, RF24, RF2 e RF5. A Previsão V02 descreve uma fase como "Tela no Konsig - envio para o aprovador e tela de controle" (previsao-entregas-2026-v02.txt, células C34:D34 da planilha, modificada 06/11/2026).

**Estado no Jira.** Não há épico, card no Downstream nem item no Upstream para esta fase (downstream_16-11.csv, extração 16/11/2026 10h26; upstream_16-11.csv, extração 16/11/2026 9h51).

**Sprint planejada.** Sprint 20, como "Quitação - Fase 4", sem estimativa (previsao-entregas-2026-v02.txt, células A19:J19 da planilha, modificada 06/11/2026).

### 3.5 Fase 4 · Pagamento via PagAuto e API do Banco do Brasil

**Escopo conhecido.** Pagamento via PagAuto com a API do Banco do Brasil (decisão de 09/11/2026, contexto-mestre.md, seção 10). A análise da API do BB é responsabilidade do usuário e não consta no pacote de fontes.

**Estado no Jira.** Não há épico, card no Downstream nem item no Upstream para esta fase (downstream_16-11.csv, extração 16/11/2026 10h26; upstream_16-11.csv, extração 16/11/2026 9h51).

**Sprint planejada.** Sprint 19, como "Quitação - Fase 2 · Pagamento BB - Pagauto", sem estimativa (previsao-entregas-2026-v02.txt, células A17:J17 e C32:D32 da planilha, modificada 06/11/2026).

### 3.6 Itens adjacentes (fora do escopo do Projeto Quitação)

Os itens abaixo usam a palavra "quitação", mas pertencem a outros projetos. Não devem ser somados ao Projeto Quitação no pool.

| Chave | Resumo | Status | Projeto a que pertence | Fonte |
|---|---|---|---|---|
| GDP-52 | [KON] PARADINHA QUITAÇÃO (High) | CONCLUÍDO em 06/10/2026 | Paradinha | gdp_16-11.csv, 16/11/2026 9h51 |
| DS-82 | Paradinha - Quitação (épico ligado ao GDP-52) | CONCLUÍDO em 25/09/2026; 3 cards, 3 concluídos (DS-83, DS-84, DS-205) | Paradinha | downstream_16-11.csv e epicos_downstream_16-11.csv, extração 16/11/2026 10h26 |
| DS-318 | [PARADINHA] Remoção de bloqueio para propostas Reprovadas | CONCLUÍDO (Sprint 16), sem épico | Paradinha | downstream_16-11.csv, extração 16/11/2026 10h26 |
| DS-50 / DS-400 | Regressão automatizada da Paradinha Quitação / testes do relatório | CONCLUÍDO (Sprint 18 / Sprint 19) | Regressão automatizada (DS-53) | downstream_16-11.csv, extração 16/11/2026 10h26 |
| GDP-77 | [KON] PARADINHA - ANÁLISE (Medium) | BACKLOG UPSTREAM; descrição contém apenas o modelo vazio | Paradinha | gdp_16-11.csv, extração 16/11/2026 9h51 |
| GDP-140 / US-91 | [KON] NOVAS REGRAS PARADINHA (Medium) | EM UPSTREAM / ANÁLISE FUNCIONAL | Paradinha | gdp_16-11.csv e upstream_16-11.csv, extração 16/11/2026 9h51 |
| DS-187 | Inclusão da coluna de valor de quitação (Switch + Comprovante) | CONCLUÍDO (Sprint 15), épico DS-116 | Tratativa Interna | downstream_16-11.csv, extração 16/11/2026 10h26 |
| DS-297 | Valor de quitação no relatório de tratativa interna (Chamado) | BACKLOG, sem épico | Tratativa Interna | downstream_16-11.csv, extração 16/11/2026 10h26 |
| US-90 | [KON] VALOR DE QUITAÇÃO NO RELATÓRIO DE TRATATIVA INTERNA | BACKLOG, descrição vazia | Tratativa Interna | upstream_16-11.csv, extração 16/11/2026 9h51 |
| DS-177 / DS-178 | Campos de quitação na seção Dados da Operação Original | CONCLUÍDO (Sprint 15), épico DS-176 | OCR Boletos | downstream_16-11.csv, extração 16/11/2026 10h26 |

O GDP-145 não entra nesta tabela porque seu título mistura Paradinha e Quitação (seção 4.4).

## 4. Divergências entre fontes

### 4.1 Numeração das fases: Previsão V02 (06/11) × contexto-mestre e DS-500 (09/11 em diante)

| Fase | Previsão V02 (06/11/2026) | Contexto-mestre (16/11/2026) e DS-500 (09/11/2026) |
|---|---|---|
| 1 | ADM - Tela de cadastro das regras | Tela de parametrização de regras (entregue, apenas cadastral) |
| 2 | **Pagamento BB - Pagauto** (Sprint 19) | **Motor de validação com tela de visualização** |
| 3 | Motor de validação (Sprint 20) | Não numerada; integração bancária "por último" |
| 4 | Tela no Konsig - envio para o aprovador e tela de controle (Sprint 20) | Não numerada |

Fontes: previsao-entregas-2026-v02.txt, células A16:J19 e C31:D34 da planilha (modificada 06/11/2026); contexto-mestre.md, seção 10; DS-500 (downstream_16-11.csv, 16/11/2026 10h26).

A Previsão V02 é anterior à decisão de 09/11/2026 e coloca o pagamento BB antes do motor. A sequência vigente é a do contexto-mestre. **Recomendação:** pedir à responsável pela planilha de esforço a atualização para a numeração da seção 3.1 antes do uso no pool.

### 4.2 Fase 1 "entregue" × Jira aberto

O contexto-mestre (seção 10) afirma que a tela de parametrização "foi entregue". Na extração de 16/11/2026 10h26, o DS-415 está em CODE REVIEW e o DS-416 em EM DESENVOLVIMENTO, ambos na segunda sprint (Sprint 18 e Sprint 19), e o épico DS-418 está em EM DESENVOLVIMENTO. O DS-500 cita um teste da tela em 09/11/2026 com ajustes apontados. Leitura deste documento: a tela foi entregue para teste, mas não está concluída no fluxo do Downstream. **[ALÉM DA FONTE — decisão do usuário]** A expressão "entregue para teste" não consta em nenhuma fonte; a divergência deve ser confirmada pelo usuário, responsável pela documentação técnica da Quitação (contexto-mestre.md, seção 10).

### 4.3 GDP-76 em Medium sendo prioridade da empresa

O GDP-76 ([KON] SISTEMATIZAÇÃO DA QUITAÇÃO) está com prioridade **Medium** e status EM DOWNSTREAM (gdp_16-11.csv, 16/11/2026 9h51). O contexto-mestre (seção 10) classifica o projeto como prioridade da empresa. No GDP há 5 itens Highest e 10 High em 90; desses, 4 Highest e 8 High não estão concluídos (gdp_16-11.csv, extração 16/11/2026 9h51). O cartão (GDP-38) está em Highest. O GDP-76 também não tem item associado: não aponta para o US-69, o DS-418 nem o DS-500.

Consequência para o pool: se a prioridade do GDP for usada para ordenar as demandas, a Quitação, em Medium, fica atrás dos 4 itens Highest e dos 8 High não concluídos (gdp_16-11.csv, extração 16/11/2026 9h51). A lógica do pool, porém, é a de um balanço, não de uma fila: da capacidade, descontam-se primeiro a sustentação, os chamados com SLA, as exigências regulatórias e os projetos em andamento, "como a Quitação", e só depois as três prioridades (prompt-comite.md, 16/11/2026). **Recomendação:** tratar a Quitação no pool como compromisso em andamento, fora da fila, e levar ao comitê a correção do GDP-76 para Highest. **[ALÉM DA FONTE — decisão do usuário]**

### 4.4 GDP-145 criado em 13/11 com modelo vazio

O GDP-145 ([KON] PARAMETRIZAÇÕES PARADINHA QUITAÇÃO) foi criado em 13/11/2026, está em BACKLOG UPSTREAM, prioridade Medium, sem responsável, sem item associado, e a descrição contém apenas o texto-modelo ("Nome do solicitante da demanda", "Explicar o cenário atual…") (gdp_16-11.csv, 16/11/2026 9h51). A fonte não permite saber se é escopo novo da Quitação (parametrização já coberta pela Fase 1) ou da Paradinha. Até ser preenchido, o item não pode ser dimensionado nem incluído no pool.

### 4.5 Exportação em dois cards

O DS-507 ("Exportar a avaliação para comparação com a planilha") e o DS-509 ("Exportar a avaliação do motor para Excel") têm em comum o arquivo .xlsx gerado com os filtros aplicados, as colunas na ordem da aba EXTRAÇÃO DE INFORMAÇÃO e o CPF mascarado conforme o perfil (RNF 3). Diferem nos pontos abaixo (downstream_16-11.csv, extração 16/11/2026 10h26):

| Aspecto | DS-507 | DS-509 |
|---|---|---|
| Finalidade | "comparar com a planilha durante o modo sombra" | "consultar as avaliações fora do sistema" |
| Origem | "Referência: critério de avanço da Fase 2"; colunas G a N da aba EXTRAÇÃO DE INFORMAÇÃO | "Origem: decisão da equipe em 09/11/2026"; "A exportação não consta no Documento de Requisitos V04"; colunas da aba (seção 2 e seção 7 do documento) |
| Requisito citado | Não cita o RF10 | Cita o RF10 |
| Nome do botão | "Exportar" | "Exportar Excel" |
| Colunas | Inclui um resultado por validador | Sem resultado por validador; termina na decisão final |

O DS-509 é o único registro, nas fontes, da decisão da equipe de 09/11/2026 listada como "Decidido" na seção 6. **Recomendação:** manter um único card, o DS-507 (que inclui o resultado por validador), e cancelar o DS-509 somente depois de acrescentar ao DS-507 a origem "decisão da equipe em 09/11/2026", a referência ao RF10 e a finalidade de consulta fora do sistema, para que a decisão continue rastreável. Com isso, a Fase 2 passa de 8 para 7 cards. **[ALÉM DA FONTE — decisão do usuário]**

### 4.6 Previsão de sprint × estado real

| Fase (numeração da seção 3.1) | Previsão V02 (06/11/2026) | Estado em 16/11/2026 (extração 10h26) |
|---|---|---|
| 1 | Sprint 18 a 19 | 0 de 2 cards concluídos; a Sprint 19 termina em 20/11/2026 |
| 2 | Sprint 20 (como "Fase 3 - Motor de validação") | 8 cards em BACKLOG, sem sprint |
| 3 | Sprint 20 (como "Fase 4") | Sem card |
| 4 | Sprint 19 (como "Fase 2 - Pagamento BB") | Sem card |

A Previsão V02 também registra um único desenvolvedor nas quatro fases (células J16 a J19 da planilha) e ressalva que "QA Teste e Deploy podem ultrapassar o prazo" (previsao-entregas-2026-v02.txt, 06/11/2026). As sprints da Previsão V02 para a Quitação não devem ser usadas no pool sem replanejamento.

## 5. O que falta para dimensionar

| Lacuna | Afeta | Situação no pacote |
|---|---|---|
| Documento de Requisitos V04 (26/10/2026), citado no DS-500 | Fases 2, 3 e 4 | Não recebido |
| Cards dos ajustes do teste de 09/11/2026 na tela de Administração | Fase 1 | Não constam no DS-418 |
| Escopo dos efeitos RF23, RF24, RF2 e RF5 e da tela de envio ao aprovador e de controle | Fase 3 | Sem épico e sem card; descrição do DS-500 truncada na extração |
| Análise da API do Banco do Brasil e do PagAuto | Fase 4 | Responsabilidade do usuário; não consta no pacote |
| BPMN TO-BE | Fases 3 e 4 | Responsabilidade do usuário; não consta no pacote |
| Conteúdo do GDP-145 | Fase 1 ou Paradinha | Modelo vazio |
| Critério de avanço da Fase 2 (citado no DS-507, sem descrição nas fontes) | Fase 2; a leitura de que esse critério libera a Fase 3 é deste documento **[ALÉM DA FONTE — decisão do usuário]** | O critério não está descrito nas fontes |

**Tamanho disponível hoje, pelas faixas propostas.** As faixas PP (até 2 cards), P (até 4), M (até 9), G (até 20) e GG (acima de 20) são proposta sem decisão (contexto-mestre.md, seção 7). Por elas, a Fase 1 tem 2 cards (PP) e a Fase 2 tem 8 cards (M), ou 7 se a seção 4.5 for aceita. As Fases 3 e 4 não têm tamanho.

**Recomendação para o pool (entrega em 30/11/2026).** Como no pool de 2027 projeto = épico (decisão de 13/11/2026, contexto-mestre.md, seção 6), lançar uma linha por épico, ambas como trabalho em andamento descontado da capacidade: DS-418 (Fase 1), com 2 cards abertos, e DS-500 (Fase 2), com 8 cards abertos (epicos_downstream_16-11.csv, 16/11/2026 10h26), contra a capacidade de projeto de 22,75 cards de épico por sprint (contexto-mestre.md, seção 5, auditoria de 13/11/2026). Lançar a Fase 3 e a Fase 4 como linhas "não dimensionadas", cada uma com a indicação de que falta criar o épico e com a dependência explícita, em vez de estimá-las sem escopo. O nome "Projeto Quitação" serve apenas como rótulo de agrupamento dessas linhas, não como um projeto único no pool. Dimensioná-las com o estimador da Calculadora de Tamanho PP a GG assim que o Documento de Requisitos V04 e a análise da API do BB estiverem disponíveis. **[ALÉM DA FONTE — decisão do usuário]**

**Risco a registrar.** A Fase 4 é integração nova no Konsig legado, que não tem CI/CD (US-43, BACKLOG, upstream_16-11.csv, 16/11/2026 9h51; contexto-mestre.md, seção 7). O efeito desse risco sobre o prazo da Quitação não está medido nas fontes.

## 6. Decidido, em aberto, bloqueado e obsoleto

### Decidido
- Sistema: Konsig legado (contexto-mestre.md, seção 10).
- Pagamento via PagAuto com a API do Banco do Brasil (09/11/2026).
- Fase 2 em modo sombra, sem efeito sobre as propostas: escopo registrado no card DS-500 (criado em 09/11/2026), não decisão consolidada do contexto-mestre (seção 2).
- Integração bancária por último (contexto-mestre.md, seção 10).
- Exportação da avaliação para Excel incluída na Fase 2 (DS-509, decisão da equipe de 09/11/2026).

### Em aberto
- Numeração e conteúdo das Fases 3 e 4 (seção 3.1).
- Prioridade do GDP-76 (Medium) frente à classificação de prioridade da empresa (seção 4.3).
- Unificação do DS-507 e do DS-509 (seção 4.5).
- Classificação e conteúdo do GDP-145 (seção 4.4).
- Rastreabilidade GDP-76 ↔ US-69 ↔ DS-418 / DS-500, hoje sem vínculo no Jira.
- Replanejamento das sprints da Quitação na planilha de esforço do Downstream (seção 4.6).

### Bloqueado
- Conclusão da Fase 1 no Jira: DS-415 e DS-416 sem Categorias, exigidas pela regra 3 do experimento vigente desde a Sprint 19.
- Início da Fase 2: depende da Fase 1 com os ajustes do teste de 09/11/2026 (pré-requisito declarado no DS-500).
- Dimensionamento das Fases 3 e 4: depende do Documento de Requisitos V04, da análise da API do BB e do BPMN TO-BE, não disponíveis no pacote.

### Obsoleto
- Numeração das fases da Previsão V02 (06/11/2026), em que a Fase 2 é o pagamento BB: superada pela sequência vigente após 09/11/2026.
- Sprints da Quitação na Previsão V02 (Fase 1 até a S19; Fases 2 a 4 entre a S19 e a S20): não refletem o estado de 16/11/2026.

## 7. Decisões necessárias

1. Adotar a numeração da seção 3.1 (Fase 3 = efeitos, envio ao aprovador e tela de controle; Fase 4 = PagAuto e API do BB) e pedir a atualização da Previsão V02. Recomendado.
2. Levar ao comitê a correção da prioridade do GDP-76 de Medium para Highest e, no pool, tratar a Quitação como compromisso em andamento, fora da fila. Recomendado.
3. Unificar a exportação no DS-507, levando para ele a origem "decisão da equipe em 09/11/2026", a referência ao RF10 e a finalidade de consulta fora do sistema, e só então cancelar o DS-509 (seção 4.5). Recomendado.
4. Devolver o GDP-145 ao solicitante para preenchimento do modelo até 30/11/2026, data de entrega do pool; sem preenchimento, mantê-lo classificado como Paradinha (o título e as categorias do item citam Paradinha; as categorias não citam Quitação, gdp_16-11.csv, extração 16/11/2026 9h51) e fora do pool. Recomendado. **[ALÉM DA FONTE — decisão do usuário]**
5. Preencher Categorias e PO no DS-418, DS-415 e DS-416 e vincular GDP-76, US-69, DS-418 e DS-500 no Jira.
6. Lançar as Fases 3 e 4 no pool como "não dimensionadas" e fixar a data de entrega do Documento de Requisitos V04 e da análise da API do BB para dimensioná-las.

## 8. Ressalvas

- Este documento não altera nem reescreve os números da linha de base da Sprint 18.
- Os nomes de pessoas presentes nas fontes foram omitidos por não serem necessários a este insumo.
- O pacote de fontes não traz padrões de mercado, as 47 ações do PDTI nem indicadores por ação; este documento não trata desses temas.

## 9. Fontes

| Arquivo | Conteúdo usado | Data |
|---|---|---|
| contexto-mestre.md | Seções 4, 5, 6, 7 e 10 | 16/11/2026 |
| gdp_16-11.csv | GDP-52, GDP-76, GDP-77, GDP-140, GDP-145; distribuição de prioridades (90 itens) | Extração 16/11/2026 9h51 |
| upstream_16-11.csv | US-43, US-69, US-88, US-89, US-90, US-91 | Extração 16/11/2026 9h51 |
| downstream_16-11.csv | DS-418, DS-415, DS-416, DS-500, DS-501, DS-503 a DS-509 e itens adjacentes da seção 3.6 | Extração 16/11/2026 10h26 |
| epicos_downstream_16-11.csv | Contagem de cards por épico (DS-418, DS-500, DS-82) | 16/11/2026 10h26 |
| previsao-entregas-2026-v02.txt | Fases, sprints, estimativa e alocação da Quitação | Modificada 06/11/2026 |
| review-sprint-18.txt | Slide 17 (Esforço de Downstream 2026) | Extração 06/11/2026 16h46 |
| prompt-comite.md | Lógica do pool e divergência do GDP-76 | 16/11/2026 |
| LEIA-ME.md | Completude das extrações e calendário de sprints | 16/11/2026 |
