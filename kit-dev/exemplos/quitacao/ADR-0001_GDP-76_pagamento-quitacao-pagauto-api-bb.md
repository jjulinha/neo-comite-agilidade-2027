<!--
EXEMPLO PREENCHIDO · ADR técnico · Kit de documentação TI Neo Crédito · preenchimento de modelos/ADR.md
Destino real: docs/adr/ADR-0001_GDP-76_pagamento-quitacao-pagauto-api-bb.md no repositório do Konsig ([A CONFIRMAR] qual repositório, README seção 4.1).
Um ADR, uma decisão: este registra o componente de pagamento. A ordem das fases (integração bancária por último) é o ADR-0002.
Fontes: contexto-mestre.md, seção 10 (16/11/2026); insumos/quitacao-estado-e-faseamento.md e insumos/sistemas-e-tecnologias.md (16/11/2026);
downstream_16-11.csv e epicos_downstream_16-11.csv (16/11/2026 10h26); upstream_16-11.csv e gdp_16-11.csv (16/11/2026 9h51).
-->

# ADR-0001 · Pagar a quitação pelo PagAuto com a API do Banco do Brasil

## 1. Identificação

| Campo | Valor |
|---|---|
| Número | ADR-0001 |
| Tipo | [x] Técnica (tecnologia, arquitetura, integração, dados) · [ ] Padrão de desenvolvimento · [ ] Mudança de documentação ou de processo |
| Status | Aceito (decisão de 09/11/2026, `contexto-mestre.md`, seção 10). Quem aprovou: [A CONFIRMAR], ver seção 8 |
| Sistema afetado | **Konsig** (legado). Não se aplica ao NeoKonsig. |
| Item que motivou | GDP-76 |
| Data da proposta | [A CONFIRMAR: as fontes registram só a data da decisão] |
| Data da decisão | 09/11/2026 |
| Revisar em | Conclusão da análise da API do BB, antes de criar o épico da Fase 4 |
| Substitui | Nenhum |

---

## 2. Contexto

- **O pagamento da quitação é manual.** A quitação de dívida e o pagamento residual são feitos "de maneira manual através de um EXCEL" (US-69, `upstream_16-11.csv`, 16/11/2026 9h51), com Konsig, planilhas, WhatsApp e portais bancários (DS-418, `downstream_16-11.csv`, 16/11/2026 10h26). A demanda pede que o sistema traga valor de cada boleto ou carta TED, banco a quitar e vencimento (GDP-76, `gdp_16-11.csv`, 16/11/2026 9h51).
- **O PagAuto já existe no Konsig.** É o componente de pagamentos e comprovantes, em produção (`insumos/sistemas-e-tecnologias.md`, 16/11/2026; DS-59 cita os comprovantes do PAGAUTO).
- **O Konsig já consome uma API do Banco do Brasil.** A validação automática das contas do BB foi entregue no épico DS-92 "Retorno de pagamentos BB" (GDP-60, CONCLUÍDO em 16/09/2026; DS-93). Se a API de pagamento é a mesma API, o mesmo produto ou o mesmo contrato: [A CONFIRMAR].
- **O Konsig não tem CI/CD.** US-43 em BACKLOG desde 14/08/2026; padrão de release (DS-550) em Backlog (`epicos_downstream_16-11.csv`, 16/11/2026 10h26).
- **Motivo da escolha:** não registrado nas fontes [A CONFIRMAR]. Os fatos acima são compatíveis com a decisão, mas não são o motivo declarado pelos decisores.

---

## 3. Decisão

Decidimos que o pagamento da quitação no Konsig é feito pelo **PagAuto com a API do Banco do Brasil**. Vale para a etapa de pagamento do Projeto Quitação (Fase 4, ver ADR-0002), a partir da criação do épico dessa fase.

Ficam fora desta decisão, por dependerem da análise da API do BB (responsabilidade do analista de requisitos, `contexto-mestre.md`, seção 10, não recebida): forma de pagamento por boleto ou TED, tratamento de falha e de estorno, conciliação do retorno, limites de valor e alçada de aprovação [A CONFIRMAR].

---

## 4. Alternativas consideradas

| Alternativa | Prós | Contras | Por que não foi escolhida |
|---|---|---|---|
| A · PagAuto com a API do BB (escolhida) | Componente em produção no Konsig; integração com o BB já conhecida no legado (GDP-60) | Integração nova num sistema sem CI/CD (US-43) | — |
| B · Outro componente, outro banco ou outro canal | [A CONFIRMAR] | [A CONFIRMAR] | Nenhuma fonte registra que tenha sido considerada. Se foi, os decisores registram aqui |
| C · Não fazer nada: manter o pagamento manual nos portais bancários, com planilha | Nenhum desenvolvimento | Mantém o risco financeiro e de rastreamento registrado no US-69 | É o que o projeto substitui (DS-418, US-69) |

Só uma alternativa ativa aparece nas fontes; a B fica como lacuna, e não como alternativa inventada.

---

## 5. Consequências

| Tipo | Consequência |
|---|---|
| Positiva | O pagamento reaproveita um componente que já opera pagamentos e comprovantes no Konsig |
| Negativa ou custo | Integração bancária nova num sistema sem CI/CD: cada deploy da Fase 4 exige passos manuais descritos no Plano de Implementação dessa fase |
| Risco | Observabilidade do PagAuto pendente (migração do APM pausada, DS-305; subtarefa do PagAuto em Backlog, DS-323). Credenciais, certificado e homologação da API do BB não descritos em nenhuma fonte [A CONFIRMAR] |
| Reversão | Pagamento já enviado ao banco não se desfaz por rollback de código; a contingência é operacional (voltar ao pagamento manual nos portais) e deve constar no Plano da Fase 4 |

Obrigações criadas: criar o épico da Fase 4 quando o escopo existir (hoje não há épico, insumo, seção 3.5) e vincular GDP-76, US-69, DS-418, DS-500 e esse épico no Jira (insumo, seção 6).

---

## 6. Impacto em documentos existentes

| Documento | ID no Drive ou caminho | Seção afetada | O que muda | Responsável pela atualização (papel) | Prazo | Feito? |
|---|---|---|---|---|---|---|
| Inventário de Sistemas | `1LwSqMSxgldjHxNQmj34uDAI_refDOkWG` | Linhas do PagAuto e do Banco do Brasil | Registrar a integração PagAuto × API do BB para pagamento da quitação no Konsig | Responsável pelo Inventário [A CONFIRMAR] | [A CONFIRMAR] | [ ] |
| Konsig Arquitetura | `1u3NsVaAXvnayi6I7eCJ4z41fC2yh1naP` | Integrações externas [A CONFIRMAR seção] | Incluir o fluxo de pagamento da quitação | Tech lead do Konsig | [A CONFIRMAR] | [ ] |
| Documento de Requisitos V04 da Quitação (26/10/2026) | Não recebido | Requisitos de pagamento | Confirmar se prevê PagAuto e API do BB; se não, nova versão | Analista de requisitos | [A CONFIRMAR] | [ ] |
| BPMN TO-BE da Quitação | Não recebido | Etapa de pagamento | Desenhar o pagamento via PagAuto e API do BB | Analista de requisitos | [A CONFIRMAR] | [ ] |
| PRD da Fase 2 | `docs/prd/GDP-76_quitacao-fase-2-motor.md` | 4.2 Fora do escopo | Citar este ADR na linha do pagamento | Analista funcional | Feito na v0.1 | [x] |

---

## 7. Conformidade e segurança

| Pergunta | Resposta |
|---|---|
| A decisão muda onde ou como dado pessoal é tratado? | Sim: dados de pagamento e do cliente passam a trafegar do Konsig ao banco pela API [A CONFIRMAR com o DPO: categorias, base legal e retenção] |
| Envolve dado de cartão (PAN, CVV, trilha)? | Não |
| Envolve fornecedor novo ou processamento em nuvem? | Não: o Banco do Brasil já é integrado ao Konsig (GDP-60). Se o produto ou o contrato da API de pagamento for diferente do da validação de contas, a resposta muda [A CONFIRMAR] |

---

## 8. Quem decide (DACI)

| Papel DACI | Quem (papel ou fórum) | Observação |
|---|---|---|
| **D**river | Analista de requisitos | Responsável pela análise da API do BB (`contexto-mestre.md`, seção 10) |
| **A**pprover | [A CONFIRMAR]: as fontes registram data e conteúdo da decisão, não quem decidiu. Pelo modelo, tech lead do Konsig | Um único aprovador |
| **C**ontributors | PO da Quitação, Financeiro, infraestrutura, Segurança e Conformidade | |
| **I**nformed | Time do Konsig | |

---

## 9. Links

| Item | Link |
|---|---|
| Item do Jira que motivou | GDP-76 |
| Registro da decisão no comitê | Não se aplica: decisão técnica do projeto, não do Comitê de Agilidade |
| PRD relacionado | `docs/prd/GDP-76_quitacao-fase-2-motor.md` (fora do escopo da Fase 2) |
| Plano de Implementação relacionado | A criar, para a Fase 4 |
| ADR relacionado | `docs/adr/ADR-0002_GDP-76_ordem-das-fases-quitacao.md` |
| Pull request que aplicou a decisão | Ainda não existe |
