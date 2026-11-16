<!--
EXEMPLO PREENCHIDO · PRD curto (tamanho M) · Kit de documentação TI Neo Crédito · preenchimento de modelos/PRD.md
Destino real: docs/prd/GDP-76_quitacao-fase-2-motor.md no repositório do Konsig ([A CONFIRMAR] qual repositório, README seção 4.1).
Seções obrigatórias do PRD curto: 1, 2, 3, 4, 7, 10, 11, 14, 15 e 16. As demais foram preenchidas onde as fontes trazem conteúdo; onde não trazem, "Não se aplica" com o motivo.
Fontes, somente: contexto-mestre.md, seção 10 (16/11/2026); insumos/quitacao-estado-e-faseamento.md (16/11/2026);
downstream_16-11.csv (16/11/2026 10h26: DS-500, DS-501, DS-503 a DS-509, DS-415, DS-416, DS-418); upstream_16-11.csv (16/11/2026 9h51: US-69);
gdp_16-11.csv (16/11/2026 9h51: GDP-76); D1-pool/regua-tamanho-tempo.md (v1, 16/11/2026).
Limite de fonte: o Documento de Requisitos V04 (26/10/2026), de onde os cards tiram os códigos ES, RF, RN, RNF, PC e PRE, não está no pacote.
Esses códigos são citados como "Doc. V04 <código>" para não se confundirem com a numeração RNxx deste PRD. As descrições do DS-500, DS-501, DS-503 e DS-505 chegaram truncadas na extração.
-->

# Executar o motor de validação da quitação em modo sombra

## 1. Identificação

### 1.1 Dados do projeto

| Campo | Valor |
|---|---|
| Nome do projeto | Quitação · Fase 2 · Motor de validação e tela de visualização |
| Sistema | **Konsig** (legado). Este documento não trata do NeoKonsig. |
| Item GDP | GDP-76 · [KON] SISTEMATIZAÇÃO DA QUITAÇÃO |
| Itens Upstream | US-69 (CONCLUÍDO UPSTREAM em 26/10/2026) |
| Épico(s) Downstream | DS-500 (8 cards, todos em BACKLOG, sem sprint; o épico está na Sprint 19) |
| Solicitante / área | Financeiro |
| Responsável pelo documento | Analista funcional |
| Data de abertura | 16/11/2026 |
| Prazo esperado pela área | Não informado. Posição no pool de 2027: jan/27 (`D1-pool/pool-2027-plano.xlsx`, aba Pool 2027, linha 6) |
| Prioridade no GDP | Medium (`gdp_16-11.csv`, 16/11/2026 9h51), embora o projeto seja prioridade da empresa (`contexto-mestre.md`, seção 10). Divergência registrada na seção 13, R03 |
| Classe de serviço | Standard (campo Classe do DS-500 e dos 8 cards) |
| Risco | [A CONFIRMAR: nenhuma fonte classifica o risco da demanda] |
| Vinculado ao PDTI | [A CONFIRMAR: o PDTI 2026–2028 recebido não cita a Quitação] |
| Natureza | [ ] Tem potencial financeiro · [ ] Gera atendimento · [x] Reduz fluxo operacional · [ ] Regulatória. Base: ganho "Eficiência operacional" da Fase 2 na Previsão de entregas V02 (06/11/2026) **[ALÉM DA FONTE — decisão do usuário: correspondência entre o ganho da planilha e a Natureza]** |
| Status do documento | Rascunho |
| Documentos relacionados | Documento de Requisitos V04 (26/10/2026, não recebido) · `ADR-0001_GDP-76_pagamento-quitacao-pagauto-api-bb.md` · `ADR-0002_GDP-76_ordem-das-fases-quitacao.md` · `DS-500_plano-quitacao-fase-2.md` · protótipo "Quitação · Avaliação do motor" (citado no DS-505, não recebido) |

### 1.2 Versionamento

| Data | Responsável (papel) | Versão | Descrição da alteração |
|---|---|---|---|
| 16/11/2026 | Analista funcional | 0.1 | Elaboração do documento a partir do épico DS-500 e dos cards DS-501 e DS-503 a DS-509. |

---

## 2. Problema

O Financeiro executa a quitação de dívida e o pagamento residual "de maneira manual através de um EXCEL", com consequência registrada de "Risco financeiro e de ratreamento" [sic] (US-69). O processo é "predominantemente manual (Konsig + planilhas + WhatsApp + portais bancários)" (DS-418). Para decidir o pagamento, o Financeiro depende do download do relatório e das fórmulas da planilha (DS-501 e DS-503, códigos D01 e D02, sem descrição nas fontes [A CONFIRMAR]). A Fase 1 (DS-418) entregou a tela Administração de Quitação, mas ela é apenas cadastral: nenhuma regra é aplicada a proposta real (`contexto-mestre.md`, seção 10). Volume diário de propostas em AND - AGUARD QUITACAO e valor envolvido: [A CONFIRMAR com o Financeiro].

---

## 3. Objetivo e métrica de sucesso

| Objetivo | Métrica | Linha de base (fonte e data) | Meta | Quando medir |
|---|---|---|---|---|
| Aplicar às propostas reais as regras cadastradas na Fase 1 sem alterar nenhuma proposta | Propostas alteradas pelo motor após as execuções | Não existe: o motor não roda hoje | Zero (DS-508: "confirmação de que nenhuma proposta foi alterada após as execuções") | A cada execução do teste do DS-508 e durante o modo sombra |
| Comparar a decisão do motor com a decisão da planilha antes de automatizar o pagamento | Propostas em que motor e planilha concordam ÷ propostas avaliadas no modo sombra **[ALÉM DA FONTE — decisão do usuário: leitura de "comparar com a planilha durante o modo sombra", DS-507]** | Não existe | [A CONFIRMAR: o "critério de avanço da Fase 2", citado no DS-507, não está descrito; meta e período definidos pelo Financeiro com o PO] | Durante o modo sombra, pela exportação |

---

## 4. Escopo e fora de escopo

### 4.1 Dentro do escopo

- Executar o motor sobre as propostas elegíveis, no horário agendado e sob demanda (RN01, RN08 · DS-501).
- Aplicar as regras ativas e vigentes, por prioridade, e definir a decisão final (RN03 a RN05 · DS-503).
- Registrar cada avaliação de forma auditável (RN07 · DS-504).
- Mostrar ao Financeiro a lista e o detalhe das avaliações (DS-505, DS-506).
- Exportar as avaliações em .xlsx (RN09 · DS-507, DS-509).
- Testar o motor com a tabela de decisão e os exemplos do Anexo I do Doc. V04 (DS-508).

### 4.2 Fora do escopo

| Item | Motivo | Onde será tratado |
|---|---|---|
| Mudar situação ou status da proposta, enviar e-mail, montar lote (Doc. V04 RF23, RF24, RF2, RF5) | Modo sombra (RN02) | Fase 3, pela numeração do insumo da Quitação, seção 3.1 **[ALÉM DA FONTE — decisão do usuário]**; a descrição do DS-500 está truncada em "ficam para a Fase" |
| Tela de envio ao aprovador e de controle | Depende dos efeitos do motor | Fase 3 (mesma ressalva) |
| Pagamento via PagAuto com a API do Banco do Brasil | Decisão de 09/11/2026 e ordem das fases | Fase 4 (ADR-0001 e ADR-0002) |
| Ajustes da tela Administração de Quitação apontados no teste de 09/11/2026 | Pertencem à Fase 1 | DS-418; hoje sem card (seção 11, D01) |
| Outras esteiras e outras situações da proposta | Fora da regra RN01 | Não previsto |

---

## 5. Perfis (papéis e responsabilidades)

| Perfil | Papel na funcionalidade | O que pode fazer | O que não pode fazer |
|---|---|---|---|
| Analista do Financeiro | Usuário da avaliação | Consultar lista e detalhe, acionar "Reavaliar", exportar (DS-501, DS-505, DS-506, DS-507) | Editar ou excluir registro de avaliação (RN07) |
| Administrador das regras | Mantém as regras na tela da Fase 1 | Nada novo nesta fase | — |
| Perfis de acesso ao CPF | Definem a máscara exibida e exportada (Doc. V04 RNF 3) | [A CONFIRMAR: perfis e regra de máscara estão no Doc. V04, não recebido] | — |

---

## 6. Fluxo atual × proposto

### 6.1 Macroetapas

| # | Macroetapa | Hoje (como é feito) | Proposto (o que muda) | Responsável | Dependências |
|---|---|---|---|---|---|
| 1 | Captura | O Financeiro baixa o relatório e filtra em planilha | O motor captura as propostas elegíveis (RN01) | Konsig | Regras cadastradas na Fase 1 |
| 2 | Avaliação | Fórmulas da planilha | Regras parametrizadas, por prioridade (RN03 a RN05) | Konsig | Tabela de decisão do Doc. V04 |
| 3 | Registro | Sem registro auditável | Registro por proposta e execução (RN07) | Konsig | — |
| 4 | Conferência | Planilha | Lista, detalhe e exportação para comparar com a planilha | Financeiro | Protótipo do DS-505 |

### 6.2 Diagrama

Não elaborado neste exemplo: o BPMN TO-BE da Quitação é responsabilidade do analista de requisitos (`contexto-mestre.md`, seção 10) e não consta no pacote. Protótipo de referência: "Quitação · Avaliação do motor" [A CONFIRMAR: arquivo não recebido].

---

## 7. Regras de negócio

| Código | Regra | Origem | Observação |
|---|---|---|---|
| RN01 | O motor avalia apenas as propostas da esteira Cartão Consignado Compra na situação AND - AGUARD QUITACAO, e nenhuma outra. | Critério de aceite do DS-501 (linha 1 da tabela de decisão do Doc. V04) | — |
| RN02 | Na Fase 2 o motor não muda situação nem status da proposta, não envia e-mail e não monta lote (modo sombra). | Escopo registrado no DS-500 (09/11/2026) | Escopo em card, não decisão consolidada do contexto-mestre (insumo, seção 2) |
| RN03 | O motor aplica somente regras ativas e vigentes na data e hora da avaliação. Regra inativa, fora da vigência ou com "alterações pendentes" usa a última versão ativada. | DS-503 (Doc. V04 RF19.3) | — |
| RN04 | Antes das regras, o grupo comercial é normalizado, e o valor normalizado é o usado nas condições. | DS-503 (Doc. V04 RN03, ES 3, PC-02) | Tabela de normalização e quem a mantém: [A CONFIRMAR] |
| RN05 | Dentro de cada validador, as regras são avaliadas pela prioridade. Resultados possíveis por regra: PAGAR, NAO_PAGAR, PAGAR_PARCIAL, ANALISE_MANUAL. | DS-503; resultados da Fase 1 (US-88, DS-415, via insumo, seção 3.2) | Restante do critério truncado; combinação dos validadores na decisão final segue a tabela de decisão do Doc. V04, seção 11 [A CONFIRMAR] |
| RN06 | Proposta sem CPF, valor, consignatária ou boleto não recebe aplicação de regras. | DS-501 | Restante do critério truncado [A CONFIRMAR] |
| RN07 | Cada avaliação é registrada por proposta e execução, com data e hora, valores usados, resultado por validador, regra e versão aplicadas, decisão final e motivo. Nova avaliação não sobrescreve a anterior; alterar uma regra não altera o registro gravado; o registro não pode ser editado nem excluído pela interface. | DS-504 (Doc. V04 RF12, RF19.6, RNF 1) | Retenção: [A CONFIRMAR] |
| RN08 | O motor executa no horário agendado e, sob demanda, pelo acionamento de "Reavaliar" para as propostas filtradas. | DS-501 (Doc. V04 PC-05) | Horário de execução: [A CONFIRMAR] (PC-05 sem descrição nas fontes) |
| RN09 | A exportação gera .xlsx com os filtros aplicados na tela, colunas na ordem da planilha atual e CPF com a máscara do perfil. | DS-507 e DS-509 (Doc. V04 RF10, RNF 3) | DS-507 inclui um resultado por validador; DS-509 não. Ver seção 11, D02 |

---

## 8. Requisitos não funcionais

| Código | Categoria | Requisito (mensurável) | Origem |
|---|---|---|---|
| RNF01 | Segurança | Registro de avaliação não editável nem excluível pela interface | DS-504 (Doc. V04 RNF 1) |
| RNF02 | LGPD | CPF com a máscara do perfil na tela e na exportação | DS-507, DS-509 (Doc. V04 RNF 3) |
| RNF03 | Desempenho | Tempo máximo da execução agendada e do "Reavaliar": [A CONFIRMAR], depende do volume (seção 2) | Nenhuma fonte define |
| RNF04 | Disponibilidade e falha | Não se aplica: a Fase 2 não chama serviço externo | — |
| RNF05 | Manutenibilidade | Um caso de teste por linha da tabela de decisão (1 a 9) e os exemplos 1 a 4 do Anexo I | DS-508 |

O Doc. V04 RNF 4 é citado no DS-500 e no DS-505, sem descrição nas fontes [A CONFIRMAR].

---

## 9. Integrações

Não se aplica: a Fase 2 não integra com parceiro nem com outro sistema. A integração com o Banco do Brasil é da Fase 4 (ADR-0001 e ADR-0002).

---

## 10. Critérios de aceite

- O motor avalia 100% das propostas da esteira Cartão Consignado Compra em AND - AGUARD QUITACAO e 0 propostas de outras esteiras ou situações (RN01).
- Após qualquer execução, nenhuma proposta tem situação ou status diferente do anterior à execução (RN02).
- Toda avaliação gera um registro com os campos da RN07; uma segunda avaliação da mesma proposta gera um segundo registro, e o primeiro permanece igual.
- O acionamento de "Reavaliar" informa quantas propostas foram avaliadas (DS-501; ver seção 11, D04, sobre o trecho "quantas tiveram alteração de status").
- A exportação gera arquivo .xlsx com os filtros da tela, as colunas da RN09 e o CPF mascarado conforme o perfil.

### 10.1 Cenários de comportamento (BDD) principais

```
Cenário: proposta elegível avaliada (caminho feliz)
  Dado que existe uma proposta da esteira Cartão Consignado Compra na situação AND - AGUARD QUITACAO e há regras vigentes cadastradas
  Quando o motor é executado
  Então a avaliação fica registrada com a decisão final e a situação da proposta permanece a mesma

Cenário: proposta em outra situação (alternativo)
  Dado que existe uma proposta da mesma esteira em situação diferente de AND - AGUARD QUITACAO
  Quando o motor é executado
  Então a proposta não é avaliada e nenhum registro é criado para ela

Cenário: regra com alterações pendentes (borda)
  Dado que a regra de um validador tem alterações pendentes e uma versão anterior ativada
  Quando o motor avalia uma proposta elegível
  Então a avaliação usa a última versão ativada e o registro mostra essa versão

Cenário: proposta sem boleto (falha)
  Dado que uma proposta elegível não tem boleto
  Quando o motor é executado
  Então as regras não são aplicadas a ela e o motivo fica visível no registro
```

O último cenário segue a RN06; o que acontece com a proposta depois disso está no trecho truncado do DS-501 [A CONFIRMAR]. Os cenários de teste com massa fictícia ficam nos cards; o DS-508 lista os casos do motor.

---

## 11. Dependências

| Código | O que falta | Quem responde (papel ou área) | Até quando | Bloqueia o caminho principal? |
|---|---|---|---|---|
| D01 | Fase 1 concluída (DS-415 em CODE REVIEW, DS-416 EM DESENVOLVIMENTO em 16/11/2026) e cards dos ajustes do teste de 09/11/2026, que não existem no DS-418 | PO e tech lead | [A CONFIRMAR] | Sim (pré-requisito declarado no DS-500) |
| D02 | Decidir entre DS-507 e DS-509, que entregam quase a mesma exportação (insumo, seção 4.5). Recomendação: manter o DS-507 e levar para ele a origem "decisão da equipe em 09/11/2026", o Doc. V04 RF10 e a finalidade de consulta fora do sistema **[ALÉM DA FONTE — decisão do usuário]** | PO | Antes do refinamento do DS-507 [A CONFIRMAR data] | Não |
| D03 | "Reavaliar" é critério do DS-501, mas o botão fica na tela do DS-505. Registrar a dependência no DS-501 ou mover o critério para o DS-505 (guia, seção 06) **[ALÉM DA FONTE — decisão do usuário]** | PO e tech lead | Antes do refinamento | Não |
| D04 | O DS-501 pede informar "quantas tiveram alteração de status", mas a RN02 impede alteração de status. Confirmar se quer dizer "alteração de decisão em relação à avaliação anterior" | PO | Antes do refinamento do DS-501 | Não |
| D05 | Número da fase que recebe os efeitos (descrição do DS-500 truncada). Recomendação: numeração do insumo (Fase 3 = efeitos) **[ALÉM DA FONTE — decisão do usuário]** | PO | [A CONFIRMAR] | Não |
| D06 | Documento de Requisitos V04 anexado ao DS-500, com PC-02, PC-05, RNF 4, D01, D02, tabela de decisão e Anexo I | Analista de requisitos | [A CONFIRMAR] | Sim (o DS-508 e a RN05 dependem da tabela de decisão) |
| D07 | Descrição do critério de avanço da Fase 2 | PO com o Financeiro | Antes do início da Fase 3 | Não |

---

## 12. Tratamento de dados pessoais (LGPD)

| Categoria de dado tratado | Finalidade | Quem acessa (perfil) | Mascaramento ou minimização | Retenção | Compartilhado com terceiro? |
|---|---|---|---|---|---|
| CPF do cliente | Identificar a proposta avaliada | Perfis do Financeiro [A CONFIRMAR] | Máscara por perfil na tela e na exportação (RNF02) | [A CONFIRMAR com o DPO] | Não |
| Dados da proposta (grupo, convênio, consignatária, valor, vencimento) | Aplicar as regras e registrar a avaliação | Perfis do Financeiro | — | Mesma do registro (RN07) [A CONFIRMAR] | Não |

A exportação leva dados da proposta para fora do sistema (DS-509: "consultar as avaliações fora do sistema"). Onde o arquivo pode ser guardado e por quanto tempo: [A CONFIRMAR com o DPO].

---

## 13. Riscos

| ID | Risco | Categoria | Probabilidade | Impacto | Mitigação | Dono (papel) |
|---|---|---|---|---|---|---|
| R01 | Construção nova no Konsig, sem CI/CD (US-43, Backlog): deploy manual com risco de regressão | Técnico | M | A | Deploy e rollback descritos no Plano, seções 5 e 8 | Tech lead |
| R02 | Doc. V04 fora do pacote e descrições truncadas: dev e QA sem a tabela de decisão completa | Negócio | A | A | D06 | Analista de requisitos |
| R03 | Prioridade Medium no GDP-76, embora o projeto seja prioridade da empresa: a demanda perde a vez numa fila ordenada por prioridade | Prazo | M | M | Levar a divergência ao comitê **[ALÉM DA FONTE — decisão do usuário]** | PO |

Probabilidade e impacto são avaliação deste exemplo **[ALÉM DA FONTE — decisão do usuário]**.

---

## 14. Tamanho estimado (régua)

| Campo | Valor |
|---|---|
| Cards de épico previstos | 8 (DS-501, DS-503 a DS-509; o DS-502 não existe). Com a decisão da D02, podem passar a 7 |
| Classe | M (5–9) |
| Referência no Downstream (dias úteis) | 16 típico / 29 conservador |
| Referência no Upstream (dias úteis) | Não se aplica: o US-69 foi concluído no Upstream em 26/10/2026 |
| Precisa quebrar antes? | Não |

Fonte: `D1-pool/regua-tamanho-tempo.md`, v1, 16/11/2026. As faixas são proposta, sem decisão do comitê.

---

## 15. Rastreabilidade

| Regra ou critério | Item GDP | Item Upstream | Card(s) Downstream | Caso(s) de teste |
|---|---|---|---|---|
| RN01, RN06, RN08 | GDP-76 | US-69 | DS-501 | DS-508 (linhas 1 e 2 da tabela de decisão) |
| RN02 | GDP-76 | US-69 | DS-501 a DS-504 | DS-508 (nenhuma proposta alterada) |
| RN03, RN04, RN05 | GDP-76 | US-69 | DS-503 | DS-508 (linhas 5 a 9; regras inativa, fora da vigência, com alterações pendentes, prioridades) |
| RN07, RNF01 | GDP-76 | US-69 | DS-504, DS-506 | [A CONFIRMAR: imutabilidade do registro não listada no DS-508] |
| RN09, RNF02 | GDP-76 | US-69 | DS-507, DS-509 | Cenários de teste do card [A CONFIRMAR: ainda não escritos] |
| Lista de avaliações | GDP-76 | US-69 | DS-505 | Cenários de teste do card [A CONFIRMAR] |

Os vínculos GDP-76 ↔ US-69 ↔ DS-500 não existem no Jira em 16/11/2026 (insumo, seção 6).

---

## 16. Aprovações

| Papel | Área | Decisão | Data | Observação |
|---|---|---|---|---|
| Área solicitante | Financeiro | Pendente | — | Aguarda a versão 0.2, com as dependências D02 a D04 resolvidas |
| PO | TI | Pendente | — | |
| Tech lead | TI | Pendente | — | Confirma o sistema (Konsig) e que a Fase 2 não exige ADR novo |
| Segurança e Conformidade / DPO | TI | Não se aplica | — | A seção 12 não declara compartilhamento com terceiro |
