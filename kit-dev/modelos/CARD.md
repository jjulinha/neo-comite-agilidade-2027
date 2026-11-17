<!--
MODELO · Card do Downstream · Kit de documentação TI Neo Crédito · v2.0 · 17/11/2026
Base: guia "Como escrever um card" (InnoviaX, v1.0, set/2026), tutorial de abertura de cards da TI, confirmado pelo usuário em 13/11/2026 (contexto-mestre.md, seção 3). O modelo de História é o do guia (seção 10). Base dos modelos 1b e 1c: guia, seção 07.
Acréscimos ao guia, marcados no texto: VERSÃO OU DEPLOY, CAUSA [FATO | HIPÓTESE] e POSTMORTEM no Bug, a DoD única e a nota de passagem [ALÉM DA FONTE — decisão do usuário]. Se divergirem do guia, a mudança vira ADR.md (gatilho "decisão difícil de reverter ou com alternativa real, inclusive de documentação").
-->
# Card do Downstream · modelo por tipo

**Quando usar.** Todo card do Downstream, em qualquer trilha (PP a GG). Em PP o card é o único documento da trilha; os gatilhos por risco (dado pessoal, integração, dinheiro, migração, decisão difícil de reverter, incidente) somam-se mesmo em PP. Ver a regra de escolha no README.
**Quando não usar.** Épico (vai no PRD/Plano), decisão com alternativa real (ADR.md), incidente (POSTMORTEM.md), rotina recorrente (RUNBOOK.md). Subtarefa herda o card pai: divide trabalho, nunca entendimento.
**Escolha o modelo:** 1a História (só o PO cria, regra 1 da S19) · 1b Tarefa técnica ou Spike · 1c Bug. DoD (2.2) e nota de passagem (2.3) valem para os três.

## 1. Modelos em branco (copie para a descrição do Jira)

### 1a. História · os 10 blocos do guia (seção 10)
```
TÍTULO: <verbo> <objeto>                      (sem "e"; ver exemplo DS-501, seção 5)
Referência: <RF/RN> em <documento> (<versão>)
Tipo: História   Sistema: <Konsig | NeoKonsig | outro do inventário>   Iniciativa: <GDP-n>   Épico: <DS-n>   Estimativa: <vazio — ver Nota Neo, seção 4>
CONTEXTO: como é hoje · limitação · o que muda · o que fica fora. Três a seis linhas.
DoR (seção 2.1)
- <documento, decisão, acesso ou resposta de terceiro, verificável com sim/não>
HISTÓRIA: Como <perfil>, eu quero <capacidade>, para que <benefício que não repete a ação>.
CENÁRIOS (3 a 7: feliz, alternativo, borda, falha)
Cenário: <nome> · Dado que <estado> · Quando <uma ação> · Então <resultado observável>
CRITÉRIOS DE ACEITE
- <afirmação binária com número, prazo ou formato · comportamento em falha · registro/auditoria>
CENÁRIOS DE TESTE (dado fictício, válido no formato)
T1 · <ação com dado concreto> · <resultado esperado>
REQUISITOS NÃO FUNCIONAIS: <só o específico deste card, ou "não se aplica: motivo">
DEPENDÊNCIAS E PENDÊNCIAS
- A DEFINIR: <o que falta> · responsável: <papel> · até <data> · bloqueia o caminho principal? <sim/não>
DoD: colar a lista da seção 2.2
```

### 1b. Tarefa técnica / Spike · registrar como Tarefa, com "Spike:" no título quando for
```
OBJETIVO: <verbo> <objeto>, para que <efeito verificável>      (a história vira esta frase; guia, seção 07)
CONTEXTO E LINKS: <por que agora> · Sistema: <Konsig | NeoKonsig | outro do inventário> · ADR/PRD: <docs/...> · Iniciativa: <GDP-n ou "sem item GDP">
O QUE MUDA: <componente, configuração, repositório ou ambiente; uma a três linhas>
CENÁRIOS (quando houver comportamento esperado; rotina de infraestrutura também tem)
Cenário: <nome> · Dado que <estado> · Quando <uma ação> · Então <resultado observável>
CRITÉRIOS DE ACEITE (binários; Spike: critério de conclusão da investigação)
- <afirmação sim/não>
COMO VERIFICAR: <comando, tela ou consulta, com o resultado esperado; é a evidência dos critérios>
RISCO E ROLLBACK: <o que pode quebrar> · <como desfazer, ou "sem rollback: contingência">
SPIKE (só Spike): PERGUNTA: <uma só> · SAÍDA ESPERADA: <ADR, nota ou protótipo descartável> · PRAZO: <data>
DoD: colar a lista da seção 2.2
```

### 1c. Bug · todos os campos são obrigatórios
```
TÍTULO: <sintoma observável> em <tela, rotina ou integração>
AMBIENTE: <produção | homologação | stag | local>      SISTEMA: <Konsig | NeoKonsig>
FASE EM QUE FOI DETECTADO: <dev | code review | QA | homologação | produção>
VERSÃO OU DEPLOY: <tag, commit ou "Deploy dd/mm"; "não identificado: <motivo>">   [ALÉM DA FONTE — decisão do usuário]
PASSOS PARA REPRODUZIR: 1. ... 2. ... 3. ...   (dado fictício; nunca copiado de produção)
ESPERADO × OBTIDO: <esperado> × <obtido>
ORIGEM: <card DS-n ou deploy que introduziu o defeito; "não identificado: <motivo>">
CAUSA [FATO | HIPÓTESE]: <causa raiz e como se sabe; hipótese fica marcada até ser confirmada>   [ALÉM DA FONTE — decisão do usuário quanto à marcação]
TESTE DE REGRESSÃO CRIADO: <nome do teste automatizado ou T-n do QA> | "não se aplica: sem mudança de código; monitor/alerta: <qual>"
POSTMORTEM: <link do POSTMORTEM.md> | "sem gatilho"  (gatilhos na seção 3)   [ALÉM DA FONTE — decisão do usuário]
DoD: colar a lista da seção 2.2
```

## 2. Blocos comuns aos três tipos

### 2.1 DoR: portão só para o caminho principal (guia, seções 02 e 03)
- Item que bloqueia o caminho principal impede a entrada na sprint. Item aberto que **não** bloqueia vira A DEFINIR com o que falta, papel responsável e data (bloco 9), e o card pode entrar.
- Todo item precisa ser verificável com sim/não por quem não escreveu o card. A DoR oficial da TI está nas Políticas Explícitas V1 [A CONFIRMAR o texto vigente].
- **Example Mapping antes do Gherkin** [ALÉM DA FONTE — decisão do usuário]: no refinamento, PO, dev e QA listam regras, exemplos e perguntas. As regras viram critérios de aceite, os exemplos viram cenários e as perguntas viram pendências.
- **INVEST é checagem na revisão do card, não campo.**

### 2.2 DoD do Downstream · lista única [ALÉM DA FONTE — decisão do usuário]
```
DoD
- [ ] Código revisado e integrado; revisor preenchido no card (regra 2 da S19)
- [ ] Testes automatizados implementados e passando (comando e resultado no PR)
- [ ] Cenários de teste executados e evidenciados; testador preenchido (regra 2 da S19)
- [ ] Validação do negócio por <área e papel>; o nome fica no responsável da etapa Aprovação POs
- [ ] Categorias, Descrição, Classe de serviço e Tipo preenchidos (regra 3 da S19); História criada pelo PO (regra 1)
- [ ] Documento em docs/ (PRD, Plano, ADR, contrato, runbook) atualizado no mesmo PR, ou o PR diz por que não
- [ ] CHECKLIST-DADOS-E-REGULACAO.md respondido no PR, quando a mudança toca dado pessoal
- [ ] Nota de passagem (2.3) registrada a cada mudança de etapa
```
- Critério de aceite fala do comportamento do produto; DoD fala do estado do trabalho. A DoD é uma só para o time e não se reescreve por card.
- Restrição de ambiente específica do card (por exemplo, sem CI/CD no Konsig, US-43) entra como linha extra.
- A DoD oficial está nas Políticas Explícitas V1, não recebidas [A CONFIRMAR]. Quando chegarem, esta lista se alinha a elas.

### 2.3 Nota de passagem de etapa (Dev → Revisor → QA → PO)
Comentário no card, a cada mudança de etapa, em três linhas. Responde ao DS-491 "passagem de bastão" (Backlog, `downstream_16-11.csv`, 16/11/2026 10h26) [ALÉM DA FONTE — decisão do usuário quanto ao formato].
```
FEITO: <o que foi entregue nesta etapa; PR ou evidência>
COMO TESTAR: <ambiente, passos ou T-n, massa fictícia>
FICOU: <o que não foi feito, risco conhecido ou "nada">
```

## 3. Checklist antes do refinamento (guia, seção 10, com as regras por campo)
- [ ] O título começa com verbo e não precisa de "e" para descrever o que faz.
- [ ] A referência ao documento de origem está escrita, com versão; o sistema (Konsig ou NeoKonsig) está declarado.
- [ ] O contexto diz como é hoje, o que muda e o que fica fora do escopo.
- [ ] Todo item do DoR é verificável com sim ou não; nenhum A DEFINIR bloqueia o caminho principal; toda pendência tem o que falta, papel e data.
- [ ] O "para que" da história (ou o OBJETIVO da Tarefa) não repete a ação em outras palavras.
- [ ] Cada cenário tem título, um único Quando, um Dado que descreve estado e um Então observável, em linguagem de negócio. Requisito não funcional não vira Gherkin.
- [ ] Os cenários cobrem caminho feliz, alternativo, borda e falha.
- [ ] Cada critério de aceite é binário, sem advérbio ("rapidamente", "adequadamente"), com os números (limites, prazos, janelas, formatos). Tarefa técnica também tem critério de aceite (guia, seção 07).
- [ ] Os cenários de teste têm dado concreto e fictício.
- [ ] Os requisitos não funcionais são específicos deste card. Dado pessoal novo, log, exportação ou parceiro novo vai para o CHECKLIST-DADOS-E-REGULACAO.md no PR, não para o card.
- [ ] Spike tem pergunta, prazo e saída esperada.
- [ ] Bug: causa sem fonte está marcada HIPÓTESE; ORIGEM aponta card ou deploy, não pessoa; a fase de detecção está preenchida. Gatilho de postmortem: P1/P2 da tabela do PDTI (slide 14), Expedite, Bug em produção, perda de dado ou pagamento errado (POSTMORTEM.md, em até 5 dias úteis). Integração externa envolvida: atualizar o CONTRATO-DE-INTEGRACAO.md da contraparte.
- [ ] O DoD fala do estado do trabalho, não do comportamento do produto.
- [ ] O card cabe numa sprint com folga, e tem entre três e sete cenários.
- [ ] Um leitor que não participou da conversa saberia o que construir e como provar.
- [ ] **Nota Neo:** nenhum dado pessoal real no card, inclusive nos cenários de teste.

Em Tarefa técnica, a história vira a linha OBJETIVO; critérios de aceite continuam obrigatórios (guia, seção 07). Em Bug, o contexto vira reprodução (passos, esperado × obtido).

## 4. Notas Neo
> **Nota Neo · tipos no Jira.** O Downstream tem os tipos Tarefa, História, Bug, Subtask e Epic (`downstream_16-11.csv`, 16/11/2026 10h26). Os tipos do guia correspondem a eles assim: Story = História, Task = Tarefa, Bug = Bug, Subtask = Subtask. Spike e Teste não têm tipo próprio: registrar como Tarefa, com a indicação "Spike:" ou "Teste:" no título ou no campo Categorias **[ALÉM DA FONTE — decisão do usuário]**; é o caso do DS-508, card de teste do motor da Quitação registrado como Tarefa. O campo "Iniciativa" do guia corresponde, na Neo, ao item do GDP de origem (por exemplo, GDP-76); card de épico técnico sem item GDP registra "sem item GDP" **[ALÉM DA FONTE — decisão do usuário]**. Pela regra 1 do experimento em vigor desde a Sprint 19, só o PO cria História; demanda nova entra como Tarefa e passa por triagem e refinamento (`contexto-mestre.md`, seção 4).
>
> **Nota Neo · estimativa.** O guia prevê o campo "Estimativa" em pontos (seção 10). Na Neo, a forma de estimar o card está **em aberto**: a decisão de 10/11/2026 (Fibonacci só depois do refinamento) está em revisão desde 13/11/2026, com a proposta de tamanho PP a GG por projeto e regra "cabe ou quebra" por card; o Fibonacci não é prática atual do time. Até a decisão do comitê: deixar o campo Estimativa do card **vazio** e registrar no épico a classe de tamanho (PP a GG) pela régua **[ALÉM DA FONTE — decisão do usuário]**. Não preencher pontos.
>
> **Nota Neo · dados pessoais.** Dado concreto nos cenários é valor **fictício**, válido no formato. Nenhum CPF, nome, contato, contrato ou número de cartão real entra no card, nem mascarado (`../README.md`, seção 8). Pessoas aparecem pelo papel.

## 5. Exemplos Neo
> **Exemplo Neo · caso a corrigir.** O título real do DS-501 é "Capturar as propostas em AND - AGUARD QUITACAO e executar o motor". Ele precisa de "e" para descrever o que faz, que é sinal de card grande (guia, seção 06) e reprova no checklist da seção 3 deste arquivo. Duas saídas: reescrever o título pelo resultado, "Executar o motor sobre as propostas em AND - AGUARD QUITACAO" **[ALÉM DA FONTE — decisão do usuário]**, ou quebrar o card, se a captura tiver valor verificável sozinha.
>
> **Exemplo Neo · cabeçalho corrigido (História, Konsig).** Título: "Executar o motor sobre as propostas em AND - AGUARD QUITACAO". Sistema: Konsig. Referência: seção de RN de `docs/prd/GDP-76_quitacao-fase-2-motor.md` (no kit, `exemplos/quitacao/GDP-76_quitacao-fase-2-motor.md`) e, como está hoje no DS-501, "ES 1, RF1, RF1.a, RF22 (caput), PRE 1, PRE 2; tabela de decisão, linhas 1 e 2" do Documento de Requisitos V04 (26/10/2026; data conforme DS-500, `downstream_16-11.csv`, 16/11/2026 10h26) [A CONFIRMAR: documento não recebido]. Iniciativa: GDP-76. Épico: DS-500. Enquanto o PRD não tiver versão aprovada, isso é item aberto da DoR, com PO e data.
>
> **Exemplo Neo · cenário (caminho feliz).** Cenário: proposta elegível avaliada · Dado que existe uma proposta da esteira Cartão Consignado Compra em AND - AGUARD QUITACAO e há regras vigentes · Quando o motor é executado · Então a avaliação fica registrada com a decisão final e a situação da proposta permanece a mesma.
>
> **Exemplo Neo · Bug preenchido a partir do DS-272 (Konsig, JUDIT; `downstream_16-11.csv`, 16/11/2026 10h26).** O DS-272 "Erro em requisição da JUDIT" foi registrado como Tarefa, natureza Arquitetura, classe Expedite, criado e resolvido em 18/09/2026; no modelo v2 seria Bug [ALÉM DA FONTE — decisão do usuário]. TÍTULO: Consulta à JUDIT retorna erro 401. AMBIENTE: [A CONFIRMAR]. FASE EM QUE FOI DETECTADO: [A CONFIRMAR]. VERSÃO OU DEPLOY: não se aplica, nenhum deploy da Neo; mudança do fornecedor em 18/09/2026. ESPERADO × OBTIDO: consulta processual retornada × erro 401. ORIGEM: atualização de segurança do fornecedor, sem aviso prévio. CAUSA [FATO]: a atualização de segurança da JUDIT barrou a autenticação (texto do card). TESTE DE REGRESSÃO: não se aplica, sem mudança de código (texto do card: "Não houve necessidade de alterar nada no nosso código"); proposta: alerta de 401 na integração [ALÉM DA FONTE — decisão do usuário]. POSTMORTEM: gatilho atingido (Expedite); ação provável: registrar autenticação e aviso de mudança no CONTRATO-DE-INTEGRACAO.md da JUDIT [ALÉM DA FONTE — decisão do usuário].

## 6. Quando quebrar (guia, seção 06)
Sinais: mais de sete cenários; título com "e"; mais de um perfil na história; parte depende de decisão inexistente enquanto outra está pronta. Como quebrar: guia, seção 06.

> **Nota Neo · teto.** O "teto combinado pelo time" citado pelo guia ainda não existe na Neo: depende da decisão do comitê sobre a regra "cabe ou quebra" **[A CONFIRMAR]**. Referência medida: na Sprint 18, a mediana da História foi 118h para uma sprint de 75h úteis (Review da Sprint 18, extração de 06/11/2026 16h46).

## 7. Uso com IA
- O card, junto com o PRD/Plano do épico, é o contexto do agente de código (nível spec-anchored). O agente lê o card antes de escrever código (AGENTS.md do repositório) e o PR cita os cenários que cobriu.
- Card pequeno é lote pequeno: o DORA 2025 aponta lotes pequenos como contrapeso à IA, que tende a gerar blocos grandes, difíceis de revisar e testar.
- Campos numerados (RN, T-n, cenários) valem mais que texto corrido: é onde o agente menos inventa. A IA não escreve no Jira (`../README.md`); o texto que ela sugerir passa por revisão humana.

## 8. Por que este formato
Os vazios medidos no Downstream que justificam cada campo estão no README do kit (`../README.md`, seção 9); o debate de mercado sobre DoR e DoD, na metodologia (`../METODOLOGIA.md`, seção 2.4).

## 9. Referências
- Definition of Done (Scrum Guide 2020): https://scrumguides.org/docs/scrumguide/v2020/2020-Scrum-Guide-US.pdf
- Crítica à DoR como portão, Mike Cohn: https://mountaingoatsoftware.com/blog/the-dangers-of-a-definition-of-ready
- "Definition of Ready considered harmful", Allan Kelly, 06/09/2017 (espelho do blog do autor): https://www.goodreads.com/author_blog_posts/15674929-definition-of-ready-considered-harmful
- Example Mapping, Matt Wynne: https://cucumber.io/blog/example-mapping-introduction
- INVEST, Bill Wake: https://xp123.com/?p=67
- Referência de Gherkin: https://cucumber.io/docs/gherkin/reference
- DORA 2025, capacidades de IA e lotes pequenos: https://cloud.google.com/blog/products/ai-machine-learning/from-adoption-to-impact-putting-the-dora-ai-capabilities-model-to-work
- Postmortem sem culpa (Google SRE): https://sre.google/sre-book/postmortem-culture/
