# Esteira de Novos · Konsig

**Documento de insumo · Reestruturação da esteira no Konsig legado**
TI Neo Crédito · Comitê de Agilidade · versão 1 · 16/11/2026

| Item | Conteúdo |
|---|---|
| Finalidade | Reunir o que as fontes sustentam sobre a reestruturação da esteira no Konsig legado e explicitar o que falta para dimensioná-la no pool de 2027. |
| Natureza | Insumo. **Não é documento de requisito.** Não existe documento de requisito da esteira nas fontes recebidas. |
| Sistema | **Konsig (legado).** Não confundir com o NeoKonsig (reescrita), que é outro sistema, com outra tecnologia. |
| Pacote de fontes | Pacote do Comitê de Agilidade de 16/11/2026 (lista completa na seção 9). |
| Convenção | Todo trecho que vai além das fontes está marcado como **[ALÉM DA FONTE — decisão do usuário]**. |

---

## 1. Recomendação

A reestruturação da esteira não pode ser dimensionada com o que existe hoje: não há documento de requisito, a ata do alinhamento "Esteira KONSIG" de 22/10/2026 não foi recebida e os itens do GDP que tratam de esteira no Konsig têm a descrição apenas com o modelo em branco (seção 3). Qualquer tamanho atribuído agora seria invenção.

O caminho recomendado **[ALÉM DA FONTE — decisão do usuário]** é:

1. **Recuperar o `.md` das etapas da esteira** (atestado no DS-401) e **verificar com o responsável pelo DS-378** se o grafo foi gerado e se há registro formal (ata) do alinhamento de 22/10/2026 (seção 2.3), antes de escrever qualquer requisito.
2. **Produzir o documento de requisito da esteira** com a estrutura proposta na seção 6, respondendo antes às perguntas da seção 5.
3. **No pool de 2027, manter a esteira como item sem tamanho**, com a pendência explícita, até o documento de requisito existir. Não estimar por analogia com o cartão.
4. **Definir a esteira-alvo antes de fechar a especificação técnica da Etapa 1 do cartão no Konsig (US-92)**, porque o cartão será construído sobre a esteira do Konsig (seção 4).

**Nota de higiene documental.** A reestruturação da esteira no Konsig legado está decidida desde 13/11/2026 (seção 7). Resta apenas atualizar a tabela da seção 6 do `contexto-mestre.md`, que registra nessa data somente o cartão, e retirar do `prompt-comite.md` a pergunta GDP-34 × Konsig.

---

## 2. O que se sabe

### 2.1 Enquadramento

| Fato | Fonte |
|---|---|
| As prioridades de 2027 já definidas, fora da disputa do pool, são: cartão de crédito, integrações com a Salesforce e reestruturação da esteira. | `prompt-comite.md`, seção 3 (16/11/2026) |
| Cartão e reestruturação da esteira, duas das três prioridades, entram no Konsig legado. | `contexto-mestre.md`, seção 7 (16/11/2026) |
| O Konsig não tem CI/CD. O item correspondente (US-43 "Konsig: CI/CD") está em BACKLOG, prioridade Medium, criado em 14/08/2026. | `contexto-mestre.md`, seção 7; `upstream_16-11.csv` (extração 16/11/2026 9h51) |
| No alinhamento da Esteira de 22/10/2026, a gestora atribuiu criticidade alta ao Admin. O GDP-31 "[NEO-KON] ADMIN" está em BACKLOG com prioridade Low. | `contexto-mestre.md`, seção 7; `gdp_16-11.csv` (extração 16/11/2026 9h51) |
| A classificação de motivos de reprovação de proposta "consta como encaminhamento nº 3 do alinhamento 'Esteira KONSIG' (22/10/2026)". | US-87, `upstream_16-11.csv` (extração 16/11/2026 9h51) |
| O escopo e o tamanho da reestruturação da esteira "ainda não têm documento". | `prompt-comite.md`, seção 4 (16/11/2026) |

**Observação sobre o alinhamento de 22/10/2026.** As fontes mostram apenas dois resultados dessa reunião: a criticidade alta do Admin (que é item do NeoKonsig, GDP-31) e o encaminhamento nº 3 (US-87, no Konsig). Os demais encaminhamentos não constam do pacote. As fontes registram, portanto, dois resultados da reunião, um ligado ao NeoKonsig (Admin, GDP-31) e outro ao Konsig (US-87). A ata é necessária para confirmar o escopo tratado.

**Observação sobre o nome "Esteira de Novos".** O termo "Novos" não aparece em nenhuma fonte do pacote como nome de esteira, produto ou tipo de operação. O nome do arquivo vem da lista de anexos do `prompt-comite.md` (seção 2). O recorte que "Novos" representa é uma das perguntas da seção 5.

### 2.2 Como a esteira do Konsig aparece hoje nos cards

Os cards concluídos e em andamento descrevem partes da esteira atual. Nenhum deles descreve a esteira inteira.

| Elemento | O que a fonte diz | Fonte (`downstream_16-11.csv`, extração 16/11/2026 10h26, salvo indicação) |
|---|---|---|
| Situação + atividade | A proposta tem uma situação (ex.: "REPROVADO", "INTEGRADO") e uma atividade (ex.: "REPROVADO PELO CORBAN"); as regras de movimentação combinam as duas. | DS-318 (Expedite, concluído em 02/10/2026) |
| Esteiras nomeadas | "esteira da paradinha (PENDENTE - AGUARD APROVAÇÃO CORBAN)"; "esteira averbação"; "esteira Cartão Consignado Compra"; "esteira de Compra". | DS-318; DS-407; DS-501; US-88 (`upstream_16-11.csv`) |
| Status citados | PEN - Aguard Aprovação/Análise Corban; AND - Aguard Quitação; And - Aguard Auditoria; Pen - Aguard Auditoria; Pen - Contato Insatisfatório. | DS-84; DS-501; DS-90 |
| Troca de esteira | Usuários externos só alteram a esteira em situações específicas (ex.: aprovador da paradinha); usuários internos da Neo têm regra própria. | DS-205, DS-84 (épico DS-82, concluído em 25/09/2026) |
| Retorno ao status anterior | Na auditoria Nuvidio, a proposta grava o status anterior ao entrar em Pen - Contato Insatisfatório e volta a ele após o retorno do parceiro ("Comportamento Normal da Esteira"). | DS-90 (épico DS-85, concluído em 20/10/2026) |
| Gatilho de avanço na digitação | O avanço da proposta na esteira é disparado pela aba "Ficha Proposta"; a tela "Minha esteira" existe para o parceiro. | DS-250 (concluído em 25/09/2026) |
| Permissões por rota | O relatório da paradinha tem acesso por permissão de rota, com visão operacional e visão comercial. | DS-83 "Relatório para acompanhamento da paradinha" (épico DS-82) |
| Áreas que reprovam | Averbação, Crédito, Risco, NP/Abertura e Suporte comercial, cada uma com lista própria de motivos. | US-87 (`upstream_16-11.csv`) |

### 2.3 Documentação técnica da esteira (não recebida)

| Chave | Resumo | Estado | O que gerou |
|---|---|---|---|
| DS-378 | SPEC DRIVEN DEVELOPMENT - DOCUMENTAR TODAS AS ETAPAS DA ESTEIRA | CONCLUÍDO em 20/10/2026 · natureza Arquitetura · classe Intangible · categoria Konsig · sem épico | "Documentar todas as etapas da esteira e possíveis caminhos, e elaborar um grafo pra demonstrar" |
| DS-401 | Documentar as etapas da Esteira | CONCLUÍDO em 22/10/2026 · natureza Arquitetura · classe Intangible · categoria Konsig · sem épico | "Atualmente temos um .md com as etapas da esteira, necessário validar as nuances de cada status, validar todas as etapas e então disponibilizar um PDF de uso comum a todos" |

Fonte: `downstream_16-11.csv` (extração 16/11/2026 10h26).

O DS-401 foi concluído no mesmo dia do alinhamento "Esteira KONSIG" (22/10/2026). Só o `.md` das etapas tem existência atestada pela fonte ("Atualmente temos um .md", DS-401); o DS-378 pede "elaborar um grafo", mas a fonte não confirma que o grafo foi gerado. Esses artefatos, se existirem, são o retrato mais próximo do AS IS técnico da esteira e devem ser a primeira entrada do documento de requisito. Nenhum deles está no pacote.

---

## 3. Itens existentes que podem compor ou ser absorvidos

Fonte: `gdp_16-11.csv` e `upstream_16-11.csv` (extração 16/11/2026 9h51); `downstream_16-11.csv` e `epicos_downstream_16-11.csv` (extração 16/11/2026 10h26).

### 3.1 Itens do GDP com "esteira" no Konsig

O GDP-34 "[NEO-KON] ESTEIRA" também tem "esteira" no resumo, mas é do NeoKonsig e não consta desta tabela (seção 7, Fora de escopo).

| Chave | Resumo | Status | Prioridade | Categorias | Criado | Descrição | Recomendação **[ALÉM DA FONTE — decisão do usuário]** |
|---|---|---|---|---|---|---|---|
| GDP-75 | [KON] ESTEIRA PARA TRATATIVA INTERNA | PRIORIZAÇÃO UPSTREAM | High | Cobrança, Financeiro, Konsig | 06/08/2026 | Apenas o modelo em branco | Candidato a compor a reestruturação. Confirmar com Cobrança/Financeiro se é uma esteira nova dentro do mesmo desenho. |
| GDP-61 | [KON] RETORNO DE PAGAMENTOS - ESTEIRA | BACKLOG UPSTREAM | High | Financeiro, Konsig, Operacional | 06/08/2026 | Apenas o modelo em branco | Candidato a compor. Avaliar junto com o GDP-117 (mesmo tema). |
| GDP-57 | [KON] NOVA ESTEIRA SIAPE | BACKLOG | Lowest | Konsig, Produtos | 06/08/2026 | Apenas o modelo em branco | Candidato a compor, se o recorte "Novos" incluir convênios. Manter Lowest até o recorte de "Novos" ser definido. Se o SIAPE entrar no recorte, elevar para a prioridade da reestruturação. |
| GDP-79 | [KON] CAMPO DE REANÁLISE NA ESTEIRA | CONCLUÍDO (resolvido 17/08/2026) | Medium | Konsig, Operacional | 06/08/2026 | Apenas o modelo em branco; sem card do Downstream associado | Não absorver. Registrar como comportamento existente no AS IS. |

### 3.2 Itens do Konsig que alteram a movimentação da proposta na esteira

Estes itens já têm escopo próprio e estão em andamento. A recomendação **[ALÉM DA FONTE — decisão do usuário]** é **não absorvê-los**: tratá-los como dependências que o documento de requisito precisa respeitar.

| Chave | Resumo | Status | Prioridade | Relação com a esteira |
|---|---|---|---|---|
| GDP-114 / US-82 | [KON] CRIVO - ESTRUTURAÇÃO DA TOMADA DE DECISÃO | EM UPSTREAM / PROTOTIPAÇÃO | Highest | "direcionar a proposta para a atividade correspondente na esteira" conforme Aprovado, Reprovado ou Análise Corban; redefine mensagens e motivos de reprovação. |
| US-87 | [KON] CLASSIFICAÇÃO DE MOTIVOS DE REPROVAÇÃO DE PROPOSTA | APROVAÇÃO SOLICITANTES | Medium | Encaminhamento nº 3 do alinhamento de 22/10/2026. Lista fechada de motivos por área. Fora do card: NeoKonsig e motivos de pendência. |
| GDP-118 / US-72 / DS-454 / DS-466 | [KON] JUDIT - ESTRUTURAÇÃO DA VALIDAÇÃO DE AÇÕES JUDICIAIS | EM DOWNSTREAM (GDP-118); APROVAÇÃO SOLICITANTES (US-72, Highest); épicos DS-454 e DS-466 EM DESENVOLVIMENTO | Medium (GDP-118) | Reprovação automática de propostas por consulta processual. |
| GDP-76 / DS-418 / DS-500 | [KON] SISTEMATIZAÇÃO DA QUITAÇÃO; Fase 1 e Fase 2 | EM DOWNSTREAM; DS-418 EM DESENVOLVIMENTO; DS-500 BACKLOG | Medium (GDP-76) | O motor da Fase 2 avalia as propostas da "esteira Cartão Consignado Compra em AND - AGUARD QUITACAO" (DS-501). |
| GDP-62 / US-83 | [KON] CRCP - VALIDAÇÃO DE CERTIFICADO | EM UPSTREAM / ESPECIFICAÇÃO TÉCNICA + TESTES | Highest | "a proposta só avance na esteira com o CPF dentro das regras". Abrange Konsig e NeoKonsig. Categoria Autorregulação (`gdp_16-11.csv`, 16/11/2026 9h51); "Risco apontado: regulatório" (US-83, `upstream_16-11.csv`, 16/11/2026 9h51). |
| GDP-117 | [KON] MELHORIAS NO FLUXO DE RETORNO DE PAGAMENTOS - BB | BACKLOG UPSTREAM | Medium | "Pendente definir quais melhorias deveremos atuar e escrever o escopo". Mesmo tema do GDP-61. |
| US-90 | [KON] VALOR DE QUITAÇÃO NO RELATÓRIO DE TRATATIVA INTERNA | BACKLOG | Medium | Mesmo tema do GDP-75 (tratativa interna). Descrição vazia. |

### 3.3 Entregas concluídas que compõem o AS IS

| Chave | Resumo | Concluído | Contribuição para o AS IS |
|---|---|---|---|
| GDP-52 / DS-82 | Paradinha - Quitação | GDP-52 resolvido 06/10/2026; DS-82 resolvido 25/09/2026 | Esteira da paradinha, troca de esteira, travas por perfil, relatório. |
| GDP-54 / DS-85 | Receptivo Nuvidio | GDP-54 resolvido 19/10/2026; DS-85 resolvido 20/10/2026 | "movimentação correta das propostas na esteira" na auditoria por vídeo. |
| GDP-60 / DS-92 | Retorno de pagamentos BB | GDP-60 resolvido 16/09/2026; DS-92 resolvido 16/09/2026 | Validação de contas do Banco do Brasil por API. |
| GDP-99 / DS-116; GDP-25 | Tratativa interna (adequação de dados; blocklist e notificação) | GDP-99 resolvido 16/09/2026; GDP-25 resolvido 05/08/2026 | Base para o GDP-75. |
| DS-378, DS-401 | Documentação das etapas da esteira | 20/10/2026 e 22/10/2026 | Ver seção 2.3. |

### 3.4 Limitação dos itens

Os GDP-57, GDP-61, GDP-75 e GDP-79 têm a descrição preenchida apenas com o modelo ("Solicitante: Nome do solicitante da demanda..."). Não há solicitante, problema, AS IS nem consequência registrados. **Não é possível dizer, com as fontes, o que cada um pede.**

---

## 4. Dependências com o cartão de crédito

| Dependência | O que a fonte diz | Fonte |
|---|---|---|
| Mesmo sistema | O cartão entra no Konsig legado (decisão de 13/11/2026). A esteira também está no Konsig legado. | `contexto-mestre.md`, seções 6 e 7 |
| O cartão percorre a esteira do Konsig | "O correspondente bancário (corban) [...] que segue o fluxo da esteira do Konsig, oferta o cartão ao cliente. A Neo Crédito segue o mesmo fluxo de aprovação do crédito consignado." | `visao-cartao-v6.txt` (03/11/2026), seção 3 |
| Macroetapas do cartão no Konsig | Macroetapas 1 a 6 (Originação, Elegibilidade, Identificação/KYC/crédito/risco, Decisão de crédito, Oferta, Contratação) têm o Konsig como responsável. A macroetapa 4 depende de "Motor de decisão [...] e esteira de pendências". | `visao-cartao-v6.txt` (03/11/2026), seção 4, Etapa 1 |
| Trabalho do cartão já aberto sobre a esteira | US-92 "[NEO-CARD] Konsig - Etapa 1 - Originação e Abertura de Conta" em ANÁLISE FUNCIONAL; subtarefa US-100 prevê testar "as APIs que iremos usar na esteira do Konsig (criação de conta, criação de cartão virtual, postagem de saque)". | `upstream_16-11.csv` (extração 16/11/2026 9h51) |
| Mesma capacidade | Cartão e esteira disputam a mesma capacidade de projeto, no mesmo sistema: 22,75 cards de épico por sprint, medida para todo o Downstream (média S15–S18: 38,25 cards; 22,75 com épico; 40,5% sem épico). As fontes não segregam a equipe por sistema. O tamanho do cartão está pendente de nova estimativa: a estimativa da planilha v13 (13/11/2026) foi descartada por pedido do usuário. | `metricas_downstream_16-11.json`, extração 16/11/2026 10h26, campo `media_S15_S18` |
| Sem CI/CD no Konsig | Construção nova no legado sem CI/CD (US-43 em BACKLOG). O épico DS-53 "Regressão automatizada" (Konsig) tem 12 cards, 3 concluídos e 9 abertos, todos em BACKLOG. | `contexto-mestre.md`, seção 7; `upstream_16-11.csv` (9h51); `epicos_downstream_16-11.csv` (16/11/2026 10h26) |
| Divergência da Visão v6 | A Visão v6 põe o pós-faturamento no NeoKonsig; vale a informação do usuário de que o cartão entra no Konsig legado. A Visão precisa ser corrigida. | `contexto-mestre.md`, seção 3 |

**Consequência para a sequência [ALÉM DA FONTE — decisão do usuário].** Se o cartão for construído sobre a esteira atual e a esteira for reestruturada depois, as integrações das macroetapas 1 a 6 serão refeitas. A recomendação é que o documento de requisito da esteira defina ao menos as etapas, status e pontos de integração da esteira-alvo antes do encerramento da especificação técnica da US-92 (subtarefa US-99, em ANÁLISE FUNCIONAL).

**Ponto a esclarecer.** O DS-501 cita uma esteira já existente chamada "Cartão Consignado Compra". As fontes não dizem qual é a relação entre essa esteira e o novo cartão de crédito da Visão v6. Não inferir; perguntar (seção 5).

---

## 5. Perguntas que precisam de resposta para dimensionar

Recomenda-se levar as perguntas ao solicitante da reestruturação em uma única sessão, com o `.md` do DS-401 e, se existirem, o grafo do DS-378 e o registro do alinhamento de 22/10/2026 em mãos **[ALÉM DA FONTE — decisão do usuário]**. As fontes não identificam o solicitante formal da reestruturação.

### 5.1 Escopo

1. O que significa "Novos" no nome "Esteira de Novos": contratos novos, um produto, um conjunto de convênios ou toda a esteira de originação?
2. A reestruturação substitui a esteira atual ou acrescenta esteiras (tratativa interna, retorno de pagamentos, SIAPE)?
3. Quais dos GDP-57, GDP-61 e GDP-75 fazem parte da reestruturação? Se o GDP-57 fizer parte, a prioridade Lowest muda?
4. Quais foram os encaminhamentos 1, 2 e 4 em diante do alinhamento de 22/10/2026, e quais são do Konsig e quais do NeoKonsig?
5. Qual o problema que a reestruturação resolve (tempo de proposta, perda de proposta, retrabalho, rastreabilidade)? Qual o indicador de sucesso?
6. A esteira "Cartão Consignado Compra" (DS-501) tem relação com o novo cartão de crédito?

### 5.2 Perfis

7. Quais perfis atuam em cada etapa: parceiro/corban, digitador, aprovador da paradinha, áreas internas (Averbação, Crédito, Risco, NP/Abertura, Suporte comercial, Financeiro, Cobrança)?
8. O modelo de permissão por rota usado no relatório da paradinha (DS-83) deve ser estendido à esteira-alvo?
9. A visão da esteira para o corban muda? (O GDP-34 trata disso, mas no NeoKonsig.)

### 5.3 Etapas e regras

10. O `.md` e o grafo do DS-378/DS-401 estão validados? O PDF de uso comum previsto no DS-401 foi publicado?
11. A lógica situação + atividade (DS-318) continua?
12. Como ficam as travas e exceções já implantadas (paradinha, retorno ao status anterior da auditoria, reanálise do GDP-79)?
13. Onde entram os motivos de reprovação (US-87) e de pendência na esteira-alvo?

### 5.4 Integrações

14. Quais integrações movimentam a proposta e precisam ser revistas: Crivo (GDP-114), Judit (GDP-118), Nuvidio (GDP-54), API do Banco do Brasil (GDP-60/GDP-117), Núclea MCB0106 (US-83), Orbitall e MBLabs (cartão)?
15. A integração com a Salesforce (outra prioridade de 2027) toca a esteira? A Visão v6 cita o atendimento multicanal pela Salesforce; as fontes não dizem se ele lê ou altera a proposta.

### 5.5 Restrições técnicas

16. A reestruturação depende da US-43 (CI/CD) ou da regressão automatizada (DS-53) para ser entregue com segurança?
17. Há migração de propostas em andamento da esteira atual para a nova?

---

## 6. Proposta de estrutura do documento de requisito

**[ALÉM DA FONTE — decisão do usuário]** A estrutura abaixo é proposta deste insumo; não vem de documento oficial. Recomenda-se seguir o modelo de documentos da Neo Crédito (contexto-mestre, seção 2) e o mesmo padrão de referência usado no Documento de Requisitos da Quitação (ES, RF, RN, RNF, tabela de decisão), citado no DS-500.

| Nº | Seção | Conteúdo | Insumo |
|---|---|---|---|
| 1 | Dados do projeto e versionamento | Solicitante, área, sistema (Konsig), vínculo com o PDTI, risco | A obter |
| 2 | Contexto e problema | Problema, impacto, indicador de sucesso | Ata de 22/10/2026 (a obter) |
| 3 | Escopo e fora de escopo | Recorte de "Novos"; itens do GDP absorvidos; exclusão explícita do NeoKonsig e do GDP-34 | Seções 3 e 5.1 deste insumo |
| 4 | AS IS | Esteiras, situações, atividades, status e transições atuais; grafo | DS-378, DS-401 (a obter); seção 2.2 deste insumo |
| 5 | Perfis e permissões | Matriz perfil × etapa × ação | DS-83, DS-205, DS-84; seção 5.2 |
| 6 | TO BE | Etapas, status, transições, gatilhos automáticos e manuais, exceções; tabela de decisão | A construir |
| 7 | Regras de negócio | Travas, reprovação, pendência, reanálise, troca de esteira | DS-318, DS-90, US-87, GDP-114 |
| 8 | Integrações | Por integração: evento, direção, efeito na proposta | Seção 5.4 |
| 9 | Pontos de encaixe do cartão | Onde as macroetapas 1 a 6 do cartão entram na esteira-alvo | `visao-cartao-v6.txt`; US-92 |
| 10 | Requisitos não funcionais | Rastreabilidade, auditoria, desempenho | A construir |
| 11 | Transição | Migração de propostas em andamento; convivência das esteiras | Seção 5.5 |
| 12 | Faseamento e critérios de aceite | Fases entregáveis; base para quebrar em cards pelo guia "Como escrever um card", seção 06 | `guia-como-escrever-card.txt` |
| 13 | Referência cruzada | Requisito × card × caso de teste × fonte | — |

O documento de requisito, uma vez aprovado, é a base para dimensionar a esteira no pool, na unidade que o comitê aprovar (proposta PP a GG em aberto, `contexto-mestre.md`, seção 7).

---

## 7. Decidido · em aberto · bloqueado · obsoleto

### Decidido

| Decisão | Data | Fonte |
|---|---|---|
| O cartão de crédito entra no Konsig legado, não no NeoKonsig. | 13/11/2026 | `contexto-mestre.md`, seção 6 |
| Reestruturação da esteira é prioridade de 2027, fora da disputa do pool. | — (data não registrada) | `prompt-comite.md`, seção 3 |
| Reestruturação da esteira no Konsig legado. | 13/11/2026 | `contexto-mestre.md`, seção 7 (16/11/2026) |
| No pool de 2027, projeto = épico. | 13/11/2026 | `contexto-mestre.md`, seção 6 |
| O guia "Como escrever um card" (InnoviaX) é o tutorial de abertura de cards. | 13/11/2026 | `contexto-mestre.md`, seção 6 |

### Em aberto

- Escopo, recorte ("Novos") e tamanho da reestruturação (seção 5).
- Quais itens do GDP compõem a reestruturação (GDP-57, GDP-61, GDP-75).
- Prioridade do GDP-57 (Lowest) frente a uma prioridade de 2027.
- Sequência entre a esteira-alvo e a especificação técnica do cartão no Konsig (US-92/US-99).
- Divergência de prioridade do Admin: criticidade alta no alinhamento de 22/10/2026 × GDP-31 em Low (NeoKonsig; contexto-mestre, seção 7).
- Prazo do cartão: Visão v6 indica novembro/2026; pela capacidade medida, o desenvolvimento termina em 2027 (contexto-mestre, seção 7).
- Relação entre a esteira "Cartão Consignado Compra" (DS-501) e o novo cartão.

### Bloqueado

- **Dimensionamento da reestruturação no pool:** bloqueado pela falta de documento de requisito, do registro do alinhamento de 22/10/2026 e do `.md` do DS-401 (e do grafo do DS-378, se gerado).
- **Escopo dos GDP-57, GDP-61 e GDP-75:** bloqueado pela descrição em branco (apenas modelo).

### Obsoleto

- Nenhum item desta frente foi identificado como obsoleto nas fontes. O GDP-79 está concluído, não obsoleto: entra como comportamento do AS IS.

### Fora de escopo deste insumo

- **GDP-34 [NEO-KON] ESTEIRA** (NeoKonsig, BACKLOG, Low). Não confundir com a reestruturação no Konsig.

---

## 8. Riscos

| Risco | Base | Tratamento recomendado **[ALÉM DA FONTE — decisão do usuário]** |
|---|---|---|
| Retrabalho no cartão se a esteira mudar depois da construção | Seção 4 | Definir a esteira-alvo antes de fechar a US-99. |
| Mudança estrutural em sistema sem CI/CD e com regressão automatizada em backlog | US-43; DS-53 (9 de 12 cards abertos) | Incluir no faseamento a dependência de regressão sobre os fluxos da esteira. |
| Sobreposição com projetos em andamento que mexem na movimentação da proposta | GDP-114, US-87, GDP-118, GDP-76, GDP-62 | Tratar como dependências no documento de requisito, não absorver. |
| Nenhum item no GDP representa a reestruturação no Konsig | `gdp_16-11.csv` | Abrir um item no GDP com o recorte aprovado, para o pool (projeto = épico) ter onde ancorar o tamanho. |

---

## 9. Fontes

| Arquivo do pacote | Conteúdo usado | Data |
|---|---|---|
| `contexto-mestre.md` | Seções 3, 6 e 7: sistemas, decisões, pontos em aberto | 16/11/2026 |
| `metricas_downstream_16-11.json` | `media_S15_S18`: 38,25 cards; 22,75 com épico; 40,5% sem épico | Extração 16/11/2026 10h26 |
| `prompt-comite.md` | Seções 2, 3 e 4: prioridades de 2027, pendências do pool | 16/11/2026 |
| `gdp_16-11.csv` | GDP-25, 31, 34, 52, 54, 57, 60, 61, 62, 75, 76, 79, 99, 114, 117, 118 | Extração 16/11/2026 9h51 |
| `upstream_16-11.csv` | US-43, 72, 82, 83, 87, 88, 90, 92, 99, 100 | Extração 16/11/2026 9h51 |
| `downstream_16-11.csv` | DS-82, 83, 84, 85, 90, 92, 205, 250, 318, 378, 401, 407, 418, 454, 466, 500, 501 | Extração 16/11/2026 10h26 |
| `epicos_downstream_16-11.csv` | DS-53 (cards totais, concluídos e abertos) | 16/11/2026 10h26 |
| `visao-cartao-v6.txt` | Seções 2 a 4: papel do Konsig, fluxo da esteira, macroetapas | 03/11/2026 |

**Não recebidos e necessários:** registro (ata), se houver, do alinhamento "Esteira KONSIG" (22/10/2026); arquivo `.md` das etapas da esteira e PDF de uso comum (DS-401); grafo de etapas (DS-378), se gerado; documento "Konsig Arquitetura" (Drive, citado no contexto-mestre, seção 3); Inventário de Sistemas.
