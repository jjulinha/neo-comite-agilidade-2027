# ADR-001 · Pagamento da quitação via PagAuto com a API do Banco do Brasil

| Item | Valor |
|---|---|
| Tipo de documento | ADR (registro de decisão de arquitetura) · exemplo preenchido do kit para os devs |
| Número | ADR-001 (primeiro registro do Konsig neste formato) |
| Status | **Aceito** |
| Data da decisão | 09/11/2026 |
| Data deste registro | 16/11/2026 |
| Sistema | **Konsig (legado)**. Não se aplica ao NeoKonsig. |
| Demanda | GDP-76 · [KON] SISTEMATIZAÇÃO DA QUITAÇÃO |
| Decisores (papéis) | [A CONFIRMAR]: as fontes registram a data e o conteúdo da decisão, não quem decidiu |
| Autor do registro (papel) | Analista de requisitos da TI |
| Substitui · substituído por | Nenhum · nenhum |
| Documentos relacionados | PRD-GDP-76-quitacao-fase2-motor-de-validacao · PLANO-GDP-76-quitacao-fase2 · insumo `insumos/quitacao-estado-e-faseamento.md` (16/11/2026) · `insumos/sistemas-e-tecnologias.md` (16/11/2026) |

> **Regra do modelo para o cabeçalho.** Entra: número sequencial, status (proposto, aceito, substituído, descartado), data da decisão e decisores por papel. Não entra: nome de pessoa nem data do registro no lugar da data da decisão. Exemplo curto: "Status: aceito · decisão de 09/11/2026".

---

## 1. Contexto

> **Regra do modelo.** Entra: o problema que obrigou a decidir e os fatos técnicos que limitam a escolha, cada um com fonte. Não entra: a decisão nem a defesa dela. Exemplo curto: "o Konsig não tem CI/CD (US-43)".

1. **O pagamento da quitação é manual.** A etapa de quitação de dívida e de pagamento residual é feita "de maneira manual através de um EXCEL" (US-69, upstream_16-11.csv, 16/11/2026 9h51), num processo "predominantemente manual (Konsig + planilhas + WhatsApp + portais bancários)" (DS-418, downstream_16-11.csv, 16/11/2026 10h26). A demanda de origem pede que o sistema traga o valor de cada boleto ou carta TED, o banco que será quitado e a data de vencimento, porque a planilha é montada à mão (GDP-76, gdp_16-11.csv, 16/11/2026 9h51).
2. **O PagAuto já existe no Konsig.** É o componente de pagamentos e comprovantes, em produção (sistemas-e-tecnologias.md, 16/11/2026; DS-59, downstream_16-11.csv, 16/11/2026 10h26, cita os comprovantes do PAGAUTO).
3. **O Konsig já consome uma API do Banco do Brasil.** A validação automática das contas do BB por API foi entregue no épico DS-92 "Retorno de pagamentos BB" (GDP-60, CONCLUÍDO em 16/09/2026; DS-93; gdp_16-11.csv e downstream_16-11.csv, 16/11/2026). Se a API de pagamento é a mesma API, o mesmo produto ou o mesmo contrato com o banco: **[A CONFIRMAR]**.
4. **O Konsig não tem CI/CD.** US-43 "Konsig: CI/CD" está em BACKLOG desde 14/08/2026; um dos objetivos listados é a "atualização de versão em qualquer horário do dia" (upstream_16-11.csv, 16/11/2026 9h51). O padrão de release (DS-550) também está em Backlog (epicos_downstream_16-11.csv, 16/11/2026 10h26).
5. **A automação foi dividida em fases.** Tela de parametrização (Fase 1, DS-418) → motor de validação com tela de visualização (Fase 2, DS-500) → efeitos do motor → pagamento (contexto-mestre.md, seção 10; insumo da Quitação, seção 3.1).

## 2. Decisão

> **Regra do modelo.** Entra: a escolha em uma ou duas frases afirmativas, com o escopo. Não entra: justificativa (vai para a seção 3) nem tarefa de implementação. Exemplo curto: "o pagamento usa o PagAuto com a API do BB".

**D1.** O pagamento da quitação no Konsig será feito via **PagAuto com a API do Banco do Brasil** (decisão de 09/11/2026, contexto-mestre.md, seção 10).

**D2.** A **integração bancária é a última etapa** do faseamento da Quitação: entra depois do motor de validação (Fase 2) e dos efeitos do motor (contexto-mestre.md, seção 10). Pela numeração adotada no insumo da Quitação, é a Fase 4 **[ALÉM DA FONTE — decisão do usuário: numeração recomendada no insumo, seção 3.1]**.

**Fora desta decisão.** Forma de pagamento por boleto ou TED, tratamento de falha e de estorno, conciliação do retorno, limites de valor e alçada de aprovação: **[A CONFIRMAR]**, dependem da análise da API do BB (responsabilidade do analista de requisitos, contexto-mestre.md, seção 10; não consta no pacote).

## 3. Motivos

> **Regra do modelo.** Entra: por que esta opção, com o fato que sustenta cada motivo. Não entra: vantagem genérica ("mais moderno"), nem motivo que ninguém registrou apresentado como se tivesse sido. Exemplo curto: "o PagAuto já está em produção no Konsig".

O motivo da decisão de 09/11/2026 **não está registrado** nas fontes **[A CONFIRMAR]**. Os fatos abaixo são compatíveis com ela e servem de base até o registro do motivo pelos decisores:

| Fato | Fonte | Relação com a decisão |
|---|---|---|
| O PagAuto já opera pagamentos e comprovantes no Konsig | sistemas-e-tecnologias.md; DS-59 | D1 reaproveita um componente existente em vez de criar outro |
| O Konsig já integra com uma API do BB (validação de contas) | GDP-60; DS-92; DS-93 | D1 parte de uma integração bancária já conhecida no legado |
| O motor da Fase 2 roda em modo sombra, sem efeito sobre as propostas | DS-500 | D2 permite validar as decisões do motor antes de qualquer pagamento automático **[ALÉM DA FONTE — decisão do usuário: leitura deste ADR, não motivo registrado]** |
| O Konsig não tem CI/CD | US-43 | D2 adia para o fim a parte de maior risco operacional **[ALÉM DA FONTE — decisão do usuário: leitura deste ADR, não motivo registrado]** |

## 4. Alternativas registradas nas fontes

> **Regra do modelo.** Entra: só alternativas que alguém considerou ou que existem de fato (o processo atual, uma versão anterior do plano), com fonte. Não entra: alternativa inventada para parecer completa. Exemplo curto: "manter o pagamento nos portais bancários (processo atual, DS-418)".

| Alternativa | Fonte | Situação |
|---|---|---|
| A1 · Manter o pagamento manual nos portais bancários, com planilha | Processo atual descrito no DS-418 e no US-69 | Não adotada. É o que o projeto substitui |
| A2 · Pagamento BB antes do motor de validação (pagamento como Fase 2 e motor como Fase 3) | Previsão de entregas V02, modificada 06/11/2026 (insumo, seção 4.1) | Superada pela ordem vigente após 09/11/2026 (D2). Numeração obsoleta |
| A3 · Outro componente de pagamento, outro banco ou outro canal de pagamento | Nenhuma fonte registra | **[A CONFIRMAR]**: se houve, os decisores devem registrar aqui |

## 5. Consequências

> **Regra do modelo.** Entra: o que fica mais fácil, o que fica mais difícil e o que passa a ser obrigatório, cada item com fonte ou com a marca de lacuna. Não entra: lista de tarefas (vai para o plano de implementação). Exemplo curto: "a Fase 4 depende da análise da API do BB".

### 5.1 Positivas

- O motor (Fase 2) e os efeitos (Fase 3) podem ser construídos e testados sem depender da API do BB (DS-500; contexto-mestre.md, seção 10).
- O pagamento usa um componente que já está em produção no Konsig (sistemas-e-tecnologias.md).

### 5.2 Negativas e riscos

| Risco | Evidência | Tratamento |
|---|---|---|
| R1 · Integração nova num sistema sem CI/CD | US-43 em BACKLOG (upstream_16-11.csv, 16/11/2026 9h51); contexto-mestre.md, seção 7 | Plano de deploy e de reversão específico da Fase 4 **[A CONFIRMAR]** |
| R2 · Observabilidade do PagAuto pendente | Migração do APM pausada (DS-305, PAUSADO); subtarefa do PagAuto em Backlog (DS-323) (downstream_16-11.csv, 16/11/2026 10h26) | Concluir o DS-323 antes da Fase 4 **[ALÉM DA FONTE — decisão do usuário]** |
| R3 · Prazo da Quitação depende de etapas sem épico | Fases 3 e 4 sem épico, sem card e sem item no Upstream; no pool, ambas estimadas pela descrição, com confiança baixa e entrega em fev/27 (pool-2027-plano.xlsx, aba Pool 2027, base Jira 16/11/2026) | Dimensionar a Fase 4 com a calculadora PP a GG quando a análise da API do BB estiver pronta |
| R4 · Credenciais, certificado e ambiente de homologação da API do BB | Nenhuma fonte descreve | **[A CONFIRMAR]** |
| R5 · Dados de pagamento e de cliente em trânsito para o banco (LGPD) | Nenhuma fonte descreve o tratamento | **[A CONFIRMAR]** |

### 5.3 Obrigações que a decisão cria

- Criar o épico da integração bancária no Downstream quando o escopo existir (hoje não há épico: insumo, seção 3.5).
- Vincular GDP-76, US-69, DS-418, DS-500 e o futuro épico da Fase 4 no Jira (insumo, seção 6).

## 6. Impacto em documentos

> **Regra do modelo.** Entra: cada documento oficial que muda por causa da decisão, a seção afetada, o que muda e o responsável por papel. Não entra: documento que não muda. Exemplo curto: "Inventário de Sistemas: incluir a integração PagAuto × API do BB na linha do Konsig".

| Documento | Onde | O que muda | Responsável (papel) | Situação em 16/11/2026 |
|---|---|---|---|---|
| Insumo "Projeto Quitação · Estado e faseamento" (`insumos/quitacao-estado-e-faseamento.md`) | Seções 2, 3.5 e 6 | Citar o ADR-001 como registro da decisão de 09/11/2026 e da ordem das fases | Analista de requisitos | A decisão já consta; falta a referência ao ADR |
| Previsão de entregas 2026 V02 (planilha de esforço do Downstream) | Linhas da Quitação (células A16:J19 e C31:D34) | Trocar a numeração: Fase 2 = motor; pagamento BB por último | Responsável pela planilha de esforço | Desatualizada (06/11/2026) |
| Inventário de Sistemas (Drive `1LwSqMSxgldjHxNQmj34uDAI_refDOkWG`) | Linhas do PagAuto e do Banco do Brasil | Registrar a integração PagAuto × API do BB para pagamento da quitação no Konsig, com certificado e validade | Responsável pelo Inventário [A CONFIRMAR] | Inventário não recebido no pacote |
| Konsig Arquitetura (Drive `1u3NsVaAXvnayi6I7eCJ4z41fC2yh1naP`) | Integrações externas | Incluir o fluxo de pagamento da quitação | Tech lead do Konsig | Documento não recebido no pacote; seção exata [A CONFIRMAR] |
| Documento de Requisitos V04 da Quitação (26/10/2026) | Requisitos de pagamento | Confirmar se já prevê o PagAuto e a API do BB; se não, nova versão | Analista de requisitos | Anterior à decisão; conteúdo [A CONFIRMAR] |
| BPMN TO-BE da Quitação | Etapa de pagamento | Desenhar o pagamento via PagAuto e API do BB | Analista de requisitos | Não consta no pacote |
| contexto-mestre.md | Seção 10 | Citar o ADR-001 junto da decisão | Analista de requisitos | A decisão já consta |
| Pool de projetos 2027 (`D1-pool/pool-2027-plano.xlsx`) | Linha 8 (integração bancária) | Atualizar tamanho e confiança quando houver épico | Responsável pelo pool | Estimada pela descrição, confiança baixa |

## 7. Revisão desta decisão

> **Regra do modelo.** Entra: o fato novo que obrigaria a reabrir a decisão. Não entra: data de revisão sem gatilho. Exemplo curto: "a análise da API do BB mostrar que ela não cobre pagamento de boleto de outros bancos".

Reabrir este ADR somente diante de fato novo, por exemplo: a análise da API do BB mostrar que ela não cobre os pagamentos que a quitação exige (boleto ou TED a outros bancos, conforme GDP-76); ou o PagAuto não suportar o volume ou o tipo de pagamento **[A CONFIRMAR: volume não consta nas fontes]**. Uma nova decisão gera um ADR novo, que marca este como substituído.
