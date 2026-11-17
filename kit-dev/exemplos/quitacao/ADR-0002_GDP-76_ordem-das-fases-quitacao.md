<!--
EXEMPLO PREENCHIDO · ADR técnico · Kit de documentação TI Neo Crédito · preenchimento de modelos/ADR.md
Destino real: docs/adr/ADR-0002_GDP-76_ordem-das-fases-quitacao.md no repositório do Konsig ([A CONFIRMAR] qual repositório definitivo; até lá, pasta provisória do README do kit, seção 4).
Formato v1 (16/11/2026): as seções 6 (impacto em documentos) e 8 (DACI) são as que o modelos/ADR.md v2 reserva para ADR de processo ou de documentação; num ADR técnico novo, não as copie.
Um ADR, uma decisão: este registra a ordem das fases. O componente de pagamento é o ADR-0001.
Fontes: contexto-mestre.md, seção 10 (16/11/2026); insumos/quitacao-estado-e-faseamento.md (16/11/2026); previsao-entregas-2026-v02 (06/11/2026);
downstream_16-11.csv e epicos_downstream_16-11.csv (16/11/2026 10h26); upstream_16-11.csv (16/11/2026 9h51); D1-pool/pool-2027-plano.xlsx (base Jira 16/11/2026).
-->

# ADR-0002 · Construir a integração bancária da Quitação por último

## 1. Identificação

| Campo | Valor |
|---|---|
| Número | ADR-0002 |
| Tipo | [x] Técnica (tecnologia, arquitetura, integração, dados) · [ ] Padrão de desenvolvimento · [ ] Mudança de documentação ou de processo |
| Status | Aceito: a ordem está registrada como vigente no `contexto-mestre.md`, seção 10, e o épico DS-500 (09/11/2026) já a aplica. Quem aprovou: [A CONFIRMAR], ver seção 8 |
| Sistema afetado | **Konsig** (legado). Não se aplica ao NeoKonsig. |
| Item que motivou | GDP-76 |
| Data da proposta | [A CONFIRMAR] |
| Data da decisão | [A CONFIRMAR: as fontes registram a ordem, não a data. A Previsão V02, de 06/11/2026, ainda trazia a ordem anterior; o DS-500, criado em 09/11/2026, já segue a nova] |
| Revisar em | Fim do modo sombra da Fase 2 (critério de avanço da Fase 2, ainda sem descrição) |
| Substitui | Nenhum ADR. Substitui a ordem da Previsão de entregas V02 (ver seção 4, alternativa B) |

---

## 2. Contexto

- A automação da Quitação no Konsig foi dividida em fases: tela de parametrização (Fase 1, DS-418, entregue em parte e apenas cadastral), motor de validação com tela de visualização (Fase 2, DS-500), efeitos do motor e pagamento (`contexto-mestre.md`, seção 10; insumo da Quitação, seção 3.1).
- A Previsão de entregas V02 (modificada em 06/11/2026) punha o pagamento BB como Fase 2 e o motor como Fase 3 (células C31:D34; insumo, seção 4.1).
- A Fase 2 roda em modo sombra: o motor calcula e registra a avaliação, mas não altera situação ou status, não envia e-mail e não monta lote (DS-500).
- O Konsig não tem CI/CD (US-43, BACKLOG desde 14/08/2026).
- **Motivo da ordem:** não registrado nas fontes [A CONFIRMAR]. Leitura deste ADR, compatível com os fatos: validar as decisões do motor antes de qualquer pagamento automático e deixar para o fim a parte de maior risco operacional **[ALÉM DA FONTE — decisão do usuário]**.

---

## 3. Decisão

Decidimos que a integração bancária (pagamento via PagAuto com a API do BB, ADR-0001) é a **última etapa** do Projeto Quitação: entra depois do motor de validação (Fase 2) e dos efeitos do motor. Pela numeração do insumo da Quitação, é a Fase 4 **[ALÉM DA FONTE — decisão do usuário: numeração recomendada no insumo, seção 3.1]**. Vale para o planejamento do projeto e para o pool de 2027 a partir deste registro.

---

## 4. Alternativas consideradas

| Alternativa | Prós | Contras | Por que não foi escolhida |
|---|---|---|---|
| A · Pagamento por último (escolhida) | Motor e efeitos são construídos e testados sem depender da API do BB | O ganho financeiro do pagamento automático chega por último | — |
| B · Pagamento BB antes do motor (ordem da Previsão V02, 06/11/2026) | Pagamento automatizado mais cedo | Pagamento automático sem decisão validada do motor [A CONFIRMAR: contra não registrado] | Superada pela ordem vigente; a numeração da V02 está obsoleta |
| C · Não fazer nada: sem ordem definida | — | Sem base para o pool nem para os épicos das Fases 3 e 4 | Não permite planejar |

---

## 5. Consequências

| Tipo | Consequência |
|---|---|
| Positiva | Motor (Fase 2) e efeitos (Fase 3) não dependem da API do BB (DS-500) |
| Negativa ou custo | A Previsão V02 e o pool precisam ser atualizados (seção 6) |
| Risco | O prazo da Quitação depende de fases sem épico: Fases 3 e 4 sem épico, sem card e sem item no Upstream; no pool, ambas estimadas pela descrição, com confiança baixa e entrega em fev/27 (`D1-pool/pool-2027-plano.xlsx`, aba Pool 2027) |
| Reversão | Antecipar o pagamento exige novo ADR que substitua este e reabre o planejamento das Fases 3 e 4 |

---

## 6. Impacto em documentos existentes

| Documento | ID no Drive ou caminho | Seção afetada | O que muda | Responsável pela atualização (papel) | Prazo | Feito? |
|---|---|---|---|---|---|---|
| Previsão de entregas 2026 V02 | Planilha de esforço do Downstream | Linhas da Quitação (A16:J19 e C31:D34) | Fase 2 = motor; pagamento BB por último | Responsável pela planilha de esforço | [A CONFIRMAR] | [ ] |
| Pool de projetos 2027 | `D1-pool/pool-2027-plano.xlsx` | Linha da integração bancária | Atualizar tamanho e confiança quando houver épico | Responsável pelo pool | Quando o épico da Fase 4 existir | [ ] |
| Insumo "Projeto Quitação · Estado e faseamento" | `insumos/quitacao-estado-e-faseamento.md` | Seções 2, 3.1 e 6 | Citar este ADR como registro da ordem das fases | Analista de requisitos | [A CONFIRMAR] | [ ] |
| `contexto-mestre.md` | Arquivo do projeto | Seção 10 | Citar este ADR junto da decisão | Analista de requisitos | [A CONFIRMAR] | [ ] |
| PRD da Fase 2 | `docs/prd/GDP-76_quitacao-fase-2-motor.md` | 4.2 Fora do escopo | Citar este ADR | Analista funcional | Feito na v0.1 | [x] |

---

## 7. Conformidade e segurança

| Pergunta | Resposta |
|---|---|
| A decisão muda onde ou como dado pessoal é tratado? | Não: a ordem das fases não altera o tratamento; o envio de dados ao banco é tratado no ADR-0001 |
| Envolve dado de cartão (PAN, CVV, trilha)? | Não |
| Envolve fornecedor novo ou processamento em nuvem? | Não |

---

## 8. Quem decide (DACI)

| Papel DACI | Quem (papel ou fórum) | Observação |
|---|---|---|
| **D**river | Analista de requisitos | |
| **A**pprover | [A CONFIRMAR]: as fontes registram a ordem, não quem decidiu. Pelo modelo, tech lead do Konsig; se a ordem mudar o pool, também a gestão da TI | Um único aprovador |
| **C**ontributors | PO da Quitação, Financeiro | |
| **I**nformed | Time do Konsig; responsável pelo pool | |

---

## 9. Links

| Item | Link |
|---|---|
| Item do Jira que motivou | GDP-76 |
| Registro da decisão no comitê | Não se aplica: decisão do projeto |
| PRD relacionado | `docs/prd/GDP-76_quitacao-fase-2-motor.md` |
| Plano de Implementação relacionado | `docs/planos/DS-500_plano-quitacao-fase-2.md` |
| ADR relacionado | `docs/adr/ADR-0001_GDP-76_pagamento-quitacao-pagauto-api-bb.md` |
| Pull request que aplicou a decisão | Não se aplica |
