<!--
MODELO · Plano de Implementação · Kit de documentação TI Neo Crédito · v1.0 · 16/11/2026 · proposta
Como usar: copie para docs/planos/<chave do épico DS>_plano-<assunto>.md no repositório do sistema afetado.
Pré-requisito: PRD aprovado (ou, em PP/P, item de origem identificado). ADRs da demanda em status Aceito.
Um Plano por épico. Em GG: um Plano por entrega, cada entrega com seu épico.
Plano curto (tamanho M): seções 1, 2, 3, 4, 5, 7, 8, 9, 11 e 12 obrigatórias; as demais podem ser "Não se aplica: <motivo>".
As seções 5 (Ambientes e deploy) e 8 (Rollback) são obrigatórias em todo Plano, de qualquer tamanho: o README atribui ao Plano o deploy e o rollback (seção 2, etapa 9), e no Konsig, sem CI/CD (US-43), o deploy manual é o principal risco técnico (insumos/sistemas-e-tecnologias.md, ponto de atenção A1).
Apague os blocos "Orientação" antes de enviar para aprovação.
-->

# Plano de Implementação · <Nome da entrega>

## 1. Identificação

| Campo | Valor |
|---|---|
| Sistema | <**Konsig** (legado) **ou** **NeoKonsig** (reescrita) ou outro sistema do Inventário. Um único sistema.> |
| Épico | <DS-n> |
| PRD de origem | `docs/prd/<arquivo>` · versão <x.y> |
| ADRs aplicáveis | <ADR-nnnn (Aceito), ...> |
| Item GDP / Upstream | <GDP-n / US-n> |
| Tamanho pela régua | <classe e número de cards> |
| Status | <Rascunho · Aprovado · Em execução · Concluído · Cancelado> |
| Responsável pelo plano | <papel: tech lead> |
| Aprovação | <papel: PO> · <dd/mm/aaaa> |

### Versionamento

| Data | Responsável (papel) | Versão | Descrição da alteração |
|---|---|---|---|
| <dd/mm/aaaa> | <tech lead> | 0.1 | Elaboração do plano. |

---

## 2. Entregas

| # | Entrega | O que fica verificável ao final | Regras do PRD cobertas | Cards previstos | Tamanho |
|---|---|---|---|---|---|
| E1 | <nome> | <o que a área de negócio consegue ver ou testar> | <RN01, RN02> | <n> | <PP · P · M> |
| E2 | | | | | |

> **Orientação.** Entra: entregas que, cada uma sozinha, produzem algo que alguém fora do time consegue verificar. Não entra: entregas por camada técnica ("back-end", "front-end") ou "parte 1 / parte 2" sem resultado próprio (guia InnoviaX, seção 06, "Como não quebrar"). Uma entrega G deve ser avaliada para quebra em M; uma entrega GG não entra no plano sem ser quebrada (`D1-pool/regua-tamanho-tempo.md`, seções 3 e 6).
>
> **Exemplo (Quitação Fase 2, Konsig, DS-500):** E1 · Motor em modo sombra: captura das propostas, aplicação das regras com decisão final registrada e teste do motor (DS-501, DS-503, DS-504, DS-508) · verificável pela consulta do registro de avaliação · P (4 cards). E2 · Visualização e exportação: lista, detalhe e exportação (DS-505, DS-506, DS-507, DS-509) · verificável pela área Financeiro na tela · P (4 cards). Total: 8 cards, épico M. O card de teste (DS-508) fica dentro da entrega que ele prova; ele não é uma entrega própria.

---

## 3. Sequência e dependências

| Entrega | Depende de | Tipo de dependência | Situação |
|---|---|---|---|
| E1 | <entrega, ADR, ambiente, parceiro> | <técnica · negócio · externa> | <resolvida · aberta: dono e data> |

> **Orientação.** Entra: a ordem e o motivo da ordem. Dependência externa (parceiro, outra área) sempre com dono e data. Não entra: tarefas internas do time.
>
> **Exemplo:** E1 depende da Fase 1 concluída, com os ajustes do teste de 09/11/2026 na tela de Administração (pré-requisito declarado no DS-500) · negócio · aberta: DS-415 em Code Review e DS-416 em Em desenvolvimento na extração de 16/11/2026 10h26.

---

## 4. Épicos e cards previstos

| Entrega | Card (título: verbo + objeto) | Tipo | Critério de quebra usado (seção 06 do guia) | Referência no PRD | Chave DS |
|---|---|---|---|---|---|
| E1 | <título> | <História · Tarefa · Bug (Spike e Teste registrados como Tarefa [A CONFIRMAR])> | <regra de negócio · tipo de documento ou fluxo · caminho · etapa do processo> | <RN01, seção 10> | <DS-n, após criação> |

> **Orientação.** Entra: todos os cards previstos, com o critério de quebra usado. Use os quatro critérios do guia: por regra de negócio (preferencial), por tipo de documento ou fluxo, por caminho (feliz primeiro, falha depois, só se o caminho feliz puder ir para produção com segurança) e por etapa do processo. Confira cada card contra os sinais de card grande da seção 06: mais de sete cenários, título que precisa de "e", mais de um perfil na história, parte dependente de decisão inexistente. Não entra: subtarefa como card (subtarefa divide trabalho, não entendimento, guia seção 07).
>
> Tipos no Jira: o Downstream tem Tarefa, História, Bug, Subtask e Epic (`downstream_16-11.csv`, 16/11/2026 10h26). Spike e Teste do guia são registrados como Tarefa, com o prefixo no título **[A CONFIRMAR com o administrador do Jira]** (ver `modelos/CARD.md`, seção 1).
>
> Regras do experimento em vigor desde a Sprint 19 (`contexto-mestre.md`, seção 4): História só é criada pelo PO; demanda nova entra como Tarefa; cada etapa do Downstream exige responsável; o card só vai para Concluído com Categorias, Descrição, Classe de serviço e Tipo preenchidos.
>
> **Exemplo:** E1 · "Aplicar as regras parametrizadas por prioridade e definir a decisão final" · História · por regra de negócio · RN da tabela de decisão · DS-503.

---

## 5. Ambientes e deploy

| Item | Konsig | NeoKonsig |
|---|---|---|
| Pipeline de CI/CD | **Não existe** (US-43, Backlog, `upstream_16-11.csv`, 16/11/2026 9h51) | [A CONFIRMAR no Inventário de Sistemas] |
| Ambientes disponíveis | [A CONFIRMAR no Inventário de Sistemas] | [A CONFIRMAR no Inventário de Sistemas] |
| Homologação dedicada | [A CONFIRMAR] | [A CONFIRMAR] |
| Padrão de release | Sem padrão; adoção do DS-550 no Konsig [A CONFIRMAR] (o DS-550, em Backlog, começa pelo Keycloak; `insumos/sistemas-e-tecnologias.md`, A1) | Em definição no DS-550 (Backlog) [A CONFIRMAR o alcance no NeoKonsig] |

> **Orientação.** Preencha **apenas a coluna do sistema deste plano** e apague a outra. Entra: ambiente em que cada entrega é testada e por onde passa até a produção; passos manuais de deploy, um por linha, com quem executa (papel); janela de implantação; a etapa Waiting for deploy do Downstream e quanto tempo se espera nela. Não entra: credenciais, endereços de servidor, identificadores de conta.
>
> No Konsig, como não há pipeline, o plano descreve o deploy manual passo a passo e o que é conferido depois de cada passo. Esse é o principal risco técnico de construção nova no legado (`insumos/sistemas-e-tecnologias.md`, ponto de atenção A1).
>
> **Exemplo (Konsig):** 1 · Tech lead gera o pacote a partir do branch principal revisado. 2 · Infraestrutura aplica em [ambiente A CONFIRMAR]. 3 · QA executa a regressão manual dos fluxos de quitação. 4 · PO libera para produção. [ALÉM DA FONTE — decisão do usuário: sequência ilustrativa; o procedimento real depende do Inventário e do DS-550.]

---

## 6. Migração de dados

| Item | Resposta |
|---|---|
| Há carga, conversão ou correção de dado existente? | <Não · Sim> |
| Origem e destino | <tabela/sistema de origem → destino, sem dado real> |
| Volume estimado | <ordem de grandeza> |
| Validação | <contagem antes × depois, amostra conferida pela área> |
| Dado pessoal envolvido | <categorias; regra de mascaramento; parecer do DPO quando houver transferência a terceiro> |
| Reversão | <como desfazer> |

> **Orientação.** Entra: qualquer alteração em dado que já existe em produção, inclusive carga inicial de parametrização. Não entra: exemplo com dado real. Em integração entre Konsig e NeoKonsig, registrar qual sistema é a fonte única do dado; essa delimitação ainda está em aberto (`insumos/sistemas-e-tecnologias.md`, ponto de atenção A6).
>
> **Exemplo:** Quitação Fase 2: Não se aplica. O motor só lê propostas e regras e grava o registro novo da avaliação; não altera dado existente (modo sombra, DS-500).

---

## 7. Plano de teste

| Nível | O que cobre | Quem executa (papel) | Ambiente | Evidência | Critério de aprovação |
|---|---|---|---|---|---|
| Teste do desenvolvedor | Regras de cada card | Dev | <ambiente> | Testes automatizados no pull request | Testes passando no Code Review |
| QA Teste | Cenários de teste dos cards (bloco 7), caminhos feliz, alternativo, borda e falha | QA | <ambiente> | Roteiro executado com resultado por cenário | Todos os cenários aprovados; reprovação marcada com QA-REJECTED |
| Regressão | Fluxos existentes afetados | QA | <ambiente> | Lista de fluxos e resultado | Nenhuma regressão aberta |
| Aprovação POs / homologação | Critérios de aceite do PRD (seção 10) | PO com a área solicitante | <ambiente> | Registro no Jira | Aceite da área |

> **Orientação.** Entra: o que é testado, por quem, onde e o que conta como evidência. A massa de teste é sintética: dado fictício, válido no formato, nunca copiado de produção. Não entra: repetição dos cenários dos cards; aqui se planeja, nos cards se detalha. Se não houver ambiente de homologação dedicado, registrar onde a validação ocorre e o risco, como o guia faz no DoD do card A1 (seção 08).
>
> Linha de base do fluxo a observar: na Sprint 18, a média em QA Teste foi 41h e havia 14 itens em Aprovação POs; 66% do ciclo mediano aconteceu depois do código pronto (Review da Sprint 18, extração de 06/11/2026 16h46).

---

## 8. Rollback

| Entrega | Gatilho para reverter | Como reverter | Tempo estimado | Quem decide (papel) | Dado criado no período: o que fazer |
|---|---|---|---|---|---|
| E1 | <sintoma observável> | <versão anterior, desativação por parâmetro, script> | <minutos ou horas> | <tech lead · PO> | <manter, descartar, corrigir> |

> **Orientação.** Entra: um rollback por entrega que vai para produção, decidido antes do deploy. Não entra: "reverter se der problema". Quando não há rollback possível (por exemplo, pagamento já enviado a banco), dizer isso e descrever a contingência operacional.
>
> **Exemplo:** E1 · motor registrando decisão para proposta fora de AND - AGUARD QUITACAO · desativar a execução do motor e voltar à conferência por planilha · [A CONFIRMAR] · tech lead · manter os registros, marcados como inválidos para a comparação.

---

## 9. Comunicação

| Momento | Público | Mensagem | Canal | Responsável (papel) |
|---|---|---|---|---|
| Antes do deploy | <área solicitante, atendimento> | <o que muda, quando, o que fazer se algo falhar> | <canal> | <PO> |
| Depois do deploy | | | | |
| Em caso de rollback | | | | |

> **Orientação.** Entra: quem precisa saber antes, durante e depois, e o que fazer. Não entra: lista de distribuição com nomes ou e-mails.

---

## 10. Riscos

| ID | Risco | Probabilidade | Impacto | Mitigação | Dono (papel) |
|---|---|---|---|---|---|
| R01 | <evento e consequência> | <A · M · B> | <A · M · B> | <ação> | <papel> |

> **Orientação.** Entra: riscos de execução (prazo, ambiente, dependência externa, concentração de conhecimento). Os riscos de produto ficam no PRD; não repetir. Concentração é registrada pelo papel, não pela pessoa.
>
> **Exemplo:** R01 · Uma única pessoa desenvolvendo as quatro fases da Quitação (Previsão de entregas V02, 06/11/2026): ausência atrasa todas as entregas · M · A · par de revisão fixo e registro das decisões no PRD · tech lead.

---

## 11. Datas estimadas (régua)

| Entrega | Classe | Início previsto | Referência típica (dias úteis) | Referência conservadora (dias úteis) | Fim previsto (típico) | Fim previsto (conservador) |
|---|---|---|---|---|---|---|
| Upstream (se ainda não concluído) | — | <data> | 29 | 44 | <data> | <data> |
| E1 | <PP · P · M> | <data> | 16 | 29 | <data> | <data> |
| E2 | <G> | <data> | 66 (piso) | 86 | <data> | <data> |

> **Orientação.** Fonte: `D1-pool/regua-tamanho-tempo.md`, versão 1, 16/11/2026, medida do primeiro card criado ao último card concluído do épico, em dias úteis (10 dias úteis = 1 sprint). **Faixas e referências são proposta, sem decisão do comitê.** PP, P e M usam a mesma referência, porque os dados não sustentam prazos diferentes entre elas. GG não tem referência: quebrar antes. Para épico já em andamento, se o tempo decorrido passou da referência, usar o ritmo do próprio épico: cards abertos × dias decorridos ÷ cards concluídos.
>
> Não entra: estimativa em pontos ou Fibonacci, que não são prática atual. A data de início vem da posição da demanda no pool de 2027, não do desejo da área.
>
> **Exemplo:** Quitação Fase 2 (M, 8 cards). Premissa de início: jan/27, posição da Fase 2 no pool de 2027 (`D1-pool/pool-2027-plano.xlsx`, aba Pool 2027, linha 6); primeiro dia útil, 04/01/2027 **[ALÉM DA FONTE — decisão do usuário]**. Fim típico: início + 16 dias úteis = 25/01/2027. Fim conservador: início + 29 dias úteis = 11/02/2027. Feriados e recesso não descontados. Se o desenvolvimento começar antes, vale a regra 3 da régua (seção 4): o épico em andamento conta a partir do primeiro card criado (09/11/2026); em 16/11/2026 restariam 11 dias úteis no típico (até 01/12/2026) e 24 no conservador (até 18/12/2026). O exemplo preenchido (`exemplos/quitacao/DS-500_plano-quitacao-fase-2.md`) usa a mesma premissa.

---

## 12. Critério de pronto do plano

O plano é considerado concluído quando todos os itens abaixo forem verdadeiros:

- [ ] Todos os cards das seções 2 e 4 estão em Concluído no Jira, com Categorias, Descrição, Classe de serviço e Tipo preenchidos (regra 3 do experimento S19).
- [ ] Todos os critérios de aceite do PRD (seção 10) foram aceitos pela área solicitante.
- [ ] A matriz de rastreabilidade do PRD (seção 15) está completa: toda regra tem card e teste.
- [ ] As entregas estão em produção e o rollback não foi acionado, ou foi acionado e encerrado com registro.
- [ ] Os documentos listados na seção 6 dos ADRs aplicáveis foram atualizados.
- [ ] O realizado foi registrado ao lado do estimado: cards previstos × cards de fato e dias úteis previstos × realizados (registro da régua, que alimenta o experimento de previsão das Sprints 20 a 22 previsto no `contexto-mestre.md`, seção 7).
- [ ] O status do PRD e deste plano foi alterado para Concluído.
