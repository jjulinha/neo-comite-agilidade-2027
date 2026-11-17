# Kit de documentação para desenvolvimento · TI Neo Crédito · v2

| Item | Valor |
|---|---|
| O que é | Conjunto de 11 modelos de documento e 5 exemplos preenchidos, para que cada demanda tenha o documento de origem que o card cita, que a área solicitante aprova e que o agente de IA lê como contexto |
| Versão | 2.0 · 17/11/2026 · substitui a v1.0 de 16/11/2026 |
| Situação | **Proposta para o Comitê de Agilidade.** Nenhum modelo está aprovado. A adoção depende de decisão registrada em DACI no comitê (decisão de 10/11/2026: um tema por reunião). Toda a regra de escolha da seção 2 é **[ALÉM DA FONTE — decisão do usuário]** |
| Relação com as demandas do comitê | Concretiza o documento 6 do conjunto mínimo da Demanda 2 ([`D2-documentos-para-a-IA.md`](../D2-documentos-ia/D2-documentos-para-a-IA.md), seção 5) e alimenta indicadores da Demanda 3 ([`METODOLOGIA.md`](METODOLOGIA.md), seção 6) |
| Por que estes documentos e não outros | Pesquisa de mercado, o que foi adotado e descartado, e a matriz projeto real × documento: [`METODOLOGIA.md`](METODOLOGIA.md) |

**Convenções usadas em todo o kit**

- **[A CONFIRMAR]**: informação que deveria existir em documento oficial da Neo, mas que não foi recebida (por exemplo, o Inventário de Sistemas).
- **[ALÉM DA FONTE — decisão do usuário]**: proposta deste kit que não está em nenhuma fonte e precisa de decisão.
- Todo número traz a fonte e a data de extração. As contagens foram feitas sobre as exportações do Jira de 16/11/2026 (GDP e Upstream às 9h51; Downstream às 10h26).
- **Konsig** (legado) e **NeoKonsig** (reescrita) são sistemas distintos. Todo documento declara um, e só um, sistema. Uma demanda que toque os dois gera documentos separados, ligados por referência cruzada. A partir de 2027 o time inteiro vai para o Konsig; o NeoKonsig termina na Entrega 1 (DS-251).
- Pessoas aparecem pelo papel (PO, tech lead, dev, revisor, QA, área solicitante), nunca pelo nome.
- Tamanho é PP/P/M/G/GG pela régua ([`D1-pool/regua-tamanho-tempo.md`](../D1-pool/regua-tamanho-tempo.md), v1, 16/11/2026), **proposta sem decisão do comitê**. O time não usa Fibonacci nem planning poker.

---

## 0. Comece aqui: o que você está fazendo?

| Situação | Abra |
|---|---|
| Recebi um item novo e preciso saber que documento escrever | Seção 2 (passos 1 a 3) |
| Vou abrir ou refinar um card (História, Tarefa técnica, Spike, Bug) | [`modelos/CARD.md`](modelos/CARD.md) |
| A demanda tem 3 cards ou mais | [`modelos/PRD.md`](modelos/PRD.md) (núcleo) |
| A demanda tem 5 cards ou mais, ou mexe em dinheiro ou migração | [`modelos/PLANO-DE-IMPLEMENTACAO.md`](modelos/PLANO-DE-IMPLEMENTACAO.md) |
| Vou criar ou mudar integração com parceiro ou entre Konsig e NeoKonsig | [`modelos/CONTRATO-DE-INTEGRACAO.md`](modelos/CONTRATO-DE-INTEGRACAO.md) |
| O card toca CPF, telefone, log, exportação, anexo nominal ou parceiro novo | [`modelos/CHECKLIST-DADOS-E-REGULACAO.md`](modelos/CHECKLIST-DADOS-E-REGULACAO.md) |
| Tenho uma decisão difícil de reverter ou com alternativa real | [`modelos/ADR.md`](modelos/ADR.md) |
| Vou fazer deploy manual no Konsig, ou há rotina diária, ou a mesma falha voltou | [`modelos/RUNBOOK.md`](modelos/RUNBOOK.md) |
| Deu Bug em produção, Expedite, perda de dado ou pagamento errado | Modelo de Bug do [`CARD.md`](modelos/CARD.md) e [`modelos/POSTMORTEM.md`](modelos/POSTMORTEM.md) |
| Vou sair de férias, trocar de time, ou o sistema vai parar de receber time | [`modelos/PASSAGEM.md`](modelos/PASSAGEM.md) |
| É minha primeira demanda no Konsig, ou estou montando o repositório para a IA | [`modelos/SISTEMA.md`](modelos/SISTEMA.md) e [`modelos/AGENTS.md`](modelos/AGENTS.md) |

---

## 1. O que é o kit

O kit dá a cada demanda o documento de origem que hoje falta: o guia "Como escrever um card" (InnoviaX v1.0, set/2026, tutorial oficial de cards desde 13/11/2026, `contexto-mestre.md`, seção 6) exige no bloco 1 do card "referência ao documento de origem, com versão", mas não define esse documento. O kit define.

Três princípios, todos **[ALÉM DA FONTE — decisão do usuário]**:

1. **Pouco documento, proporcional ao risco.** O tamanho escolhe a trilha mínima; os gatilhos de risco acrescentam documentos em qualquer tamanho, inclusive PP. Uma demanda pequena sem risco tem só o card.
2. **Spec-anchored.** PRD, Plano e card são o contexto do agente de IA e ficam ao lado do código. Quem muda o comportamento atualiza o documento no mesmo PR. O documento não é descartado depois do código (spec-first) nem gera o código sozinho (spec-as-source). Fundamento em [`METODOLOGIA.md`](METODOLOGIA.md), seção 2.
3. **Um assunto por arquivo, um tipo por arquivo.** Cada modelo é de um tipo do Diátaxis (https://diataxis.fr/): referência (contrato, sistema, checklist), how-to (runbook, passagem), explicação (ADR) e modelos de trabalho (PRD, Plano, Card, AGENTS).

**O que o kit não faz:** não substitui o Fluxo de Desenvolvimento TI V3, as Políticas Explícitas V1 nem o Documento de Visão de projetos grandes. Ele se encaixa neles. Onde um modelo conflitar com um desses documentos, o conflito vira um ADR de mudança de documentação, e não uma regra silenciosa. Não obriga ferramenta nova (Spec Kit, Kiro, Log4brains) nem escreve no Jira.

**O que mudou da v1 para a v2**

| v1 (16/11/2026) | v2 (17/11/2026) |
|---|---|
| Documento escolhido só pelo tamanho, que só existia depois do PRD | Tamanho provisório pela descrição + gatilhos de risco (seção 2) |
| PRD "curto" com 10 seções obrigatórias | PRD núcleo de uma página (P e M) e completo (G e GG), com RN em EARS, não objetivos e tabela de decisão |
| Card de 10 blocos para todo tipo | Card mínimo por tipo: História, Tarefa técnica/Spike, Bug; DoD explícita; nota de passagem de etapa |
| ADR com DACI e impacto em 8 documentos em toda decisão | ADR enxuto (Nygard/MADR mínimo), Y-statement opcional, ideias abandonadas |
| `CLAUDE.md` como modelo próprio | `AGENTS.md` canônico; o `CLAUDE.md` do repositório tem uma linha: `@AGENTS.md` |
| Sem modelo de integração, operação, incidente, dado pessoal, sistema ou passagem | `CONTRATO-DE-INTEGRACAO`, `RUNBOOK`, `POSTMORTEM`, `CHECKLIST-DADOS-E-REGULACAO`, `SISTEMA`, `PASSAGEM` |
| Indicadores de adoção no README | Movidos para [`METODOLOGIA.md`](METODOLOGIA.md), seção 6, sem alteração dos números |

---

## 2. Qual documento usar

Toda a regra desta seção é **[ALÉM DA FONTE — decisão do usuário]**. A régua PP/P/M/G/GG é proposta sem decisão (`D1-pool/regua-tamanho-tempo.md`, v1, 16/11/2026).

### Passo 1 · Tamanho provisório

Use o tamanho do [`pool-2027-plano.xlsx`](../D1-pool/pool-2027-plano.xlsx) (aba Pool 2027) ou estime pela descrição do item: **PP** 1–2 cards, **P** 3–4, **M** 5–9, **G** 10–20, **GG** mais de 20. Na dúvida, comece pela trilha mais leve e promova o documento quando a contagem de cards subir. Isso resolve a circularidade da v1, em que o tamanho só existia depois do PRD.

### Passo 2 · Trilha por tamanho

| Tamanho | Documentos da trilha | Observação |
|---|---|---|
| **PP** (1–2 cards) | Só [`CARD.md`](modelos/CARD.md), no modelo do tipo (História, Tarefa técnica/Spike ou Bug) | Sem PRD e sem Plano |
| **P** (3–4) | `CARD.md` + [`PRD.md`](modelos/PRD.md) **núcleo de uma página**: problema, objetivo, não objetivos e fora de escopo, RN em EARS, critérios Dado/Quando/Então | O núcleo pode morar no épico do Jira ou em `docs/`. Sem Plano |
| **M** (5–9) | PRD núcleo + [`PLANO-DE-IMPLEMENTACAO.md`](modelos/PLANO-DE-IMPLEMENTACAO.md) curto: entregas, deploy e rollback, teste e datas pela régua | |
| **G** (10–20) | PRD completo + Plano completo. **Apetite** (teto de tempo que a área aceita) recomendado | A régua manda quebrar GG em entregas G ou M antes do pool (`regua-tamanho-tempo.md`, seção 3) e recomenda estender a regra ao G (quebrar em M), decisão pendente no comitê (seção 7) |
| **GG** (mais de 20) | Como G, com **apetite obrigatório** e a seção "Desenho e alternativas" do Plano quando houver integração nova ou trade-off real | |
| **Toda trilha** | PRD, Plano e cards são o contexto do agente de IA (spec-anchored). Quem muda o comportamento atualiza o documento no mesmo PR | |

### Passo 3 · Gatilhos por risco (somam-se à trilha, em qualquer tamanho, inclusive PP)

**Tamanho × risco: o que se acrescenta**

| Trilha | Integração externa nova ou alterada | Dinheiro | Dado pessoal | Migração |
|---|---|---|---|---|
| **PP** | + `CONTRATO-DE-INTEGRACAO.md` por contraparte; + `RUNBOOK.md` se houver rotina agendada ou falha conhecida | Promove a P: PRD núcleo com tabela de decisão e RN em EARS; um teste por linha da tabela; `ADR.md`; seção "Corte" do Plano (solta) com go/no-go por passo na primeira ida a produção | Checklist, parte B, no PR | Só a seção "Corte" do Plano, solta |
| **P** | Igual a PP | PRD núcleo **com** tabela de decisão; um teste por linha; ADR; seção "Corte" solta | Checklist parte A no PRD e parte B no PR | Seção "Corte" solta |
| **M** | Igual a PP | Tabela de decisão no PRD; um teste por linha; ADR; seção "Corte" do Plano com go/no-go | Checklist A no PRD, B no PR | Seção "Corte" do Plano |
| **G** | Igual a PP | Igual a M | Igual a M | Igual a M |
| **GG** | Igual a PP, e "Desenho e alternativas" no Plano | Igual a M | Igual a M | Igual a M |

Detalhe de cada gatilho:

- **Integração externa nova ou alterada** (API, SFTP, fila, inclusive entre Konsig e NeoKonsig): [`CONTRATO-DE-INTEGRACAO.md`](modelos/CONTRATO-DE-INTEGRACAO.md), um por contraparte. Se houver rotina agendada ou falha conhecida, acrescente [`RUNBOOK.md`](modelos/RUNBOOK.md).
- **Dado pessoal** (campo novo, log, exportação, relatório com CPF, anexo com relação nominal, parceiro novo recebendo dado, massa para IA): [`CHECKLIST-DADOS-E-REGULACAO.md`](modelos/CHECKLIST-DADOS-E-REGULACAO.md) no PR. Resposta "sim" a tratamento novo ou a compartilhamento novo aciona o DPO; o RIPD não é escrito pelo dev. Dado de cartão (PAN/CVV) nunca entra.
- **Dinheiro** (pagamento, liquidação, repasse, remuneração de correspondente, decisão automática de crédito): PRD com tabela de decisão e RN em EARS, mesmo em P; um cenário de teste por linha da tabela; [`ADR.md`](modelos/ADR.md) obrigatório; seção de corte do Plano com go/no-go por passo na primeira ida a produção.
- **Migração** (dados, repositório, infraestrutura, troca de parceiro, mudança de layout, modo sombra para efeito real): seção "Corte" do Plano com go/no-go, tempo máximo e rollback por passo, ou a declaração de que não há rollback e qual é a contingência. Em PP/P sem Plano, use só essa seção.

**Demais gatilhos**

| Gatilho | Documento | Observação |
|---|---|---|
| Decisão difícil de reverter ou com alternativa real, inclusive de processo ou de documentação | [`ADR.md`](modelos/ADR.md) | Independe do tamanho. Um G sem decisão nova não gera ADR; um PP que muda um padrão gera |
| Regulatória | Norma de origem e data de vigência no PRD | Classe de serviço "data fixa" (Fixed Date) |
| Incidente: P1/P2 da tabela do PDTI (slide 14), Expedite, Bug em produção, perda de dado, pagamento errado | [`POSTMORTEM.md`](modelos/POSTMORTEM.md) em até 5 dias úteis | Todo Bug, de qualquer tamanho, usa o modelo de Bug do `CARD.md` com causa (fato ou hipótese), versão ou deploy e card de origem |
| Rotina recorrente, deploy manual ou falha que já ocorreu duas vezes | [`RUNBOOK.md`](modelos/RUNBOOK.md) | Inclui o registro de release enquanto o Konsig não tem CI/CD (US-43, Backlog, `upstream_16-11.csv`, 16/11/2026 9h51) |
| Saída de pessoa (férias, ausência, troca de time) ou encerramento de sistema (NeoKonsig na Entrega 1) | [`PASSAGEM.md`](modelos/PASSAGEM.md) | Passar card de etapa (Dev → Revisor → QA → PO) usa a nota de passagem do `CARD.md`, não este modelo |
| Primeira demanda num sistema, ou dev novo no sistema | Ler [`SISTEMA.md`](modelos/SISTEMA.md) (Konsig primeiro) e o [`AGENTS.md`](modelos/AGENTS.md) do repositório | Um `SISTEMA.md` e um `AGENTS.md` por repositório |

**Exemplos da realidade da Neo** (`epicos_downstream_16-11.csv`, 16/11/2026 10h26; tamanhos de `pool-2027-plano.xlsx`). A matriz completa, com os 11 projetos, está em [`METODOLOGIA.md`](METODOLOGIA.md), seção 5.

- Quitação Fase 1 (DS-418, Konsig, 2 cards) → PP: só os cards.
- Quitação Fase 2 (DS-500, Konsig, 8 cards) → M com gatilho de dinheiro e de migração (modo sombra): PRD núcleo com tabela de decisão, Plano curto com seção "Corte", ADR, checklist (CPF na exportação). Exemplo preenchido: [`exemplos/quitacao/GDP-76_quitacao-fase-2-motor.md`](exemplos/quitacao/GDP-76_quitacao-fase-2-motor.md).
- Correção de vulnerabilidades (DS-65, Konsig, 20 cards) → G técnico, sem item GDP: PRD e Plano nomeados pela chave do épico; ADR para cada mudança de padrão de segurança (por exemplo, o token na URL do DS-81).
- Parceiros, Entrega 1 (DS-251, NeoKonsig, 83 cards) → GG em fim de vida: não se abre Plano novo; o documento que falta é a `PASSAGEM.md` (estado de parada) e o contrato da fila NeoKonsig → Konsig.
- Cartão de crédito consignado (GDP-38, Konsig, decisão de 13/11/2026) → GG: a Visão do Cartão v6 (03/11/2026) faz o papel de PRD-mãe depois de corrigida para o Konsig; um PRD por bloco, um contrato por contraparte.

---

## 3. O fluxo: em que momento cada documento nasce e quem aprova

```
GDP ─────────► Upstream ───────────────────────────────► Downstream ──────────────────────────────────► Produção
item GDP-n     US-n                                      épico DS-n → cards DS-n
roteiro GDP    PRD núcleo/completo · checklist A         Plano (+ Corte) · cards (CARD.md)               RUNBOOK · registro de release
               CONTRATO (integração) · ADR (decisão)     checklist B no PR · docs/ atualizado no PR      POSTMORTEM (incidente) · PASSAGEM (saída)
               apetite (G/GG)                            Em desenvolvimento → Code Review → QA Teste →
                                                         Aprovação POs → Waiting for deploy → Concluído
```

| Etapa | Board e status no Jira | Documento que nasce aqui | Quem escreve | Quem aprova | Libera a etapa seguinte |
|---|---|---|---|---|---|
| 1. Entrada | GDP: Backlog Upstream → Priorização Upstream | Nenhum documento do kit. Roteiro de abertura do GDP (Solicitante, Área solicitante, Contexto da solicitação, Descrição do problema ou necessidade, Como o processo funciona atualmente, Consequências do cenário atual). **Tamanho provisório** (passo 1). Em G/GG, o **apetite** | Área solicitante | Gestão da TI (priorização) | Item GDP priorizado, com o roteiro preenchido. Item com o modelo vazio não é dimensionado |
| 2. Análise funcional | Upstream: Análise funcional | **PRD núcleo** (P em diante); em G/GG, PRD completo. **Checklist parte A** colado no PRD | Analista funcional / PO | — | PRD em revisão |
| 3. Prototipação | Upstream: Prototipação | Seção de fluxo do PRD, com link do protótipo | Analista / UX | Área solicitante | Protótipo validado |
| 4. Especificação técnica + testes | Upstream: Especificação técnica + testes | Tabela de decisão e RN em EARS (gatilho de dinheiro); **CONTRATO-DE-INTEGRACAO** (gatilho de integração); **ADR** (decisão); "Desenho e alternativas" (GG) | PO + tech lead | PO (PRD); tech lead (ADR técnico, contrato); Comitê de Agilidade (ADR de processo ou de documentação) | PRD revisado; ADR aceito; contrato com os campos obrigatórios |
| 5. Aprovação | Upstream: Aprovação solicitantes → Concluído Upstream | PRD com aprovação registrada e tamanho pela régua (Políticas Explícitas V1, seção 3.8: dimensionamento inicial obrigatório ao concluir no Upstream). Checklist: DPO ou Segurança & Conformidade acionados quando a resposta pedir | PO | **Área solicitante**, no PDF ou link do PRD (seção 4) | Demanda pronta para o Downstream |
| 6. Planejamento | Downstream: criação do épico (projeto = épico, decisão de 13/11/2026) | **Plano** (M em diante), com seção **Corte** se houver dinheiro ou migração (em PP/P, só a seção Corte) | Tech lead + PO | PO; o go/no-go de cada passo do corte é registrado por PO e tech lead | Épico e cards criados |
| 7. Cards | Downstream: Backlog | **Card** no modelo do tipo, com DoR como lista de refinamento | PO (Histórias, regra 1 do experimento S19); time (Tarefas, Bugs) | Refinamento | Card pronto para entrar |
| 8. Construção e teste | Em desenvolvimento → Code Review → QA Teste → Aprovação POs | Código + `docs/` atualizado no **mesmo PR**; **checklist parte B** no PR se tocar dado pessoal; nota de passagem de etapa no card | Dev, revisor, QA, PO, com responsável em cada etapa (regra 2 do experimento S19) | Revisor (PR); QA (cenários); PO (card) | Card aprovado |
| 9. Implantação | Waiting for deploy → Concluído | **RUNBOOK** de deploy e rollback (Konsig manual) e linha no registro de release; runbook da rotina nova antes da primeira execução | Tech lead / infraestrutura | Tech lead | Em produção |
| 10. Registro | Concluído (com Categorias, Descrição, Classe de serviço e Tipo, regra 3 do experimento S19) | PRD e Plano com status final; ADR atualizado; realizado × estimado registrado na régua | PO + tech lead | — | Documentos fechados |
| Em qualquer momento | — | **POSTMORTEM** (até 5 dias úteis após o incidente); **PASSAGEM** (antes da saída ou da parada); **SISTEMA.md** e **AGENTS.md** (na criação ou migração do repositório, mantidos em todo PR que mude o que descrevem) | Tech lead (postmortem, sistema, agents); quem sai (passagem) | Tech lead; ações do postmortem viram cards no Jira | — |

Os status acima são os das exportações de 16/11/2026 (`upstream_16-11.csv`, 9h51; `downstream_16-11.csv`, 10h26) e do fluxo do `contexto-mestre.md`, seção 3. A coluna de documentos e a de aprovação são proposta **[ALÉM DA FONTE — decisão do usuário]**.

---

## 4. Onde ficam os arquivos: Jira × repositório

| Onde | O quê |
|---|---|
| **Jira** | Item GDP (roteiro de abertura); card (modelo do `CARD.md` colado na descrição, inclusive DoD e nota de passagem); PRD núcleo de **P**, quando o PO preferir no épico; link para cada documento do repositório |
| **Descrição do PR/MR** | Checklist de dados, parte B; cenários cobertos; resultado dos testes com o comando usado |
| **Repositório do sistema, pasta `docs/`** | PRD (P em diante, salvo P no épico), Plano, ADR, contrato, runbook, postmortem, passagem e `SISTEMA.md`. Um sistema por repositório e por documento |
| **Raiz do repositório** | `AGENTS.md` (canônico) e `CLAUDE.md` com uma linha só: `@AGENTS.md` |
| **PDF ou link onde a área solicitante lê** (Drive) | PRD e documentos de negócio, para leitura e aprovação de quem não usa Git. O PDF ou o link aponta para a versão do repositório; a aprovação registrada cita essa versão |
| **Repositório do Comitê de Agilidade** | ADR de processo ou de documentação, sem sistema (ex.: [`exemplos/processo/ADR-0001_CHAVE-A-CONFIRMAR_nota-vigencia-fluxo-v3.md`](exemplos/processo/ADR-0001_CHAVE-A-CONFIRMAR_nota-vigencia-fluxo-v3.md)) |

**Estrutura de `docs/` no repositório de um sistema** **[ALÉM DA FONTE — decisão do usuário]**:

```
<repositório do sistema>/
├── AGENTS.md                ← instruções para agentes e para dev novo (modelos/AGENTS.md)
├── CLAUDE.md                ← uma linha: @AGENTS.md
└── docs/
    ├── README.md            ← índice: chave do Jira, título, tipo, status, versão
    ├── SISTEMA.md           ← referência do sistema (modelos/SISTEMA.md)
    ├── prd/                 GDP-76_quitacao-fase-2-motor.md
    ├── planos/              DS-500_plano-quitacao-fase-2.md
    ├── adr/                 ADR-0001_GDP-76_pagamento-quitacao-pagauto-api-bb.md
    ├── integracoes/         banco-do-brasil.md
    ├── runbooks/            deploy-konsig-api.md
    ├── postmortems/         2026-09-18_DS-272_judit-401.md
    └── passagem/            DS-251_neokonsig-estado-de-parada.md
```

- Demanda do Konsig: repositório do Konsig. Demanda do NeoKonsig: repositório do NeoKonsig. Nunca um documento para os dois.
- **Pasta provisória** **[ALÉM DA FONTE — decisão do usuário]**. O Konsig está em migração de repositórios para o GitLab gerenciado (DS-175, há 6 sprints em aberto segundo a Review da Sprint 18, 06/11/2026 16h46; épico DS-495 em Backlog, `epicos_downstream_16-11.csv`, 16/11/2026 10h26), e qual repositório do Konsig recebe `docs/` é **[A CONFIRMAR]**. Até a definição:
  1. o documento vai para `docs/` do repositório do Konsig em que o card abre o MR, com a estrutura acima;
  2. documento que nasce antes de haver MR (PRD no Upstream) fica no Drive onde a área solicitante aprova e entra no repositório no primeiro MR da demanda;
  3. quando o DS-175/DS-495 definir o repositório, o tech lead move os arquivos (`git mv`) e atualiza os links dos cards.
- O Documento de Visão de projetos grandes e os documentos de requisito hoje guardados no Drive (Requisitos V04 da Quitação, escopo v7 do JUDIT, V6 do NMP) continuam no Drive. O PRD do repositório aponta para eles pelo ID do Drive e traz para dentro só as RN, a tabela de decisão e os critérios, com versão.

**Versionamento e status.** Versão `0.x` em rascunho ou revisão, `1.0` na aprovação, `1.1`/`1.2` para ajustes sem mudança de escopo, `2.0` para mudança de escopo, que exige nova aprovação e revisão dos cards que citam a versão anterior (achados pelo campo "Referência" do card). Toda alteração entra por PR; o histórico do Git é a trilha de auditoria. Status: PRD (Rascunho · Em revisão · Aprovado · Em execução · Concluído · Substituído); ADR (Proposto · Aceito · Rejeitado · Substituído por ADR-nnnn · Obsoleto); Plano (Rascunho · Aprovado · Em execução · Concluído · Cancelado).

**Ligação com o Jira.** Regra mínima de rastreabilidade: GDP ↔ US ↔ épico DS associados no Jira e citados no PRD. Hoje esse vínculo falta em projeto prioritário: o GDP-76 não aponta para o US-69, o DS-418 nem o DS-500 (`insumos/quitacao-estado-e-faseamento.md`, seção 4.3).

---

## 5. Convenção de nomes

Nomes em minúsculas, sem acento, palavras separadas por hífen; a chave do Jira em maiúsculas. Toda a convenção é **[ALÉM DA FONTE — decisão do usuário]**.

| Documento | Caminho e nome | Exemplo |
|---|---|---|
| PRD | `docs/prd/<chave>_<assunto>.md`. Chave = GDP; sem GDP, a US; sem GDP nem US (épico técnico), o épico DS | `GDP-76_quitacao-fase-2-motor.md` · `DS-65_correcao-de-vulnerabilidades.md` |
| PRD de bloco ou entrega de um GG | `docs/prd/<chave GDP>_E<n>_<assunto>.md` | `GDP-38_E1_originacao-cartao.md` |
| Plano | `docs/planos/<épico DS>_plano-<assunto>.md` | `DS-500_plano-quitacao-fase-2.md` |
| Seção Corte solta (PP/P) | `docs/planos/<chave>_corte-<assunto>.md` | `DS-175_corte-repositorios-gitlab.md` |
| ADR | `docs/adr/ADR-<nnnn>_<chave>_<assunto>.md`, numeração própria por repositório | `ADR-0001_GDP-76_pagamento-quitacao-pagauto-api-bb.md` |
| ADR de processo sem item no Jira | `ADR-<nnnn>_CHAVE-A-CONFIRMAR_<assunto>.md`, no repositório do comitê, renomeado quando a Tarefa for aberta | `ADR-0001_CHAVE-A-CONFIRMAR_nota-vigencia-fluxo-v3.md` |
| Contrato de integração | `docs/integracoes/<contraparte>.md`; se houver lugar comum aos dois sistemas, `<contraparte>-<sistema>.md` | `orbitall-arquivos.md` · `neokonsig-fila-corban.md` |
| Runbook | `docs/runbooks/<assunto>.md` | `nmp-importacao-abr.md` · `deploy-konsig-api.md` |
| Postmortem | `docs/postmortems/AAAA-MM-DD_<chave>_<assunto>.md` (data do incidente) | `2026-09-18_DS-272_judit-401.md` |
| Passagem | `docs/passagem/<chave>_<assunto>.md` | `DS-251_neokonsig-estado-de-parada.md` |
| Sistema | `docs/SISTEMA.md` (um por repositório) | — |
| Agentes | `AGENTS.md` e `CLAUDE.md` na raiz | — |
| Checklist de dados | Sem arquivo: parte A no PRD, parte B na descrição do PR | — |
| Card | Sem arquivo: descrição do card no Jira | — |

Os nomes dos modelos no kit são sempre em maiúsculas (`PRD.md`, `ADR.md`, `PLANO-DE-IMPLEMENTACAO.md`, `CARD.md`, `AGENTS.md`, `CONTRATO-DE-INTEGRACAO.md`, `RUNBOOK.md`, `POSTMORTEM.md`, `CHECKLIST-DADOS-E-REGULACAO.md`, `SISTEMA.md`, `PASSAGEM.md`); o arquivo copiado para o repositório segue a tabela acima.

---

## 6. Modelos e exemplos

### 6.1 Modelos (`modelos/`)

| Modelo | Tipo (Diátaxis) | Para quê | Gatilho |
|---|---|---|---|
| [`PRD.md`](modelos/PRD.md) | Modelo de trabalho | O quê e por quê. Núcleo de uma página (P, M) e seções adicionais (G, GG): RN em EARS, não objetivos, tabela de decisão, apetite | P em diante; dinheiro em qualquer tamanho |
| [`PLANO-DE-IMPLEMENTACAO.md`](modelos/PLANO-DE-IMPLEMENTACAO.md) | Modelo de trabalho | Como entregar (equivale a `plan.md` + `tasks.md` do Spec Kit, sem a ferramenta): trilha curta para M; desenho e corte para G/GG, migração e dinheiro | M em diante; seção Corte em qualquer tamanho com dinheiro ou migração |
| [`CARD.md`](modelos/CARD.md) | Modelo de trabalho | Card mínimo por tipo (História, Tarefa técnica/Spike, Bug), DoR como lista de refinamento, DoD explícita, nota de passagem de etapa | Todo card |
| [`AGENTS.md`](modelos/AGENTS.md) | Modelo de trabalho | Instruções para agentes de código e dev novo, com a "constituição" do time. Substitui o `CLAUDE.md` da v1 | Um por repositório, Konsig primeiro |
| [`ADR.md`](modelos/ADR.md) | Explicação | Registro de decisão enxuto (Nygard/MADR mínimo), com ideias abandonadas e Y-statement opcional | Decisão difícil de reverter ou com alternativa real; dinheiro |
| [`CONTRATO-DE-INTEGRACAO.md`](modelos/CONTRATO-DE-INTEGRACAO.md) | Referência | Ficha por contraparte: protocolo, autenticação, certificado, layout, horários, idempotência, erros, contato por papel | Integração nova ou alterada |
| [`SISTEMA.md`](modelos/SISTEMA.md) | Referência | arc42 enxuto (seções 3, 9 e 11) + C4 nível 1. Porta de entrada no sistema | Um por sistema, Konsig primeiro |
| [`CHECKLIST-DADOS-E-REGULACAO.md`](modelos/CHECKLIST-DADOS-E-REGULACAO.md) | Referência | Perguntas sim/não que acionam o DPO ou Segurança & Conformidade | Dado pessoal; norma; fornecedor novo |
| [`RUNBOOK.md`](modelos/RUNBOOK.md) | How-to | Rotina recorrente, falha conhecida, deploy e rollback manual, registro de release | Rotina, deploy manual, falha repetida |
| [`PASSAGEM.md`](modelos/PASSAGEM.md) | How-to | Estado de parada de sistema ou entrega; saída de pessoa | NeoKonsig na Entrega 1; férias, ausência, troca de time |
| [`POSTMORTEM.md`](modelos/POSTMORTEM.md) | Modelo de trabalho | Análise pós-incidente sem culpa, com gatilho definido antes | P1/P2, Expedite, Bug em produção, perda de dado, pagamento errado |

### 6.2 Exemplos preenchidos (`exemplos/`)

| Exemplo | O que mostra |
|---|---|
| [`quitacao/GDP-76_quitacao-fase-2-motor.md`](exemplos/quitacao/GDP-76_quitacao-fase-2-motor.md) | **PRD v2**, trilha M, núcleo com gatilho de dinheiro: RN em EARS, não objetivos, tabela de decisão com um teste por linha (DS-508) e respostas do checklist. Konsig. O Documento de Requisitos V04 (26/10/2026) não foi recebido: o conteúdo vem dos cards do DS-500 [A CONFIRMAR] |
| [`quitacao/DS-500_plano-quitacao-fase-2.md`](exemplos/quitacao/DS-500_plano-quitacao-fase-2.md) | Plano do mesmo épico, **estrutura v1: não siga a numeração de seções** (a do modelo v2 é outra). Regras do PRD remapeadas para a numeração do PRD v2 (RN01 a RN08) em 17/11/2026. Ainda **sem** a seção Corte que o gatilho de dinheiro e de migração (modo sombra) exige na v2: pendência registrada no PRD do exemplo |
| [`quitacao/ADR-0001_GDP-76_pagamento-quitacao-pagauto-api-bb.md`](exemplos/quitacao/ADR-0001_GDP-76_pagamento-quitacao-pagauto-api-bb.md) | ADR técnico: componente de pagamento da quitação (PagAuto + API BB). Formato v1: traz DACI e impacto em documentos, que o ADR v2 dispensa em decisão técnica |
| [`quitacao/ADR-0002_GDP-76_ordem-das-fases-quitacao.md`](exemplos/quitacao/ADR-0002_GDP-76_ordem-das-fases-quitacao.md) | ADR técnico: ordem das fases, integração bancária por último. Uma decisão por ADR. Formato v1, como o ADR-0001 |
| [`processo/ADR-0001_CHAVE-A-CONFIRMAR_nota-vigencia-fluxo-v3.md`](exemplos/processo/ADR-0001_CHAVE-A-CONFIRMAR_nota-vigencia-fluxo-v3.md) | ADR de mudança de documentação: nota de vigência sobre o Fibonacci no Fluxo de Desenvolvimento TI V3 |

Só o PRD de exemplo foi reescrito na estrutura v2. O Plano DS-500 e os dois ADRs técnicos da Quitação continuam na estrutura v1: o conteúdo vale, a forma não. O Plano tem outra numeração de seções (siga a do modelo v2); os ADRs trazem DACI e impacto em documentos, seções que o ADR v2 reserva para decisão de processo ou de documentação. O Plano cita as regras do PRD pela numeração do PRD v2.

---

## 7. Como usar com IA (spec-driven, nível spec-anchored)

**A regra.** O agente de IA não recebe "o pedido"; recebe o card, o PRD citado no card, os ADRs aceitos do assunto, o Plano do épico, o contrato da integração tocada e o `AGENTS.md` do repositório. Quando o comportamento muda, o documento muda no mesmo PR. É o nível spec-anchored da análise de Birgitta Böckeler (Thoughtworks), e não Spec Kit ou Kiro como processo obrigatório: ver [`METODOLOGIA.md`](METODOLOGIA.md), seção 2.

### 7.1 O que fornecer e o que não fornecer

| Para produzir | Entregue à IA | Não entregue |
|---|---|---|
| PRD | Descrição do item GDP já anonimizada; anotações da análise funcional; [`modelos/PRD.md`](modelos/PRD.md); `AGENTS.md` e `docs/SISTEMA.md` do repositório | Planilhas operacionais com dados de clientes; contratos; prints de tela com CPF ou nome |
| ADR | Contexto técnico escrito pelo tech lead; ADRs anteriores do repositório; trecho do Inventário de Sistemas | Credenciais, endereços internos de servidores, identificadores de contas |
| Contrato | Manual ou especificação do parceiro (OpenAPI/AsyncAPI quando houver), com versão; exemplos de requisição e resposta **anonimizados** | Certificados, chaves, senhas, payload de produção |
| Plano | PRD aprovado; ADRs aceitos; régua de tamanho; [`modelos/PLANO-DE-IMPLEMENTACAO.md`](modelos/PLANO-DE-IMPLEMENTACAO.md) | — |
| Cards | PRD aprovado; Plano; [`modelos/CARD.md`](modelos/CARD.md); o guia InnoviaX | Massa de produção para os cenários de teste |
| Código | Card, PRD, ADR, Plano, contrato; `AGENTS.md` do repositório | — |

### 7.2 O que a IA devolve

- Rascunho no modelo, com cada lacuna marcada **[A CONFIRMAR]** e cada acréscimo marcado **[ALÉM DA FONTE — decisão do usuário]**.
- Lista de perguntas abertas, cada uma com quem responde (papel).
- RN reescritas em EARS e cenários Dado/Quando/Então, um teste por linha da tabela de decisão.
- Sugestão de quebra dos cards (guia, seção 06), com o critério usado.
- Cenários de teste com **massa sintética**: válida no formato, fictícia no conteúdo.

### 7.3 O que exige revisão humana, sempre

| Item | Quem revisa |
|---|---|
| RN, tabela de decisão e critérios de aceite | PO e área solicitante |
| Decisão do ADR e alternativas descartadas | Tech lead; comitê quando for padrão, processo ou documentação |
| Tamanho estimado, apetite e datas do Plano | PO e tech lead, contra a régua (os parâmetros da régua são editados só pelo responsável, decisão de 10/11/2026) |
| Sistema afetado (Konsig ou NeoKonsig) | Tech lead |
| Ausência de dado pessoal no texto final | Autor do documento, antes do commit |
| `AGENTS.md` | Tech lead, linha a linha. Nunca gerado por `/init` sem revisão: arquivos de contexto tendem a não melhorar a taxa de sucesso e sobem o custo de inferência em mais de 20%; os escritos por humano se saem um pouco melhor que os gerados por LLM, e o arquivo ajuda quando traz prática não padrão (Gloaguen et al., https://arxiv.org/abs/2602.11988). Percentuais por tipo de arquivo: [A CONFIRMAR no artigo] |
| Código gerado | Revisor no Code Review e QA no QA Teste, como qualquer código |

### 7.4 AGENTS.md e CLAUDE.md

- `AGENTS.md` é o arquivo canônico (formato aberto, sob a Agentic AI Foundation/Linux Foundation desde 09/12/2025: https://openai.com/index/agentic-ai-foundation/). Curto (menos de 200 linhas), escrito por humano, só com o que o modelo não sabe: comandos, regras sem exceção, nomes de status, armadilhas do legado.
- `CLAUDE.md` do repositório tem uma linha: `@AGENTS.md`. Outros agentes (Copilot, Cursor) recebem só um apontador para o `AGENTS.md`. Dois arquivos de regra que dizem a mesma coisa divergem com o tempo.
- Quais agentes o time usa e com que aprovação: **[A CONFIRMAR]**. A regra de uso de IA (documento 1 da Demanda 2) ainda não foi aprovada.
- As regras do `CLAUDE.md` v1 que faltavam no modelo (Fibonacci e Melhorias Scrum TI V2; usar os modelos do kit; um commit por mudança lógica; QA Teste não substituído pelos testes do agente; Inventário de Sistemas como fonte da stack) foram incorporadas ao [`modelos/AGENTS.md`](modelos/AGENTS.md) em 17/11/2026 (constituição, regra 8, e seções 1, 3, 5 e 6).

**A IA não decide prioridade, não altera parâmetros da régua, não escreve no Jira e não é conectada a ele** enquanto a regra de uso de IA não estiver aprovada e o conector Atlassian não tiver sido validado com a segurança (`contexto-mestre.md`, seção 9; [`D2-documentos-para-a-IA.md`](../D2-documentos-ia/D2-documentos-para-a-IA.md), seção 4.2).

---

## 8. Regra de LGPD para todos os documentos do kit

1. **Nenhum dado pessoal** em PRD, ADR, Plano, card, contrato, runbook, postmortem, passagem, `SISTEMA.md` ou `AGENTS.md`: nada de CPF, CNPJ de pessoa física empresária, nome de cliente, e-mail, telefone, matrícula, número de contrato ou de proposta real, nem número de cartão. Isso vale também para exemplos, cenários de teste, prints e anexos.
2. **Pessoas da Neo por papel**, não por nome: "PO", "tech lead", "dev", "revisor", "QA", "área Financeiro".
3. **Massa de teste sintética.** O guia pede dado concreto nos cenários de teste (seção 04) e usa CPF como exemplo de campo (seção 03). Dado concreto aqui significa um valor fictício que exercita a regra (por exemplo, "CPF com dígito verificador inválido", "proposta fictícia na situação AND - AGUARD QUITACAO"), nunca um valor copiado de produção.
4. **Dado de cartão nunca entra**, nem mascarado: PAN, CVV e trilha ficam fora de qualquer documento, log de exemplo ou prompt de IA (Visão do Cartão v6, riscos R18 e R19, 03/11/2026).
5. **O PRD declara o tratamento de dado pessoal da demanda** (checklist, parte A): quais categorias de dado, finalidade, mascaramento por perfil, retenção e compartilhamento. Declarar o tratamento é diferente de expor o dado. O RIPD, quando necessário, é do DPO, não do PRD.
6. **Antes do commit**, o autor confere o documento contra os itens 1 a 4. A anonimização automática das exportações do Jira já deixou resíduos (quatro ocorrências de e-mail codificado em URL; [`D2-documentos-para-a-IA.md`](../D2-documentos-ia/D2-documentos-para-a-IA.md), seção 4.1, risco R3), por isso a conferência humana não é opcional.

Os itens 1 a 6 são proposta **[ALÉM DA FONTE — decisão do usuário]** e devem ser conciliados com a regra de uso de IA e de anonimização, que depende de parecer do DPO. Fluxo de acionamento do DPO: **[A CONFIRMAR]**.

---

## 9. O problema medido

O kit resolve um problema medido, não estético. Na exportação do Downstream de 16/11/2026, 10h26 (`downstream_16-11.csv`), entre os 363 cards (Tarefa, História e Bug):

| O que o card traz na descrição | Cards | Critério de contagem |
|---|---|---|
| Nenhuma descrição | 80 de 363 | campo vazio |
| História no formato "eu quero" | 23 de 363 | texto "eu quero" |
| Critério de aceite | 21 de 363 | "critério(s) de aceite" |
| Cenário com "dado … então" | 7 de 363 | expressão regular sem diferenciar maiúsculas: `\bdado\b` e `\bentão\b` no mesmo texto. Com maiúsculas exatas ("Dado", "Então") o resultado cai para 4 (DS-299 a DS-302); a medição recorrente usa o critério sem diferenciar maiúsculas |
| DoR | 14 de 363 | "DoR" ou "Definition of Ready" |
| DoD | 0 de 363 | "DoD" ou "Definition of Done" |
| Bug com causa raiz | 1 de 31 Bugs | "causa raiz" |
| Bug com item associado (card de origem) | 1 de 31 Bugs | campo "itens associados" preenchido; nenhum Bug tem os dois (causa raiz e item associado) |

E a rastreabilidade entre os boards é parcial: 15 dos 35 épicos do Downstream têm item do GDP associado (`downstream_16-11.csv`, 16/11/2026 10h26), e o GDP-76 (Quitação), em Downstream, não aponta para nenhum épico (`gdp_16-11.csv`, 16/11/2026 9h51).

**Onde estão os vazios.** Dos 80 cards sem descrição, 48 são Tarefa, 28 História e 4 Bug (`downstream_16-11.csv`, 16/11/2026 10h26). Por isso a v2 traz um card mínimo para Tarefa técnica e para Bug, e não só para História. Na Sprint 19 a descrição subiu para 60 de 63 cards, mas só 8 de 19 Histórias trazem critério de aceite (mesma fonte, cards criados de 09/11 a 16/11/2026): o problema passou de ausência de texto para qualidade do card.

**Onde está o gargalo.** Na Sprint 18, 66% do ciclo mediano aconteceu depois do código pronto (`contexto-mestre.md`, seção 5; Review da Sprint 18, extração de 06/11/2026 16h46). O que falta é documento de origem, critério de pronto e passagem entre etapas, não um método de especificação mais sofisticado.

A série por sprint e os indicadores de adoção do kit estão em [`METODOLOGIA.md`](METODOLOGIA.md), seção 6.

---

## 10. Decidido, em aberto, bloqueado

| Situação | Item |
|---|---|
| **Decidido** | Guia InnoviaX como tutorial de cards (13/11/2026). Projeto = épico (13/11/2026). Regras do Downstream da S19 (10/11/2026). Konsig e NeoKonsig distintos; cartão no Konsig legado (13/11/2026). |
| **Em aberto** | Adoção deste kit e da regra de escolha da seção 2. Faixas PP a GG e referências de tempo da régua. Teto de tamanho do card ("cabe ou quebra"), que o guia cita na seção 06 e ainda não existe. Repositório que recebe `docs/` no Konsig (DS-175/DS-495) e a pasta provisória da seção 4. Gatilho de postmortem pela tabela P1–P4 do PDTI (slide 14). Agentes de IA em uso no time. Dono da sustentação do NeoKonsig em 2027. Divergência sobre a realocação para o Konsig: a regra recebida diz "time inteiro" depois da Entrega 1 do NeoKonsig; `D1-pool/D1-pool-2027-roteiro-e-pendencias.md` (§4 item 1 e §5 item 1) recomenda realocar metade [A CONFIRMAR decisão registrada]. |
| **Bloqueado** | Stack por sistema no `AGENTS.md` e no `SISTEMA.md`: depende do Inventário de Sistemas e do "Konsig Arquitetura", não recebidos. Uso da IA com conteúdo do Jira: depende da regra de uso de IA (Demanda 2, documento 1). Enquadramento regulatório do checklist: depende de parecer jurídico/compliance. |
