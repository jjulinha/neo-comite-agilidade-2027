# Demanda 1 · Pool de projetos priorizados para 2027

**TI Neo Crédito · Comitê de Agilidade · versão 1.1 (refeita do zero e revisada) · 16/11/2026**

Entrega à Dani em 30/11/2026. A apresentação aos executivos é responsabilidade da Dani. Este documento traz a estrutura da apresentação, sem slides montados, e a matriz de pendências.

**Planilha que acompanha:** `pool-desenvolvimento-2027.xlsx`, nesta pasta. Todas as contas abaixo saem dela. A planilha foi recalculada por completo em três estados de premissas (base, com demanda nova e combinado) e bate com o modelo de conferência: nenhum erro de fórmula e nenhuma divergência por linha.

**Bases.** Nenhuma planilha de pool anterior foi usada como base.

| Base | Origem | Data |
|---|---|---|
| GDP e Upstream | Jira | Extração de 16/11/2026, 9h51 (90 e 65 itens) |
| Downstream | Jira | Extração de 16/11/2026, 10h26 (475 itens, project = DS) |
| Linha de base | Review da Sprint 18 | Extração de 06/11/2026, 16h46 |
| Cartão | Visão do Cartão de Crédito v6 | 03/11/2026 |
| Critérios de quebra | Guia "Como escrever um card" (InnoviaX v1.0), seção 06 | Setembro/2026 |
| Estrutura da TI | PDTI 2026–2028 (apresentação) | 20/08/2026 |
| Esforço planejado do Downstream | Previsão de entregas 2026 V02 | 06/11/2026 |
| Decisões vigentes | Contexto-mestre | 16/11/2026 |

---

## 1. Leitura estratégica

O pedido é um pool de projetos priorizados ao longo do tempo. O problema real é mostrar à diretoria **se o que já está comprometido para 2027 cabe na capacidade medida, o que fica de fora e quanto custaria atender o que ficou de fora.**

Uma fila ordenada responde só à primeira parte. Por isso o material é um **balanço**:
- Da vazão do desenvolvimento, sai primeiro o trabalho fora de projetos: sustentação, chamados, arquitetura, débito técnico e melhorias avulsas.
- O restante é consumido nesta ordem:
  1. o que já está em andamento;
  2. o regulatório;
  3. as três prioridades da diretoria: cartão no Konsig legado, integrações com a Salesforce e reestruturação da esteira no Konsig legado;
  4. a continuidade a decidir;
  5. a fila do GDP, por prioridade.
- A demanda nova entra na fila. Ela não passa à frente do compromisso.

**Mensagem central recomendada para a Dani:**

> O compromisso de 2027 cabe: 240 cards, 37% da capacidade de projeto até dez/2027. Ele fecha em T2 2027, e o desenvolvimento do cartão fecha no mesmo trimestre. Isso vale mesmo que a demanda nova continue no ritmo atual, porque ela entra na fila. Quem paga pela demanda nova é a fila: no ritmo de entrada de set–out/2026, ficam sem capacidade em 2027 **268,6 cards**. Atender tudo custaria **11,8 sprints adicionais de capacidade de projeto**, o equivalente a um **time 41% maior** (fator 1,41). As decisões da diretoria são **quanto entra**, **o que fica sem escopo** e **se o time cresce**.

**O que soa bem e o que se sustenta.**
- *"Tudo cabe em 2027"* soa bem, mas só vale com o backlog de hoje, sem nada novo.
- O que se sustenta é: *o compromisso cabe e fecha em T2; o que não cabe é a fila somada à entrada nova, e o preço disso é conhecido*. É verdadeiro, demonstrável com o Jira de 16/11 e útil para decidir.

**Três ressalvas que acompanham a mensagem:**
1. O trabalho em andamento é piso. O épico do Módulo de Parceiros (DS-251) está crescendo: 16 dos 24 cards abertos foram criados entre 09/11 e 16/11/2026. As entregas seguintes do módulo ainda não têm cards.
2. Duas das três prioridades não têm escopo escrito. A Salesforce e a esteira entram como hipótese.
3. 92 dos 272 cards da fila são hipótese: são 23 itens sem escopo, com 4 cards cada.

---

## 2. Números-chave (fonte e data em cada linha)

| Número | Valor | Fonte e data |
|---|---|---|
| Cards concluídos por sprint, média S15–S18 | 38,25 (35, 38, 27, 53) | Jira, Downstream, 16/11/2026 10h26; aba Vazão |
| Parcela da vazão fora de projetos (sem épico) | 40,5% (62 de 153) | Idem |
| Sustentação (bugs + chamados) | 15,0% (23 de 153); 22 desses 23 estão dentro dos 40,5% sem épico | Idem; confere com o contexto-mestre, seção 5 |
| Capacidade de projeto por sprint | 22,75 cards de épico | Fórmula 38,25 × (1 − 62/153); confere com o contexto-mestre, seção 5 |
| Capacidade até dez/2026 (2,5 sprints) / por trimestre de 2027 (6,5 sprints) | 56,875 / 147,875 cards | Aba Premissas |
| Capacidade de projeto até dez/2027 | 648,375 cards | Aba Balanço |
| Trabalho já em andamento | 111 cards: 98 abertos e medidos no Downstream (61 de negócio + 37 de épicos técnicos sem item no GDP) + 13 de hipótese de classe (GDP-111 Dashboard de Parceiros, P; Quitação, tela no Konsig, M; Quitação, integração bancária, M) | Jira, Downstream, 16/11/2026 10h26; aba Pool |
| Regulatório | 25 cards, todos por classe: CRCP (G), MCB (M), PLD (M) e CNPJ alfanumérico (P) | Jira, GDP e Upstream, 16/11/2026 9h51 |
| Cartão de crédito (Konsig legado) | 78 cards no cenário base (mínimo 46, máximo 119), em 18 blocos | Visão v6 (03/11/2026) e guia, seção 06; aba Cartão |
| Salesforce / esteira | 5 / 21 cards, **hipóteses sem documento** | Aba Premissas |
| Compromisso | 240 cards = 37% da capacidade até dez/2027; fecha em T2 2027 | Aba Balanço |
| Fila | 268 cards em 45 itens, mais 4 cards de continuidade a decidir (NeoFaz) | Aba Balanço |
| Itens da fila sem escopo | 23 itens (21 do GDP + US-90 e US-35, do Upstream sem item no GDP), com 92 cards de hipótese. O GDP-145, também com template vazio, foi tratado como duplicidade do GDP-140 | Aba Balanço; Jira, GDP, 16/11/2026 9h51 |
| Entrada × saída no GDP | 7,5 itens criados por mês × 5,5 concluídos por mês (set–out/2026) | Jira, GDP, 16/11/2026 9h51 |
| Demanda nova até dez/2027 (no ritmo de set–out) | 405 cards: 7,5 itens por mês × 4 cards × 13,5 meses | Premissas B10, B11, B15 e B20 |

**Divergência registrada: tamanho do cartão.** O contexto-mestre (16/11/2026) registra o cartão estimado em 135 cards pela planilha v13 (blocos A a M). Esta versão estima de novo, do zero, pela Visão v6 e pelo guia: 46, 78 ou 119 cards.
- A v13 não foi usada, por pedido do usuário, e não foi possível conferir a diferença bloco a bloco.
- Três fatores explicam a maior parte da queda:
  1. o saque (macroetapa 16) ficou fora, porque está marcado "[validar]" na visão (+4 a 7 cards se entrar);
  2. a macroetapa 21 e o cartão físico ficaram fora;
  3. os itens executados por terceiros (Orbitall, MBLabs, Mastercard, Salesforce) só geram cards de integração do lado Neo.
- Mesmo com 135 cards, o compromisso fecha em T2 2027, com 46% da capacidade (aba Cenários).

**Ressalva de leitura.** A capacidade é a vazão medida, não uma promessa. O balanço mostra a janela mais cedo possível em fila única e não modela espera em revisão, QA e aprovação. Na S18, o ciclo mediano de uma entrega foi de 63h, e 66% dele aconteceu depois do código pronto (Review da Sprint 18, extração de 06/11/2026 16h46).

---

## 3. Estrutura da apresentação (para a Dani montar)

São 9 slides e 1 anexo. Cada slide traz um título que já é a conclusão, o dado que o sustenta, onde ele está na planilha e a fonte com data.

| # | Título (conclusão) | Conteúdo e visual | Onde está na planilha | Fonte e data |
|---|---|---|---|---|
| 1 | O compromisso de 2027 cabe e fecha em T2 2027; a fila com a demanda nova não cabe, e atendê-la custa um time 41% maior | Quatro números: 240 cards (37%), T2 2027, 268,6 cards sem capacidade com a demanda nova, fator de time 1,41 | Balanço B20:B23; Cenários, linha 6 (demanda nova no ritmo de set–out, depois dos High) | Jira 16/11/2026; aba Cenários |
| 2 | A capacidade real de projeto é de 22,75 cards por sprint, não de 38 | Vazão por sprint, com épico × sem épico (S11–S19), e destaque nos 40,5% fora de projetos | Painel, gráfico 3; aba Vazão | Jira, Downstream, 16/11/2026 10h26 |
| 3 | Até o fim de 2026, toda a capacidade vai para o trabalho já aberto | "Até dez/2026": 56,875 de capacidade × 111 de trabalho em andamento. Destaque: 37 cards são de épicos técnicos (regressão, deploy, vulnerabilidades, observabilidade), invisíveis no GDP | Balanço, linha 9; Pool, ordens 1 a 17 | Jira, Downstream, 16/11/2026 10h26 |
| 4 | Capacidade × consumo por trimestre | Barras empilhadas por grupo com a linha de capacidade. Mostrar duas versões: sem e com demanda nova (Premissas B9) | Painel, gráfico 1; Balanço B5:H16 | Planilha |
| 5 | As três prioridades: o cartão está estimado; Salesforce e esteira não têm escopo | Cartão com 46 / 78 / 119 cards; Salesforce e esteira como faixas (0–12 e 12–83) | Abas Cartão e Premissas B35:B37; Cenários | Visão v6 (03/11/2026); guia, seção 06 |
| 6 | O prazo de novembro/2026 do cartão não se sustenta | Em 16/11/2026 não há card do cartão no Downstream, e as frentes US-92 a US-97 estão em Análise funcional desde 27/10/2026. O desenvolvimento fecha em T2 2027 (T1 no cenário mínimo). Ficam fora da conta, como caminho crítico: certificação Mastercard, PCI DSS e a definição da esteira-alvo antes de fechar a especificação da US-92 | Balanço B23; Cenários | Jira, Upstream, 16/11/2026 9h51; Visão v6; `insumos/Esteira de Novos - Konsig.md` |
| 7 | A fila só cabe no papel: 23 itens não têm escopo, 4 deles High ou Highest | Fila por prioridade (cabe × sem capacidade × sem escopo); destaque para GDP-83 (Highest) e GDP-75, GDP-72 e GDP-61 (High) | Painel, gráfico 2; Balanço, linhas 38 a 43 | Jira, GDP, 16/11/2026 9h51 |
| 8 | Para onde vai a capacidade, por sistema | Konsig exceto cartão: 232; Konsig e NeoKonsig a repartir (CRCP e CNPJ): 15; NeoKonsig: 117; cartão: 78; NeoFaz: 30; demais: 40 cards | Painel, gráfico 4; Balanço, linhas 47 a 55 | Planilha, premissas-base |
| 9 | Decisões que a diretoria precisa tomar | As 5 decisões da seção 5, com o efeito de cada uma em cards, trimestre e custo | Aba Cenários | Planilha |
| Anexo | Premissas e limites do modelo | Unidade, fórmula da capacidade, classes de tamanho e o que o modelo não faz | Leia-me, Premissas | — |

**Regra para os slides.** Konsig e NeoKonsig sempre separados. Nenhuma afirmação de uso de Fibonacci. Nenhum dado por pessoa. Todo número com fonte e data no rodapé.

---

## 4. Matriz de pendências: o que muda se cada uma for resolvida para um lado ou para o outro

Os efeitos foram calculados na planilha com o mesmo modelo das fórmulas (aba Cenários). **Cenário-base:**
- compromisso de 240 cards (37%), fechando em T2 2027;
- cartão fechando em T2 2027;
- nada sem capacidade;
- fator de time mínimo para atender tudo até dez/2027: 0,79.

| # | Pendência | Lado A → efeito | Lado B → efeito | Quem decide | Recomendação |
|---|---|---|---|---|---|
| 1 | **Demanda nova em 2027.** Entrada no GDP de 7,5 itens por mês, contra 5,5 concluídos por mês, em set–out/2026 | Metade do ritmo: 66,1 cards sem capacidade (9 projetos da fila); custo de 2,9 sprints, fator 1,10 | Ritmo de set–out: 268,6 cards sem capacidade; custo de 11,8 sprints, fator 1,41. Se a demanda nova entrar depois dos High, 36 projetos Medium, Low e Lowest da fila ficam sem capacidade (214 cards). No fim da fila, sobram 268,6 cards da própria demanda nova. O compromisso continua fechando em T2 nos dois casos | Dani e diretoria | **A decisão de maior efeito.** Definir uma cota de entrada por trimestre, ou aceitar que a fila não anda, ou contratar. Mostrar o custo em sprints e em fator de time |
| 2 | **Time de desenvolvimento em 2027 (fator de time).** O prompt cita 36 pessoas (PDTI) e 16 a 18 (comitê de julho). A apresentação do PDTI soma 28 posições na TI inteira e nomeia 5 devs no Núcleo de Soluções (slide 10). Na S19, 9 nomes aparecem no campo DEVs | Time 20% menor (0,8): capacidade de 518,7; compromisso em 46%, ainda em T2. Com o backlog de hoje, tudo ainda cabe (fator mínimo 0,79) | Time 20% maior (1,2): capacidade de 778,05; compromisso e cartão em T1 | Dani | Trocar "quantas pessoas" por "quantos devs em tempo integral em 2027, comparado com as S15–S18". Até a resposta, manter 1,0 |
| 3 | **Escopo da reestruturação da esteira** (Konsig legado; sem documento) | Porte G (12): compromisso de 231 (36%) | Porte de Parceiros (83): compromisso de 302 (47%), ainda T2 | Dani e solicitante | Os 21 cards do cenário-base são hipótese de trabalho. O insumo da esteira recomenda não dimensionar sem documento [ALÉM DA FONTE — decisão do usuário]. Exigir o documento de requisito ou apresentar como faixa de 12 a 83. A esteira-alvo é pré-requisito da especificação da Etapa 1 do cartão (US-92) |
| 4 | **Escopo das integrações com a Salesforce** | Já contido no atendimento do cartão (bloco J): 0 card, compromisso de 235 | Integração própria G (12): compromisso de 247 | Dani | Confirmar se é a mesma integração do atendimento do cartão. Se for, zerar para não contar duas vezes |
| 5 | **Prazo e tamanho do cartão.** A Visão v6 indica novembro/2026 | Mínimo (46): o cartão fecha em T1 2027 | Máximo (119): T2 2027, compromisso em 43%. Com os 135 da v13: T2 2027, 46% | Dani, com a área de Produto | Registrar que novembro/2026 não se sustenta. Validar os blocos com os POs. O saque soma de 4 a 7 cards se entrar |
| 6 | **Itens sem escopo** (23; 4 High ou Highest) | Contados como 0: fila de 180 cards | Contados como M (5): fila de 295 cards | POs e solicitantes | Regra de entrada: item sem escopo não recebe capacidade. Documentar primeiro GDP-83, GDP-75, GDP-72 e GDP-61 |
| 7 | **Módulos grandes sem base** (GG: GDP-30 Convênio NeoKonsig, High; GDP-36 Financeiro NeoKonsig; GDP-88 Inventário NeoFaz) | GG no piso (21 cada): tudo cabe | GG no porte de Parceiros (83 cada): 49,6 cards sem capacidade (7 projetos); custo de 2,2 sprints, fator 1,08 | Dani e Vinícius Nunes | Não aceitar GG no pool: quebrar em entregas G, como foi feito na Entrega 1 de Parceiros |
| 8 | **Prioridade dos módulos do NeoKonsig no GDP** (Low e Lowest, contra a criticidade alta dada ao Admin em 22/10/2026) | NeoKonsig à frente da fila do Konsig: com GG = 83, os 49,6 cards sem capacidade passam a cair sobre 12 projetos (11 do Konsig e o US-35, de sistema não informado) | Manter a prioridade do GDP: com GG = 83, 7 projetos sem capacidade (4 do NeoKonsig e 3 do Konsig) | Dani | Atualizar as prioridades no GDP antes de 30/11. É essa ordem que decide quem fica sem capacidade |
| 9 | **Prioridade do GDP-76 (Quitação) no GDP**: Medium, embora seja prioridade da empresa (contexto-mestre, seção 10) | Corrigir para High: sem efeito no balanço, porque já está em andamento | Manter: o GDP continua sinalizando errado para a diretoria | Dani | Corrigir no GDP |
| 10 | **Esteira no Konsig legado, e não o GDP-34 (NeoKonsig).** Informado pelo usuário; consta no contexto-mestre como em aberto (seção 7), não na tabela de decisões (seção 6) | Registrar como decisão: o GDP-34 segue na fila como módulo do NeoKonsig | Não registrar: o tema volta a ser discutido | Usuário e Dani | Registrar a decisão em DACI e na seção 6 do contexto-mestre |
| 11 | **GDP-87 (Autorregulação NeoKonsig) é exigência com data?** | Sim: entra como regulatório; compromisso de 244 | Não: continua na fila, sem escopo | Jurídico e Dani | Pedir a norma e o prazo |
| 12 | **Reserva para épicos técnicos novos** | 0%: base | 12% (taxa das S15–S18): capacidade de 570,57; compromisso em 42% | Dani e tech lead | Usar 12% no material da diretoria. O trabalho técnico existe e hoje não aparece no GDP |
| 13 | **Itens despriorizados no Upstream e abertos no GDP** (GDP-80 ↔ US-25; GDP-59 ↔ US-23) | Fechar no GDP: nada muda, porque já estão fora | Reativar: voltam para a fila | Solicitantes | Fechar no GDP |
| 14 | **GDP-145** (criado em 13/11/2026, template vazio) | Parte da linha Paradinha (GDP-140): 0 card | Projeto próprio: item sem escopo | Solicitante | Consolidar com o GDP-140 |
| 15 | **NeoFaz Compras e Viagens** (4 cards abertos) | Continuar: 4 cards em T2 2027 | Encerrar: libera 4 cards | Dani | Decidir junto com o GDP-88 (Inventário NeoFaz, GG) |

**Cenários combinados** (aba Cenários):
- **Pessimista sem demanda nova** (cartão no máximo, esteira com 83, Salesforce com 12, GG com 83 e reserva de 12%): compromisso em 61%, fecha em T3; 237,4 cards sem capacidade (30 projetos); custo de 11,9 sprints, fator 1,42.
- **Pessimista com demanda nova** (o anterior + o ritmo de set–out): 642,4 cards sem capacidade; custo de 32,1 sprints, fator 2,13. É o pior caso.
- **Otimista** (fator 1,2, cartão no mínimo, esteira com 12 e Salesforce dentro do cartão): compromisso em 25%, fecha em T1.

---

## 5. Decisões que a diretoria precisa tomar (síntese para o slide 9)

1. **Quanto entra em 2027:** cota de demanda nova por trimestre. No ritmo atual, atender tudo exige um time 41% maior.
2. **Escopo escrito da esteira e da Salesforce**, na data que a Dani fixar. Sem isso, duas das três prioridades são hipótese.
3. **Regra "sem escopo, sem capacidade"** para os 23 itens da fila sem escopo (21 do GDP e 2 do Upstream), começando pelos 4 de prioridade alta.
4. **Quebra dos módulos GG** do NeoKonsig e do NeoFaz antes de qualquer data.
5. **Prazo do cartão:** registrar que novembro/2026 não se sustenta e replanejar a partir da liberação da US-92, que depende da definição da esteira-alvo.

---

## 6. Situação dos temas

| Situação | Itens |
|---|---|
| **Decidido** | Projeto = épico (13/11/2026). Cartão no Konsig legado (13/11/2026). As três prioridades de 2027 estão fora da disputa. Quitação paga via PagAuto com a API do BB, com a integração bancária por último (09/11/2026). Capacidade em cards de épico, sem "total menos 15%" (contexto-mestre, seção 5) |
| **Informado, a formalizar** | Reestruturação da esteira no Konsig legado, e não o GDP-34 (pendência 10) |
| **Em aberto** | Cota de demanda nova. Fator de time 2027. Escopo da esteira e da Salesforce. Tamanho do cartão (faixa). Prioridades do NeoKonsig e do GDP-76 no GDP. Classes PP a GG (proposta, sem decisão do comitê). GDP-87. GDP-145. NeoFaz |
| **Bloqueado** | Dimensionamento da integração bancária da Quitação, até a análise da API do BB: entra como hipótese M. Tamanho da esteira, até o documento de requisito. 23 itens da fila, até o preenchimento do template |
| **Obsoleto** | Prazo de novembro/2026 do cartão. Épicos DS-395 (cards concluídos, épico aberto) e DS-156 (sem cards desde 17/08/2026): recomendação de encerrar. Planilhas de pool anteriores: substituídas por esta, por pedido do usuário |

**Nota sobre a Quitação.** As etapas sem épico estão identificadas pela descrição (tela no Konsig; integração bancária PagAuto/BB), não por número. A numeração das fases diverge entre a Previsão V02 (06/11/2026) e o insumo da Quitação (`insumos/quitacao-estado-e-faseamento.md`).

---

## 7. Riscos que a apresentação precisa declarar

1. **Demanda nova.** Não está no cenário-base. No ritmo atual, deixa 268,6 cards sem capacidade (pendência 1).
2. **O trabalho em andamento é piso.** O Módulo de Parceiros está crescendo, e as entregas seguintes não estão medidas.
3. **Concentração no Konsig legado.** Cartão, esteira, Quitação, regulatório e a maior parte da fila disputam o mesmo sistema, que não tem CI/CD (US-43, Upstream, 16/11/2026 9h51).
4. **Gargalo pós-código.** A média em QA Teste subiu de 7h para 41h da S17 para a S18 (Review da Sprint 18, extração de 06/11/2026). A capacidade em cards não cresce enquanto esse gargalo continuar.
5. **Classes G e GG com amostra pequena.** G tem 1 épico concluído. GG tem 1 épico, ainda aberto (aba Épicos DS).
6. **Previsão V02 × balanço.** A planilha de esforço do Downstream (06/11/2026) planeja Quitação, CRCP e JUDIT ainda em 2026. Pela vazão medida, a capacidade até dez/2026 (56,875 cards) não cobre nem o trabalho já aberto (111 cards).

---

## 8. Fechamento

- **O que fazer agora:** levar à Dani as pendências 1, 2, 3 e 4. São as que mudam a mensagem; as demais só ajustam trimestre ou corrigem o GDP.
- **O que fica para depois:** as 47 ações do PDTI (rodada posterior, como definido no pedido) e a montagem dos slides pela Dani.
- **O que cortar:** apresentar o backlog inteiro como "déficit". Mistura compromisso com desejo; o custo correto é o da seção 4, pendência 1.
- **Decisão necessária:** se o material da diretoria mostra o cenário-base, o de demanda nova ou os dois. Recomendação: os dois, lado a lado, com o custo em sprints e em fator de time.
- **Menor próximo passo útil:** pedir ao solicitante da esteira e ao responsável pela Salesforce um parágrafo de escopo cada, até 23/11/2026.
