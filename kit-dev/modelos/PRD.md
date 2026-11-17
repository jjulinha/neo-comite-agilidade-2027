<!--
MODELO · Documento de Requisitos de Produto (PRD) · Kit de documentação TI Neo Crédito · v2.0 · 17/11/2026 · proposta
Substitui o PRD.md v1.0 (16/11/2026). A escolha de trilha e toda a estrutura em dois níveis são [ALÉM DA FONTE — decisão do usuário].
A régua PP/P/M/G/GG é proposta sem decisão (D1-pool/regua-tamanho-tempo.md, v1, 16/11/2026).
-->

# Modelo de PRD (núcleo + completo)

O PRD diz **o quê e por quê** de uma demanda. Serve a dois leitores ao mesmo tempo: a área solicitante, que aprova, e o agente de IA, que o recebe como contexto junto com o card. Por isso as regras são numeradas e escritas em EARS, e os critérios em Dado/Quando/Então.

Convenções do kit, mantidas do v1:
- **Um documento, um sistema.** Konsig (legado) e NeoKonsig (reescrita) nunca dividem o mesmo PRD. Integração entre os dois é integração entre sistemas distintos.
- **[A CONFIRMAR]**: deveria existir em documento oficial e não foi recebido.
- **[ALÉM DA FONTE — decisão do usuário]**: não está em nenhuma fonte; é proposta de quem escreveu.

## Quando usar / quando não usar

| Trilha (tamanho provisório) | PRD | O que preencher |
|---|---|---|
| **PP** (1–2 cards) | **Não usa.** Só o CARD.md no modelo do tipo. | Gatilho de **dinheiro** promove a demanda para P: PRD núcleo com a seção 12 (tabela de decisão) e RN em EARS. |
| **P** (3–4 cards) | **Núcleo** (seções 1 a 7). Pode morar no épico do Jira ou em `docs/`. | Sem Plano. |
| **M** (5–9 cards) | **Núcleo** (seções 1 a 7). | Mais o Plano curto. |
| **G** (10–20 cards) | **Completo** (núcleo + seções 8 a 15). Apetite recomendado. | Plano completo. A régua manda quebrar GG em entregas G ou M (`regua-tamanho-tempo.md`, seção 3) e recomenda estender a quebra ao G, decisão pendente (seção 7). |
| **GG** (mais de 20) | **Completo**, com **apetite obrigatório**. | Plano completo; "Desenho e alternativas" no Plano se houver integração nova ou trade-off real. |

- **Tamanho antes do PRD.** Use o tamanho do `D1-pool/pool-2027-plano.xlsx` ou estime pela descrição. Na dúvida, comece pela trilha mais leve e **promova o documento** (núcleo → completo) quando a contagem de cards subir. Não espere o PRD para saber o tamanho.
- **Gatilhos que se somam ao PRD**, em qualquer tamanho: integração nova ou alterada → `CONTRATO-DE-INTEGRACAO.md`; dado pessoal → `CHECKLIST-DADOS-E-REGULACAO.md`; dinheiro → tabela de decisão (seção 12) com um teste por linha + ADR + seção Corte do Plano com go/no-go na primeira ida a produção; decisão difícil de reverter → `ADR.md`.
- **Não use o PRD para:** decisão técnica (vai no ADR), passo de entrega, deploy ou rollback (vai no Plano), detalhe de um card (vai no CARD.md), RIPD (é do DPO, não do dev).

**Onde fica.** `docs/prd/<chave>_<assunto>.md` no repositório do sistema. A área solicitante lê e aprova em PDF ou link do Drive que aponta para a versão do repositório (seção 7). Enquanto o repositório do Konsig que recebe `docs/` estiver [A CONFIRMAR] (DS-175/DS-495), use a pasta provisória definida no README do kit.

**Uso com IA.** O PRD vai no contexto do agente junto com o card (e o Plano, quando houver): é dele que o agente tira as RN e os cenários. O nível é *spec-anchored* (Böckeler, martinfowler.com): o documento fica vivo ao lado do código, e **quem muda o comportamento atualiza o PRD no mesmo PR**. Mudança de escopo sobe a versão (seção 7). A IA não escreve no Jira.

---

## Cópia em branco · núcleo (P e M)

Copie o bloco abaixo inteiro. Não tem orientação para apagar: as orientações estão no fim deste arquivo. Seção que não se aplica: `Não se aplica: <motivo em uma linha>`.

~~~markdown
# <Título: verbo + objeto>

## 1. Cabeçalho
| Sistema (um só) | Chave Jira | Natureza | Status · versão |
|---|---|---|---|
| <Konsig ou NeoKonsig> | <GDP-n · US-n · DS-n> | <Potencial financeiro · Gera atendimento · Reduz fluxo operacional> | <Rascunho · Em revisão · Aprovado · Em execução · Concluído · Substituído> · v0.1 |

Atividade regulatória (natureza no Jira Downstream, só se for): norma de origem <norma, artigo> · data de vigência <dd/mm/aaaa>
Dados e regulação: responda CHECKLIST-DADOS-E-REGULACAO.md e cole aqui as respostas sim/não.

## 2. Problema e por que agora
<Como é hoje, quem é afetado, o que dá errado, consequência observada. Por que agora: data, norma, risco.>

## 3. Objetivo e métrica de sucesso
| Objetivo | Métrica | Linha de base (fonte, data) | Meta |
|---|---|---|---|
| <o que muda para o negócio> | <fórmula> | <valor, fonte, data> ou [A CONFIRMAR] | <valor> |

## 4. Não objetivos e fora do escopo
Não objetivos (poderiam ser objetivo e foram descartados):
- <...>

| Fora do escopo | Onde será tratado |
|---|---|
| <item que alguém suporia incluído> | <fase n, GDP-n, não será feito> |

## 5. Regras de negócio (EARS)
| RN | Regra | Origem |
|---|---|---|
| RN01 | QUANDO <gatilho>, o <sistema> DEVE <resposta>. | <norma, card, decisão com data> |
| RN02 | SE <condição indesejada>, ENTÃO o <sistema> DEVE <resposta>. | <...> |

## 6. Critérios de aceite
```gherkin
Cenário: <caminho feliz> (RN01)
  Dado que <estado inicial>
  Quando <uma ação>
  Então <resultado observável>

Cenário: <falha> (RN02)
```

## 7. Dependências, perguntas em aberto e aprovação
| Pendência ou pergunta | Quem responde (papel) | Até quando | Bloqueia? |
|---|---|---|---|
| <...> | <papel> | <dd/mm/aaaa> | <Sim · Não> |

| Versão | Data | Mudança | Aprovada por (papel, área) | Onde (PDF ou link do Drive) |
|---|---|---|---|---|
| 0.1 | <dd/mm/aaaa> | Elaboração | — | — |
~~~

## Cópia em branco · seções do completo (G e GG)

Cole depois da seção 7 do núcleo.

~~~markdown
## 8. Apetite
<Teto de tempo que a área aceita pagar, decidido antes da solução: n semanas ou n sprints. Se a estimativa passar disso, corta-se escopo.>

## 9. Perfis
| Perfil (acesso no sistema) | Pode | Não pode |
|---|---|---|
| <perfil> | <ações> | <restrições> |

## 10. Fluxo atual × proposto
| # | Etapa | Hoje | Proposto | Responsável (área ou sistema) |
|---|---|---|---|---|
| 1 | <etapa> | <manual, planilha, sistema> | <o que muda> | <...> |

Esteira (máquina de estados), quando for o caso:
| Estado de origem | Evento ou gatilho | Estado de destino | Quem dispara | Exceção |
|---|---|---|---|---|
| <situação + atividade> | <...> | <...> | <perfil, sistema, rotina> | <paradinha, retorno, reanálise> |

## 11. Requisitos não funcionais (EARS)
| RNF | Categoria | Requisito | Origem |
|---|---|---|---|
| RNF01 | <Segurança · Auditoria · LGPD · Desempenho · Falha> | ENQUANTO <estado>, o <sistema> DEVE <resposta mensurável>. | <...> |

## 12. Tabela de decisão
| Linha | <Condição A> | <Condição B> | Decisão | Precedência | Vigência da regra (RN, versão, início–fim) | Caso de teste |
|---|---|---|---|---|---|---|
| 1 | <valor> | <valor> | <DECISAO> | <1 = vence> | <RN0n, v1, dd/mm/aaaa–> | T1 |

## 13. Integrações
| Contraparte | Sentido | Meio | Contrato |
|---|---|---|---|
| <parceiro ou sistema> | <envio · recebimento · ambos> | <API · SFTP · fila> | [CONTRATO-DE-INTEGRACAO](<link>) |

## 14. Riscos
| ID | Risco (evento → consequência) | Prob. | Impacto | Mitigação | Dono (papel) |
|---|---|---|---|---|---|
| R01 | <...> | <A · M · B> | <A · M · B> | <...> | <papel> |

## 15. Rastreabilidade
| RN / RNF / linha da tabela | Card(s) | Caso(s) de teste |
|---|---|---|
| RN01 | DS-n | T1 |
~~~

---

## Orientações por seção

Padrão de cada item: **Entra** (o que precisa estar), **Não entra** (o que sobra ou está no lugar errado), **Caso Neo** (o que aconteceu num projeto real e o que a seção evita).

### 1. Cabeçalho

- **Entra:** um único sistema; a chave do Jira que representa a demanda (GDP-n; ou US-n/DS-n quando não houver GDP); a natureza, nas opções da Visão do Cartão v6 (Potencial financeiro · Gera atendimento · Reduz fluxo operacional); status e versão. O roteiro do GDP não tem campo de natureza.
- **Não confunda com o campo "natureza" do Jira Downstream:** é outro vocabulário (Nova funcionalidade, Arquitetura, Melhoria, Débito técnico, Chamado, Atividade regulatória) (`downstream_16-11.csv`, 16/11/2026 10h26). Demanda regulatória usa o valor "Atividade regulatória" de lá, preenchido no Jira.
- **Atividade regulatória:** norma de origem e data de vigência são obrigatórias no PRD. A data de vigência casa com a classe de serviço "Fixed Date" no Jira (`contexto-mestre.md`, Classes de serviço).
- **Dados e regulação:** não repita aqui as perguntas do checklist. Cole só as respostas sim/não. Se alguma resposta acionar o DPO ou Segurança & Conformidade, isso vira pendência na seção 7.
- **Não entra:** prioridade, solicitante, datas de abertura, épicos, classe de serviço, responsável. Tudo isso já está no Jira; o v1 pedia o mesmo metadado no PRD, no Plano, no ADR, no card e no Jira. Nunca nome de pessoa.

### 2. Problema e por que agora

- **Entra:** situação atual verificável, inclusive passos manuais e fora do sistema; consequência observada; por que fazer agora (data de norma, risco, decisão). Três a dez linhas. Reaproveite o roteiro de abertura do GDP.
- **Não entra:** a solução; adjetivo sem fato ("processo ruim").
- **Caso Neo:** 56 de 90 itens do GDP trazem o texto-modelo vazio idêntico; 57 contando o GDP-6, que repete o modelo com asteriscos (`gdp_16-11.csv`, 16/11/2026 9h51), entre eles GDP-83 (Cobmais Parte 2) e GDP-132 (NMP). Sem problema escrito, a demanda não tem como ser dimensionada.

### 3. Objetivo e métrica de sucesso

- **Entra:** um a três objetivos de negócio, cada um com métrica que se mede sem abrir o código. Toda linha de base cita fonte e data; se não existe, [A CONFIRMAR] e o papel de quem mede.
- **Não entra:** objetivo técnico ("migrar para a versão X"), que vai para o ADR; meta sem linha de base.

### 4. Não objetivos e fora do escopo

São duas coisas diferentes:
- **Não objetivo** (Google design docs; modelo de Kevin Yien): algo que *poderia razoavelmente* ser objetivo e foi descartado de propósito. Ex.: "Não é objetivo da Fase 2 reduzir o tempo do Financeiro; é comparar a decisão do motor com a da planilha".
- **Fora do escopo:** item que alguém suporia incluído, sempre com a coluna **onde será tratado** (fase, outro GDP, "não será feito"). É o que permite recusar acréscimo depois.
- **Não entra:** lista de telas ou de tabelas; "onde será tratado" em branco.
- **Caso Neo (escopo esquecido):** o DS-500 diz "Os efeitos (RF23, RF24, RF2, RF5) ficam para a Fase" e não diz qual fase nem o escopo dela (`downstream_16-11.csv`, 16/11/2026 10h26). A coluna "onde será tratado" com o número da fase teria fechado isso.
- **Caso Neo (escopo sem origem):** DS-507 e DS-509 são duas exportações, e o DS-509 diz "A exportação não consta no Documento de Requisitos V04" (mesma fonte). Ou entra no PRD com RN e origem, ou vai para o fora do escopo.

### 5. Regras de negócio (EARS)

- **Entra:** uma regra por linha, **número estável** (não muda entre versões; regra removida fica riscada, com a versão em que saiu) e **origem por linha** (norma, card, decisão com data, área). São estes números que os cards citam.
- **Redação EARS** (Easy Approach to Requirements Syntax, Mavin et al., Rolls-Royce, IEEE RE'09). A tradução das palavras-chave é [ALÉM DA FONTE — decisão do usuário]. Ordem fixa das cláusulas: `ENQUANTO <pré-condição>, QUANDO <gatilho>, o <sistema> DEVE <resposta>`.

| Padrão | Forma | Exemplo |
|---|---|---|
| Ubíquo (sempre vale) | O <sistema> DEVE <resposta>. | O motor DEVE avaliar apenas propostas da esteira Cartão Consignado Compra na situação AND - AGUARD QUITACAO. (DS-501) |
| Por evento | QUANDO <gatilho>, o <sistema> DEVE <resposta>. | QUANDO o motor avaliar uma proposta sem regra vigente, o sistema DEVE registrar a decisão ANALISE_MANUAL com o motivo. [ALÉM DA FONTE — decisão do usuário: ilustrativo] |
| Por estado | ENQUANTO <estado>, o <sistema> DEVE <resposta>. | ENQUANTO o motor estiver em modo sombra, o sistema NÃO DEVE alterar situação nem status da proposta. (DS-500)<br>ENQUANTO o perfil do usuário não tiver permissão de ver CPF, a exportação DEVE trazer o CPF mascarado. (DS-507, DS-509; RNF 3) |
| Opcional (recurso do produto incluído ou não) | ONDE <recurso ou configuração existir>, o <sistema> DEVE <resposta>. | ONDE a exportação em Excel estiver habilitada, a tela de avaliação do motor DEVE exibir o botão "Exportar Excel". [ALÉM DA FONTE — decisão do usuário: ilustrativo] |
| Comportamento indesejado | SE <condição indesejada>, ENTÃO o <sistema> DEVE <resposta>. | SE a importação diária falhar nas 3 tentativas, ENTÃO o sistema DEVE notificar via Teams e manter a base anterior. (DS-98: 3 tentativas antes das 07h, notificar via Teams; manter a base anterior em caso de falha é [ALÉM DA FONTE — decisão do usuário: ilustrativo]) |

- **Não entra:** comportamento de tela; regra sem origem; regra "por referência" sem conteúdo.
- **Caso Neo (regra citada sem conteúdo):** o DS-393 (NMP) diz que o sistema "deve aplicar a regra de precedência definida" para CPF presente nas listas de bloqueio e de desbloqueio, e a regra não está no card (`downstream_16-11.csv`, 16/11/2026 10h26). No PRD, essa regra é uma RN em EARS com origem, ou uma linha com precedência na tabela de decisão (seção 12).
- **EARS garante regra bem escrita, não regra certa.** Quem confirma a regra é a área solicitante, na aprovação.

### 6. Critérios de aceite

- **Entra:** cenários Dado/Quando/Então só para **comportamento observável**: caminho feliz, alternativo, borda e falha. Cada cenário cita a RN que prova. Os cards herdam daqui; o cenário com dado concreto fica no card.
- **EARS e cenário não são a mesma coisa:** EARS diz **o que deve valer**; o cenário diz **como testar**. Uma RN pode ter vários cenários.
- **Não entra:** RNF em Gherkin (desempenho, segurança e auditoria ficam na seção 11 em EARS); advérbio ("rapidamente"); detalhe de implementação; critério que não vira teste.

### 7. Dependências, perguntas em aberto e aprovação

- **Entra:** o que não depende do time, sempre com dono (papel) e data; pergunta em aberto com quem responde; o histórico de versões com a aprovação de cada uma.
- **Versão:** 0.x em rascunho; 1.0 na aprovação; 1.x ajuste sem mudança de escopo; **2.0 mudança de escopo**, que reabre a aprovação e exige revisar os cards que citam a versão anterior (regra do v1).
- **Como a área aprova fora do Git:** exporte o PRD em PDF (ou publique no Drive) com a versão no nome e no rodapé; a área aprova pela transição "Aprovação solicitantes" do Jira, anexando ou linkando aquele PDF; o PO registra na tabela a versão, a data, papel e área, e onde está o PDF. O nome de quem aprovou fica no histórico do Jira, não no documento. [ALÉM DA FONTE — decisão do usuário]
- **Não entra:** tarefa de desenvolvimento; "a definir" sem dono; nome de pessoa.
- **Caso Neo (desenvolvimento sem aprovação):** a US-72 (JUDIT) está em APROVAÇÃO SOLICITANTES desde 14/09/2026 (`upstream_16-11.csv`, 16/11/2026 9h51) enquanto o épico DS-466 tem 4 cards em desenvolvimento (`epicos_downstream_16-11.csv`, 16/11/2026 10h26). Sem versão aprovada, o que está sendo construído pode não ser o que a área quer.
- **Caso Neo (mudança de escopo sem registro):** a US-85 diz que o usuário confirma a equipe "a cada login"; o DS-458 diz que "O login não exige abertura ou confirmação do modal", e a troca passa ao menu do perfil (DS-460) (`upstream_16-11.csv` 9h51 e `downstream_16-11.csv` 10h26, 16/11/2026). Isso é mudança de escopo: exige PRD v2.0, com a nova RN e nova aprovação.

### 8. Apetite (G recomendado, GG obrigatório)

- **Entra:** o teto de tempo que a área aceita pagar, decidido antes da solução (Shape Up, Basecamp). A régua dá a estimativa; o apetite dá o limite. Estimativa acima do apetite → corta-se escopo, não se estica prazo.
- **Não entra:** ciclos de 6 semanas, mesa de apostas ou o resto do Shape Up; só o apetite é aproveitado. Pontos ou Fibonacci também não: não são prática atual do time.

### 9. Perfis

- **Entra:** perfis de acesso do sistema e atores externos (parceiro, processadora). Perfil que ainda não existe: [A CONFIRMAR] e o dono da definição.
- **Não entra:** nome de pessoa ou de usuário.

### 10. Fluxo atual × proposto

- **Entra:** a sequência de negócio, uma linha por etapa, com "Hoje" e "Proposto". Em demanda de **esteira**, a tabela de estados e transições (estado de origem, evento, destino, quem dispara, exceção): é o AS-IS que falta na Esteira de Novos.
- **Não entra:** descrição de tela; códigos de RN dentro do protótipo.
- **Caso Neo:** 3 dos 31 Bugs do Downstream ligados à movimentação da proposta na esteira ou ao lock da ficha: DS-28, DS-364 e DS-388 (`downstream_16-11.csv`, 16/11/2026 10h26; lista e critério em `../METODOLOGIA.md`, seção 4; classificação própria **[ALÉM DA FONTE — decisão do usuário]**).

### 11. Requisitos não funcionais (EARS)

- **Entra:** só o que é específico da demanda, mensurável e em EARS: auditoria ("QUANDO o motor registrar uma avaliação, o sistema DEVE gravar data, regra aplicada e resultado"), mascaramento, tempo máximo, comportamento quando o serviço externo cai. Em demanda do cartão, o que vem do PCI DSS e da Mastercard listados na Visão do Cartão v6, sem transcrever a norma. Dado de cartão (PAN/CVV) nunca entra em exemplo.
- **Não entra:** "o sistema deve ser seguro e performático"; RNF em Gherkin.

### 12. Tabela de decisão (completo; obrigatória com gatilho de dinheiro em qualquer trilha)

- **Entra:** uma linha por combinação de condições, com a decisão, a **precedência** (qual linha vence quando duas casam), a **vigência** da regra (RN, versão, início e fim) e **um caso de teste por linha**. Use quando houver motor de regras, decisão automática de crédito ou pagamento.
- **Não entra:** combinação sem decisão; linha sem teste; regra "vigente" sem data.
- **Caso Neo (modelo a seguir):** o DS-508 (Quitação Fase 2) testa "um caso por linha da tabela de decisão" (`downstream_16-11.csv`, 16/11/2026 10h26), e o DS-415 define as decisões PAGAR, NAO_PAGAR, PAGAR_PARCIAL e ANALISE_MANUAL. O exemplo `exemplos/quitacao/GDP-76_quitacao-fase-2-motor.md` mostra a tabela preenchida.
- **Caso Neo (precedência):** a "regra de precedência definida" do DS-393 (NMP) é exatamente uma coluna desta tabela.

### 13. Integrações

- **Entra:** só a lista das contrapartes tocadas pela demanda, com link para o `CONTRATO-DE-INTEGRACAO.md` de cada uma. Integração Konsig ↔ NeoKonsig também entra, como integração entre sistemas distintos.
- **Não entra:** autenticação, leiaute, erros, horário, endereço de servidor, credencial: isso é do contrato, não do PRD. Contraparte sem contrato: [A CONFIRMAR] e o card que vai escrevê-lo.

### 14. Riscos

- **Entra:** evento incerto → consequência, com probabilidade, impacto, mitigação e dono por papel.
- **Não entra:** problema que já aconteceu (isso é dependência ou pendência, seção 7).

### 15. Rastreabilidade

- **Entra:** cada RN, RNF e linha da tabela de decisão ligada ao card que a implementa e ao teste que a prova. Preencha a coluna de cards depois do Plano.
- **Uma regra sem card é escopo esquecido; um card sem regra é escopo inventado.**
- **Caso Neo:** 15 de 35 épicos do Downstream têm item do GDP associado (`downstream_16-11.csv`, 16/11/2026 10h26); o GDP-76 não tem item associado, e DS-418 e DS-500 não apontam para o GDP.

---

## Referências de mercado

Conteúdo marcado "(via busca)" veio de trechos do buscador, porque a rede da sessão bloqueou a página em 17/11/2026: confira o original antes de citar em documento oficial.

- **PRD ágil, curto e ligado ao épico; escopo e fora de escopo; perguntas em aberto** (Atlassian): https://www.atlassian.com/agile/product-management/requirements
- **Não objetivos (Non-Goals) no modelo de PRD de Kevin Yien, Square; one-pager de Lenny Rachitsky** (lista de modelos de Lenny Rachitsky) (via busca): https://www.lennysnewsletter.com/p/my-favorite-templates-issue-37
- **PRD focado no problema, separado do RFC da solução** (HashiCorp): https://www.hashicorp.com/how-hashicorp-works/articles/prd-template
- **Objetivos e não objetivos; design doc só quando há trade-off** (Google, por Malte Ubl) (via busca): https://www.industrialempathy.com/posts/design-docs-at-google/
- **EARS, cinco padrões de requisito** (Mavin et al., IEEE RE'09): https://en.wikipedia.org/wiki/Easy_Approach_to_Requirements_Syntax
- **Apetite: quanto o problema vale, não quanto vai levar** (Shape Up, Basecamp, cap. 3 'Set Boundaries') (via busca): https://basecamp.com/shapeup/1.2-chapter-03
- **Spec-driven development em Assess: specs longas e difíceis de revisar** (Thoughtworks Technology Radar): https://www.thoughtworks.com/radar/techniques/spec-driven-development
- **Spec-first, spec-anchored e spec-as-source** (Birgitta Böckeler, martinfowler.com) (via busca): https://www.martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html
