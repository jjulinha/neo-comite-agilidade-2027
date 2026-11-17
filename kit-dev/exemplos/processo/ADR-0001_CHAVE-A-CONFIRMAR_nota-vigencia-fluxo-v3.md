<!--
EXEMPLO PREENCHIDO · ADR de MUDANÇA DE DOCUMENTAÇÃO · Kit de documentação TI Neo Crédito · preenchimento de modelos/ADR.md
Destino real: repositório do Comitê de Agilidade ou página do comitê no Confluence [ALÉM DA FONTE — decisão do usuário], conforme modelos/ADR.md, "Onde fica".
Numeração: ADR-0001 do repositório do comitê (sequência própria, independente da do Konsig).
Chave: a mudança ainda não tem item no Jira. O nome do arquivo usa CHAVE-A-CONFIRMAR até que se abra uma Tarefa para ela; então o arquivo é renomeado (README, seção 5).
Fontes: contexto-mestre.md, seções 3, 6, 7 e 11 (16/11/2026); D2-documentos-ia/D2-documentos-para-a-IA.md, seções 1.1 e 5 (documento 4);
modelos/CARD.md e o modelo CLAUDE.md do kit v1 (16/11/2026; no kit v2 substituído por modelos/AGENTS.md, 17/11/2026); metricas_downstream_16-11.json (16/11/2026 10h26).
O conteúdo atual do Fluxo de Desenvolvimento TI V3 e das Políticas Explícitas V1 não foi recebido: as seções afetadas são [A CONFIRMAR].
-->

# ADR-0001 · Incluir nota de vigência sobre o Fibonacci no Fluxo de Desenvolvimento TI V3

## 1. Identificação

| Campo | Valor |
|---|---|
| Número | ADR-0001 (repositório do Comitê de Agilidade) |
| Tipo | [ ] Técnica · [ ] Padrão de desenvolvimento · [x] **Mudança de documentação ou de processo** |
| Status | Proposto |
| Sistema afetado | Processo da TI (sem sistema) |
| Item que motivou | [A CONFIRMAR]: não há item no Jira. Recomendação: abrir uma Tarefa para a mudança **[ALÉM DA FONTE — decisão do usuário]** |
| Data da proposta | 16/11/2026 |
| Data da decisão | — (Proposto) |
| Revisar em | Decisão do comitê sobre a troca do Fibonacci por PP a GG no projeto e "cabe ou quebra" no card (experimento proposto para as Sprints 20 a 22) |
| Substitui | Nenhum |

---

## 2. Contexto

- O Fluxo de Desenvolvimento TI V3 (`14F0QqrDgqEmAxzHdrdtLYhWNYrJiKdsr`) ainda cita Fibonacci, que **não é praticado** pelo time (`contexto-mestre.md`, seção 3).
- A decisão de 10/11/2026 prevê o Fibonacci somente depois do refinamento, não na planning direta. Ela está **em revisão desde 13/11/2026**, com a proposta de PP a GG no projeto e regra "cabe ou quebra" no card (`contexto-mestre.md`, seções 6 e 7). A proposta reverte a decisão de 10/11 e precisa passar pelo comitê.
- O Fluxo V3 é um dos seis documentos do conjunto mínimo que a IA precisa (D2, seção 5, documento 4). Uma IA que leia o Fluxo V3 sem ressalva recomenda uma prática que não existe (D2, seção 1.1); o `contexto-mestre.md`, seção 11, lista "afirmar que o time usa Fibonacci ou planning poker hoje" entre o que evitar.
- Restrição: o Fluxo V3 não foi recebido no pacote de fontes. O ponto exato em que o Fibonacci aparece é [A CONFIRMAR].

---

## 3. Decisão

Decidimos incluir no início do Fluxo de Desenvolvimento TI V3 a nota de vigência definida no D2 (seção 5, documento 4):

> "O Fibonacci citado aqui não é praticado pelo time. A decisão de 10/11/2026 (Fibonacci só depois do refinamento) está em revisão desde 13/11/2026; o tamanho de projeto proposto é PP/P/M/G/GG (D1-pool/regua-tamanho-tempo.md, proposta sem decisão)."

Vale a partir da publicação da nota, para todos os leitores do documento, inclusive assistentes de IA. A nota é provisória: quando o comitê decidir sobre PP a GG e "cabe ou quebra", ela é trocada pelo texto da decisão, por um novo ADR que substitua este.

Fica fora desta decisão a conferência dos status do Fluxo V3 com os status em uso no Jira, inclusive PAUSADO (12 itens abertos em 16/11/2026, `metricas_downstream_16-11.json`, 10h26), que o D2 inclui no mesmo critério de pronto do documento 4. É uma segunda mudança de documentação e merece ADR próprio **[ALÉM DA FONTE — decisão do usuário]**.

---

## 4. Alternativas consideradas

| Alternativa | Prós | Contras | Por que não foi escolhida |
|---|---|---|---|
| A · Nota de vigência no início do documento (escolhida) | Corrige a leitura hoje, sem antecipar a decisão em aberto; texto já definido no D2 | O documento continua com o trecho antigo no corpo | — |
| B · Reescrever agora a seção do Fluxo V3 que trata de estimativa | Resolve de vez | Depende da decisão em aberto sobre PP a GG; seria refeita depois | Antecipa o mérito de uma decisão que o comitê ainda não tomou |
| C · Não fazer nada | Nenhum esforço | A IA e quem chega ao time continuam lendo uma prática que não existe | Mantém o erro previsível registrado no D2, seção 1.1 |

---

## 5. Consequências

| Tipo | Consequência |
|---|---|
| Positiva | Leitores e assistentes de IA deixam de tomar o Fibonacci como prática atual. Verificável: o Fluxo V3 publicado com a nota, e o `AGENTS.md` dos repositórios (com o `CLAUDE.md` contendo só `@AGENTS.md`) sem instrução contraditória |
| Negativa ou custo | O documento passa a ter uma nota que remete a uma decisão em revisão; quem lê precisa consultar o registro do comitê |
| Risco | A nota ficar desatualizada quando o comitê decidir. Percebido na revisão prevista na seção 1 ("Revisar em") |
| Reversão | Retirar a nota do documento; custo baixo |

---

## 6. Impacto em documentos existentes

| Documento | ID no Drive ou caminho | Seção afetada | O que muda | Responsável pela atualização (papel) | Prazo | Feito? |
|---|---|---|---|---|---|---|
| Fluxo de Desenvolvimento TI V3 | `14F0QqrDgqEmAxzHdrdtLYhWNYrJiKdsr` | Início do documento; trecho que cita Fibonacci [A CONFIRMAR seção] | Incluir a nota de vigência da seção 3 | Gestão do processo de desenvolvimento (dono sugerido no D2) | [A CONFIRMAR] | [ ] |
| Políticas Explícitas V1 | `14vzbIjpsUxObg8uha21YlUS6DtBTTqf7` | Seção 3.8 (dimensionamento inicial) e qualquer trecho que cite Fibonacci ou pontos [A CONFIRMAR: documento não recebido] | Se citar Fibonacci como prática, receber a mesma nota; se não citar, nenhuma mudança | Gestão do processo de desenvolvimento | [A CONFIRMAR] | [ ] |
| Modelo de card do kit | `kit-dev/modelos/CARD.md` | Seção 4, "Nota Neo · estimativa" | Citar este ADR como registro da ressalva | Responsável pelo kit | Na aceitação deste ADR | [ ] |
| Modelo de `AGENTS.md` do kit (substitui o modelo `CLAUDE.md` do v1) | `kit-dev/modelos/AGENTS.md` | Seção 2 (constituição): instrução "Não afirme que o time usa Fibonacci ou planning poker", que estava na seção 7 do `CLAUDE.md` v1; incluída como regra 8 em 17/11/2026, com fonte contexto-mestre §3 e §11 | Citar este ADR como fonte da regra 8 | Responsável pelo kit | Na aceitação deste ADR | [ ] |
| `AGENTS.md` dos repositórios do Konsig e do NeoKonsig | `AGENTS.md` na raiz de cada repositório | Mesma instrução | Conferir que a instrução existe e é a mesma | Tech lead de cada sistema | [A CONFIRMAR] | [ ] |
| Demanda 2 · documento 4 do conjunto mínimo | `D2-documentos-ia/D2-documentos-para-a-IA.md` | Seção 5, linha 4 ("Fluxo de Desenvolvimento TI V3 com nota de vigência") | Situação passa de "Existe, não recebido" para "Nota aplicada", com referência a este ADR; o texto da nota do critério de pronto é o da seção 3 deste ADR | Responsável pela Demanda 2 | Na aplicação da nota no Fluxo V3 | [ ] |
| Melhorias Scrum TI V2 | `1VHKIDjuAW6Vdezh1uOgxgrpCHPoAILmX` | — | Nenhuma: são sugestões não aplicadas e ficam fora da base da IA (D2, seção 5) | — | — | Não se aplica |

---

## 7. Conformidade e segurança

| Pergunta | Resposta |
|---|---|
| A decisão muda onde ou como dado pessoal é tratado? | Não |
| Envolve dado de cartão (PAN, CVV, trilha)? | Não |
| Envolve fornecedor novo ou processamento em nuvem? | Não |

---

## 8. Quem decide (DACI)

| Papel DACI | Quem (papel ou fórum) | Observação |
|---|---|---|
| **D**river | Gestão do processo de desenvolvimento | Dono sugerido no D2 para o documento 4 **[ALÉM DA FONTE — decisão do usuário]** |
| **A**pprover | Comitê de Agilidade, em reunião com este tema como pauta própria (decisão de 10/11/2026: um tema por reunião, registro em DACI) | **[ALÉM DA FONTE — decisão do usuário]**: atribuição proposta pelo modelo de ADR |
| **C**ontributors | PO, tech leads do Konsig e do NeoKonsig, QA | |
| **I**nformed | Time de desenvolvimento; quem mantém os `AGENTS.md` dos repositórios | |

---

## 9. Links

| Item | Link |
|---|---|
| Item do Jira que motivou | [A CONFIRMAR]: Tarefa a abrir |
| Registro da decisão no comitê (página do Confluence) | [A CONFIRMAR]: após a reunião |
| PRD relacionado | Não se aplica |
| Plano de Implementação relacionado | Não se aplica |
| ADR substituído ou relacionado | Nenhum |
| Pull request que aplicou a decisão | Não se aplica: documento no Drive; a evidência é a nova versão do Fluxo V3 |
