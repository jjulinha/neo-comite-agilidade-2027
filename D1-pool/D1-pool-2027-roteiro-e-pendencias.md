# Demanda 1 · Pool de projetos priorizados para 2027

**TI Neo Crédito · Comitê de Agilidade · versão 2 (capacidade por linha de sistema) · 16/11/2026**

Entrega à Dani em 30/11/2026. A apresentação aos executivos é responsabilidade da Dani. Este documento traz a estrutura da apresentação, sem slides montados, e a matriz de pendências.

**Planilha:** `pool-desenvolvimento-2027.xlsx`, nesta pasta. Comece pela aba **Resumo**, que está em linguagem simples. A planilha foi recalculada em cinco estados de premissas (base, time como um bloco só, demanda nova, realocação e combinado) e bate com o modelo de conferência, sem erro de fórmula e sem divergência por linha.

**Bases.** Nenhuma planilha de pool anterior foi usada como base.

| Base | Origem | Data |
|---|---|---|
| GDP e Upstream | Jira | Extração de 16/11/2026, 9h51 (90 e 65 itens) |
| Downstream | Jira | Extração de 16/11/2026, 10h26 (475 itens) |
| Linha de base | Review da Sprint 18 | Extração de 06/11/2026, 16h46 |
| Cartão | Visão do Cartão de Crédito v6 | 03/11/2026 |
| Critérios de quebra | Guia "Como escrever um card", seção 06 | — |
| Estrutura da TI | PDTI 2026–2028 (apresentação) | 20/08/2026 |
| Esforço planejado do Downstream | Previsão de entregas 2026 V02 | 06/11/2026 |
| Decisões vigentes | Contexto-mestre | 16/11/2026 |

---

## 0. O que mudou da versão 1.1 para a 2, e por quê

A versão 1.1 dizia que o compromisso de 2027 cabia e fechava em T2 2027. **Essa conclusão estava errada.** O modelo somava a capacidade do time inteiro, 22,75 cards de épico por sprint, como se qualquer dev pudesse pegar qualquer card.

O Jira mostra outra coisa. Cards de épico concluídos nas S15 a S18, por linha:

| Linha | Cards concluídos (S15–S18) | Por sprint |
|---|---|---|
| Konsig | 33 | 8,25 |
| NeoKonsig | 39 | 9,75 |
| Épicos técnicos | 18 | 4,5 |
| Outros (NeoFaz) | 1 | — |

**Cada linha tem o seu time.** Os 33 cards do Konsig foram feitos por 4 devs, e um deles fez 16.

O cartão, a esteira, a Salesforce, a Quitação, o JUDIT, o Não Me Perturbe e o regulatório são todos do Konsig. A versão 2 separa a capacidade por linha, na proporção medida, e confirma a leitura do usuário: **não há capacidade no Konsig para projetos novos em 2027, além do que já está comprometido.**

**Dois testes de robustez:**
1. **A S18 foi atípica?** Na S18 o Konsig fez só 2 cards, porque o time foi para Parceiros. Mesmo com a média das S15 a S17 (10,3 cards por sprint), a capacidade do Konsig até dez/2027 fica em cerca de 294 cards, abaixo dos 313 de demanda. A conclusão se mantém, com margem menor.
2. **As estimativas crescem depois de começar?** Sim. Nos épicos com 5 ou mais cards, o tamanho final foi 1,25 vez (mediana dos concluídos) a 1,375 vez (todos) o número de cards que existiam na primeira entrega. No Módulo de Parceiros, 80 dos 83 cards foram criados depois da primeira entrega. Os tamanhos por classe já vêm de épicos concluídos e incluem esse crescimento. O cartão, estimado de baixo para cima, não inclui; por isso há um cenário "cartão × 1,3".

---

## 1. Leitura estratégica

O problema real é mostrar à diretoria **onde está o gargalo**. Não falta capacidade na TI como um todo. Falta capacidade **no Konsig**, que é onde estão as três prioridades de 2027. Ao mesmo tempo, **o NeoKonsig vai ficar com folga** depois do Módulo de Parceiros.

**Mensagem central recomendada para a Dani:**

> Em 2027, o Konsig entrega cerca de 8 cards de épico por sprint e precisaria de 11 para dar conta do que está na mesa. Só o compromisso do Konsig (trabalho em andamento, regulatório, cartão, Salesforce e esteira) ocupa três trimestres e termina em T3 2027, ou em T4 se o cartão crescer como os outros épicos. Da fila do Konsig cabem 12 dos 31 itens, todos no último trimestre: os 7 de prioridade alta e 5 Medium. 24 projetos ficam para depois de 2027 (18 do Konsig e 6 de NeoFaz, site e outros). O NeoKonsig termina o Módulo de Parceiros e fica com folga. **A decisão é realocar parte desse time para o Konsig ou aceitar que, em 2027, o Konsig faz só o compromisso.** Com metade do time NeoKonsig no Konsig, o compromisso termina em T2 2027 e a fila do Konsig cabe no ano.

**O que soa bem e o que se sustenta.**
- *"A TI tem capacidade para 2027"* soa bem, mas é falso para o Konsig.
- O que se sustenta é: *o gargalo é o Konsig; a folga está no NeoKonsig; a saída é realocar ou cortar*. É verdadeiro, demonstrável com o Jira de 16/11 e acionável.

---

## 2. Números-chave (fonte e data em cada linha)

| Número | Valor | Fonte e data |
|---|---|---|
| Cards concluídos por sprint, média S15–S18 | 38,25 (35, 38, 27, 53) | Jira, Downstream, 16/11/2026 10h26; aba Vazão |
| Parcela fora de projetos (sem épico) | 40,5% (62 de 153), incluindo a sustentação (15,0%) | Idem |
| Capacidade de projeto, time inteiro | 22,75 cards de épico por sprint | Fórmula 38,25 × (1 − 62/153); contexto-mestre, seção 5 |
| **Capacidade do Konsig** | **8,25 por sprint**; 235,1 cards até dez/2027 | Aba Vazão, cards por linha (33 de 91) |
| Capacidade do NeoKonsig | 9,75 por sprint; 277,9 cards até dez/2027 | Idem (39 de 91) |
| **Demanda do Konsig até dez/2027** | **313 cards**: 176 de compromisso + 137 da fila (31 itens) | Aba Balanço, linha 59 |
| Capacidade necessária no Konsig | 10,98 cards por sprint (+33%); faltam 77,9 cards | Aba Balanço, D59 e F59 |
| Compromisso do Konsig | Em andamento 47; regulatório 25; cartão 78; Salesforce 5; esteira 21 (em cards). Os épicos técnicos (37 cards em andamento) ficam na linha Técnico | Aba Pool |
| Demanda do NeoKonsig | 117 cards (Parceiros em andamento, Dashboard e módulos da fila); sobram cerca de 161 | Aba Balanço, linha 60 |
| Compromisso fecha | T3 2027; o cartão também fecha em T3 2027 | Aba Balanço, B22 e B23 |
| Fila sem capacidade em 2027 | 24 projetos (115,8 cards): 18 do Konsig e 6 de NeoFaz, site e outros | Aba Balanço, B25 e B26 |
| Fila do Konsig que cabe | 12 itens, todos em T4 2027: os Highest e High (GDP-114, 83, 106, 105, 75, 72, 61) e os Medium GDP-139, 138, 137, 135 e 84 | Aba Pool |
| Itens da fila sem escopo | 23 (21 do GDP + US-90 e US-35), com 4 cards de hipótese cada | Aba Balanço |
| Entrada × saída no GDP | 7,5 itens criados por mês × 5,5 concluídos por mês (set–out/2026) | Jira, GDP, 16/11/2026 9h51 |

**Divergência registrada: tamanho do cartão.** O contexto-mestre registra 135 cards pela planilha v13. Esta versão estima do zero pela Visão v6: 46, 78 ou 119 cards. A v13 não foi usada, por pedido do usuário. Com 135 cards, o compromisso do Konsig fecha só em T4 2027 e o Konsig precisaria de 12,98 cards por sprint.

---

## 3. Estrutura da apresentação (para a Dani montar)

| # | Título (conclusão) | Conteúdo e visual | Onde está na planilha |
|---|---|---|---|
| 1 | O gargalo de 2027 é o Konsig: entrega 8 cards de épico por sprint e precisaria de 11 | Demanda × capacidade por linha (Konsig, NeoKonsig, técnico, outros) | Painel, gráfico 5; Balanço, linhas 59 a 62; Resumo |
| 2 | Cada sistema tem o seu time; somar a capacidade da TI esconde o problema | Cards de épico por linha nas S15 a S18 (33 / 39 / 18 / 1) | Aba Vazão, linhas 21 a 26 |
| 3 | O compromisso do Konsig ocupa três trimestres de 2027 | Em andamento, regulatório, cartão, Salesforce e esteira, por trimestre; termina em T3 2027 (T4 se o cartão crescer) | Balanço; Pool filtrado em Linha = Konsig |
| 4 | Da fila do Konsig, só cabe a prioridade alta e pouco mais, e só no fim do ano | Fila por prioridade; 18 projetos do Konsig sem capacidade | Painel, gráfico 2; Pool |
| 5 | O NeoKonsig vai ter folga depois de Parceiros | 117 cards de demanda × 278 de capacidade | Balanço, linha 60 |
| 6 | Realocar metade do NeoKonsig resolve 2027 | Base × alavancas (realocar, crescer o Konsig em 20%, as duas) | Aba Cenários, linhas em destaque |
| 7 | O prazo de novembro/2026 do cartão não se sustenta | No base, o cartão fecha em T3 2027; com realocação, em T2 | Balanço B23; Cenários |
| 8 | Demanda nova e itens sem escopo pioram o quadro | Ritmo de set–out e 23 itens sem escopo | Cenários |
| 9 | Decisões para a diretoria | As decisões da seção 5 | — |

**Regras para os slides:** Konsig e NeoKonsig sempre separados; nenhuma afirmação de uso de Fibonacci; nenhum dado por pessoa; fonte e data no rodapé.

---

## 4. Matriz de pendências e alavancas

Cenário-base: compromisso fecha em T3 2027; cartão em T3 2027; 24 projetos da fila sem capacidade; o Konsig precisa de 10,98 cards por sprint e entrega 8,25.

| # | Pendência ou alavanca | Efeito | Quem decide | Recomendação |
|---|---|---|---|---|
| 1 | **Realocar metade do time NeoKonsig para o Konsig** (parcelas 52,5 / 19,5) | Compromisso e cartão fecham em T2 2027. A fila do Konsig cabe em 2027 e só 6 projetos de outros sistemas ficam de fora. O NeoKonsig continua com 139 cards de capacidade para 117 de demanda | Dani | **A decisão principal.** Fazer depois que a Entrega 1 de Parceiros terminar. Um cenário de mover o time inteiro deixa o NeoKonsig sem capacidade para concluir Parceiros, por isso não é recomendado |
| 2 | **Crescer o Konsig em 20%** (contratação) | Compromisso fecha em T3 2027 (o cartão em T2); 14 projetos da fila continuam sem capacidade | Dani e diretoria | Sozinho não resolve. Só faz sentido junto com a alavanca 1 |
| 3 | **Demanda nova no Konsig** no ritmo de set–out | O compromisso continua em T3 2027, mas a fila e a própria demanda nova ficam sem capacidade: o Konsig precisaria de 25,2 cards por sprint | Dani e diretoria | Regra de entrada: demanda nova do Konsig só entra se outra sair |
| 4 | **Escopo da esteira** (sem documento) | Do porte de Parceiros (83): o compromisso do Konsig não fecha em 2027 | Dani e solicitante | Exigir o documento de requisito antes de 30/11 ou apresentar como faixa |
| 5 | **Tamanho do cartão** | Com crescimento medido (× 1,3): o compromisso fecha em T4 2027 e o cartão em T3. No máximo (119): ambos em T4 2027. Com 135 (v13): ambos em T4 2027 | Dani e Produto | Registrar que novembro/2026 não se sustenta |
| 6 | **Salesforce** dentro do atendimento do cartão (bloco J) | 5 cards a menos no Konsig; sem mudança de trimestre | Dani | Confirmar para não contar duas vezes |
| 7 | **Itens sem escopo** (23; 4 High ou Highest) | Contados como 0: o Konsig precisaria de 8,60 cards por sprint e ainda faltariam cerca de 10 cards | POs e solicitantes | Item sem escopo não entra no pool |
| 8 | **Parcela de cada linha** | Medida em só 4 sprints. Com a média das S15 a S17 no Konsig, a conclusão se mantém | POs e tech lead | Validar e registrar a alocação real de cada dev (Premissas, "Capacidade por linha") |
| 9 | **Prioridades do NeoKonsig e do GDP-76 no GDP** | Não mudam o gargalo do Konsig | Dani | Atualizar no GDP |
| 10 | **GDP-145, GDP-80/US-25, GDP-59/US-23, NeoFaz** | Pouco efeito | Solicitantes e Dani | Fechar ou consolidar no GDP |

---

## 5. Decisões para a diretoria (síntese para o slide 9)

1. **Realocar parte do time NeoKonsig para o Konsig** depois da Entrega 1 de Parceiros, ou aceitar que em 2027 o Konsig faz só o compromisso.
2. **Regra de entrada no Konsig:** demanda nova só entra se outra sair.
3. **Escopo escrito da esteira e da Salesforce.** Hoje são hipóteses de 21 e 5 cards.
4. **Prazo do cartão:** replanejar a partir da liberação da US-92. No base, o desenvolvimento termina em T3 2027; com realocação, em T2.
5. **Itens sem escopo** não recebem capacidade.

---

## 6. Situação dos temas

| Situação | Itens |
|---|---|
| **Decidido** | Projeto = épico (13/11/2026). Cartão no Konsig legado (13/11/2026). As três prioridades de 2027 estão fora da disputa. Capacidade em cards de épico (contexto-mestre, seção 5) |
| **Em aberto** | Realocação entre linhas. Regra de entrada no Konsig. Escopo da esteira e da Salesforce. Tamanho do cartão. Parcela de cada linha. Classes PP a GG (proposta) |
| **Bloqueado** | Tamanho da esteira, até o documento de requisito. 23 itens da fila, até o preenchimento do template |
| **Obsoleto** | A conclusão da versão 1.1 de que o compromisso fecha em T2 2027 com o time atual (no modelo por linha, fecha em T3). O prazo de novembro/2026 do cartão |

---

## 7. Riscos que a apresentação precisa declarar

1. **Concentração de pessoas no Konsig.** São 4 devs na linha, e um deles fez 16 dos 33 cards das S15 a S18. Férias ou saída dessa pessoa reduzem a capacidade do Konsig de forma relevante.
2. **O Konsig não tem CI/CD** (US-43), e é nele que entra quase todo o compromisso.
3. **Gargalo pós-código.** A média em QA Teste subiu de 7h para 41h da S17 para a S18 (Review da Sprint 18, extração de 06/11/2026).
4. **A parcela por linha foi medida em 4 sprints** e varia muito: o Konsig fez de 2 a 12 cards por sprint.
5. **Os épicos crescem depois de começar** (fator mediano de 1,25 a 1,375). Isso vale sobretudo para o cartão e para a esteira.

---

## 8. Fechamento

- **O que fazer agora:** levar à Dani a alavanca 1 (realocação) e a regra de entrada no Konsig. São as decisões que mudam 2027.
- **O que fica para depois:** as 47 ações do PDTI e a montagem dos slides pela Dani.
- **O que cortar:** a mensagem "a TI tem capacidade". Ela é verdadeira só na soma e esconde o gargalo.
- **Decisão necessária:** se o material para a diretoria já traz a proposta de realocação ou só o diagnóstico. Recomendação: diagnóstico e proposta juntos, porque a realocação é a única alavanca que resolve sem contratação.
- **Menor próximo passo útil:** confirmar com o tech lead quem está, de fato, em cada linha. A parcela por linha é a premissa que mais pesa no resultado.
