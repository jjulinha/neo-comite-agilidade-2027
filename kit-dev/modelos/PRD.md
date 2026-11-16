<!--
MODELO · Documento de Requisitos de Produto (PRD) · Kit de documentação TI Neo Crédito · v1.0 · 16/11/2026 · proposta
Como usar: copie este arquivo para docs/prd/<chave GDP>_<assunto>.md no repositório do sistema afetado.
Apague todos os blocos "Orientação" antes de enviar para revisão. Mantenha os títulos das seções.
Seção que não se aplica: escreva "Não se aplica: <motivo em uma linha>". Seção vazia não é aceita.
PRD curto (tamanho M): seções 1, 2, 3, 4, 7, 10, 11, 14, 15 e 16 obrigatórias; as demais podem ser "Não se aplica".
A seção 16 (Aprovações) é obrigatória em todo PRD, porque é a saída exigida para concluir no Upstream (README, seção 2, etapa 5).
Compatibilidade: o cabeçalho segue o padrão da Visão do Cartão de Crédito v6 (03/11/2026): Dados do Projeto, Versionamento,
Contexto e objetivos, Papéis, Macroetapas, Regras, Riscos. Os critérios e cenários seguem o guia "Como escrever um card" (InnoviaX v1.0).
-->

# <Título da demanda: verbo + objeto>

## 1. Identificação

### 1.1 Dados do projeto

| Campo | Valor |
|---|---|
| Nome do projeto | <nome> |
| Sistema | <**Konsig** (legado) **ou** **NeoKonsig** (reescrita) ou outro sistema do Inventário. Um único sistema por PRD.> |
| Item GDP | <GDP-n> |
| Itens Upstream | <US-n, US-n> |
| Épico(s) Downstream | <DS-n, preenchido após o Plano de Implementação> |
| Solicitante / área | <área solicitante, sem nome de pessoa> |
| Responsável pelo documento | <papel: PO, analista funcional> |
| Data de abertura | <dd/mm/aaaa> |
| Prazo esperado pela área | <mês/ano ou "não informado"> |
| Prioridade no GDP | <Highest, High, Medium, Low, Lowest> |
| Classe de serviço | <Expedite · Fixed Date · Standard · Intangible> |
| Risco | <Alto · Médio · Baixo> |
| Vinculado ao PDTI | <Sim (diretriz: ...) · Não> |
| Natureza | [ ] Tem potencial financeiro · [ ] Gera atendimento · [ ] Reduz fluxo operacional · [ ] Regulatória |
| Status do documento | <Rascunho · Em revisão · Aprovado · Em execução · Concluído · Substituído> |
| Documentos relacionados | <Visão (ID no Drive), PRD-mãe, ADRs, protótipo> |

> **Orientação.** Entra: o que identifica a demanda e a amarra ao Jira. Não entra: nomes de pessoas, solução técnica. Os campos Natureza e Vinculado ao PDTI repetem o cabeçalho da Visão do Cartão v6 para que o PRD e a Visão se leiam do mesmo jeito; "Regulatória" é acréscimo deste modelo **[ALÉM DA FONTE — decisão do usuário]**.
>
> **Exemplo:** Nome do projeto: Quitação · Fase 2 · Motor de validação. Sistema: **Konsig** (legado). Item GDP: GDP-76. Itens Upstream: US-69. Épico: DS-500. Solicitante / área: Financeiro. Responsável pelo documento: analista funcional.

### 1.2 Versionamento

| Data | Responsável (papel) | Versão | Descrição da alteração |
|---|---|---|---|
| <dd/mm/aaaa> | <PO> | 0.1 | Elaboração do documento. |

> **Orientação.** 0.x em rascunho e revisão; 1.0 na aprovação; 1.x para ajuste sem mudança de escopo; 2.0 para mudança de escopo, que reabre aprovação e exige revisar os cards cuja referência (bloco 1 do card) cita a versão anterior.

---

## 2. Problema

<Como o processo funciona hoje, quem é afetado, o que dá errado e qual a consequência. Três a dez linhas.>

> **Orientação.** Entra: situação atual verificável, inclusive passos manuais e fora do sistema; consequência medida ou observada (retrabalho, risco operacional, reclamação). Não entra: a solução; adjetivos sem fato ("processo ruim"). Reaproveite o roteiro de abertura do GDP (Contexto da solicitação, Descrição do problema, Como o processo funciona atualmente, Consequências do cenário atual), sem copiar o nome do solicitante.
>
> **Exemplo:** O Financeiro executa a quitação de dívida e o pagamento residual das propostas da esteira Cartão Consignado Compra de forma manual, com Konsig, planilhas e portais bancários (DS-418). A conferência das regras de pagamento é feita em planilha, sem registro auditável da decisão, com risco financeiro e de rastreamento (US-69).

---

## 3. Objetivo e métrica de sucesso

| Objetivo | Métrica | Linha de base (fonte e data) | Meta | Quando medir |
|---|---|---|---|---|
| <o que muda para o negócio> | <fórmula> | <valor, fonte, data> ou [A CONFIRMAR] | <valor> | <data ou evento> |

> **Orientação.** Entra: um a três objetivos de negócio, cada um com métrica que alguém consegue medir sem abrir o código. Toda linha de base cita a fonte e a data. Não entra: objetivo técnico ("migrar para a versão X"), que vai para o ADR; meta sem linha de base. Se a linha de base não existe, registre [A CONFIRMAR] e diga quem mede.
>
> **Exemplo:** Objetivo: comparar a decisão do motor com a decisão da planilha antes de automatizar o pagamento. Métrica: propostas em que motor e planilha concordam ÷ propostas avaliadas no modo sombra **[ALÉM DA FONTE — decisão do usuário: leitura de "comparar com a planilha durante o modo sombra", DS-507]**. Linha de base: não existe [A CONFIRMAR: o critério de avanço da Fase 2, citado no DS-507, não está descrito]. Meta: definida pela área Financeiro.

---

## 4. Escopo e fora de escopo

### 4.1 Dentro do escopo

- <capacidade 1>
- <capacidade 2>

### 4.2 Fora do escopo

| Item | Motivo | Onde será tratado |
|---|---|---|
| <item> | <motivo> | <fase, outro GDP, não será feito> |

> **Orientação.** Entra: capacidades em linguagem de negócio; no fora de escopo, o que alguém poderia supor que está incluído. Não entra: lista de telas ou de tabelas. O fora de escopo é o que permite recusar acréscimos depois; ele precisa ser tão explícito quanto o escopo.
>
> **Exemplo:** Dentro: aplicar às propostas em AND - AGUARD QUITACAO as regras cadastradas na Fase 1 e registrar cada avaliação. Fora: alterar situação ou status da proposta, enviar e-mail e montar lote de pagamento (modo sombra, registrado no DS-500); pagamento via PagAuto com a API do Banco do Brasil (fase posterior, decisão de 09/11/2026).

---

## 5. Perfis (papéis e responsabilidades)

| Perfil | Papel na funcionalidade | O que pode fazer | O que não pode fazer |
|---|---|---|---|
| <perfil de acesso no sistema> | <papel> | <ações> | <restrições> |

> **Orientação.** Entra: perfis de acesso do sistema e atores externos (parceiros, processadoras), no formato da tabela de papéis da Visão do Cartão v6. Não entra: nome de pessoa ou de usuário. Quando o sistema ainda não tem o perfil, registre [A CONFIRMAR] e o dono da definição.
>
> **Exemplo:** Analista do Financeiro: consulta a lista e o detalhe das avaliações e exporta para Excel; vê CPF mascarado conforme o perfil. Não altera regra nem decisão.

---

## 6. Fluxo atual × proposto

### 6.1 Macroetapas

| # | Macroetapa | Hoje (como é feito) | Proposto (o que muda) | Responsável | Dependências |
|---|---|---|---|---|---|
| 1 | <etapa> | <manual, planilha, sistema> | <comportamento novo> | <área ou sistema> | <parceiro, outra etapa> |

### 6.2 Diagrama

<Link para o BPMN AS-IS e TO-BE ou para o protótipo. Se não houver: "Não elaborado" e o motivo.>

> **Orientação.** Entra: a sequência de negócio, uma linha por etapa, no formato da tabela de macroetapas da Visão do Cartão v6 (#, macroetapa, escopo, responsável, dependências), acrescida da coluna "Hoje". Não entra: descrição de tela; códigos de requisito dentro do protótipo (nas telas, nunca citar RF ou RN).
>
> **Exemplo:** 1 · Captura: hoje o Financeiro filtra as propostas em planilha; proposto, o motor captura as propostas em AND - AGUARD QUITACAO. Responsável: Konsig. Dependência: regras cadastradas na Fase 1 (DS-418).

---

## 7. Regras de negócio

| Código | Regra | Origem | Observação |
|---|---|---|---|
| RN01 | <afirmação verificável, com número, prazo ou condição> | <norma, contrato, decisão com data, área> | <exceção, vigência> |
| RN02 | ... | ... | ... |

> **Orientação.** Entra: uma regra por linha, numerada e estável (o número não muda entre versões; regra removida fica riscada com a versão em que saiu), com a origem de cada uma. Não entra: comportamento de tela; regra sem origem. Toda regra que não estiver na fonte da demanda leva [ALÉM DA FONTE — decisão do usuário]. São estes códigos que os cards citam no bloco 1.
>
> **Exemplo:** RN01 · O motor avalia apenas propostas da esteira Cartão Consignado Compra na situação AND - AGUARD QUITACAO. Origem: critério de aceite do DS-501. RN02 · Na Fase 2 o motor não altera situação nem status da proposta. Origem: escopo registrado no DS-500.

---

## 8. Requisitos não funcionais

| Código | Categoria | Requisito (mensurável) | Origem |
|---|---|---|---|
| RNF01 | Segurança | <controle de acesso por perfil, trilha de auditoria> | <política, ADR> |
| RNF02 | LGPD | <mascaramento, minimização, retenção> | <LGPD, parecer do DPO> |
| RNF03 | Desempenho | <tempo máximo, volume> | <área, medição> |
| RNF04 | Disponibilidade e falha | <comportamento quando o serviço externo cai> | <contrato, área> |
| RNF05 | Manutenibilidade | <teste automatizado, simulação de serviço externo> | <tech lead> |

> **Orientação.** Entra: só o que for específico desta demanda, com número. Não entra: "o sistema deve ser seguro e performático". Em demanda do cartão, registre o que vem do PCI DSS e da Mastercard listados na Visão do Cartão v6 (não guardar CVV, mascarar PAN em logs, escopo do ambiente de dados de cartão, riscos R18 e R19), sem transcrever o texto das normas.
>
> **Exemplo:** RNF01 · Toda avaliação do motor fica registrada com data, regra aplicada e resultado, e pode ser consultada pelo Financeiro sem acesso ao banco. RNF02 · Na exportação para Excel, o CPF aparece mascarado conforme o perfil (DS-507 e DS-509).

---

## 9. Integrações

| Parceiro ou sistema | Finalidade | Sentido | Meio | Contrato, manual ou leiaute (versão) | Situação |
|---|---|---|---|---|---|
| <parceiro> | <para quê> | <envio, recebimento, ambos> | <API, arquivo SFTP, fila> | <documento e versão> | <existente · nova · [A CONFIRMAR]> |

> **Orientação.** Entra: cada integração tocada pela demanda, com o documento técnico de origem e a versão. Integração entre Konsig e NeoKonsig também entra aqui, como integração entre sistemas distintos, com o dono de cada dado. Não entra: endereço de servidor, credencial, identificador de conta. Tecnologia que não estiver no Inventário de Sistemas: [A CONFIRMAR no Inventário de Sistemas].
>
> **Exemplo:** Banco do Brasil · pagamento da quitação · envio · API do BB via PagAuto · análise da API [A CONFIRMAR: não recebida] · nova, fase posterior (decisão de 09/11/2026).

---

## 10. Critérios de aceite

- <afirmação binária, com número, prazo, formato ou janela>
- <comportamento exigido em falha>
- <exigência de registro ou auditoria>

### 10.1 Cenários de comportamento (BDD) principais

```
Cenário: <título curto · caminho feliz>
  Dado que <estado inicial verificável>
  Quando <uma única ação>
  Então <resultado observável por quem lê>

Cenário: <alternativo>
Cenário: <borda>
Cenário: <falha>
```

> **Orientação.** Entra: os critérios de aceite da demanda como um todo e os cenários que cobrem caminho feliz, alternativo, borda e falha (guia InnoviaX, seções 03 a 05). Os cards herdam daqui e detalham; os cenários de teste com dado concreto ficam nos cards. Não entra: advérbio ("rapidamente"), critério que não vira teste, detalhe de implementação.
>
> **Exemplo de critério:** A exportação gera um arquivo .xlsx com os filtros aplicados, as colunas na ordem da aba de extração e o CPF mascarado conforme o perfil.
> **Exemplo de cenário (falha):** Cenário: regra sem vigência ativa. Dado que nenhuma regra do validador está vigente na data da avaliação, quando o motor avalia a proposta, então a decisão registrada é ANALISE_MANUAL e o motivo fica visível no detalhe. [ALÉM DA FONTE — decisão do usuário: exemplo ilustrativo; o comportamento real depende da tabela de decisão do Documento de Requisitos V04.]

---

## 11. Dependências

| O que falta | Quem responde (papel ou área) | Até quando | Bloqueia o caminho principal? |
|---|---|---|---|
| <documento, decisão, acesso, ambiente> | <papel> | <dd/mm/aaaa> | <Sim · Não> |

> **Orientação.** Entra: o que precisa existir e não depende do time de desenvolvimento, sempre com dono e data (guia InnoviaX, bloco 9). Não entra: tarefa de desenvolvimento; "a definir" sem dono. Se bloqueia o caminho principal, a demanda não sai do Upstream.
>
> **Exemplo:** Ajustes apontados no teste de 09/11/2026 da tela de Administração de Quitação · tech lead · [A CONFIRMAR data] · Sim (pré-requisito da Fase 2 declarado no DS-500).

---

## 12. Tratamento de dados pessoais (LGPD)

| Categoria de dado tratado | Finalidade | Quem acessa (perfil) | Mascaramento ou minimização | Retenção | Compartilhado com terceiro? |
|---|---|---|---|---|---|
| <ex.: CPF do cliente> | <para quê> | <perfil> | <regra> | <prazo ou [A CONFIRMAR com o DPO]> | <Não · Sim: parceiro e base contratual> |

> **Orientação.** Entra: a declaração do tratamento, não o dado. Não entra em nenhuma hipótese: CPF, nome, contato ou contrato reais, nem em exemplo. Demanda que envie dado pessoal a parceiro novo ou a fornecedor de IA precisa de parecer do DPO antes da aprovação **[ALÉM DA FONTE — decisão do usuário]**.

---

## 13. Riscos

| ID | Risco | Categoria | Probabilidade | Impacto | Mitigação | Dono (papel) |
|---|---|---|---|---|---|---|
| R01 | <evento incerto e consequência> | <técnico, negócio, regulatório, prazo> | <A · M · B> | <A · M · B> | <ação> | <papel> |

> **Orientação.** Entra: risco com evento e consequência, no formato da tabela de riscos da Visão do Cartão v6 (ID, risco consolidado, categoria, mitigação), acrescida de probabilidade, impacto e dono. Não entra: problema que já aconteceu (isso é dependência ou pendência).
>
> **Exemplo:** R01 · Construção nova no Konsig, que não tem pipeline de CI/CD (US-43, Backlog): implantação manual aumenta o risco de regressão. Técnico · M · A · Plano de teste com regressão manual dos fluxos de quitação; deploy acompanhado pelo tech lead · tech lead.

---

## 14. Tamanho estimado (régua)

| Campo | Valor |
|---|---|
| Cards de épico previstos | <n> (quebra pela seção 06 do guia; detalhe no Plano) |
| Classe | <PP 1–2 · P 3–4 · M 5–9 · G 10–20 · GG > 20> |
| Referência no Downstream (dias úteis) | <PP–M: 16 típico / 29 conservador · G: 66 piso / 86 · GG: não estimar, quebrar> |
| Referência no Upstream (dias úteis) | 29 típico / 44 conservador |
| Precisa quebrar antes? | <Sim, se GG; recomendado avaliar para G> |

> **Orientação.** Fonte das faixas e das referências: `D1-pool/regua-tamanho-tempo.md` (versão 1, 16/11/2026). **As faixas são proposta sem decisão do comitê.** Não entra: pontos de história nem Fibonacci, que não são prática atual do time. O tamanho é registrado ao concluir no Upstream (Políticas Explícitas V1, seção 3.8) e comparado com o realizado no fechamento.
>
> **Exemplo:** Quitação Fase 2: 8 cards (DS-501, DS-503 a DS-509), classe M, referência de 16 dias úteis no Downstream (29 conservador).

---

## 15. Rastreabilidade

| Regra ou critério | Item GDP | Item Upstream | Card(s) Downstream | Caso(s) de teste |
|---|---|---|---|---|
| RN01 | GDP-n | US-n | DS-n | T1, T2 |

> **Orientação.** Entra: cada regra (seção 7) e cada RNF (seção 8) ligados ao card que a implementa e ao teste que a prova. Uma regra sem card é escopo esquecido; um card sem regra é escopo inventado. Preencha a coluna de cards depois do Plano de Implementação.

---

## 16. Aprovações

| Papel | Área | Decisão | Data | Observação |
|---|---|---|---|---|
| Área solicitante | <área> | <Aprovado · Aprovado com ressalva · Reprovado> | <dd/mm/aaaa> | |
| PO | TI | | | |
| Tech lead | TI | | | Confirma sistema (Konsig ou NeoKonsig) e necessidade de ADR |
| Segurança e Conformidade / DPO | TI | | | Somente se a seção 12 declarar compartilhamento com terceiro ou dado sensível |

> **Orientação.** A aprovação registra papel e área; o nome de quem aprovou fica no histórico do Jira (Aprovação solicitantes), não no documento. A linha de Segurança e Conformidade é proposta deste modelo **[ALÉM DA FONTE — decisão do usuário]**.
