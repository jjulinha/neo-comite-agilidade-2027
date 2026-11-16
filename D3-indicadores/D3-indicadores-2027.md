# Indicadores para 2027 · TI Neo Crédito

**Demanda 3 do Comitê de Agilidade (solicitação da Dani, reunião de 12/11/2026)**

| Item | Valor |
|---|---|
| Documento | D3 · Indicadores para 2027 |
| Versão | 1.0 · proposta para decisão |
| Data | 16/11/2026 |
| Escopo | Indicadores de Fluxo (Downstream), Portfólio (GDP) e Serviço (SLA) |
| Situação | Proposta. Nenhuma meta deste documento está aprovada. |

Convenções deste documento:

- **[meta é proposta — decisão da Dani]**: toda meta de 2027 é proposta e depende de aprovação.
- **[ALÉM DA FONTE — decisão do usuário]**: conteúdo que não está em nenhum documento-fonte do pacote e foi formulado nesta análise.
- Os números da linha de base da Sprint 18 são reproduzidos sem arredondamento, como estão na fonte.
- Os cálculos feitos nesta análise sobre as exportações do Jira são identificados como "cálculo sobre `<arquivo>`".

---

## 1. Objetivo

Propor um conjunto enxuto de indicadores para 2027 que:

1. derive das diretrizes do PDTI 2026–2028, sem criar um conjunto paralelo;
2. alimente o Painel Indicadores Neo;
3. tenha, para cada indicador, fórmula, fonte do dado no Jira, linha de base datada, meta proposta e frequência;
4. sinalize, sem decidir, tudo o que toque a remuneração variável (SLA vinculado a bônus).

## 2. Situação das fontes

### 2.1 Fontes utilizadas

| Arquivo do pacote | Conteúdo usado | Data |
|---|---|---|
| `review-sprint-18.txt` | Linha de base da Sprint 18 (slides 1 a 16) | extração do Jira de 06/11/2026, 16h46 |
| `contexto-mestre.md`, seção 5 | Linha de base S18 consolidada e vazão S15–S18 | atualização de 16/11/2026 (vazão: extração de 13/11/2026, 13h20) |
| `metricas_downstream_16-11.json` | Vazão por sprint S11–S19, parcela sem épico, sustentação, abertos | calculado da extração de 16/11/2026, 10h26 |
| `downstream_16-11.csv` | 475 itens do board Downstream (project = DS) | extração de 16/11/2026, 10h26 |
| `epicos_downstream_16-11.csv` | Cards por épico e vínculos | calculado em 16/11/2026, 10h26 |
| `upstream_16-11.csv` | 65 itens do board Upstream (vínculos US → GDP) | extração de 16/11/2026, 9h51 |
| `gdp_16-11.csv` | 90 itens do board Gestão de Projetos | extração de 16/11/2026, 9h51 |
| `pdti-2026-2028.txt` | Pilares e diretrizes (slides 3 a 8); SLA e bônus (slides 14 e 15) | apresentação modificada em 20/08/2026 |

### 2.2 O que a fonte não traz

- **A apresentação do PDTI recebida não define indicadores por ação**, não traz as 47 ações nem metas numéricas. Ela traz pilares, diretrizes e ações sem indicador (slides 4 a 8) e a tabela de SLA com o vínculo ao bônus (slides 14 e 15). Por isso, cada indicador deste documento está **amarrado a uma diretriz do PDTI**, e não a um indicador do PDTI. Essa amarração é proposta desta análise **[ALÉM DA FONTE — decisão do usuário]**.
- **Divergência registrada:** o `prompt-comite.md` (seção 4, Demanda 3) afirma que "o PDTI define indicadores por ação, mas sem metas numéricas". A apresentação recebida não contém esses indicadores. Se existir uma versão do PDTI (v1.3 citada no prompt) com indicadores por ação, este documento precisa ser revisto contra ela antes da aprovação.
- **Não recebidos** (LEIA-ME.md, 16/11/2026): Painel Indicadores Neo · Requisitos (28/09/2026), Relatório de metas TI · SLA 1º semestre/2026, Comitê PDTI julho/2026, Inventário de Sistemas.
- **Tempo por status** não consta das exportações de 16/11/2026: o `downstream_16-11.csv` traz status atual, datas de criação e resolução e responsáveis, mas não o histórico de status. Todos os tempos por etapa deste documento vêm da `review-sprint-18.txt`.

## 3. Estado dos temas

| Estado | Tema |
|---|---|
| **Decidido** | Regras do fluxo Downstream em vigor a partir da Sprint 19 e métrica do experimento (tempo em Code Review, QA Teste e Aprovação POs contra a S18) · decisão de 10/11/2026 (contexto-mestre, seções 4 e 6). |
| **Decidido** | No pool de 2027, projeto = épico; um projeto tem vários cards · 13/11/2026. |
| **Decidido** | Capacidade de projeto medida em cards de épico: 38,25 × (1 − 40,5%) = 22,75 por sprint (contexto-mestre, seção 5, auditoria de 13/11/2026). |
| **Decidido (regra do PDTI)** | SLA por prioridade P1 a P4 e bônus com gatilho de 70%, apuração semestral, "até 1 salário/ano" (`pdti-2026-2028.txt`, slides 14 e 15). Este documento não altera essa regra. |
| **Em aberto** | Metas de 2027 de todos os indicadores (seção 5). |
| **Em aberto** | Troca do Fibonacci por PP a GG com regra "cabe ou quebra" e o experimento S20–S22 de erro da previsão (contexto-mestre, seção 7). Nenhum indicador deste documento depende dessa decisão. |
| **Em aberto** | Limite de WIP (contexto-mestre, seção 7). |
| **Bloqueado** | Linha de base do SLA: depende do Relatório de metas TI · SLA 1º semestre/2026 (não recebido). |
| **Bloqueado** | Mapeamento para o Painel Indicadores Neo: depende do documento de requisitos do Painel (não recebido). |
| **Bloqueado** | Medição da Sprint 19 no experimento: a sprint termina em 20/11/2026 e a extração de 16/11 não traz tempo por status. |
| **Obsoleto** | Calculadora de story points (substituída pela Calculadora de Tamanho PP a GG em 13/11/2026; contexto-mestre, seção 6). |
| **Obsoleto** | Capacidade calculada como "total menos 15% de sustentação" (superestima a capacidade de projeto em cerca de 43%, contexto-mestre, seção 5). |
| **Obsoleto** | Média de 44,5 cards por sprint do comitê PDTI de julho: não se reproduz na unidade Tarefa/História/Bug (contexto-mestre, seção 5). |

## 4. Recomendação

Adotar **oito indicadores**: quatro de Fluxo, três de Portfólio e um de Serviço. O critério de entrada foi: (a) responder a uma pergunta de decisão que a Dani ou o comitê já fizeram; (b) ter dado no Jira ou em documento oficial; (c) não medir pessoas; (d) não induzir comportamento contrário ao objetivo.

| Código | Indicador | Grupo | Linha de base | Meta 2027 proposta |
|---|---|---|---|---|
| F1 | Vazão de cards concluídos por sprint | Fluxo | 38,25 (média S15–S18; `metricas_downstream_16-11.json`, 16/11/2026 10h26) | Piso de 38,25 (média móvel de 4 sprints) |
| F2 | Ciclo mediano de uma entrega | Fluxo | 63h; História 118h (S18; `review-sprint-18.txt`, slides 9 e 13, 06/11/2026 16h46) | História mediana abaixo de 75h |
| F3 | Tempo médio nas etapas pós-código | Fluxo | Code Review 20h · QA Teste 41h · Aprovação POs 26h (S18; `review-sprint-18.txt`, slide 8, 06/11/2026 16h46) | QA abaixo de 10h; Code Review até 8h; Aprovação POs até 18h |
| F4 | Entregas de funcionalidade sem QA Teste | Fluxo | 12 (7 Nova funcionalidade + 5 Melhoria, S18; `review-sprint-18.txt`, slide 11, 06/11/2026 16h46) | Zero sem dispensa registrada |
| P1 | Capacidade de projeto realizada | Portfólio | 22,75 cards de épico por sprint (S15–S18; `metricas_downstream_16-11.json`, 16/11/2026 10h26) | Média trimestral ≥ 22,75 |
| P2 | Aderência do pool trimestral | Portfólio | Linha de base a levantar (1º trimestre de 2027) | ≥ 80% |
| P3 | Rastreabilidade do trabalho ao GDP | Portfólio | 65 de 91 cards de épico com vínculo ao GDP (S15–S18; cálculo sobre `downstream_16-11.csv`, `epicos_downstream_16-11.csv` e `upstream_16-11.csv`, 16/11/2026) | 100% dos épicos abertos em 2027 |
| S1 | Atendimentos no prazo do SLA, por prioridade | Serviço | Linha de base a levantar (depende do Relatório de metas TI · SLA 1º semestre/2026, não recebido) | Sem proposta de alteração: gatilho de 70% vigente |

Todas as metas da tabela são **[meta é proposta — decisão da Dani]**. As fichas da seção 5 indicam quais metas vêm de fonte e quais são **[ALÉM DA FONTE — decisão do usuário]**.

---

## 5. Fichas dos indicadores

### 5.1 Fluxo (board Downstream)

#### F1 · Vazão de cards concluídos por sprint

| Campo | Conteúdo |
|---|---|
| Pergunta que responde | Quantos cards o desenvolvimento entrega por sprint, e quanto disso é sustentação? |
| Fórmula | Contagem de itens com `tipo` ∈ {Tarefa, História, Bug} e `resolvido` dentro da sprint. Sprint da conclusão = 18 + piso((resolvido − 26/10/2026) / 14 dias). Excluem-se Subtask e Epic. Desdobramento: sustentação = (Bugs + itens com natureza Chamado) ÷ vazão. |
| Fonte do dado | Jira, board Downstream (project = DS), campos Tipo de item, Resolvido e Natureza. |
| Linha de base | S15 = 35 · S16 = 38 · S17 = 27 · S18 = 53 · média S15–S18 = 38,25 (`metricas_downstream_16-11.json`, extração de 16/11/2026, 10h26). Sustentação S15–S18: 23 de 153 = 15,0% (contexto-mestre, seção 5; extração de 13/11/2026, 13h20). O contexto-mestre exibe a média como "38,3" na tabela e usa 38,25 na fórmula da capacidade; este documento adota 38,25. |
| Dado parcial | S19 = 40 cards até 16/11/2026, 10h26, com a sprint em andamento até 20/11/2026 (`metricas_downstream_16-11.json`). |
| Meta 2027 | Média móvel de 4 sprints não inferior a 38,25, com o mesmo tamanho de time **[meta é proposta — decisão da Dani] [ALÉM DA FONTE — decisão do usuário]**. |
| Racional | Vazão em cards depende do tamanho do card. Uma meta de aumento induziria a fatiar cards para inflar a contagem. Por isso a meta é um piso que protege a premissa de capacidade do pool, e não um alvo de crescimento. |
| Frequência | Por sprint, na review; consolidação trimestral no Painel. **[ALÉM DA FONTE — decisão do usuário]** |
| Pilar / diretriz do PDTI | Excelência Operacional · "Elevar a maturidade dos processos da TI", com "aumento de performance frente aos indicadores" (slide 7). |
| Dono sugerido | Responsável pela review da sprint do Downstream (Núcleo de Soluções). **[ALÉM DA FONTE — decisão do usuário]** |
| Limitações | A contagem trata cards de tamanhos diferentes como iguais. A sprint da conclusão é derivada da data de resolução, e não do campo Sprint do Jira. Pessoas no campo DEVs: 7 a 9, média 7,75 (contexto-mestre, seção 5, extração de 13/11/2026, 13h20); 5 a 8, média 7,0 (S15 = 8, S16 = 5, S17 = 7, S18 = 8; `metricas_downstream_16-11.json`, extração de 16/11/2026, 10h26). **Divergência registrada:** prevalece a extração de 16/11 até a confirmação do usuário. A comparação entre sprints precisa ser lida com o tamanho do time ao lado. |

#### F2 · Ciclo mediano de uma entrega

| Campo | Conteúdo |
|---|---|
| Pergunta que responde | Quanto tempo um card leva do início do desenvolvimento até o deploy (Em desenvolvimento a Waiting for deploy), conforme `review-sprint-18.txt`, slides 9 e 13? |
| Fórmula | Mediana, entre os itens entregues na sprint (status Aprovação POs, Waiting for deploy ou Concluído), da soma das horas úteis nos status Em desenvolvimento, Code Review, QA Teste, Aprovação POs e Waiting for deploy. Dia útil de 7h30. Desdobramento obrigatório por tipo de item (Bug, Tarefa, História). |
| Fonte do dado | Jira, board Downstream, histórico de status (tempo em status). |
| Linha de base | Ciclo mediano de uma entrega = 63h · mediana em desenvolvimento = 4h · mediana depois do desenvolvimento = 27h · 66% das horas depois do código pronto · por tipo: Bug 12h, Tarefa 29h, História 118h · sprint = 75h úteis (`review-sprint-18.txt`, slides 9 e 13; extração de 06/11/2026, 16h46). |
| Meta 2027 | Ciclo mediano de História abaixo de 75h **[meta é proposta — decisão da Dani] [ALÉM DA FONTE — decisão do usuário]**. O valor vem do slide 15 da review S18 (oportunidade 04) como sugestão para a S19; a adoção como meta de 2027 é proposta desta análise. O slide 15 sugere escolher no máximo três oportunidades, e o slide 16 não registra quais foram escolhidas. Para o ciclo geral, não se propõe meta: ele é acompanhado como contexto. |
| Racional | A História mediana (118h) não cabe numa sprint de 75h e alimenta o carryover (slide 13). Se a História couber na sprint, cai o peso das atividades herdadas (46,9% na S18). |
| Frequência | Por sprint; consolidação trimestral no Painel. **[ALÉM DA FONTE — decisão do usuário]** |
| Pilar / diretriz do PDTI | Tech First · "Definir padrões de desenvolvimento que garantam entregas ágeis e consistentes" (slide 6). |
| Dono sugerido | PO do Núcleo de Soluções. **[ALÉM DA FONTE — decisão do usuário]** |
| Limitações | O Jira acumula o tempo da vida inteira do item, inclusive antes da sprint (slide 10, notas). A extração de 16/11/2026 não contém tempo por status: o cálculo depende de nova extração com histórico. |

#### F3 · Tempo médio nas etapas pós-código

| Campo | Conteúdo |
|---|---|
| Pergunta que responde | Onde o card espera depois que o código fica pronto, e as travas da Sprint 19 aceleraram ou seguraram o fluxo? |
| Fórmula | Para cada etapa (Code Review, QA Teste, Aprovação POs): média das horas úteis no status, para os itens da sprint, na extração do último dia da sprint. Mediana publicada ao lado da média. |
| Fonte do dado | Jira, board Downstream, histórico de status. |
| Linha de base | Médias S18: Code Review 20h · QA Teste 41h · Aprovação POs 26h. Medianas S18: Code Review 7,7h · QA 46,8h · Aprovação POs 6,6h. Série de médias: Code Review S15 11, S16 14, S17 8; QA Teste S15 30, S16 18, S17 7; Aprovação POs S15 18, S16 29, S17 20 (`review-sprint-18.txt`, slide 8; extração de 06/11/2026, 16h46). A escolha do recorte está justificada na seção 6.2. |
| Meta 2027 | QA Teste: média abaixo de 10h **[meta é proposta — decisão da Dani] [ALÉM DA FONTE — decisão do usuário]**; o valor vem do slide 15 da review S18 (oportunidade 01) como sugestão para a S19; a adoção como meta de 2027 é proposta desta análise. Code Review: média até 8h. Aprovação POs: média até 18h **[meta é proposta — decisão da Dani] [ALÉM DA FONTE — decisão do usuário]**. |
| Racional | 66% das horas do ciclo estão depois do código pronto (slide 9): a alavanca está na espera entre etapas. As metas de Code Review (8h, S17) e Aprovação POs (18h, S15) são os menores valores da própria série S15–S18, o que mostra que o patamar já foi atingido pelo time. |
| Frequência | Por sprint; consolidação trimestral no Painel. **[ALÉM DA FONTE — decisão do usuário]** |
| Pilar / diretriz do PDTI | Tech First · "Definir padrões de desenvolvimento que garantam entregas ágeis e consistentes" (slide 6); Pessoas & Cultura · "Fomentar uma cultura ágil" (slide 4). |
| Dono sugerido | Responsável pela review da sprint, com o QA do Núcleo de Soluções para a etapa QA Teste. **[ALÉM DA FONTE — decisão do usuário]** |
| Limitações | As médias de S15 a S17 vieram da review da Sprint 17 e "o recorte de itens da review anterior pode diferir" (slide 8, notas). O tempo em Code Review e QA inclui a fila antes de a atividade começar (slide 9, notas). Itens em andamento seguem acumulando tempo, então o valor depende da hora da extração. |

#### F4 · Entregas de funcionalidade sem QA Teste

| Campo | Conteúdo |
|---|---|
| Pergunta que responde | Quanta funcionalidade chega à produção sem passar pelo teste previsto no Fluxo? |
| Fórmula | Contagem de itens entregues na sprint (Aprovação POs em diante) com natureza Nova funcionalidade ou Melhoria e sem tempo registrado no status QA Teste, menos os que têm dispensa de QA registrada no card. Publicar também o total de entregas sem QA, por natureza. |
| Fonte do dado | Jira, board Downstream: histórico de status (QA Teste) e campo Natureza. O registro da dispensa ainda não existe como campo **[ALÉM DA FONTE — decisão do usuário]**. |
| Linha de base | 27 de 67 entregas sem QA Teste (40% das entregas). Por natureza: Arquitetura 11, Nova funcionalidade 7, Melhoria 5, Chamado 4. Nova funcionalidade + Melhoria sem QA = 12 (`review-sprint-18.txt`, slide 11; extração de 06/11/2026, 16h46). |
| Meta 2027 | Zero entregas de Nova funcionalidade ou Melhoria sem QA Teste ou sem dispensa registrada. **[meta é proposta — decisão da Dani] [ALÉM DA FONTE — decisão do usuário]**. O valor vem do slide 15 da review S18 ("nenhuma funcionalidade sem QA", oportunidade 02) como sugestão para a S19; a adoção como meta de 2027 é proposta desta análise. |
| Racional | A review registra que "as 12 novas funcionalidades e melhorias sem QA são risco de produção" (slide 11). Arquitetura sem QA pode ser decisão consciente; por isso a meta incide sobre funcionalidade. |
| Frequência | Por sprint; consolidação trimestral no Painel. **[ALÉM DA FONTE — decisão do usuário]** |
| Pilar / diretriz do PDTI | Tech First · ação "Adotar pipeline CI/CD ... permitindo que essas entregas sejam frequentes e confiáveis" (slide 6). |
| Dono sugerido | QA do Núcleo de Soluções. **[ALÉM DA FONTE — decisão do usuário]** |
| Limitações | "Sem QA" significa sem tempo no status: o item pode ter pulado o status no Jira sem deixar de ser testado (slide 11, notas). A regra de quando o QA pode ser dispensado ainda não está escrita (slide 15, oportunidade 02). |

### 5.2 Portfólio (board GDP)

#### P1 · Capacidade de projeto realizada

| Campo | Conteúdo |
|---|---|
| Pergunta que responde | A premissa de capacidade do pool de 2027 está se confirmando? |
| Fórmula | Média, no trimestre, dos cards concluídos por sprint (Tarefa, História, Bug) que têm épico preenchido. Desdobramento: parcela sem épico = cards sem épico ÷ vazão (F1). |
| Fonte do dado | Jira, board Downstream, campos Tipo de item, Resolvido e Épico (pai). |
| Linha de base | Cards de épico concluídos: S15 = 18 · S16 = 24 · S17 = 15 · S18 = 34 · média = 22,75. Sem épico S15–S18: 62 de 153 (40,5%) (`metricas_downstream_16-11.json`, extração de 16/11/2026, 10h26; contexto-mestre, seção 5). |
| Dado parcial | S19 = 32 cards de épico de 40 até 16/11/2026, 10h26 (`metricas_downstream_16-11.json`). |
| Meta 2027 | Média trimestral ≥ 22,75 cards de épico por sprint. Se ficar abaixo em dois trimestres seguidos, o pool é recalculado **[meta é proposta — decisão da Dani] [ALÉM DA FONTE — decisão do usuário]**. |
| Racional | O pool de 2027 usa 22,75 cards de épico por sprint como capacidade (decisão da auditoria de 13/11/2026). O indicador verifica a premissa do balanço trimestral em vez de criar um alvo novo. |
| Frequência | Por sprint (acompanhamento); trimestral (Painel e revisão do pool). **[ALÉM DA FONTE — decisão do usuário]** |
| Pilar / diretriz do PDTI | Parceiros & Clientes no Centro · "Priorizar entregas de valor que impulsionem a performance organizacional de parceiros e clientes" (slide 5). |
| Dono sugerido | Responsável pelo pool de 2027 (Gestão de TI). **[ALÉM DA FONTE — decisão do usuário]** |
| Limitações | Se trabalho técnico hoje sem épico (Arquitetura 29, Débito técnico 11 em S15–S18) passar a ter épico, a capacidade sobe no número sem ganho real. Toda mudança de regra de vínculo a épico precisa ser registrada e a série, comparada antes e depois. |

#### P2 · Aderência do pool trimestral

| Campo | Conteúdo |
|---|---|
| Pergunta que responde | O que o pool prometeu para o trimestre foi entregue no trimestre? |
| Fórmula | Projetos (épicos) previstos no pool para concluir no trimestre e concluídos até o último dia do trimestre ÷ projetos previstos para concluir no trimestre. Projetos de fora do pool que entraram no trimestre são contados à parte, como entrada não planejada. |
| Fonte do dado | Planilha do pool de desenvolvimento 2027 (previsão por trimestre) cruzada com o Jira, board GDP (Status, Resolvido) e board Downstream (status do épico). |
| Linha de base | **Linha de base a levantar.** A previsão trimestral sai do pool refeito no Entregável 1 (entrega à Dani em 30/11/2026); a planilha v13 não é usada como base, por pedido do usuário. Primeira medição ao fim do 1º trimestre de 2027. |
| Meta 2027 | ≥ 80% dos projetos previstos concluídos no trimestre, revista após os dois primeiros trimestres **[meta é proposta — decisão da Dani] [ALÉM DA FONTE — decisão do usuário]**. |
| Racional | O pool é a Demanda 1 e vai sustentar a apresentação da Dani aos executivos. Sem medir a aderência, o pool não aprende com o próprio erro. |
| Frequência | Trimestral. **[ALÉM DA FONTE — decisão do usuário]** |
| Pilar / diretriz do PDTI | Parceiros & Clientes no Centro · "Priorizar entregas de valor..." (slide 5); Excelência Operacional · "Elevar a maturidade dos processos da TI" (slide 7). |
| Dono sugerido | Responsável pelo pool de 2027 (Gestão de TI). **[ALÉM DA FONTE — decisão do usuário]** |
| Limitações | O lead time do GDP não serve de apoio: no `gdp_16-11.csv` todos os 90 itens foram criados a partir de 27/07/2026, e 17 dos 33 concluídos foram criados e resolvidos no mesmo dia (05 e 06/08/2026). O mais provável é carga inicial do board, e não fluxo real **[ALÉM DA FONTE — decisão do usuário]**. |

#### P3 · Rastreabilidade do trabalho ao GDP

| Campo | Conteúdo |
|---|---|
| Pergunta que responde | Quanto da capacidade de projeto está ligado a um item aprovado no portfólio? |
| Fórmula | Cards de épico concluídos no período cujo épico tem vínculo com item GDP (direto, em Itens associados, ou por meio de item US do Upstream vinculado a GDP) ÷ cards de épico concluídos no período. |
| Fonte do dado | Jira, boards Downstream (Épico, Itens associados), Upstream (Itens associados) e GDP. |
| Linha de base | Por vínculo no Jira: 65 de 91 cards de épico concluídos em S15–S18 têm vínculo ao GDP, e 26 não têm. Os 26 estão em: Atalho Formalização – Resolução de débitos técnicos 7, Organização Deploy 4, Correção vulnerabilidades 4, Melhorar mensagens de erro na ficha proposta 3, Regressão automatizada 2, OCR Boletos – Parte 2 2, Não me perturbe 2, OCR Boletos – Fluxo de Boleto PDF para usuários externos 1, Migrar keycloak para o novo GitLab 1 (cálculo sobre `downstream_16-11.csv`, `epicos_downstream_16-11.csv` e `upstream_16-11.csv`, extração de 16/11/2026). S19 parcial: 18 de 32 com vínculo. |
| Divergência | A auditoria de 13/11/2026 registra 11 de 91 cards de épico (12%) em épicos técnicos **sem item no GDP** (contexto-mestre, seção 5). A diferença (26 contra 11) indica 15 cards de épicos que têm item correspondente no GDP, mas sem vínculo no Jira **[ALÉM DA FONTE — decisão do usuário]**. Indício conferido em `gdp_16-11.csv` (extração de 16/11/2026, 9h51): existem GDP-82 (Atalho aba de formalização), GDP-78 e GDP-139 (OCR de boletos) e GDP-132 (Não me perturbe), sem vínculo nos épicos DS-271, DS-395, DS-291 e DS-97 (`epicos_downstream_16-11.csv`). O indicador usa o vínculo no Jira, porque é o único critério medido automaticamente. |
| Meta 2027 | 100% dos épicos abertos a partir de 01/01/2027 com vínculo ao GDP **[meta é proposta — decisão da Dani] [ALÉM DA FONTE — decisão do usuário]**. |
| Racional | A decisão de 13/11/2026 (projeto = épico) só se sustenta se cada épico estiver ligado ao portfólio. Sem o vínculo, P1 e P2 medem trabalho que o GDP não enxerga. |
| Frequência | Trimestral; checagem de épicos novos na planning. **[ALÉM DA FONTE — decisão do usuário]** |
| Pilar / diretriz do PDTI | Tech First · "Estabelecer governança clara para adoção, manutenção e evolução de tecnologias" (slide 6). |
| Dono sugerido | PO do Núcleo de Soluções. **[ALÉM DA FONTE — decisão do usuário]** |
| Limitações | Épicos técnicos (por exemplo, migrações para o GitLab) podem não ter item no GDP por decisão. Antes de cobrar a meta, é preciso decidir se todo épico técnico entra no GDP. |

### 5.3 Serviço (SLA)

#### S1 · Atendimentos no prazo do SLA, por prioridade

| Campo | Conteúdo |
|---|---|
| Pergunta que responde | A sustentação atende os chamados dentro do prazo acordado, e o gatilho do bônus foi alcançado? |
| Fórmula | Chamados no prazo ÷ total de chamados no período, por prioridade (P1 Crítica, P2 Alta, P3 Média, P4 Baixa), com gatilho de 70% (`pdti-2026-2028.txt`, slide 15). Prazos por prioridade e nível (Resposta, N1, N2, N3) conforme o slide 14. |
| Fonte do dado | Ferramenta de registro de chamados da sustentação, **não identificada no pacote**. O board Downstream tem natureza Chamado, mas não tem campo de prioridade P1 a P4 nem de prazo, e não serve como fonte. |
| Linha de base | **Linha de base a levantar** com a Dani (Gestão de TI), a partir do Relatório de metas TI · SLA 1º semestre/2026 (não recebido). |
| Meta 2027 | Nenhuma alteração proposta. A regra vigente é a do PDTI: gatilho de 70%, apuração semestral, peso do bônus P1 50%, P2 30%, P3 15%, P4 5% (slide 15). Qualquer mudança é **decisão da Dani e do RH**. |
| Racional | É o único indicador já institucionalizado no PDTI e ligado a remuneração. Entra no conjunto para que o Painel o mostre ao lado dos indicadores de fluxo, sem que esta análise altere a regra. |
| Frequência | Acompanhamento mensal **[ALÉM DA FONTE — decisão do usuário]**; apuração semestral (fonte, slide 15). |
| Pilar / diretriz do PDTI | Excelência Operacional · "Elevar a maturidade dos processos da TI" (slide 7); seção Sustentação de sistemas (slides 14 e 15). |
| Dono sugerido | Gestão de TI (Núcleo de Gestão, slide 11) **[ALÉM DA FONTE — decisão do usuário]**. O PDTI não define o dono do SLA: o slide 10 prevê "01 Sustentação (TBD)" no Núcleo de Soluções, o slide 11 lista os níveis N1 a N3 no Núcleo de Infraestrutura & Comunicação, e o slide 14 não diz quem responde por cada nível. |
| Limitações | O PDTI não define a ferramenta, o relógio (horário útil ou corrido) nem o tratamento de chamados reabertos. O slide 14 grafa "3 dia útil" para P3 em N3. |

---

### 5.4 Medição atual · Sprints 15 a 19 (Jira de 16/11/2026, 10h26)

Série por sprint para a apresentação (seção **Indicadores** do HTML `apresentacao/pool-2027-com-sem-neokonsig.html`). Cálculo em `downstream_16-11.csv`, `epicos_downstream_16-11.csv` e `gdp_16-11.csv`; sprint atribuída pela data de resolução. **S19 é parcial**: vai até 20/11/2026.

| Indicador | S15 | S16 | S17 | S18 | S19 parcial |
|---|---|---|---|---|---|
| F1 Vazão (cards Tarefa/História/Bug concluídos) | 35 | 38 | 27 | 53 | 40 |
| P1 Cards de épico concluídos | 18 | 24 | 15 | 34 | 32 |
| Cards sem épico (%) | 48,6 | 36,8 | 44,4 | 35,8 | 20,0 |
| P3 Cards de épico rastreáveis ao GDP (%) | 61,1 | 66,7 | 80,0 | 76,5 | 56,2 |
| F4 (proxy) Testador preenchido (%) | 57,1 | 50,0 | 29,6 | 24,5 | 47,5 |
| Revisor preenchido (%) | 51,4 | 34,2 | 29,6 | 24,5 | 40,0 |
| Categorias preenchidas (%) | 88,6 | 86,8 | 92,6 | 96,2 | 100,0 |

| Indicador | Situação da medição |
|---|---|
| F1, P1, P3 | Medidos no Jira. |
| F2, F3 | Só pela Review S18 (63h; História 118h; CR 20h, QA 41h, Aprovação 26h). A exportação não traz histórico de status; o lead time criado→resolvido não serve como substituto (mistura fila do Upstream). Pedir exportação com histórico de status. |
| F4 | Review S18 (12 funcionalidades e melhorias sem QA). Série acima é proxy (Testador preenchido), não o indicador. |
| P2 | Primeira medição em abr/2027. Plano base sem NeoKonsig prevê entregas de projeto: até dez/2026 3 · T1/2027 17 · T2 3 · T3 15 · T4 17. |
| S1 | Sem dado: relatório de SLA do 1º semestre/2026 não recebido. |

Sinais secundários (não são indicadores): 127 cards abertos no Downstream, 9 deles há 3 sprints ou mais; GDP criados × concluídos: set/2026 8 × 5, out/2026 7 × 6.

## 6. Experimento do Downstream · Sprint 19

### 6.1 O que se mede

Pela decisão de 10/11/2026: o tempo em **Code Review**, **QA Teste** e **Aprovação POs** na Sprint 19 (09/11 a 20/11/2026), comparado com a Sprint 18, para verificar se as três regras (Histórias só pelo PO, responsável obrigatório em cada etapa, classificação para concluir) aceleraram ou seguraram o fluxo. A revisão acontece na retro.

### 6.2 Recorte da linha de base S18: slide 8

A review oferece dois recortes:

| Etapa | Slide 8 · itens da sprint (média) | Slide 8 · mediana | Slide 10 · itens entregues (média, n) |
|---|---|---|---|
| Code Review | 20h | 7,7h | 16h (43 itens) |
| QA Teste | 41h | 46,8h | 42h (40 itens) |
| Aprovação POs | 26h | 6,6h | 26h (21 itens) |

Fonte: `review-sprint-18.txt`, slides 8 e 10; extração de 06/11/2026, 16h46.

**Recomendação: usar o slide 8 (itens da sprint), com média e mediana.** Justificativa:

1. As regras da S19 valem para todo card que se move na sprint, e não só para os entregues. O slide 10 exclui os itens que travaram antes de Aprovação POs, que são justamente os que o experimento quer enxergar.
2. O slide 8 é o único recorte com série histórica (S15 a S18). Com ele, a S19 é lida contra quatro sprints, e não contra um ponto isolado.
3. O slide 8 traz as medianas, que reduzem o peso de valores extremos; o tempo acumulado de itens herdados continua dentro dos dois números (slide 8, notas). No slide 10, 25 dos 40 itens que passaram por QA são herdados (notas do slide 10).
4. O valor de 41h em QA Teste, já usado no contexto-mestre e no board do comitê, é o do slide 8.

O slide 10 fica como leitura complementar.

### 6.3 Como medir a S19

- Extração do Jira no último dia da sprint (20/11/2026), no fim do dia, com histórico de status, pelo mesmo procedimento da S18: itens da sprint, horas úteis com dia de 7h30, média e mediana por etapa.
- Comparar S19 × S18 nas três etapas. Ler o resultado como sinal, e não como conclusão: uma sprint isolada não sustenta decisão.
- **Medição da S19: a levantar.** A extração de 16/11/2026 não contém tempo por status.

### 6.4 Sinal já disponível: preenchimento dos campos (regras 2 e 3)

Enquanto o tempo por etapa não é medido, o preenchimento dos campos mostra se as regras estão sendo cumpridas. Cálculo sobre `downstream_16-11.csv` (extração de 16/11/2026, 10h26), cards Tarefa, História e Bug concluídos em cada sprint:

| Campo preenchido | S18 (53 cards) | S19 parcial (40 cards) |
|---|---|---|
| Revisor | 13 (24,53%) | 16 (40,0%) |
| Testador | 13 (24,53%) | 19 (47,5%) |
| PO | 9 (16,98%) | 14 (35,0%) |
| DEVs | 33 (62,26%) | 30 (75,0%) |
| Categorias, Descrição, Classe de serviço e Natureza, todos preenchidos | 35 (66,04%) | 39 (97,5%) |

Leitura e limites:

- A regra 3 (classificação para concluir) aparece quase integralmente cumprida na S19 parcial.
- A regra 2 (responsável por etapa) melhorou, mas o denominador é o total de concluídos, e não os itens que passaram por cada etapa. Itens que não passaram por QA Teste não precisariam de testador, e itens herdados entraram nas etapas antes de 09/11. A taxa real de cumprimento só sai com o histórico de status.
- Os 53 cards da S18 neste cálculo seguem a regra de sprint da conclusão por data de resolução. Eles não se confundem com as 51 concluídas da review (slide 2), que usam outro recorte.
- Premissa desta análise: o campo "Tipo" da regra 3 foi lido como **Natureza** (tipo de demanda), porque o tipo de item é obrigatório no Jira **[ALÉM DA FONTE — decisão do usuário]**.

---

## 7. Indicadores que ficaram de fora

| Indicador | Motivo |
|---|---|
| Story points e velocity | Não entram porque a troca do Fibonacci por PP a GG está em aberto e depende do comitê (contexto-mestre, seção 7). O uso de Fibonacci não é prática atual do time. |
| Erro da previsão PP a GG (cards estimados × entregues) | Depende da decisão do comitê sobre o experimento S20–S22 (contexto-mestre, seção 7). É candidato a entrar depois dessa decisão. |
| Contagem por pessoa (cards por dev, testes ou revisões por pessoa) | Mede pessoas, e não o fluxo. Os dados de concentração (11 de 14 testes e 11 de 23 revisões pela mesma pessoa) são parciais e a própria review os trata como "hipótese de sobrecarga, não de desempenho" (slide 14). Seguem como diagnóstico na review, fora do Painel. |
| Taxa de conclusão da sprint (53% na S18) | Varia com o volume puxado para a sprint e com os cards abertos depois da planning. Incentiva puxar menos. F1 e F2 respondem melhor à mesma pergunta. |
| Cards criados depois da planning (37 na S18) | A review registra que "a data de criação não serve para medir escopo novo" (slide 7, notas). |
| Peso das atividades herdadas (46,9% na S18) | É efeito do ciclo longo (F2). Segue na review como contexto. |
| Tempo em Backlog e em Waiting for deploy | Backlog mede fila de priorização, e não fluxo de desenvolvimento. Waiting for deploy está estável (15h na S18, slide 8). Volta ao conjunto se a CI/CD mudar o deploy. |
| Itens na 3ª sprint ou mais (5 na S18) | Fica fora do Painel; a review S18 propõe tratá-lo na 3ª sprint (quebrar, pausar com motivo ou cancelar; slide 15, oportunidade 05), sem decisão registrada. |
| Lead time do GDP (criação → conclusão) | Base não confiável: 17 dos 33 itens concluídos foram criados e resolvidos no mesmo dia, e todos os itens foram criados a partir de 27/07/2026 (`gdp_16-11.csv`). Pode ser reavaliado com os itens criados a partir de 2027. |
| Média de 44,5 cards por sprint (comitê de julho) | Não se reproduz na unidade Tarefa/História/Bug. |

---

## 8. Remuneração: pontos sinalizados para a Dani e o RH

Este documento não decide nada que afete a remuneração. Ficam sinalizados:

1. **S1 (SLA)** está vinculado ao bônus semestral (até 1 salário/ano, gatilho de 70%, `pdti-2026-2028.txt`, slide 15). Nenhuma alteração de fórmula, gatilho, peso ou fonte é proposta aqui.
2. **Fonte do S1:** se a TI adotar uma ferramenta ou regra de classificação diferente da usada no 1º semestre de 2026, o resultado do bônus muda. A decisão é da Dani e do RH.
3. **F1 a F4 e P1 a P3:** recomenda-se **não** vinculá-los a remuneração. Vazão e tempo por etapa vinculados a bônus induzem fatiar cards e pular status no Jira, o que destruiria a comparabilidade da linha de base **[ALÉM DA FONTE — decisão do usuário]**.

---

## 9. Decisões necessárias

| Nº | Decisão | Quem decide | Recomendação desta análise |
|---|---|---|---|
| 1 | Aprovar o conjunto de oito indicadores (F1 a F4, P1 a P3, S1) | Dani | Aprovar. |
| 2 | Aprovar as metas propostas para 2027 | Dani | Aprovar F2, F3 e F4, cujo valor vem das sugestões do slide 15 para a S19, estendidas a 2027 por esta análise; validar as demais metas marcadas como além da fonte. |
| 3 | Confirmar que o SLA e o bônus seguem a regra do PDTI sem alteração e fornecer o Relatório de metas/SLA do 1º semestre de 2026 como linha de base | Dani e RH | Manter a regra; enviar o relatório. |
| 4 | Confirmar que nenhum indicador de fluxo ou portfólio será vinculado a remuneração | Dani e RH | Não vincular. |
| 5 | Adotar o slide 8 da review S18 como linha de base do experimento | Comitê de Agilidade | Adotar. |
| 6 | Definir o critério de rastreabilidade: vínculo no Jira (26 de 91 sem vínculo) ou auditoria (11 de 91 sem item no GDP) | Dani | Vínculo no Jira, por ser medido automaticamente. |
| 7 | Decidir se todo épico técnico precisa de item no GDP | Dani | Sim, para que P1 e P2 vejam toda a capacidade de projeto. |
| 8 | Confirmar a leitura de "Tipo" da regra 3 como Natureza (tipo de demanda) | Usuário | Confirmar. |
| 9 | Enviar o documento de requisitos do Painel Indicadores Neo e a versão do PDTI com indicadores por ação, se houver | Dani | Necessário antes de publicar no Painel. |

## 10. Encaminhamento

- **Fazer agora:** agendar a extração do Jira com histórico de status para 20/11/2026, no fim do dia, e medir F3 da S19 com o recorte do slide 8.
- **Fica para depois:** o erro da previsão PP a GG, que depende da decisão do comitê sobre o experimento S20–S22.
- **Decisão que o usuário precisa tomar:** levar à Dani as decisões 3 e 4 (SLA e remuneração) antes de qualquer publicação no Painel.
- **Menor próximo passo útil:** pedir à Dani o Relatório de metas TI · SLA 1º semestre/2026 e o documento de requisitos do Painel Indicadores Neo.

## 11. Referências cruzadas

- Contexto-mestre, seções 4 (experimento), 5 (linha de base e vazão), 6 (decisões) e 7 (em aberto).
- `prompt-comite.md`, seção 4, Demanda 3.
- Demanda 1 (pool de 2027): P1 e P2 verificam a premissa de capacidade (22,75 cards de épico por sprint) e a previsão trimestral do pool.
- Demanda 2 (documentos para a IA): o documento de requisitos do Painel Indicadores Neo e o Relatório de SLA são insumos comuns às duas demandas.
- `review-sprint-18.txt`, slides 8, 9, 10, 11, 13, 14 e 15.
- `pdti-2026-2028.txt`, slides 4 a 8 (pilares e diretrizes) e 14 e 15 (SLA e bônus).
