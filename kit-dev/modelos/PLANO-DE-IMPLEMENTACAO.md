<!--
MODELO · Plano de Implementação · Kit de documentação TI Neo Crédito · v2.0 · 17/11/2026 · proposta
Substitui a v1.0 de 16/11/2026. Mudanças: Plano curto com 4 seções em M; seção opcional "Desenho e alternativas" (GG);
seção 8 ampliada para "Corte e rollback", usável sozinha em PP/P; lista de tarefas para o agente de IA (seção 12);
tabela de deploy com Konsig primeiro e NeoKonsig só até a Entrega 1.
Como usar: copie para docs/planos/<chave do épico DS>_plano-<assunto>.md no repositório do sistema afetado.
Enquanto o repositório do Konsig que recebe docs/ estiver [A CONFIRMAR] (DS-175/DS-495), use a pasta provisória definida no README do kit, seção 4.
Apague os blocos "Orientação" antes de enviar para aprovação.
-->

# Plano de Implementação · <Nome da entrega>

## Quando usar / quando não usar

É o "como entregar" de uma demanda: equivale ao `plan.md` + `tasks.md` do GitHub Spec Kit, sem a ferramenta. O PRD diz o quê e por quê; o Plano diz em que ordem, por onde passa até a produção, como se testa, como se volta atrás e quando termina.

| Situação | O que fazer |
|---|---|
| **PP** (1–2 cards) ou **P** (3–4 cards) | **Não use o Plano.** Card + PRD núcleo bastam. Exceção: se houver gatilho de migração ou de dinheiro (abaixo), use **só a seção 8** como documento solto. |
| **M** (5–9 cards) | **Plano curto:** seções 2, 5, 7 e 11 (mais a tabela 8.1, uma linha por entrega). Cabeçalho de 4 linhas. O resto: apague. |
| **G** (10–20 cards) | Plano completo. A régua manda quebrar GG em entregas G ou M (`regua-tamanho-tempo.md`, seção 3) e recomenda estender a quebra ao G, decisão pendente (seção 7); cada entrega ganha sua linha nas seções 2, 8 e 11. |
| **GG** (mais de 20 cards) | Plano completo, um por entrega, cada entrega com seu épico. Seção 4 (Desenho e alternativas) obrigatória quando houver integração nova ou trade-off real. |
| **Migração** (dados, repositório, infraestrutura, troca de parceiro, mudança de layout, modo sombra → efeito real) | Seção 8.2 **obrigatória**, em qualquer tamanho, inclusive PP/P. |
| **Dinheiro** (pagamento, liquidação, repasse, remuneração de correspondente, decisão automática de crédito) | Na **primeira ida a produção**, seção 8.2 obrigatória com go/no-go por passo, em qualquer tamanho. Seção 7 com um cenário por linha da tabela de decisão do PRD. |
| **Mudança de banco no Konsig** | Seção 8.4 obrigatória, em qualquer tamanho: o Konsig não tem migrations **[ALÉM DA FONTE — decisão do usuário: gatilho não previsto no desenho v2; evidência US-43 e DS-93]**. |
| Agente de IA vai implementar | Seção 12 (tarefas pequenas e testáveis) preenchida antes de abrir a sessão do agente **[ALÉM DA FONTE — decisão do usuário: gatilho não previsto no desenho v2]**. |

**Não use o Plano para:** repetir o épico do Jira (responsáveis, status, GDP/US; a chave DS só entra como vínculo do card à entrega, na seção 2.2), repetir a rastreabilidade do PRD, registrar decisão (isso é ADR), descrever operação recorrente do sistema (isso é RUNBOOK.md) ou detalhar cenário de teste (isso fica no card).

**Pré-requisito:** PRD núcleo aprovado e ADRs da demanda em status Aceito.

Tamanhos PP/P/M/G/GG: `D1-pool/regua-tamanho-tempo.md`, v1, 16/11/2026, **proposta sem decisão do comitê**. Na dúvida sobre o tamanho, comece pela trilha mais leve e promova o Plano quando a contagem de cards subir. Toda a regra de escolha desta tabela é **[ALÉM DA FONTE — decisão do usuário]**.

**Spec-anchored:** este Plano, o PRD e os cards são o contexto do agente de IA. Quem muda a ordem das entregas, o deploy ou o rollback durante a construção atualiza este arquivo **no mesmo PR** da mudança.

---

## 1. Cabeçalho

| Campo | Valor |
|---|---|
| Sistema | <**Konsig** (legado) ou outro sistema do Inventário. Um único sistema. NeoKonsig só para o que resta da Entrega 1 (DS-251).> |
| Épico · PRD · ADRs | <DS-n> · `docs/prd/<arquivo>` · <ADR-nnnn, ...> |
| Trilha e gatilhos | <M · G · GG; ou "PP/P, só seção 8"> · <migração · dinheiro · banco Konsig [ALÉM DA FONTE — decisão do usuário] · integração nova · nenhum> |
| Status | <Rascunho · Aprovado (PO, dd/mm/aaaa) · Em execução · Concluído · Cancelado> |

> **Orientação.** Entra: só o que o Jira não diz ou o que liga este arquivo aos outros documentos. Não entra: GDP, US, tamanho, responsáveis e versionamento em tabela. Isso já está no épico e no histórico do Git; repetir aqui só cria divergência com o Jira.

---

## 2. Entregas e cards previstos · obrigatória em M, G, GG

### 2.1 Entregas

| # | Entrega | O que fica verificável ao final | Regras do PRD cobertas | Cards previstos | Tamanho |
|---|---|---|---|---|---|
| E1 | <nome> | <o que a área de negócio consegue ver ou testar> | <RN01, RN02> | <n> | <PP · P · M> |
| E2 | | | | | |

> **Orientação.** Entra: entregas que, cada uma sozinha, produzem algo que alguém fora do time consegue verificar. Não entra: entregas por camada técnica ("back-end", "front-end") ou "parte 1 / parte 2" sem resultado próprio (guia InnoviaX, seção 06, "Como não quebrar"). Uma entrega G deve ser avaliada para quebra em M; uma entrega GG não entra no plano sem ser quebrada (`D1-pool/regua-tamanho-tempo.md`, seção 3; proposta da régua, em aberto no comitê, seção 6).
>
> **Exemplo (Quitação Fase 2, Konsig, DS-500):** E1 · Motor em modo sombra: captura das propostas, aplicação das regras com decisão final registrada e teste do motor (DS-501, DS-503, DS-504, DS-508) · verificável pela consulta do registro de avaliação · P (4 cards). E2 · Visualização e exportação: lista, detalhe e exportação (DS-505, DS-506, DS-507, DS-509) · verificável pela área Financeiro na tela · P (4 cards). Total: 8 cards, épico M. O card de teste (DS-508) fica dentro da entrega que ele prova; ele não é uma entrega própria.

### 2.2 Cards previstos e critério de quebra

| Entrega | Card (título: verbo + objeto) | Tipo | Critério de quebra usado (seção 06 do guia) | Regra do PRD | Chave DS |
|---|---|---|---|---|---|
| E1 | <título> | <História · Tarefa · Bug (Spike e Teste registrados como Tarefa [ALÉM DA FONTE — decisão do usuário])> | <regra de negócio · tipo de documento ou fluxo · caminho · etapa do processo> | <RN01> | <DS-n, após criação> |

> **Orientação.** Entra: todos os cards previstos, com o critério de quebra usado. Use os quatro critérios do guia: por regra de negócio (preferencial), por tipo de documento ou fluxo, por caminho (feliz primeiro, falha depois, só se o caminho feliz puder ir para produção com segurança) e por etapa do processo. Confira cada card contra os sinais de card grande da seção 06: mais de sete cenários, título que precisa de "e", mais de um perfil na história, parte dependente de decisão inexistente. Não entra: subtarefa como card (subtarefa divide trabalho, não entendimento, guia seção 07); a matriz regra × card × teste, que é do PRD (aponte para ela, não copie).
>
> Tipos no Jira: o Downstream tem Tarefa, História, Bug, Subtask e Epic (`downstream_16-11.csv`, 16/11/2026 10h26). Spike e Teste do guia são registrados como Tarefa, com o prefixo no título **[ALÉM DA FONTE — decisão do usuário]** (ver `modelos/CARD.md`, Nota Neo · tipos no Jira).
>
> Regras do experimento em vigor desde a Sprint 19 (`contexto-mestre.md`, seção 4): História só é criada pelo PO; demanda nova entra como Tarefa; cada etapa do Downstream exige responsável; o card só vai para Concluído com Categorias, Descrição, Classe de serviço e Tipo preenchidos.
>
> **Exemplo:** E1 · "Aplicar as regras parametrizadas por prioridade e definir a decisão final" · História · por regra de negócio · RN da tabela de decisão · DS-503.

---

## 3. Sequência e dependências · G e GG

| Entrega | Depende de | Tipo de dependência | Situação |
|---|---|---|---|
| E1 | <entrega, ADR, ambiente, parceiro> | <técnica · negócio · externa> | <resolvida · aberta: dono (papel) e data> |

> **Orientação.** Entra: a ordem e o motivo da ordem, e só a dependência que o épico do Jira não mostra (parceiro, outra área, ambiente). Dependência externa sempre com dono e data. Em M, escreva a dependência numa linha dentro da seção 2.1, se houver. Não entra: tarefas internas do time; links que já estão no épico.
>
> **Exemplo:** E1 depende da Fase 1 concluída, com os ajustes do teste de 09/11/2026 na tela de Administração (pré-requisito declarado no DS-500) · negócio · aberta: DS-415 em Code Review e DS-416 em Em desenvolvimento na extração de 16/11/2026 10h26.

---

## 4. Desenho e alternativas · opcional; obrigatória em GG com integração nova ou trade-off real

Formato do design doc do Google (Malte Ubl, "Design Docs at Google"), reduzido. **[ALÉM DA FONTE — decisão do usuário]** quanto a usá-lo como seção do Plano, e não como documento próprio.

| Bloco | O que escrever (curto) |
|---|---|
| Contexto e escopo | <o que existe hoje e o que muda; um parágrafo. Não repita o problema do PRD: aponte para ele.> |
| Desenho | <componentes tocados, fluxo de dados, APIs/arquivos/filas, onde cada dado é gravado; um diagrama simples se ajudar> |
| Alternativas consideradas | <2 ou 3 opções reais, cada uma com por que foi descartada> |
| Preocupações transversais | <segurança · dado pessoal (CHECKLIST-DADOS-E-REGULACAO.md) · observabilidade (log, alerta) · desempenho · operação (RUNBOOK.md)> |

> **Orientação.** Entra: o desenho quando há mais de um caminho razoável e errar custa caro, por exemplo uma integração nova num sistema sem CI/CD. Não entra: manual de implementação disfarçado de desenho. Se a solução é óbvia e não há trade-off, **não preencha** (o próprio texto do Google trata esse caso). Se daqui sair uma decisão difícil de reverter, ela vira **ADR** e esta seção só aponta para o ADR; o contrato com a contraparte vai para **CONTRATO-DE-INTEGRACAO.md**.
>
> **Exemplo (onde caberia):** Quitação Fase 4, PagAuto com a API do BB, no Konsig. A decisão já está no ADR-0001 do exemplo (`exemplos/quitacao/ADR-0001_GDP-76_pagamento-quitacao-pagauto-api-bb.md`); a seção 4 do Plano da Fase 4 descreveria só o fluxo (motor → aprovador → PagAuto → BB → retorno/comprovante) e as preocupações transversais, como a idempotência do pagamento e o download do comprovante, que já falhou após uma refatoração (DS-59, `downstream_16-11.csv`, 16/11/2026 10h26).

---

## 5. Ambientes e deploy · obrigatória em M, G, GG

| Item | Konsig (sistema de 2027) | NeoKonsig (só até a Entrega 1, DS-251) |
|---|---|---|
| Pipeline de CI/CD | **Não existe** (US-43, Backlog, `upstream_16-11.csv`, 16/11/2026 9h51) | Existe (DS-315, DS-494, `downstream_16-11.csv`, 16/11/2026 10h26) [A CONFIRMAR no Inventário de Sistemas] |
| Ambientes disponíveis | [A CONFIRMAR no Inventário de Sistemas] | [A CONFIRMAR no Inventário de Sistemas]; produção ativa (DS-421) |
| Homologação dedicada | [A CONFIRMAR] | [A CONFIRMAR]; mock da CAF em homologação a retirar (DS-567) |
| Padrão de release | Sem padrão; adoção do DS-550 no Konsig [A CONFIRMAR] (o DS-550, em Backlog, começa pelo Keycloak; `insumos/sistemas-e-tecnologias.md`, A1) | Em definição no DS-550 (Backlog, inclui o neo-konsig no DS-559) [A CONFIRMAR o alcance no NeoKonsig] |
| Mudança de banco | **DDL manual, sem migrations** (US-43). Ver seção 8.4. | [A CONFIRMAR] |
| Depois da Entrega 1 | Recebe o time inteiro em 2027 | Plano novo **não** é aberto no NeoKonsig. Pendências e sustentação vão para PASSAGEM.md e RUNBOOK.md. |

> **Orientação.** Preencha **apenas a coluna do sistema deste plano** e apague a outra. Entra: ambiente em que cada entrega é testada e por onde passa até a produção; passos manuais de deploy, um por linha, com quem executa (papel); janela de implantação; a etapa Waiting for deploy do Downstream e quanto tempo se espera nela. Não entra: credenciais, endereços de servidor, identificadores de conta.
>
> No Konsig, como não há pipeline, o plano descreve o deploy manual passo a passo e o que é conferido depois de cada passo. Esse é o principal risco técnico de construção nova no legado (`insumos/sistemas-e-tecnologias.md`, ponto de atenção A1).
>
> **Exemplo (Konsig):** 1 · Tech lead gera o pacote a partir do branch principal revisado. 2 · Infraestrutura aplica em [ambiente A CONFIRMAR]. 3 · QA executa a regressão manual dos fluxos de quitação. 4 · PO libera para produção. [ALÉM DA FONTE — decisão do usuário: sequência ilustrativa; o procedimento real depende do Inventário e do DS-550.]
>
> **Konsig primeiro.** A coluna do NeoKonsig só existe para fechar a Entrega 1 (DS-251: 83 cards, 59 concluídos e 24 abertos, `epicos_downstream_16-11.csv`, 16/11/2026 10h26). Quem chega do NeoKonsig não deve supor no Konsig o CI/CD, as jornadas automatizadas na pipeline (DS-471, em Code Review em 16/11/2026 10h26) nem o RabbitMQ/Keycloak que tinha lá. Se o deploy manual do Konsig se repete igual a cada entrega, ele vira RUNBOOK.md e esta seção só aponta para ele, com as diferenças desta entrega.

---

## 6. Migração de dados · G/GG, ou quando houver gatilho de migração

| Item | Resposta |
|---|---|
| Há carga, conversão ou correção de dado existente? | <Não · Sim → preencha também a seção 8.2> |
| Origem e destino | <tabela/sistema de origem → destino, sem dado real> |
| Volume estimado | <ordem de grandeza> |
| Validação | <contagem antes × depois, amostra conferida pela área> |
| Dado pessoal envolvido | <categorias; regra de mascaramento; CHECKLIST-DADOS-E-REGULACAO.md no PR; DPO acionado quando houver tratamento ou compartilhamento novo> |
| Reversão | <como desfazer; ou "não há rollback" + contingência, na seção 8.2> |

> **Orientação.** Entra: qualquer alteração em dado que já existe em produção, inclusive carga inicial de parametrização. Não entra: exemplo com dado real. Em integração entre Konsig e NeoKonsig, registrar qual sistema é a fonte única do dado; essa delimitação ainda está em aberto (`insumos/sistemas-e-tecnologias.md`, ponto de atenção A6).
>
> **Exemplo:** Quitação Fase 2: Não se aplica. O motor só lê propostas e regras e grava o registro novo da avaliação; não altera dado existente (modo sombra, DS-500).

---

## 7. Plano de teste · obrigatória em M, G, GG

| Nível | O que cobre | Quem executa (papel) | Ambiente | Evidência | Critério de aprovação |
|---|---|---|---|---|---|
| Teste do desenvolvedor | Regras de cada card | Dev | <ambiente> | Testes automatizados no pull request | Testes passando no Code Review |
| QA Teste | Cenários de teste dos cards (bloco 7), caminhos feliz, alternativo, borda e falha | QA | <ambiente> | Roteiro executado com resultado por cenário | Todos os cenários aprovados; reprovação marcada com QA-REJECTED |
| Regressão | Fluxos existentes afetados | QA | <ambiente> | Lista de fluxos e resultado | Nenhuma regressão aberta |
| Aprovação POs / homologação | Critérios de aceite do PRD | PO com a área solicitante | <ambiente> | Registro no Jira | Aceite da área |
| Tabela de decisão (gatilho de dinheiro) | **Um cenário por linha** da tabela de decisão do PRD | Dev e QA | <ambiente> | Resultado por linha | Todas as linhas aprovadas |

> **Orientação.** Entra: o que é testado, por quem, onde e o que conta como evidência. A massa de teste é sintética: dado fictício, válido no formato, nunca copiado de produção. Não entra: repetição dos cenários dos cards; aqui se planeja, nos cards se detalha. Se não houver ambiente de homologação dedicado, registrar onde a validação ocorre e o risco, como o guia faz no DoD do card A1 (seção 08).
>
> Linha de base do fluxo a observar: na Sprint 18, a média em QA Teste foi 41h e havia 14 itens em Aprovação POs; 66% do ciclo mediano aconteceu depois do código pronto (Review da Sprint 18, extração de 06/11/2026 16h46).
>
> **Exemplo (tabela de decisão):** o DS-508 testa um caso por linha da tabela de decisão (seção 11 do Documento de Requisitos V04, linhas 1 a 9) e os exemplos 1 a 4 do Anexo I (`downstream_16-11.csv`, 16/11/2026 10h26). Cada linha termina em PAGAR, NAO_PAGAR, PAGAR_PARCIAL ou ANALISE_MANUAL (DS-415). Na S18, 11 de 14 testes com testador registrado foram feitos pela mesma pessoa (Review S18, 06/11/2026 16h46): registre o testador por papel e, se possível, alterne.

---

## 8. Corte e rollback · 8.1 obrigatória em M, G, GG; 8.2 a 8.5 por gatilho, em qualquer tamanho

**Quando 8.2 é obrigatória, inclusive em PP/P sem Plano** (nesse caso, copie só a seção 8 como documento solto, `docs/planos/<chave>_corte-<assunto>.md`):
- migração de dados, de repositório ou de infraestrutura;
- troca de parceiro ou mudança de layout de arquivo/API;
- passagem de modo sombra para efeito real;
- primeira ida a produção com dinheiro (pagamento, liquidação, repasse, remuneração de correspondente, decisão automática de crédito).

### 8.1 Rollback por entrega

| Entrega | Gatilho para reverter | Como reverter | Tempo estimado | Quem decide (papel) | Dado criado no período: o que fazer |
|---|---|---|---|---|---|
| E1 | <sintoma observável> | <versão anterior, desativação por parâmetro, script> | <minutos ou horas> | <tech lead · PO> | <manter, descartar, corrigir> |

> **Orientação.** Entra: um rollback por entrega que vai para produção, decidido antes do deploy. Não entra: "reverter se der problema". Quando não há rollback possível (por exemplo, pagamento já enviado a banco), dizer isso e descrever a contingência operacional.
>
> **Exemplo:** E1 · motor registrando decisão para proposta fora de AND - AGUARD QUITACAO · desativar a execução do motor e voltar à conferência por planilha · [A CONFIRMAR] · tech lead · manter os registros, marcados como inválidos para a comparação.

### 8.2 Corte passo a passo (go/no-go)

Pré-requisitos do corte: <ADR aceito · contrato de integração revisado · runbook de rollback testado em homologação · comunicação da seção 9 enviada · testes de verificação listados abaixo>

| Passo | O que é feito | Responsável (papel) | Go/no-go: critério para seguir | Tempo máximo | Verificação (o que se confere, listado antes) | Rollback deste passo, ou "não há rollback" + contingência |
|---|---|---|---|---|---|---|
| 0 | Decisão de iniciar | PO + tech lead | <pré-requisitos todos marcados> | — | — | Não iniciar |
| 1 | <passo> | <dev · infraestrutura · QA · PO> | <condição objetiva, ex.: contagem origem = destino> | <min/h; ao estourar, aciona o rollback> | <consulta, tela, relatório> | <como volta> |
| 2 | | | | | | |

**Retenção dos dados de origem:** <o que fica guardado (planilha, tabela antiga, repositório antigo), onde, por quanto tempo depois do corte, e quem apaga (papel). Com dado pessoal: prazo alinhado ao CHECKLIST-DADOS-E-REGULACAO.md.>

> **Orientação.** Entra: cada passo com dono por papel, critério de seguir ou parar, tempo máximo e o rollback daquele passo. O Google Cloud, na série "Database migration: concepts and principles", recomenda manter os dados de origem como contingência até o destino operar de forma confiável (Parte 1), definir e repetir a verificação de equivalência entre origem e destino e decidir cedo se o fallback será preparado, porque voltar os dados ao sistema de origem é uma migração completa no sentido inverso (Parte 2) (via busca). O tempo máximo por passo com rollback ao estourar não foi localizado no resumo da busca: conferir no original antes de atribuí-lo ao Google. Quando não há volta, escreva **"não há rollback"** e a contingência operacional: isso é resposta válida; deixar em branco não é. Não entra: "monitorar e reverter se necessário"; passo sem dono; critério subjetivo ("se estiver ok").
>
> Para mudar uma interface sem quebrar quem consome, use **parallel change** (expandir, migrar, contrair): o novo convive com o velho, os consumidores migram, e só então o velho sai (Danilo Sato, bliki de martinfowler.com, via busca). Cada fase é um passo desta tabela.
>
> **Exemplo 1 · Quitação, planilha → modo sombra → efeito real (Konsig):**
> - Passo A (Fase 2, DS-500): o motor roda em **modo sombra**; a planilha do Financeiro continua sendo a base da decisão. Go/no-go para a Fase seguinte: o "critério de avanço da Fase 2", citado no DS-507 e **não descrito em nenhuma fonte [A CONFIRMAR]**, medido pela comparação motor × planilha exportada no DS-507. Rollback: desligar a execução agendada e voltar só à planilha.
> - Passo B (efeito real, RF23, RF24, RF2 e RF5; o texto do DS-500 na extração termina em "ficam para a Fase", truncado (`downstream_16-11.csv`, 16/11/2026 10h26); número da fase [A CONFIRMAR no Jira]; o insumo da Quitação propõe Fase 3 [ALÉM DA FONTE — decisão do usuário]): o motor passa a mudar situação de proposta. Rollback: desligar o efeito pela flag de release (8.3); propostas já movidas são corrigidas no destino, pelo procedimento do runbook [A CONFIRMAR].
> - Passo C (Fase 4, PagAuto + API BB): **não há rollback**. "Pagamento já enviado ao banco não se desfaz por rollback de código; a contingência é operacional (voltar ao pagamento manual nos portais)" (`exemplos/quitacao/ADR-0001_GDP-76_pagamento-quitacao-pagauto-api-bb.md`). Go/no-go: primeiro lote pequeno conferido pelo Financeiro antes de liberar o volume **[ALÉM DA FONTE — decisão do usuário]**.
> - Retenção: a planilha do Financeiro fica preservada até a área aceitar o efeito real [ALÉM DA FONTE — decisão do usuário quanto ao prazo].
>
> **Exemplo 2 · Próxima migração de repositório do Konsig (DS-175/DS-495):** registrar os passos aqui; o DS-519 (variáveis de ambiente, sem descrição, `downstream_16-11.csv`, 16/11/2026 10h26) mostra o que costuma ficar de fora.

### 8.3 Feature flags de release

| Flag | O que liga | Valor no corte | Quem muda (papel) | Data de remoção do código da flag | Card de remoção |
|---|---|---|---|---|---|
| <nome> | <comportamento novo> | <desligada → ligada no passo n> | <tech lead> | <dd/mm/aaaa> | <DS-n> |

> **Orientação.** Entra: toda flag criada para liberar a entrega aos poucos ou para servir de rollback do passo. Flag de release é temporária: Pete Hodgson classifica as flags em release, experimento, ops e permissão e recomenda remover as de release depois da implantação ("Feature Toggles (aka Feature Flags)", via busca). Por isso a data de remoção e o card são obrigatórios. Não entra: parâmetro de negócio permanente (isso é regra, vai para o PRD); flag sem dono.

### 8.4 Mudança de banco no Konsig (sem migrations)

| # | Script DDL/DML (nome do arquivo no repositório) | Ambiente e ordem | Quem aplica (papel) | Antes ou depois do pacote de código | Verificação | Script de reversão |
|---|---|---|---|---|---|---|
| 1 | `<docs/planos/sql/DS-n_01_<assunto>.sql>` | <homologação → produção> | <infraestrutura · dev> | <antes> | <consulta que confirma a estrutura> | `<..._01_reverte.sql>` ou "não há rollback" + contingência |

> **Orientação.** Entra: todo DDL ou DML manual que acompanha a entrega, versionado no repositório e com a ordem de aplicação. O Konsig não tem "versionamento de base de dados (migrations)" (US-43, Backlog, `upstream_16-11.csv`, 16/11/2026 9h51). O DS-93 registra "SE FOR SUBIR, TEM QUE ATUALIZAR O DB" e passou por 7 sprints (S9 a S15) (`downstream_16-11.csv`, 16/11/2026 10h26): o script esquecido é o risco concreto. Prefira mudança aditiva (coluna nova antes, remoção da antiga só depois que nada a usa, como no parallel change). Não entra: dado real no script; credencial.

### 8.5 Checagem rápida da seção 8

- [ ] Todo passo tem dono por papel, go/no-go objetivo, tempo máximo e verificação.
- [ ] Todo passo tem rollback ou a frase "não há rollback" com a contingência.
- [ ] A retenção dos dados de origem tem prazo e dono.
- [ ] Toda flag de release tem data e card de remoção.
- [ ] Todo script de banco do Konsig está no repositório, com ordem e reversão.
- [ ] Se o procedimento vai se repetir, ele virou RUNBOOK.md.

---

## 9. Comunicação · G/GG, ou junto da seção 8.2

| Momento | Público | Mensagem | Canal | Responsável (papel) |
|---|---|---|---|---|
| Antes do deploy ou do corte | <área solicitante, atendimento> | <o que muda, quando, o que fazer se algo falhar> | <canal> | <PO> |
| Depois do deploy | | | | |
| Em caso de rollback ou contingência | | | | |

> **Orientação.** Entra: quem precisa saber antes, durante e depois, e o que fazer. Não entra: lista de distribuição com nomes ou e-mails.

---

## 10. Riscos de execução · G e GG

| ID | Risco | Probabilidade | Impacto | Mitigação | Dono (papel) |
|---|---|---|---|---|---|
| R01 | <evento e consequência> | <A · M · B> | <A · M · B> | <ação> | <papel> |

> **Orientação.** Entra: riscos de execução (prazo, ambiente, dependência externa, concentração de conhecimento). Os riscos de produto ficam no PRD: aponte para eles, não repita. Concentração é registrada pelo papel, não pela pessoa; ausência prevista aciona PASSAGEM.md.
>
> **Exemplo:** R01 · Uma única pessoa desenvolvendo as quatro fases da Quitação (Previsão de entregas V02, 06/11/2026): ausência atrasa todas as entregas · M · A · par de revisão fixo, registro das decisões no PRD e PASSAGEM.md antes de ausência · tech lead.

---

## 11. Datas estimadas (régua) · obrigatória em M, G, GG

| Entrega | Classe | Início previsto | Referência típica (dias úteis) | Referência conservadora (dias úteis) | Fim previsto (típico) | Fim previsto (conservador) |
|---|---|---|---|---|---|---|
| Upstream (se ainda não concluído) | — | <data> | 29 | 44 | <data> | <data> |
| E1 | <PP · P · M> | <data> | 16 | 29 | <data> | <data> |
| E2 | <G> | <data> | 66 (piso) | 86 | <data> | <data> |

**Premissas:** <de onde vem a data de início; convenção de contagem (o dia de início conta como dia 1 ou não); feriados descontados ou não; o que acontece com a data se a premissa cair> · **Apetite (G recomendado, GG obrigatório):** <teto de tempo que a área aceita; se a estimativa passar dele, corta-se escopo, não se estica prazo>

> **Orientação.** Fonte: `D1-pool/regua-tamanho-tempo.md`, versão 1, 16/11/2026, medida do primeiro card criado ao último card concluído do épico, em dias úteis (10 dias úteis = 1 sprint). **Faixas e referências são proposta, sem decisão do comitê.** PP, P e M usam a mesma referência, porque os dados não sustentam prazos diferentes entre elas. GG não tem referência: quebrar antes. Para épico já em andamento, se o tempo decorrido passou da referência, usar o ritmo do próprio épico: cards abertos × dias decorridos ÷ cards concluídos.
>
> Não entra: estimativa em pontos ou Fibonacci, que não são prática atual. A data de início vem da posição da demanda no pool de 2027, não do desejo da área. O apetite vem do Shape Up (Basecamp), aproveitado só como teto de tempo, sem ciclos de 6 semanas **[ALÉM DA FONTE — decisão do usuário]**.
>
> **Exemplo:** Quitação Fase 2 (M, 8 cards). Premissa de início: jan/27, posição da Fase 2 no pool de 2027 (`D1-pool/pool-2027-plano.xlsx`, aba Pool 2027, Nº 6 (linha 11 da planilha), "Quitação · Fase 2", Início do desenvolvimento jan/27); primeiro dia útil, 04/01/2027 **[ALÉM DA FONTE — decisão do usuário]**. Convenção: o dia de início não conta; fim = início + N dias úteis, segunda a sexta **[ALÉM DA FONTE — decisão do usuário: a régua não define a convenção]**. Fim típico: 04/01/2027 + 16 dias úteis = 26/01/2027. Fim conservador: 04/01/2027 + 29 dias úteis = 12/02/2027. Feriados e recesso não descontados. Se o desenvolvimento começar antes, vale a regra 3 da régua (seção 4): o épico em andamento conta a partir do primeiro card criado (09/11/2026), com a mesma convenção; em 16/11/2026 restariam 11 dias úteis no típico (até 01/12/2026) e 24 no conservador (até 18/12/2026). O exemplo preenchido (`exemplos/quitacao/DS-500_plano-quitacao-fase-2.md`) usa a mesma premissa e deve seguir a mesma convenção.

---

## 12. Tarefas para implementação · entrada do agente de IA

Uma lista por card (ou por entrega, em M), em lotes pequenos. Cada tarefa cabe num PR revisável e tem critério de aceite próprio.

| # | Card | Tarefa (verbo + objeto, uma coisa só) | Arquivos/área provável | Critério de aceite (verificável) | Teste que prova | Feita |
|---|---|---|---|---|---|---|
| T1 | <DS-n> | <ex.: criar tabela de registro da avaliação> | <módulo> | <ex.: script aplicado em homologação; consulta retorna as colunas do PRD> | <teste ou consulta> | [ ] |
| T2 | <DS-n> | | | | | [ ] |

> **Orientação.** Entra: tarefas que um dev ou o agente de IA executa uma de cada vez, cada uma terminando com algo que se testa, na ordem em que devem ser feitas. Cada critério de aceite aponta para uma RN do PRD ou para um cenário Dado/Quando/Então do card. O DORA 2025 põe **lotes pequenos** entre as sete capacidades que fazem a IA dar resultado: a IA gera blocos grandes, difíceis de revisar e testar. Este bloco é o equivalente ao `tasks.md` do Spec Kit e do Kiro, sem adotar a ferramenta (o GitHub Spec Kit e a técnica spec-driven development estão em Assess no Thoughtworks Radar). Não entra: tarefa sem critério ("ajustar back-end"); tarefa que mistura sistemas (Konsig e NeoKonsig nunca na mesma tarefa); dado real em exemplo; tarefa que o agente executa sem revisão humana do PR.
>
> Ao entregar a lista ao agente, junte: o PRD núcleo, esta seção, o card e o AGENTS.md do repositório. Se o agente mudar a ordem ou descobrir tarefa nova, a lista é atualizada no mesmo PR.
>
> **Exemplo (E1 da Quitação Fase 2, DS-503):** T1 · ler as regras vigentes por prioridade · critério: com duas regras vigentes para a mesma proposta, retorna a de maior prioridade · teste unitário. T2 · gravar a decisão final com regra e versão · critério: cada avaliação grava decisão, regra e versão, sem alterar a situação da proposta (modo sombra, DS-500) · teste do DS-508 para a linha correspondente da tabela. **[ALÉM DA FONTE — decisão do usuário: quebra ilustrativa; o card não traz tarefas.]**

---

## 13. Critério de pronto do plano

O plano é considerado concluído quando todos os itens abaixo forem verdadeiros:

- [ ] Todos os cards da seção 2 estão em Concluído no Jira, com Categorias, Descrição, Classe de serviço e Tipo preenchidos (regra 3 do experimento S19).
- [ ] Todos os critérios de aceite do PRD foram aceitos pela área solicitante.
- [ ] A rastreabilidade do PRD está completa: toda regra tem card e teste (conferida no PRD, não copiada aqui).
- [ ] As entregas estão em produção e o rollback não foi acionado, ou foi acionado e encerrado com registro.
- [ ] Toda flag de release da seção 8.3 foi removida ou tem card de remoção com data.
- [ ] Os dados de origem da seção 8.2 foram descartados no prazo, ou o prazo ainda corre com dono.
- [ ] Os documentos apontados nas consequências dos ADRs aplicáveis foram atualizados; procedimento repetível virou RUNBOOK.md.
- [ ] O realizado foi registrado ao lado do estimado: cards previstos × cards de fato e dias úteis previstos × realizados (registro da régua, que alimentaria o experimento S20–S22 proposto no `contexto-mestre.md`, seção 7, em aberto, depende do comitê).
- [ ] O status do PRD e deste plano foi alterado para Concluído.

---

## Referências de mercado

Conteúdo obtido por busca na web em 16 e 17/11/2026; vários hosts estavam bloqueados na rede da sessão e foram lidos por resumo ("via busca"). Conferir o original antes de citar em documento oficial.

- Design doc do Google (contexto, desenho, alternativas, preocupações transversais; quando não escrever): https://www.industrialempathy.com/posts/design-docs-at-google/ (via busca)
- Google Cloud, Database migration: concepts and principles, Parte 1 (retenção dos dados de origem como contingência): https://docs.cloud.google.com/architecture/database-migration-concepts-principles-part-1 (via busca)
- Google Cloud, Database migration: concepts and principles, Parte 2 (execução, verificação de equivalência, fallback e seu custo): https://docs.cloud.google.com/architecture/database-migration-concepts-principles-part-2 (via busca)
- Parallel change (expandir, migrar, contrair), Danilo Sato, bliki de martinfowler.com: https://martinfowler.com/bliki/ParallelChange.html (via busca)
- Pete Hodgson, Feature Toggles (aka Feature Flags) (tipos de flag; remoção das flags de release): https://martinfowler.com/articles/feature-toggles.html (via busca)
- Referência secundária, verbete FeatureFlag, que remete ao artigo acima: https://martinfowler.com/bliki/FeatureFlag.html (via busca)
- DORA 2025, modelo de capacidades de IA (lotes pequenos; dados internos acessíveis à IA): https://cloud.google.com/blog/products/ai-machine-learning/from-adoption-to-impact-putting-the-dora-ai-capabilities-model-to-work
- GitHub Spec Kit (`spec.md`, `plan.md`, `tasks.md`): https://github.com/github/spec-kit
- Kiro, specs em `requirements.md`, `design.md`, `tasks.md`: https://kiro.dev/docs/specs/concepts (via busca)
- Thoughtworks Technology Radar, spec-driven development e GitHub Spec Kit em Assess: https://www.thoughtworks.com/radar/techniques/spec-driven-development · https://www.thoughtworks.com/radar/languages-and-frameworks/github-spec-kit
- Spec-first, spec-anchored, spec-as-source (Birgitta Böckeler): https://www.martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html (via busca)
- Shape Up, apetite (capítulo "Set Boundaries"): https://basecamp.com/shapeup/1.2-chapter-03 (via busca)
