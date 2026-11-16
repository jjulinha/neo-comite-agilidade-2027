# Régua de tamanho × tempo · PP a GG

**TI Neo Crédito · Comitê de Agilidade · versão 1 · 16/11/2026**

Planilha: `regua-tamanho-tempo-2027.xlsx`, nesta pasta. Comece pela aba **Resumo**, que traz as informações principais em linguagem simples e com os tempos em semanas e meses. As demais abas trazem o detalhe e se atualizam juntas.

**Situação: proposta para o comitê.** As classes PP a GG estão em aberto, sem decisão (contexto-mestre, seção 7). Os parâmetros da régua são editados só pelo responsável (decisão de 10/11/2026).

**Fontes:**
- Jira, Downstream (project = DS), 475 itens, extração de 16/11/2026, 10h26.
- Jira, Upstream, extração de 16/11/2026, 9h51.
- Pool de projetos 2027 v1.1 (16/11/2026), para o tamanho e o período de cada demanda.

---

## 1. O problema real

O pedido é associar cada tamanho (PP a GG) a um tempo de entrega no Upstream e no Downstream, e classificar as demandas de hoje. Os dados mostram que essa associação funciona só em parte:

- **No Downstream, o tamanho prevê o tempo a partir de G.** De PP a M, o tempo de calendário é praticamente o mesmo. A explicação provável é a espera: na S18, 66% do ciclo mediano aconteceu depois do código pronto (Review da Sprint 18, extração de 06/11/2026 16h46). Esta régua ainda não separa trabalho de espera.
- **No Upstream, o tamanho não prevê o tempo.** O que manda é quanto tempo a demanda fica parada esperando aprovação ou priorização.

Por isso a régua tem **três faixas de tempo no Downstream** (PP–M, G e GG) e **uma referência única no Upstream**, com um alarme de demanda parada. Uma tabela com cinco tempos diferentes no Downstream daria precisão que os dados não têm.

---

## 2. Como é medido

| Etapa | Início | Fim | Observação |
|---|---|---|---|
| Downstream | Primeiro card do épico criado | Último card do épico concluído | Épico aberto: conta até 16/11/2026 e vale como **piso** (o tempo real será maior) |
| Upstream | Item principal criado no board Upstream | Conclusão no Upstream | Itens abertos: idade e dias parados no status atual |

- **Unidade:** dias úteis (segunda a sexta, sem feriados). 10 dias úteis = 1 sprint; 5 = 1 semana.
- **Tamanho:** cards de épico do Downstream (Tarefa, História e Bug ligados ao épico): PP 1–2, P 3–4, M 5–9, G 10–20, GG acima de 20.
- **Limites da medida:**
  - A extração do Jira não traz o histórico de status, então não separa trabalho de espera.
  - Sete dos épicos concluídos começaram na migração do board (17/08/2026). A data de início deles é a da migração.

---

## 3. A régua

### Downstream (do primeiro card ao último card concluído, em dias úteis)

| Classe | Épicos concluídos (n) | Mediana | P85 | Mín–máx | Abertos: maior idade (piso) | **Referência típica** | **Referência conservadora** |
|---|---|---|---|---|---|---|---|
| PP (1–2 cards) | 5 | 16 | 32 | 4–47 | 72 | 16 | 29 |
| P (3–4) | 5 | 19 | 24,8 | 11–29 | 65 | 16 | 29 |
| M (5–9) | 4 | 10,5 | 25,4 | 3–33 | 66 | 16 | 29 |
| **PP–M agregado** | **14** | **16** | **29,2** | 3–47 | 72 | **16 (≈ 3 semanas)** | **29 (≈ 6 semanas)** |
| G (10–20) | 1 | 46 | — | 46 | 86 | **66 (piso)** | **86** |
| GG (> 20) | 0 | — | — | — | 80 (Parceiros, Entrega 1, com 24 cards abertos; é piso, não referência) | **não estimar** | **não estimar** |

**Como ler cada classe:**
- **PP–M:** a referência é o grupo agregado de 14 épicos. Separar PP, P e M não muda o tempo: as medianas (16, 19 e 10,5) se sobrepõem e as amostras são de 4 a 5 épicos.
- **G:** o único épico concluído levou 46 dias úteis. Os três G abertos já estão com 66, 82 e 86 dias úteis: DS-53 (regressão automatizada), DS-65 (vulnerabilidades) e DS-77 (Kanban). Por isso o típico adotado é 66, como piso.
- **GG:** não tem base. A regra proposta é **quebrar em entregas G ou M antes de entrar no pool**. Para um GG que já está em andamento (só o DS-251), o restante é estimado pelo ritmo do próprio épico.

### Upstream (da criação à conclusão no Upstream, em dias úteis)

| Escopo | Concluídos (n) | Mediana | P85 | Mín–máx | Abertos (n) | Abertos acima do P85 | **Referência típica** | **Referência conservadora** |
|---|---|---|---|---|---|---|---|---|
| Todas as classes | 9 | 29 | 43,8 | 2–57 | 23 | 9 | **29 (≈ 6 semanas)** | **44 (≈ 9 semanas)** |
| Ajuste pequeno (PP sem tela nem integração) | proposta | — | — | — | — | — | 5 | 10 |

- Os ajustes pequenos (US-107 e US-85) levaram 2 dias úteis.
- Os itens de M a GG levaram de 27 a 57 dias úteis, sem relação com o tamanho.
- **Itens abertos acima do P85 (9):** US-19 Convênio NeoKonsig (72), US-34 Migração do Slack, US-35, US-36, US-37 e US-43 (66 cada), US-50 MCB (63), US-53 Score Xerox (57) e US-72 JUDIT (45).

---

## 4. Como estimar uma demanda (regra de uso)

1. **Classificar** pelo número de cards previsto, com os critérios de quebra do guia "Como escrever um card" (seção 06).
2. **Upstream restante** = referência do Upstream − idade do item no Upstream (mínimo 0). Se a idade já passou do conservador (44), o item está travado e precisa de decisão: priorizar, despriorizar ou quebrar.
3. **Downstream** = referência da classe. Para épico em andamento, a referência menos o tempo já decorrido. Se o épico já passou da referência, vale o **ritmo do próprio épico**: cards abertos × dias decorridos ÷ cards concluídos.
4. **Total** = Upstream restante + Downstream. É o tempo de atravessamento depois que a demanda começa. A data de início vem da posição no pool, na coluna "Período em que cabe no pool".
5. **Registrar a estimativa e o realizado.** Isso alimenta o experimento S20–S22 já previsto no contexto-mestre (seção 7), cuja métrica é o erro da previsão.

---

## 5. As demandas de hoje na régua (71 linhas da aba "Demandas hoje")

| Classe | Demandas | Cards a consumir | Total restante típico, média (dias úteis) |
|---|---|---|---|
| PP | 5 | 9 | 26,8 (4 com estimativa; o DS-495 não tem card concluído) |
| P | 10 | 26 | 51 (sem GDP-27 e GDP-28, cerca de 31) |
| M | 15 | 84 | 26,2 (14 com estimativa; o DS-24 não tem card concluído) |
| G | 11 | 115 | 85,5 |
| GG | 5 | 108 | não estimável pela régua; só o DS-251, em andamento, tem estimativa (33 pelo ritmo do épico) |
| Programa (cartão, 18 blocos de 2 a 10 cards) | 1 | 78 | prazo vem do pool (T2 2027) |
| Sem escopo | 24 | — | não estimável |

**Ressalvas da tabela:**
- A média de P (51) é puxada pelo GDP-27 e pelo GDP-28 (NeoFaz): épicos de 3 cards, com 1 concluído em 65 dias úteis, que pelo ritmo projetam 130 dias úteis cada. Sem eles, a média de P fica em torno de 31.
- Nos épicos em andamento, a classe usa o **tamanho total do épico**, não os cards que restam. Por exemplo, o DS-65 tem 20 cards e é G, mesmo com 8 abertos.
- Quando uma demanda junta dois épicos, o tamanho é a soma dos dois. O GDP-118 (JUDIT: DS-454 + DS-466, 5 cards cada) soma 10 e fica como G. O GDP-132 (NMP: DS-330 + DS-97) soma 6 e fica como M.

### O que a régua mostra que precisa de decisão

**1. Desenvolvimentos acima da referência ou sem ritmo.**

| Demanda | Situação | Restante pelo ritmo do épico (dias úteis) |
|---|---|---|
| DS-53 (regressão automatizada, G) | 3 de 12 cards em 66 dias úteis | cerca de 198 |
| DS-65 (vulnerabilidades, G) | 12 de 20 cards em 82 dias úteis | cerca de 55 |
| DS-77 (Kanban, G) | 6 de 10 cards em 86 dias úteis | cerca de 57 |
| GDP-132 (NMP) | 4 de 6 cards em 72 dias úteis | cerca de 36 |
| GDP-27 e GDP-28 (NeoFaz) | 1 de 3 cards concluído em cada, em 65 dias úteis | cerca de 130 cada |
| DS-251 (Parceiros, Entrega 1, GG) | 59 de 83 cards em 80 dias úteis; GG não tem referência | cerca de 33 |
| DS-24 e DS-495 | nenhum card concluído (66 e 59 dias úteis) | ritmo desconhecido |

Os seis primeiros já passaram da referência típica da classe. Para todos, a recomendação é quebrar, pausar com motivo ou cancelar, conforme a oportunidade 05 da Review da Sprint 18.

**2. Upstream travado.** Nove demandas estão paradas no status atual há mais de 2 sprints. Sete delas também passaram do conservador de 44 dias úteis no Upstream:

| Demanda | Item no Upstream | Status | Idade (dias úteis) |
|---|---|---|---|
| GDP-30 (Convênio NeoKonsig) | US-19 | Análise funcional | 72 |
| GDP-96 (MCB) | US-50 | Prototipação | 63 |
| GDP-138 | US-72 | Aprovação dos solicitantes | 45 |
| US-43 (CI/CD do Konsig) | US-43 | Backlog | 66 |
| US-37 (CNPJ alfanumérico) | US-37 | Backlog | 66 |
| GDP-95 (Migração do Slack) | US-34 | Análise funcional | 66 |
| US-35 (Modernização tecnológica) | US-35 | Backlog | 66 |

As outras duas paradas há mais de 2 sprints são o GDP-62 (CRCP) e o GDP-114 (Crivo), ainda abaixo do conservador. O GDP-105 (US-53) passou do conservador (57 dias úteis), mas mudou de status há 6 dias úteis.

Esse é o maior ganho rápido de prazo: a espera no Upstream, não o desenvolvimento.

**3. Itens sem escopo.** 24 itens não são estimáveis: os 23 do pool e o GDP-145. A régua não resolve isso. Só o preenchimento do template resolve.

**4. Os G e GG da fila.**
- G na fila: GDP-62 CRCP, GDP-114 Crivo, GDP-84, GDP-34, GDP-35, GDP-32 e US-43 CI/CD do Konsig.
- GG: GDP-30 Convênio, GDP-36 Financeiro, GDP-88 Inventário NeoFaz e a reestruturação da esteira.
- Com a régua, cada G leva pelo menos 66 dias úteis (cerca de 3 meses) no Downstream.

---

## 6. Situação dos temas

| Situação | Itens |
|---|---|
| **Decidido** | Projeto = épico (13/11/2026). Parâmetros editáveis só pelo responsável (10/11/2026). A calculadora não é integrada ao Jira (10/11/2026) |
| **Em aberto (para o comitê)** | Adotar as faixas de tamanho PP a GG. Adotar as três faixas de tempo no Downstream (PP–M, G, GG) e a referência única no Upstream. Regra "GG não entra sem quebra". Alarme de Upstream: item com mais de 20 dias úteis no mesmo status ou acima de 44 dias úteis de idade vai para decisão |
| **Bloqueado** | Separar tempo de trabalho e tempo de espera por etapa: exige a extração do Jira com histórico de status (changelog), que não veio |

---

## 7. Fechamento

- **O que fazer agora:** levar ao comitê a proposta das três faixas de tempo no Downstream, da referência única no Upstream e do alarme de item parado. Usar a lista do item 2 da seção 5 como primeira pauta de desbloqueio.
- **O que fica para depois:** separar trabalho e espera por etapa, quando houver extração com histórico de status. Refazer as medianas no fim da S22, com mais épicos concluídos.
- **O que cortar:** prometer prazos diferentes para PP, P e M. Os dados não sustentam essa diferença.
- **Decisão necessária:** se G entra no pool como está ou se passa a ter a mesma regra do GG (quebrar em M). Recomendação: quebrar. Um G leva pelo menos 3 meses no Downstream, e os três G abertos já estão com 66 dias úteis ou mais (66, 82 e 86).
- **Menor próximo passo útil:** pedir ao administrador do Jira uma exportação do Downstream e do Upstream **com histórico de status**, para medir o tempo por etapa.
