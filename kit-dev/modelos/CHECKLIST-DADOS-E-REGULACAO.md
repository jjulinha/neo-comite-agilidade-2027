# Checklist de dados e regulação (PRD e PR)

> **Ressalva.** O enquadramento da Neo em cada norma é **[A CONFIRMAR — parecer jurídico/compliance]**. A operação regulada do cartão cabe à Atlanta (`insumos/sistemas-e-tecnologias.md`). As normas foram lidas via busca, não no texto oficial: confira a redação literal antes de citar. Todo o checklist é proposta **[ALÉM DA FONTE — decisão do usuário]**.

**Quando usar.** Parte A: o PO cola no PRD (trilhas P a GG). Parte B: o dev cola na descrição do PR, em **qualquer tamanho, inclusive PP**, sempre que o card tocar dado pessoal (campo novo, log, exportação, relatório com CPF, anexo com relação nominal, parceiro novo recebendo dado, massa para IA).
**Quando não usar.** Mudança sem dado pessoal e sem norma (ex.: ajuste de layout de tela sem campo novo): basta escrever "não toca dado pessoal" no PR.
**Regra.** Aciona o **DPO** quando a resposta indicar tratamento novo de dado pessoal (A1, A2, campo novo) ou compartilhamento novo (parceiro novo recebendo dado). Fornecedor novo de processamento, nuvem ou IA (A4) ou card que toca o cartão aciona **Segurança & Conformidade**. O checklist não faz o trabalho deles: **o RIPD não é escrito pelo dev nem cabe no PRD**.

---

## Parte A · PRD (perguntas do produto)

Responda em uma linha cada. "Não se aplica" e "nenhum dado pessoal novo" são respostas válidas.

| # | Pergunta | Resposta | Base (conferir no texto oficial) |
|---|---|---|---|
| A1 | Dados pessoais tratados: quais, finalidade, base legal, retenção, compartilhamento? | | LGPD arts. 6º e 7º |
| A2 | Aciona o DPO? (sim/não e por quê). O PRD registra a decisão, não o RIPD. | | LGPD art. 37 (registro) e art. 38 (RIPD) |
| A3 | Trilha de auditoria: qual evento, quem, quando, qual decisão, onde fica, por quanto tempo? | | CMN 4.893, art. 3º, alterado pela CMN 5.274/2025 **[A CONFIRMAR se chega à Neo via instituição regulada]** |
| A4 | Fornecedor novo de processamento, nuvem ou IA? Se sim, encaminhar a Segurança & Conformidade. | | CMN 4.893 (contratação) |
| A5 | Só consignado: que evidência da contratação se guarda e por quanto tempo? | | INSS: IN PRES/INSS 138/2022, artigo e prazo de guarda **[A CONFIRMAR — leitura do texto oficial]** **[A CONFIRMAR se a Neo opera INSS]**; convênios de servidores **[A CONFIRMAR]** |
| A6 | Natureza Regulatória: norma de origem e data de vigência (classe de serviço "data fixa")? | | A norma que motiva a demanda, só ela |
| A7 | Muda o que precisa ser detectado ou comunicado em incidente? | | LGPD arts. 46 e 48 |

**Exemplo preenchido (Quitação Fase 2, GDP-76 / DS-500, Konsig; `downstream_16-11.csv`, 16/11/2026 10h26).** A1: CPF na tela de avaliação (DS-505) e na exportação .xlsx (DS-507/DS-509, duplicados **[A CONFIRMAR qual fica]**), mascarado por perfil (RNF 3); retenção **[A CONFIRMAR]**. A2: sim, exportação nova com CPF (o DS-509 diz que ela "não consta no Documento de Requisitos V04", enquanto o DS-507 cita o "critério de avanço da Fase 2"). A3: cada avaliação do motor registrada de forma auditável (DS-504); local e prazo **[A CONFIRMAR]**. A4: não na Fase 2. A API do Banco do Brasil e o PagAuto ficam para fase posterior (Fase 4 na numeração proposta em `insumos/quitacao-estado-e-faseamento.md` §3.1; a Previsão V02 ainda usa outra numeração) **[A CONFIRMAR]**. A5 a A7: não se aplica.

---

## Parte B · PR (dev)

Responda cada linha por escrito. Não use caixa de seleção: caixa vazia não diz se é esquecimento, "não" ou "não se aplica".

**B1 · Gatilhos** (responda "sim" ou "não"; "sim" aciona o dono indicado)

| Gatilho | Resposta (sim/não) | Se "sim" |
|---|---|---|
| **Campo novo** de dado pessoal? | | Conferir se está declarado na Parte A do PRD; se não há PRD (PP), avisar o PO. Aciona o DPO. |
| **Parceiro novo recebendo dado?** | | Aciona o DPO e abre CONTRATO-DE-INTEGRACAO.md. |
| **Toca o cartão?** | | Aciona Segurança & Conformidade. Escopo do CDE e PCI DSS v4.0.1 verificados (riscos R18 e R19 da Visão do Cartão v6, 03/11/2026). |

**B2 · Verificações** (responda "OK", "não OK (motivo)" ou "n/a")

| Verificação | Resposta |
|---|---|
| **Log** sem CPF ou com mascaramento. | |
| **Fixture e massa de teste sintéticas**: valor fictício que exercita a regra, nunca copiado de produção. | |
| **Exportação ou relatório com CPF**: mascaramento por perfil (padrão da Quitação, RNF 3, DS-507/DS-509). | |
| **Anexo com relação nominal** não fica no Jira sem regra de guarda (caso DS-465: configuração de 40 usuários a partir da relação nominal anexada ao card; `downstream_16-11.csv`, 16/11/2026 10h26). | |
| **Dado enviado à IA** está anonimizado. A regra de uso de IA e de anonimização está "Não localizado" (D2 §2.1). Até haver regra aprovada pelo DPO, valem os portões do US-80 (`upstream_16-11.csv`, 16/11/2026 9h51); na dúvida, não envie. | |
| **Sem PAN/CVV**: dado de cartão (PAN, CVV, trilha) nunca entra, nem mascarado: código, log, fixture, documento ou prompt de IA. | |
| **Conferência humana antes do commit**: documento, fixture e prompt revistos à mão. A anonimização automática já deixou resíduo de e-mail (risco R3, D2 §4.1). | |

**Exagero, não exigir:**
- RIPD dentro do PRD;
- cópia de artigos de lei;
- política de segurança/LGPD repetida em todo card;
- as 14 normas e padrões da tabela 1.1 da Visão do Cartão v6 (03/11/2026) listados no PRD (basta a que motiva a demanda);
- parecer jurídico sem dado novo, fornecedor novo ou mudança na contratação;
- matriz requisito–teste–norma em PP ou P.

---

## Referências

Leituras feitas via busca em 17/11/2026, sem acesso ao texto oficial. Conferir no original antes de citar.
- LGPD, Lei 13.709/2018: https://www.planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/l13709.htm
- Voto CMN 88/2025 (Resolução CMN 5.274/2025, altera a 4.893): https://normativos.bcb.gov.br/Votos/CMN/202588/Voto_do_CMN_88_2025.pdf
- Resolução CMN 4.893/2021: buscador oficial de normas do BCB, https://www.bcb.gov.br/estabilidadefinanceira/buscanormas (pesquisar "Resolução CMN 4.893") **[A CONFIRMAR: endereço não aberto nesta revisão; o domínio não estava acessível na sessão]**
- IN PRES/INSS 138/2022 e alterações (texto consolidado): https://www.gov.br/inss/pt-br/centrais-de-conteudo/legislacao/instrucao-normativa/2022/in138pres-inss-alterada19-5-2026.pdf/@@download/file (via busca) **[A CONFIRMAR — leitura do texto oficial: artigo e prazo de guarda]**
