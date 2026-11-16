<!--
MODELO · Registro de Decisão (ADR, Architecture Decision Record) · Kit de documentação TI Neo Crédito · v1.0 · 16/11/2026 · proposta
Como usar: copie para docs/adr/ADR-<nnnn>_<chave do item>_<assunto>.md no repositório do sistema afetado.
Um ADR registra UMA decisão. Duas decisões, dois ADRs.
Um ADR aceito não é editado no mérito: se a decisão mudar, abre-se um ADR novo que o substitui, e o antigo passa a "Substituído por ADR-nnnn".
Apague os blocos "Orientação" antes de enviar para revisão.
Exemplos preenchidos: exemplos/processo/ADR-0001_CHAVE-A-CONFIRMAR_nota-vigencia-fluxo-v3.md (mudança de documentação) e exemplos/quitacao/ADR-0001 e ADR-0002 (técnicos, Konsig).
-->

# ADR-<nnnn> · <Decisão em uma frase, no infinitivo>

## 1. Identificação

| Campo | Valor |
|---|---|
| Número | ADR-<nnnn> (sequencial por repositório) |
| Tipo | [ ] Técnica (tecnologia, arquitetura, integração, dados) · [ ] Padrão de desenvolvimento · [ ] **Mudança de documentação ou de processo** |
| Status | <Proposto · Aceito · Rejeitado · Substituído por ADR-nnnn · Obsoleto> |
| Sistema afetado | <**Konsig** (legado) · **NeoKonsig** (reescrita) · outro sistema do Inventário · Processo da TI (sem sistema)> |
| Item que motivou | <GDP-n · US-n · DS-n> |
| Data da proposta | <dd/mm/aaaa> |
| Data da decisão | <dd/mm/aaaa, quando Aceito ou Rejeitado> |
| Revisar em | <data ou evento: "retro da S22", "fim do experimento"> |
| Substitui | <ADR-nnnn ou "nenhum"> |

> **Orientação.** "Sistema afetado" admite um único sistema. Se a decisão vale para Konsig e NeoKonsig, abra um ADR em cada repositório, com referência cruzada, porque as tecnologias são diferentes e a decisão pode ter consequências diferentes em cada um. Decisão de processo (sem sistema) fica no repositório deste comitê ou na página do comitê no Confluence **[ALÉM DA FONTE — decisão do usuário]**.
>
> **Status, o que cada um quer dizer:**
> - **Proposto:** escrito, em discussão. Não autoriza implementação.
> - **Aceito:** decidido pelo responsável do DACI (seção 8). Passa a valer.
> - **Rejeitado:** discutido e recusado; o registro fica para que a discussão não recomece do zero.
> - **Substituído:** outro ADR tomou o lugar; indicar qual.
> - **Obsoleto:** deixou de se aplicar sem substituto (por exemplo, o componente foi desativado).

---

## 2. Contexto

<Qual a situação, qual a força que obriga a decidir agora e quais restrições existem. Fatos com fonte e data.>

> **Orientação.** Entra: o problema, as restrições (prazo, norma, sistema legado, capacidade) e os fatos que sustentam a decisão, cada um com fonte. Não entra: a decisão (vai na seção 3); opinião sem fato.
>
> **Exemplo (mudança de documentação):** O Fluxo de Desenvolvimento TI V3 cita Fibonacci, que não é praticado pelo time. A decisão de 10/11/2026 prevê o uso somente depois do refinamento, e está em revisão desde 13/11/2026 com a proposta de PP a GG por projeto e "cabe ou quebra" por card. Uma IA que leia o Fluxo V3 sem ressalva recomenda uma prática inexistente (`D2-documentos-ia/D2-documentos-para-a-IA.md`, seção 1.1).
>
> **Exemplo (técnica, Konsig):** O Konsig não tem pipeline de CI/CD (US-43, Backlog) e vai receber construção nova em 2027 (cartão, decisão de 13/11/2026). O padrão de release e deploy está em definição no DS-550 (9 cards em Backlog), começando pelo Keycloak (`epicos_downstream_16-11.csv`, 16/11/2026 10h26).

---

## 3. Decisão

<"Decidimos <ação>." Uma decisão, no presente, com o alcance explícito: onde vale, a partir de quando, para quem.>

> **Orientação.** Entra: o que passa a ser feito, com alcance e início de vigência. Não entra: plano de execução detalhado (vai para o Plano de Implementação); justificativa longa (vai para o contexto e as alternativas).
>
> **Exemplo:** Decidimos incluir no início do Fluxo de Desenvolvimento TI V3 uma nota de vigência informando que o Fibonacci citado no documento não descreve a prática atual e remetendo à decisão vigente do Comitê de Agilidade. Vale a partir da publicação da nota, para todos os leitores do documento, inclusive assistentes de IA.

---

## 4. Alternativas consideradas

| Alternativa | Prós | Contras | Por que não foi escolhida |
|---|---|---|---|
| <A · a escolhida> | | | — |
| <B> | | | <motivo> |
| <C · não fazer nada> | | | <motivo> |

> **Orientação.** Entra: pelo menos duas alternativas reais, além de "não fazer nada". Não entra: alternativa inventada só para perder. Se só existe uma opção viável, diga por quê.
>
> **Exemplo:** B · Reescrever o Fluxo V3 inteiro agora: resolve de vez, mas depende da decisão em aberto sobre PP a GG e seria refeito depois. C · Não fazer nada: a IA e quem chega ao time continuam lendo uma prática que não existe.

---

## 5. Consequências

| Tipo | Consequência |
|---|---|
| Positiva | <o que melhora, com indicador se houver> |
| Negativa ou custo | <o que piora, custo, dívida aceita> |
| Risco | <o que pode dar errado e como será percebido> |
| Reversão | <como desfazer e quanto custa> |

> **Orientação.** Entra: efeitos para o sistema, para o time e para a operação, inclusive os ruins. Uma decisão sem consequência negativa registrada quase sempre foi mal analisada.
>
> **Exemplo (técnica, Konsig):** Negativa: até o pipeline existir, cada deploy do Konsig exige passos manuais descritos no Plano de Implementação, com tempo de Waiting for deploy maior. Risco: regressão em fluxo não coberto pela regressão automatizada (DS-53: 3 de 12 cards concluídos, `epicos_downstream_16-11.csv`, 16/11/2026 10h26).

---

## 6. Impacto em documentos existentes

| Documento | ID no Drive ou caminho | Seção afetada | O que muda | Responsável pela atualização (papel) | Prazo | Feito? |
|---|---|---|---|---|---|---|
| Fluxo de Desenvolvimento TI V3 | `14F0QqrDgqEmAxzHdrdtLYhWNYrJiKdsr` | <seção> | <mudança> | <papel> | <data> | [ ] |
| Políticas Explícitas V1 | `14vzbIjpsUxObg8uha21YlUS6DtBTTqf7` | <ex.: 3.6 Requisitos técnicos; 3.8 dimensionamento> | | | | [ ] |
| Inventário de Sistemas | `1LwSqMSxgldjHxNQmj34uDAI_refDOkWG` | <linha do sistema> | | | | [ ] |
| Konsig Arquitetura | `1u3NsVaAXvnayi6I7eCJ4z41fC2yh1naP` | | | | | [ ] |
| Guia "Como escrever um card" (InnoviaX v1.0) | arquivo do projeto, sem ID no Drive | <seção> | | | | [ ] |
| `CLAUDE.md` do repositório | `CLAUDE.md` | <seção> | | | | [ ] |
| PRDs e Planos em execução | `docs/prd/...`, `docs/planos/...` | | | | | [ ] |
| Cards abertos afetados | <chaves DS> | bloco 1 (referência) e bloco 3 (DoR) | | | | [ ] |

> **Orientação.** Esta seção é obrigatória em ADR de **mudança de documentação ou de processo** e recomendada nos demais. Entra: todo documento que, depois desta decisão, passaria a dizer algo falso. Não entra: documento só "relacionado". O ADR só passa a Aceito quando a lista estiver completa; ele só se considera aplicado quando todas as linhas estiverem com [x]. Os IDs do Drive são os registrados no `contexto-mestre.md`, seção 3 (16/11/2026); os documentos não foram recebidos no pacote de fontes e o conteúdo atual de cada um é [A CONFIRMAR].
>
> **Exemplo:** Fluxo de Desenvolvimento TI V3 · início do documento e seção que cita Fibonacci · incluir nota de vigência · responsável pela gestão do processo de desenvolvimento · [A CONFIRMAR data].

---

## 7. Conformidade e segurança

| Pergunta | Resposta |
|---|---|
| A decisão muda onde ou como dado pessoal é tratado? | <Não · Sim: o que muda; parecer do DPO em <data>> |
| Envolve dado de cartão (PAN, CVV, trilha)? | <Não · Sim: impacto no escopo do ambiente de dados de cartão> |
| Envolve fornecedor novo ou processamento em nuvem? | <Não · Sim: fornecedor, região, contrato> |

> **Orientação.** Responder às três perguntas sempre, mesmo que seja "Não". Não transcrever trecho de norma; citar a norma pelo nome e indicar o requisito interno que ela gera.

---

## 8. Quem decide (DACI)

| Papel DACI | Quem (papel ou fórum) | Observação |
|---|---|---|
| **D**river (conduz a decisão) | <papel que escreveu o ADR> | Prepara o ADR e leva ao fórum |
| **A**pprover (decide) | <tech lead para decisão técnica de um sistema · Comitê de Agilidade, com a gestora da TI, para mudança de documentação ou de processo> | Um único aprovador |
| **C**ontributors (consultados) | <PO, QA, infraestrutura, Segurança e Conformidade> | |
| **I**nformed (informados) | <time do sistema, áreas usuárias> | |

> **Orientação.** O Comitê de Agilidade registra suas decisões em DACI, em reuniões de 60 minutos com um tema por reunião (decisão de 10/11/2026). Um ADR de mudança de documentação ou de processo é levado ao comitê como tema próprio. A atribuição de "Approver" por tipo de decisão é proposta deste modelo **[ALÉM DA FONTE — decisão do usuário]**.

---

## 9. Links

| Item | Link |
|---|---|
| Item do Jira que motivou | <GDP-n / US-n / DS-n> |
| Registro da decisão no comitê (página do Confluence) | <link> |
| PRD relacionado | `docs/prd/...` |
| Plano de Implementação relacionado | `docs/planos/...` |
| ADR substituído ou relacionado | `docs/adr/...` |
| Pull request que aplicou a decisão | <link> |
