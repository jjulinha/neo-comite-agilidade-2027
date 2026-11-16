# PRD · GDP-76 · Quitação · Fase 2 · Motor de validação e tela de visualização

| Item | Valor |
|---|---|
| Tipo de documento | PRD (documento de requisitos de produto) · exemplo preenchido do kit para os devs |
| Demanda no GDP | GDP-76 · [KON] SISTEMATIZAÇÃO DA QUITAÇÃO (prioridade Medium, EM DOWNSTREAM) |
| Épico no Downstream | DS-500 · [KON] QUITAÇÃO · Fase 2 · Motor de validação e tela de visualização (8 cards, todos em BACKLOG) |
| Sistema | **Konsig (legado)**. Este documento não trata do NeoKonsig. |
| Versão · data | v0.1 · 16/11/2026 |
| Situação | Rascunho para revisão do PO e do tech lead |
| Autor (papel) | Analista de requisitos da TI |
| Aprovação (papéis) | PO da Quitação; tech lead do Konsig [A CONFIRMAR: quem ocupa cada papel na Quitação] |
| Documentos relacionados | ADR-001 (pagamento via PagAuto com a API do Banco do Brasil) · PLANO-GDP-76-quitacao-fase2 · insumo `insumos/quitacao-estado-e-faseamento.md` (16/11/2026) |

**Fontes deste PRD.** Somente: contexto-mestre.md, seção 10 (16/11/2026); insumo `quitacao-estado-e-faseamento.md` (16/11/2026); Jira: downstream_16-11.csv (extração 16/11/2026 10h26: DS-500, DS-501, DS-503 a DS-509, DS-415, DS-416, DS-418), upstream_16-11.csv (extração 16/11/2026 9h51: US-69) e gdp_16-11.csv (extração 16/11/2026 9h51: GDP-76).

**Limite de fonte.** O Documento de Requisitos V04 (26/10/2026), de onde o DS-500 tira os códigos ES, RF, RN e RNF, **não está no pacote**. Os códigos aparecem aqui como estão nos cards; o conteúdo de cada um só é descrito quando o card o descreve. As descrições do DS-500, DS-501, DS-503 e DS-505 chegaram **truncadas** na extração; o texto cortado está marcado.

---

## 1. Problema

> **Regra do modelo.** Entra: o que acontece hoje, com evidência (card, número, data). Não entra: a solução, nem adjetivos sem dado ("processo ruim"). Exemplo curto: "a quitação é feita em Excel (US-69)".

- O Financeiro executa a etapa de quitação de dívida e de pagamento residual "de maneira manual através de um EXCEL"; a consequência registrada é "Risco financeiro e de ratreamento" [sic] (US-69, upstream_16-11.csv, 16/11/2026 9h51).
- O processo atual é executado "de forma predominantemente manual (Konsig + planilhas + WhatsApp + portais bancários)" (DS-418, downstream_16-11.csv, 16/11/2026 10h26).
- Hoje o Financeiro depende do download do relatório e da planilha para decidir o pagamento (DS-501, história: "para não depender do download do relatório nem da planilha (D01)"). A decisão segue "as fórmulas da planilha" (DS-503, história, "(D02)"). O significado dos códigos D01 e D02 não consta nas fontes **[A CONFIRMAR]**.
- A Fase 1 (DS-418) entregou a tela Administração de Quitação, em que as regras dos validadores são cadastradas, mas a tela é **apenas cadastral**: nenhuma regra é aplicada a proposta real (contexto-mestre.md, seção 10).

**Volume afetado.** Quantidade de propostas por dia em AND - AGUARD QUITACAO e valor envolvido: **[A CONFIRMAR]**. Nenhuma fonte do pacote traz esse número.

## 2. Objetivo da fase

> **Regra do modelo.** Entra: o resultado que a fase entrega, em uma frase, e o que ela deliberadamente não faz. Não entra: o objetivo do projeto inteiro. Exemplo curto: "aplicar as regras às propostas reais sem alterar proposta".

Fazer com que as regras cadastradas na tela Administração de Quitação passem a ser aplicadas às propostas reais e que o Financeiro visualize o resultado de cada avaliação, **sem que o motor altere qualquer proposta nesta fase (modo sombra)** (DS-500, objetivo).

**Modo sombra** significa: o motor calcula e registra a avaliação, mas não muda situação ou status, não envia e-mail e não monta lote (DS-500). O modo sombra é escopo registrado no card DS-500 (criado em 09/11/2026), e não decisão consolidada do contexto-mestre (insumo, seção 2).

## 3. Usuários e papéis

> **Regra do modelo.** Entra: quem usa o resultado, nomeado por papel ou área. Não entra: nomes de pessoas. Exemplo curto: "Financeiro (operação da quitação)".

| Papel | O que faz nesta fase | Fonte |
|---|---|---|
| Financeiro | Consulta a lista e o detalhe das avaliações, aciona "Reavaliar", exporta para comparar com a planilha | DS-501, DS-505, DS-506, DS-507, DS-509 |
| Perfis com acesso ao CPF | Veem o CPF conforme a máscara do perfil (RNF 3) | DS-507, DS-509 |
| Administrador das regras | Mantém as regras na tela Administração de Quitação (Fase 1). Não é usuário novo nesta fase | DS-500 (pré-requisito) |

Perfis exatos de acesso à nova aba e regra de máscara por perfil: **[A CONFIRMAR]** (RNF 3 citado, conteúdo no Documento de Requisitos V04, não recebido).

## 4. Escopo

> **Regra do modelo.** Entra: cada capacidade da fase, com o card que a implementa. Não entra: capacidade sem card ou sem fonte (vai para a seção 5 ou para "em aberto"). Exemplo curto: "registro auditável da avaliação (DS-504)".

### 4.1 Dentro do escopo

| Nº | Capacidade | Card | Origem citada no card |
|---|---|---|---|
| E1 | Capturar, em horário agendado, as propostas da esteira **Cartão Consignado Compra** na situação **AND - AGUARD QUITACAO**, e nenhuma outra, e executar o motor; permitir nova execução pelo botão "Reavaliar" para as propostas filtradas | DS-501 | ES 1, RF1, RF1.a, RF22 (caput), PRE 1, PRE 2; tabela de decisão, linhas 1 e 2 |
| E2 | Aplicar as regras ativas e vigentes, por prioridade dentro de cada validador, depois de normalizar o grupo comercial, e definir a decisão final | DS-503 | RF19.3, RF19.4, RF19.5, RF22.c a RF22.f, RN02 a RN11, V02 a V06; Anexo I; tabela de decisão, linhas 5 a 9 |
| E3 | Registrar cada avaliação de forma auditável, sem sobrescrever a anterior | DS-504 | RF12, RF19.6, RNF 1; Anexo I |
| E4 | Tela de visualização: lista das propostas avaliadas, com indicadores e filtro | DS-505 | RF10, RN10, RNF 3, RNF 4, ES 12, ES 16, RF15 |
| E5 | Tela de visualização: detalhe da avaliação de uma proposta | DS-506 | RF12, RF19.6, ES 2, RNF 1 |
| E6 | Exportação da avaliação em .xlsx para comparação com a planilha durante o modo sombra | DS-507 | Critério de avanço da Fase 2; colunas G a N da aba EXTRAÇÃO DE INFORMAÇÃO |
| E7 | Exportação da avaliação em .xlsx para consulta fora do sistema (decisão da equipe em 09/11/2026; não consta no Documento de Requisitos V04) | DS-509 | RF10; RNF 3 |
| E8 | Teste do motor com a tabela de decisão (linhas 1 a 9) e os exemplos 1 a 4 do Anexo I | DS-508 | Seção 11 e Anexo I do Documento de Requisitos V04 |

E6 e E7 se sobrepõem: ver a seção 9, item Q1.

### 4.2 Fora do escopo desta fase

| Item | Para onde vai | Fonte |
|---|---|---|
| Efeitos do motor: RF23, RF24, RF2, RF5 (mudar situação ou status, enviar e-mail, montar lote) | Fase posterior. A descrição do DS-500 termina em "ficam para a Fase", sem o número (truncada) | DS-500 |
| Tela no Konsig de envio ao aprovador e de controle | Fase 3, pela numeração do insumo **[ALÉM DA FONTE — decisão do usuário]** | previsao-entregas-2026-v02 (06/11/2026), via insumo seção 3.4 |
| Pagamento via PagAuto com a API do Banco do Brasil | Fase 4, por último (ver ADR-001) | contexto-mestre.md, seção 10 |
| Ajustes da tela Administração de Quitação apontados no teste de 09/11/2026 | Fase 1 (DS-418). Pré-requisito desta fase; hoje sem card | DS-500 (pré-requisito); insumo, seção 3.2 |
| Outras esteiras e outras situações da proposta | Não previstas | DS-501 ("nenhuma outra") |
| Itens da Paradinha, da Tratativa Interna e do OCR que citam "quitação" | Outros projetos | Insumo, seção 3.6 |

## 5. Requisitos funcionais

> **Regra do modelo.** Entra: o comportamento esperado, verificável, com o card e o código de origem. Não entra: solução técnica (tabela, classe, framework) nem texto que não esteja no card ou no documento de requisitos. Exemplo curto: "uma nova avaliação não sobrescreve a anterior (DS-504)".

### 5.1 Captura e execução (DS-501)

- **RF-P1.** No horário agendado (PC-05), o motor avalia todas as propostas da esteira Cartão Consignado Compra em AND - AGUARD QUITACAO e nenhuma outra (linha 1 da tabela de decisão). Horário de execução: **[A CONFIRMAR]** (PC-05 não descrito nas fontes).
- **RF-P2.** Na tela de visualização, o usuário do Financeiro aciona "Reavaliar"; o motor executa de novo para as propostas filtradas e informa quantas foram avaliadas e quantas tiveram alteração de status.
- **RF-P3.** Proposta sem CPF, valor, consignatária ou boleto não recebe aplicação de regras; o restante do critério está truncado na extração **[A CONFIRMAR]**. A lista tem o indicador "Dados ausentes" (DS-505); que esses casos sejam os contados nele é leitura deste PRD **[A CONFIRMAR]**.

### 5.2 Aplicação das regras e decisão (DS-503)

- **RF-P4.** O motor aplica somente regras ativas e vigentes na data e hora da avaliação (RF19.3). Regra inativa, fora da vigência ou com "alterações pendentes" usa a última versão ativada.
- **RF-P5.** Antes das regras, o grupo comercial é normalizado: variações do nome de um mesmo grupo são reduzidas ao nome do grupo, e o valor normalizado é o usado nas condições (RN03, ES 3, PC-02). A tabela de normalização e quem a mantém: **[A CONFIRMAR]**.
- **RF-P6.** Dentro de cada validador, as regras são avaliadas pela prioridade; o restante do critério está truncado na extração **[A CONFIRMAR]**. Validadores V01 a V06 e resultados possíveis por regra: PAGAR, NAO_PAGAR, PAGAR_PARCIAL, ANALISE_MANUAL (Fase 1, US-88 e DS-415, via insumo seção 3.2). Regra de combinação dos resultados dos validadores na decisão final: tabela de decisão, seção 11 do Documento de Requisitos V04 **[A CONFIRMAR: documento não recebido]**.

### 5.3 Registro auditável (DS-504)

- **RF-P7.** Para cada proposta e execução, o sistema grava: data e hora; valores da proposta usados (grupo original e normalizado, convênio, consignatária, valor da quitação, vencimento); resultado por validador; regra e versão aplicadas; decisão final e motivo.
- **RF-P8.** Uma nova avaliação não sobrescreve a anterior; o histórico fica disponível por proposta.
- **RF-P9.** Alterar uma regra depois da avaliação não altera o registro já gravado.
- **RF-P10.** O registro não pode ser editado nem excluído pela interface.

### 5.4 Tela de visualização · lista (DS-505)

- **RF-P11.** Localização: Konsig › Configuração › Proposta › Quitação, nova aba "Avaliação do motor", ao lado da aba "Regras" da tela Administração de Quitação. Protótipo de referência: "Quitação · Avaliação do motor" (o arquivo do protótipo não está no pacote) **[A CONFIRMAR]**.
- **RF-P12.** Aviso fixo: "Modo sombra: o motor avalia as propostas, mas nenhuma proposta é alterada."
- **RF-P13.** Indicadores no topo, com quantidade e valor: A pagar, Avaliação manual, Análise manual, Devolução (propostas que seriam encaminhadas para ajuste, retornando para AGUARDANDO ABERTURA DE CONTA), Dados ausentes; e data e hora da última execução.
- **RF-P14.** Clicar em um indicador filtra a lista por aquela decisão. Os demais critérios do card estão truncados na extração **[A CONFIRMAR]**.

### 5.5 Tela de visualização · detalhe (DS-506)

- **RF-P15.** O detalhe abre em modal, sem sair da lista.
- **RF-P16.** Exibe os dados da proposta usados na avaliação, com grupo original e normalizado; os boletos com vencimento, valor do código de barras, saldo devedor e resultado do Validador Boleto; os validadores na ordem de aplicação, cada um com resultado, regra e versão aplicadas, a condição como foi lida (mesmo texto de "Como a regra será lida" da tela de cadastro) e o motivo; a decisão final e o encaminhamento previsto; o histórico de avaliações da proposta (data e hora, origem, decisão).

### 5.6 Exportação (DS-507 e DS-509)

- **RF-P17.** O botão de exportação gera arquivo .xlsx com os filtros aplicados na tela.
- **RF-P18.** Colunas na ordem da planilha: PROPOSTA, GRUPO, CONVENIO, VALOR, QUITACAO TOTAL, CONSIGNATARIA, DATA VENCIMENTO, um resultado por validador (somente no DS-507) e a decisão final.
- **RF-P19.** O CPF segue a máscara do perfil (RNF 3).
- Nome do botão: "Exportar" (DS-507) ou "Exportar Excel" (DS-509). Ver Q1.

## 6. Requisitos não funcionais

> **Regra do modelo.** Entra: condição mensurável de desempenho, segurança, auditoria ou volume, com origem. Não entra: requisito genérico ("o sistema deve ser rápido"). Exemplo curto: "o registro não pode ser editado pela interface (RNF 1, DS-504)".

| Código | O que as fontes dizem | Lacuna |
|---|---|---|
| RNF 1 | Auditabilidade: explicar qualquer decisão do motor (DS-504, história); registro imutável pela interface (DS-504) | Prazo de retenção do registro **[A CONFIRMAR]** |
| RNF 3 | CPF segue a máscara do perfil, inclusive na exportação (DS-507, DS-509) | Perfis e regra de máscara **[A CONFIRMAR]** |
| RNF 4 | Citado no DS-500 e no DS-505, sem descrição nas fontes | Conteúdo **[A CONFIRMAR]** |
| Desempenho | Nenhuma fonte define tempo máximo da execução agendada nem do "Reavaliar" | Meta **[A CONFIRMAR]**, depende do volume (seção 1) |
| Modo sombra | Nenhuma proposta é alterada; DS-508 exige "confirmação de que nenhuma proposta foi alterada após as execuções" | — |

**LGPD.** A exportação leva dados de proposta para fora do sistema (DS-509: "consultar as avaliações fora do sistema"). Onde o arquivo pode ser guardado e por quanto tempo: **[A CONFIRMAR]**. Nenhum exemplo deste documento contém CPF, contato ou nome de cliente.

## 7. Critérios de sucesso da fase

> **Regra do modelo.** Entra: como se sabe que a fase cumpriu o objetivo, com medida e fonte. Não entra: meta inventada sem dono. Exemplo curto: "zero propostas alteradas durante o modo sombra (DS-508)".

| Critério | Medida | Fonte |
|---|---|---|
| Modo sombra respeitado | Nenhuma proposta alterada após as execuções | DS-508 |
| Cobertura da tabela de decisão | Um caso aprovado por linha da tabela (1 a 9) e os exemplos 1 a 4 do Anexo I | DS-508 |
| Critério de avanço da Fase 2 (liberar os efeitos) | Citado no DS-507 como referência, **sem descrição nas fontes** | **[A CONFIRMAR]** |
| Concordância entre o motor e a planilha | Percentual de propostas com a mesma decisão no motor e na planilha, no período do modo sombra, medido pela exportação do DS-507 | **[ALÉM DA FONTE — decisão do usuário]**: é a leitura deste PRD para "comparar com a planilha durante o modo sombra" (DS-507); meta e período a definir |

## 8. Dependências e premissas

> **Regra do modelo.** Entra: o que precisa existir antes ou ao lado, com chave e estado na data da extração. Não entra: dependência sem item rastreável sem a marca de lacuna. Exemplo curto: "Fase 1 em CODE REVIEW (DS-415, 16/11/2026)".

| Dependência | Estado em 16/11/2026 | Fonte |
|---|---|---|
| Tela Administração de Quitação (Fase 1), com versão, prioridade e vigência das regras | DS-415 em CODE REVIEW; DS-416 EM DESENVOLVIMENTO; épico DS-418 EM DESENVOLVIMENTO | downstream_16-11.csv, 10h26 |
| Ajustes apontados no teste de 09/11/2026 na tela de Administração | Sem card no DS-418 | DS-500; insumo, seção 3.2 |
| Documento de Requisitos V04 (26/10/2026): tabela de decisão (seção 11), Anexo I, códigos ES, RF, RN, RNF | Não recebido no pacote | Insumo, seção 5 |
| Protótipo "Quitação · Avaliação do motor" | Citado no DS-505; não recebido | DS-505 |
| Planilha atual com a aba EXTRAÇÃO DE INFORMAÇÃO | Citada no DS-507 e no DS-509; não recebida | DS-507, DS-509 |
| Agendador de execução no Konsig | Mecanismo não descrito nas fontes | **[A CONFIRMAR]** |
| Rastreabilidade GDP-76 ↔ US-69 ↔ DS-418 ↔ DS-500 | Sem vínculo no Jira | Insumo, seção 6 |

## 9. Questões em aberto

> **Regra do modelo.** Entra: cada dúvida que bloqueia ou muda o desenvolvimento, com quem decide e até quando. Não entra: dúvida já decidida. Exemplo curto: "manter DS-507 ou DS-509?".

| Nº | Questão | Recomendação | Quem decide (papel) | Prazo |
|---|---|---|---|---|
| Q1 | DS-507 e DS-509 entregam quase a mesma exportação (insumo, seção 4.5) | Manter só o DS-507 (inclui o resultado por validador) e cancelar o DS-509 depois de levar para o DS-507 a origem "decisão da equipe em 09/11/2026", a referência ao RF10 e a finalidade de consulta fora do sistema **[ALÉM DA FONTE — decisão do usuário]** | PO | Antes do refinamento do DS-507 [A CONFIRMAR: data] |
| Q2 | DS-501 pede informar "quantas tiveram alteração de status", mas o modo sombra não altera status (DS-500) | Confirmar se o texto quer dizer "alteração de decisão em relação à avaliação anterior" **[A CONFIRMAR]** | PO | Antes do refinamento do DS-501 |
| Q3 | O botão "Reavaliar" é critério do DS-501, mas fica na tela do DS-505 | Registrar a dependência no DS-501 ou mover o critério para o DS-505, para que cada card possa ser validado sozinho (guia "Como escrever um card", seção 06) **[ALÉM DA FONTE — decisão do usuário]** | PO e tech lead | Antes do refinamento |
| Q4 | Número da fase que recebe os efeitos (descrição do DS-500 truncada) | Adotar a numeração do insumo (Fase 3 = efeitos, envio ao aprovador e controle) **[ALÉM DA FONTE — decisão do usuário]** | PO | — |
| Q5 | Conteúdo de PC-02, PC-05, RNF 4, D01, D02 | Anexar o Documento de Requisitos V04 ao épico DS-500 | Analista de requisitos | [A CONFIRMAR] |
| Q6 | Critério de avanço da Fase 2 | Descrevê-lo no DS-500 antes do início da Fase 3 | PO | [A CONFIRMAR] |

## 10. Rastreabilidade

> **Regra do modelo.** Entra: a ligação entre demanda, épico, cards, requisitos e testes. Não entra: requisito sem card nem card sem requisito sem a marca de lacuna. Exemplo curto: "RF-P7 → DS-504 → DS-508".

| Requisito deste PRD | Card de entrega | Código de origem (Doc. de Requisitos V04) | Teste |
|---|---|---|---|
| RF-P1 a RF-P3 | DS-501 | ES 1, RF1, RF1.a, RF22, PRE 1, PRE 2 | DS-508 (linhas 1 e 2 da tabela de decisão) |
| RF-P4 a RF-P6 | DS-503 | RF19.3 a RF19.5, RF22.c a RF22.f, RN02 a RN11 | DS-508 (linhas 5 a 9; regras inativa, fora da vigência, com alterações pendentes, prioridades) |
| RF-P7 a RF-P10 | DS-504 | RF12, RF19.6, RNF 1 | DS-508 cobre o motor; teste de imutabilidade do registro **[A CONFIRMAR: não listado no DS-508]** |
| RF-P11 a RF-P14 | DS-505 | RF10, RN10, RNF 3, RNF 4, ES 12, ES 16, RF15 | Cenários de teste no próprio card **[A CONFIRMAR]** |
| RF-P15, RF-P16 | DS-506 | RF12, RF19.6, ES 2, RNF 1 | Cenários de teste no próprio card **[A CONFIRMAR]** |
| RF-P17 a RF-P19 | DS-507 · DS-509 | RF10, RNF 3 | Cenários de teste no próprio card **[A CONFIRMAR]** |

Cadeia do GDP ao Downstream: GDP-76 → US-69 (Upstream, CONCLUÍDO UPSTREAM em 26/10/2026) → DS-418 (Fase 1) e DS-500 (Fase 2). Os vínculos não existem no Jira em 16/11/2026 (insumo, seção 6).

## 11. Situação dos temas

| Situação | Itens |
|---|---|
| **Decidido** | Sistema Konsig legado. Fase 2 = motor com tela de visualização; integração bancária por último (contexto-mestre, seção 10). Exportação para Excel incluída (decisão da equipe de 09/11/2026, DS-509) |
| **Em aberto** | Q1 a Q6 |
| **Bloqueado** | Início do desenvolvimento: depende da Fase 1 concluída com os ajustes do teste de 09/11/2026 (DS-500) |
| **Obsoleto** | Numeração da Previsão V02 (06/11/2026), em que a Fase 2 era o pagamento BB (insumo, seção 4.1) |
