<!--
EXEMPLO PREENCHIDO · Plano de Implementação curto (tamanho M) · Kit de documentação TI Neo Crédito · preenchimento de modelos/PLANO-DE-IMPLEMENTACAO.md
Destino real: docs/planos/DS-500_plano-quitacao-fase-2.md no repositório do Konsig ([A CONFIRMAR] qual repositório definitivo; até lá, pasta provisória do README do kit, seção 4).
ESTRUTURA v1 (16/11/2026): NÃO SIGA A NUMERAÇÃO DE SEÇÕES DESTE EXEMPLO. No modelo v2 (modelos/PLANO-DE-IMPLEMENTACAO.md), o Plano curto de M usa só as seções 2, 5, 7 e 11, mais a tabela 8.1;
a seção 4 do modelo é "Desenho e alternativas", a 8 é "Corte e rollback" e a 12 são as tarefas para a IA. Aqui, a seção 4 são os cards (2.2 no v2), a 8 só o rollback (8.1 no v2) e a 12 o critério de pronto (13 no v2).
O conteúdo vale; as regras do PRD foram remapeadas para a numeração do PRD v2 (GDP-76 v0.2, RN01 a RN08) em 17/11/2026.
Fontes: downstream_16-11.csv (16/11/2026 10h26); upstream_16-11.csv e gdp_16-11.csv (16/11/2026 9h51); metricas_downstream_16-11.json (16/11/2026 10h26);
D1-pool/regua-tamanho-tempo.md v1 (16/11/2026); D1-pool/pool-2027-plano.xlsx (base Jira 16/11/2026); insumos/quitacao-estado-e-faseamento.md (16/11/2026);
contexto-mestre.md, seções 4, 5 e 10; Review da Sprint 18 (extração 06/11/2026 16h46).
Pré-requisito do modelo não cumprido: o PRD de origem está em 0.2 (Rascunho). Este plano é, portanto, Rascunho e não autoriza criar cards novos.
-->

# Plano de Implementação · Quitação Fase 2 · Motor de validação e tela de visualização

## 1. Identificação

| Campo | Valor |
|---|---|
| Sistema | **Konsig** (legado). Não se aplica ao NeoKonsig. |
| Épico | DS-500 |
| PRD de origem | `docs/prd/GDP-76_quitacao-fase-2-motor.md` · versão 0.2 (Rascunho) |
| ADRs aplicáveis | ADR-0002 (ordem das fases), Aceito; ADR-0001 (pagamento via PagAuto) não se aplica a esta fase, apenas registra o que fica fora |
| Item GDP / Upstream | GDP-76 / US-69 |
| Tamanho pela régua | M · 8 cards |
| Status | Rascunho |
| Responsável pelo plano | Tech lead |
| Aprovação | PO · pendente |

### Versionamento

| Data | Responsável (papel) | Versão | Descrição da alteração |
|---|---|---|---|
| 16/11/2026 | Analista funcional, para revisão do tech lead | 0.1 | Elaboração do plano a partir dos 8 cards do DS-500. |
| 17/11/2026 | Analista funcional, para revisão do tech lead | 0.2 | RN remapeadas para o PRD v2 (GDP-76 v0.2); referências ao PRD corrigidas (seções 6, 7 e 12); datas da régua pela convenção do modelo (26/01/2027 e 12/02/2027). Estrutura de seções mantida na v1. |

---

## 2. Entregas

| # | Entrega | O que fica verificável ao final | Regras do PRD cobertas | Cards previstos | Tamanho |
|---|---|---|---|---|---|
| E1 | Motor em modo sombra | O Financeiro consulta o registro de cada avaliação, com regra, versão e decisão, e confirma que nenhuma proposta mudou de situação | RN01 a RN07 | 4: DS-501, DS-503, DS-504 e DS-508 (teste do motor) | P |
| E2 | Visualização e exportação | O Financeiro vê a lista e o detalhe das avaliações e exporta para comparar com a planilha | RN08; exibição da RN05 | 4: DS-505, DS-506, DS-507, DS-509 | P |

O DS-508 é o card de teste da E1, e não uma entrega própria: sozinho, ele não produz nada que alguém fora do time verifique. Se a pendência "Duas exportações" do PRD (seção 7) for decidida pela unificação do DS-507 com o DS-509, a E2 passa a 3 cards, ainda P.

Estado em 16/11/2026 10h26: os 8 cards em BACKLOG, sem sprint; o épico na Sprint 19. PO vazio no DS-506 e no DS-509; dev preenchido só no DS-507 (`downstream_16-11.csv`).

---

## 3. Sequência e dependências

| Entrega | Depende de | Tipo de dependência | Situação |
|---|---|---|---|
| E1 | Fase 1 concluída, com os ajustes do teste de 09/11/2026 na tela de Administração (pré-requisito do DS-500) | Negócio | Aberta: DS-415 em CODE REVIEW e DS-416 EM DESENVOLVIMENTO; ajustes sem card. Dono: PO; data [A CONFIRMAR] |
| E1 | Documento de Requisitos V04 anexado ao DS-500 (tabela de decisão e Anexo I) | Negócio | Aberta. Dono: analista de requisitos; data [A CONFIRMAR] |
| E2 | E1: a lista e o detalhe mostram o que o registro gravou (DS-504) | Técnica | Resolvida pela ordem |
| E2 (DS-507) | DS-505: a exportação usa "os filtros aplicados na tela" | Técnica | Resolvida pela ordem |

Dependência cruzada: o critério "Reavaliar" do DS-501 (E1) é acionado na tela do DS-505 (E2). Do jeito que está, o DS-501 só é aceito depois do DS-505. Tratamento: pendência do PRD, seção 7 ("Reavaliar" está no DS-501, o botão no DS-505), a decidir no refinamento **[ALÉM DA FONTE — decisão do usuário]**.

---

## 4. Épicos e cards previstos

| Entrega | Card (título: verbo + objeto) | Tipo | Critério de quebra usado (seção 06 do guia) | Referência no PRD | Chave DS |
|---|---|---|---|---|---|
| E1 | Capturar as propostas em AND - AGUARD QUITACAO e executar o motor | História | Por etapa do processo (captura e execução) | RN01, RN06, RN07 | DS-501 |
| E1 | Aplicar as regras parametrizadas por prioridade e definir a decisão final | História | Por regra de negócio | RN03, RN04 | DS-503 |
| E1 | Registrar cada avaliação de forma auditável | História | Por regra de negócio | RN05 | DS-504 |
| E1 | Testar o motor com a tabela de decisão e os exemplos do Anexo I | Tarefa (teste) | Card de teste: deriva dos cenários do DS-501, DS-503 e DS-504 (guia, seção 07) | RN01 a RN07; seção 12 (tabela de decisão) | DS-508 |
| E2 | Tela de visualização: lista de propostas avaliadas | História | Por tipo de fluxo (consulta em lista) | RN05 (exibição) | DS-505 |
| E2 | Tela de visualização: detalhe da avaliação da proposta | História | Por tipo de fluxo (consulta do detalhe) | RN05 (exibição) | DS-506 |
| E2 | Exportar a avaliação para comparação com a planilha | História | Por tipo de documento (arquivo .xlsx) | RN08 | DS-507 |
| E2 | Exportar a avaliação do motor para Excel | História | Por tipo de documento (arquivo .xlsx) | RN08 | DS-509 |

**Conferência contra os sinais de card grande (guia, seção 06).**

- DS-501: o título precisa de "e". Sugestão de título: "Executar o motor sobre as propostas em AND - AGUARD QUITACAO" **[ALÉM DA FONTE — decisão do usuário]**; ver também a dependência do "Reavaliar" na seção 3.
- DS-507 e DS-509: mesmo arquivo, mesmas colunas e mesma máscara. É duplicidade a resolver (pendência "Duas exportações", PRD seção 7), não quebra.
- Títulos dos DS-505 e DS-506 começam por substantivo, não por verbo. Sugestão: "Listar as propostas avaliadas" e "Exibir o detalhe da avaliação da proposta" **[ALÉM DA FONTE — decisão do usuário]**.
- Os critérios de quebra desta tabela foram atribuídos neste plano a cards já criados, que não os registram **[ALÉM DA FONTE — decisão do usuário]**.

---

## 5. Ambientes e deploy

| Item | Konsig |
|---|---|
| Pipeline de CI/CD | **Não existe** (US-43, BACKLOG desde 14/08/2026, `upstream_16-11.csv`, 16/11/2026 9h51) |
| Ambientes disponíveis | [A CONFIRMAR no Inventário de Sistemas] |
| Homologação dedicada | [A CONFIRMAR]: é um dos itens do US-43, cuja descrição chegou truncada |
| Padrão de release | Sem padrão. O DS-550 (9 cards em Backlog) começa pelo Keycloak; adoção no Konsig [A CONFIRMAR] |
| Waiting for deploy | 4 itens abertos em 16/11/2026 (`metricas_downstream_16-11.json`, 10h26). Tempo esperado nesta etapa: [A CONFIRMAR] |
| Precedente de deploy manual | O DS-93 (Retorno de pagamentos BB) registra que, ao subir, é preciso aplicar a DDL do card e subir os branches da aplicação web e da API |

Sequência proposta **[ALÉM DA FONTE — decisão do usuário]**:

| Ordem | O que sobe | Quem executa (papel) | Condição | Conferência depois do passo |
|---|---|---|---|---|
| 1 | Estrutura do registro de avaliação (DS-504) e motor (DS-501, DS-503), com a execução agendada desligada | Tech lead, com infraestrutura | DS-508 aprovado em [ambiente A CONFIRMAR] | Nenhuma avaliação registrada; nenhuma proposta alterada |
| 2 | Ligar a execução agendada | Tech lead | Passo 1 conferido | Primeiras execuções conferidas pelo dev e pelo QA; nenhuma proposta alterada (RN02) |
| 3 | Telas (DS-505, DS-506) e exportação (DS-507) | Tech lead | Aprovação POs | Financeiro abre a aba e exporta |

Cada card registra, antes de Waiting for deploy, os passos manuais (DDL, configuração do agendamento, ordem dos componentes) e os passos de reversão. Horário permitido para deploy no Konsig: [A CONFIRMAR].

---

## 6. Migração de dados

Não se aplica: o motor só lê propostas e regras e grava o registro novo da avaliação; não altera dado existente (modo sombra, DS-500).

---

## 7. Plano de teste

| Nível | O que cobre | Quem executa (papel) | Ambiente | Evidência | Critério de aprovação |
|---|---|---|---|---|---|
| Teste do desenvolvedor | Regras de cada card da E1 | Dev | Local | Testes automatizados no pull request | Testes passando no Code Review |
| QA Teste · motor (DS-508) | Um caso por linha da tabela de decisão (1 a 9); exemplos 1 a 4 do Anexo I; Validador Boleto (vencimento vazio, vencido e no dia; código de barras com valor igual, diferente e zerado; dois boletos com um pago); regras inativa, fora da vigência, com alterações pendentes, duas regras no mesmo validador com prioridades diferentes, condição com campo vazio, validador sem regra; nenhuma proposta alterada | QA | [A CONFIRMAR] | Roteiro com resultado por caso | Todos os casos aprovados; reprovação marcada com QA-REJECTED |
| QA Teste · registro | Registro não editável nem excluível; nova avaliação não sobrescreve a anterior | QA | [A CONFIRMAR] | Roteiro | Aprovado. Não está no DS-508: incluir **[ALÉM DA FONTE — decisão do usuário]** |
| QA Teste · E2 | Critérios de aceite do DS-505, DS-506, DS-507 e DS-509, inclusive a máscara do CPF por perfil | QA | [A CONFIRMAR] | Roteiro | Cenários de teste ainda não escritos nos cards [A CONFIRMAR] |
| Regressão | Fluxos da tela Administração de Quitação (Fase 1) | QA | [A CONFIRMAR] | Lista de fluxos e resultado | Nenhuma regressão aberta |
| Aprovação POs | Critérios de aceite do PRD, seção 6 | PO com o Financeiro | [A CONFIRMAR] | Registro no Jira | Aceite da área |

Massa de teste: propostas fictícias, válidas no formato, nunca copiadas de produção. Linha de base do fluxo: média de 41h em QA Teste na Sprint 18, contra 7h na Sprint 17; 66% do ciclo mediano depois do código pronto (Review da Sprint 18, 06/11/2026 16h46). O DS-508 concentra a maior parte do teste do motor num só card.

---

## 8. Rollback

| Entrega | Gatilho para reverter | Como reverter | Tempo estimado | Quem decide (papel) | Dado criado no período: o que fazer |
|---|---|---|---|---|---|
| E1 | Proposta com situação ou status alterado após execução, ou avaliação registrada para proposta fora da RN01 | Desligar a execução agendada e voltar à conferência por planilha; se necessário, voltar a versão anterior pelos passos de reversão dos cards | [A CONFIRMAR] | Tech lead | Manter os registros, marcados como inválidos para a comparação **[ALÉM DA FONTE — decisão do usuário]** |
| E2 | Tela ou exportação exibindo CPF sem a máscara do perfil | Retirar a aba e o botão de exportação pela versão anterior | [A CONFIRMAR] | Tech lead com o PO | Nenhum dado novo; arquivos exportados no período recolhidos [A CONFIRMAR com o DPO] |

Como desligar a execução agendada sem novo deploy: [A CONFIRMAR].

---

## 9. Comunicação

| Momento | Público | Mensagem | Canal | Responsável (papel) |
|---|---|---|---|---|
| Antes do deploy da E1 | Financeiro | O motor começa a avaliar as propostas em modo sombra; a planilha continua sendo a base da decisão | [A CONFIRMAR] | PO |
| Depois do deploy da E2 | Financeiro | Onde fica a aba "Avaliação do motor", como exportar e como registrar divergência entre motor e planilha | [A CONFIRMAR] | PO |
| Em caso de rollback | Financeiro e time do Konsig | O que foi desligado, desde quando, e que a conferência volta a ser só pela planilha | [A CONFIRMAR] | Tech lead |

---

## 10. Riscos

| ID | Risco | Probabilidade | Impacto | Mitigação | Dono (papel) |
|---|---|---|---|---|---|
| R01 | Fase 1 não concluída e ajustes sem card bloqueiam o início da E1 | A | A | Abrir os cards dos ajustes no DS-418 | PO |
| R02 | Espera em QA (41h na S18) empurra a Fase 2 para além da referência típica | M | A | Escrever os cenários de teste no refinamento | QA |
| R03 | Responsáveis vazios nos cards (regra 2 do experimento S19): o card não avança | A | M | Preencher no refinamento | PO |
| R04 | Execução agendada sem desempenho definido pode deixar o Konsig lento no horário da execução | M | M | Medir em homologação com volume representativo [A CONFIRMAR] | Tech lead |
| R05 | Concentração: uma única pessoa desenvolvendo as quatro fases da Quitação (Previsão de entregas V02, 06/11/2026) | M | A | Par de revisão fixo e decisões registradas no PRD | Tech lead |

Probabilidade e impacto são avaliação deste exemplo **[ALÉM DA FONTE — decisão do usuário]**.

---

## 11. Datas estimadas (régua)

| Entrega | Classe | Início previsto | Referência típica (dias úteis) | Referência conservadora (dias úteis) | Fim previsto (típico) | Fim previsto (conservador) |
|---|---|---|---|---|---|---|
| Upstream | — | — | Não se aplica: US-69 concluído em 26/10/2026 | — | — | — |
| Épico DS-500 (E1 + E2) | M | 04/01/2027 | 16 | 29 | 26/01/2027 | 12/02/2027 |

Premissas:

- **Início:** jan/27, posição da Fase 2 no pool de 2027, depois da Fase 1, também em jan/27 (`D1-pool/pool-2027-plano.xlsx`, aba Pool 2027, linhas 5 e 6). Primeiro dia útil de janeiro **[ALÉM DA FONTE — decisão do usuário]**.
- **Convenção de contagem:** o dia de início não conta; fim = início + N dias úteis, segunda a sexta (a mesma do modelo, seção 11) **[ALÉM DA FONTE — decisão do usuário: a régua não define a convenção]**.
- **Referência:** a régua mede o épico inteiro, do primeiro card criado ao último concluído; não há referência por entrega. PP, P e M usam a mesma referência (`D1-pool/regua-tamanho-tempo.md`, v1, seção 3). As faixas são proposta, sem decisão do comitê.
- **Esforço:** 8 cards ÷ 3,25 cards de projeto por dev por sprint = cerca de 2,5 dev-sprints; capacidade de projeto do Konsig de 8,25 cards de épico por sprint (S15–S18) (`pool-2027-plano.xlsx`, abas Capacidade por dev e Leia primeiro).
- **Não considerado:** feriados, recesso e férias; o pool registra que suas datas "não modelam férias nem a espera em QA" (aba Leia primeiro).
- **Se o desenvolvimento começar antes de jan/27:** vale a regra 3 da régua (seção 4): o épico em andamento conta a partir do primeiro card criado (09/11/2026). Em 16/11/2026, restariam 11 dias úteis no típico (até 01/12/2026) e 24 no conservador (até 18/12/2026). Esse cálculo só vale se a Fase 1 for concluída e o DS-500 entrar em sprint na S20, o que nem a extração nem o pool indicam.

Leitura: pela referência conservadora, a Fase 2 termina em 12/02/2027, dentro do mês em que o pool põe as Fases 3 e 4 ("Quitação: fev/27"). Se a Fase 2 passar da referência típica, a data de fev/27 da Quitação não se sustenta.

---

## 12. Critério de pronto do plano

O plano é considerado concluído quando todos os itens abaixo forem verdadeiros:

- [ ] Os 8 cards (ou 7, se a pendência "Duas exportações" do PRD, seção 7, unificar o DS-507 e o DS-509) estão em Concluído, com Categorias, Descrição, Classe de serviço e Tipo preenchidos (regra 3 do experimento S19).
- [ ] O DS-508 foi aprovado com evidência de que nenhuma proposta foi alterada após as execuções.
- [ ] Os critérios de aceite do PRD, seção 6, foram aceitos pelo Financeiro.
- [ ] A tabela de decisão da seção 12 do PRD tem um teste aprovado por linha, e o teste de imutabilidade do registro (RN05) foi incluído.
- [ ] E1 e E2 estão em produção, e o rollback não foi acionado, ou foi acionado e encerrado com registro.
- [ ] Os vínculos GDP-76 ↔ US-69 ↔ DS-500 existem no Jira.
- [ ] O realizado foi registrado ao lado do estimado: 8 cards previstos × cards de fato; 16 e 29 dias úteis × dias úteis realizados (registro da régua).
- [ ] O status do PRD e deste plano foi alterado para Concluído.
