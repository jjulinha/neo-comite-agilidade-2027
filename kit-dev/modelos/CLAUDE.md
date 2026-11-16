<!--
MODELO · CLAUDE.md para repositório de sistema da Neo Crédito · Kit de documentação TI · v1.0 · 16/11/2026 · proposta
Como usar: copie para a raiz do repositório do sistema com o nome CLAUDE.md e preencha a seção 1.
Konsig e NeoKonsig têm CLAUDE.md próprios. Nunca use o mesmo arquivo para os dois.
Assistentes de IA leem este arquivo antes de qualquer tarefa no repositório. Escreva instruções, não descrições.
Apague este comentário depois de preencher.
-->

# Instruções para assistentes de IA · <Nome do sistema>

Leia este arquivo inteiro antes de qualquer tarefa neste repositório. Se um pedido conflitar com estas instruções, pare e pergunte antes de executar.

## 1. Contexto do sistema (preencher)

| Campo | Valor |
|---|---|
| Sistema | <**Konsig** (legado) **ou** **NeoKonsig** (reescrita) ou outro sistema do Inventário> |
| Papel do sistema | <uma a três linhas: o que o sistema faz para o negócio> |
| Sistemas com que este repositório **não** deve ser confundido | <Konsig: "este não é o NeoKonsig" · NeoKonsig: "este não é o Konsig"> |
| Linguagens e versões | [A CONFIRMAR no Inventário de Sistemas] |
| Banco de dados | [A CONFIRMAR no Inventário de Sistemas] |
| Mensageria, cache, filas | [A CONFIRMAR no Inventário de Sistemas] |
| Autenticação | [A CONFIRMAR no Inventário de Sistemas] |
| Observabilidade (logs, APM) | [A CONFIRMAR no Inventário de Sistemas] |
| Pipeline de CI/CD | <Konsig: **não existe** (US-43, Backlog) · NeoKonsig: [A CONFIRMAR no Inventário de Sistemas]> |
| Ambientes | [A CONFIRMAR no Inventário de Sistemas] |
| Integrações externas | <lista de parceiros, conforme o Inventário; ver `docs/prd/` de cada demanda> |
| Comandos de build e teste | <comando exato para instalar dependências, rodar testes e rodar o linter> |
| Responsáveis (papéis) | <tech lead, PO do sistema> |
| Inventário de Sistemas | Drive `1LwSqMSxgldjHxNQmj34uDAI_refDOkWG` · versão consultada: <data> |

> **Orientação para quem preenche.** Toda tecnologia vem do Inventário de Sistemas oficial. O documento `insumos/sistemas-e-tecnologias.md` do Comitê de Agilidade (16/11/2026) reúne evidências do Jira (por exemplo, PHP 8 e Node no Konsig; PostgreSQL e RabbitMQ no NeoKonsig), mas registra que elas **não substituem o Inventário**. Não copie essas evidências para cá como fato: confirme no Inventário e cite a versão consultada. Enquanto não confirmar, deixe [A CONFIRMAR no Inventário de Sistemas].

---

## 2. Regras que não têm exceção

1. **Konsig não é NeoKonsig.** São sistemas diferentes, com tecnologias diferentes. Não sugira código, biblioteca, padrão ou solução de um no outro sem que um ADR aceito diga isso. Se a tarefa tocar o outro sistema (por exemplo, uma integração entre os dois), declare isso e pare para confirmação.
2. **Não invente requisito.** O comportamento esperado está no PRD, no card e nos ADRs. O que não estiver lá, pergunte. Se precisar propor algo além, marque **[ALÉM DA FONTE — decisão do usuário]** e não implemente sem confirmação.
3. **Não invente tecnologia.** Não afirme versão, biblioteca ou infraestrutura que não esteja na seção 1 ou no código. Use [A CONFIRMAR].
4. **Nenhum dado pessoal.** Não escreva CPF, CNPJ, nome de cliente, e-mail, telefone, número de contrato, de proposta ou de cartão em código, teste, fixture, log de exemplo, commit, pull request ou documento. Massa de teste é sintética: fictícia no conteúdo e válida no formato. Se encontrar dado pessoal real no repositório, não o reproduza; informe o caminho do arquivo ao revisor.
5. **Dado de cartão nunca é gravado nem logado**: PAN, CVV e trilha ficam fora de log, mensagem de erro e teste (Visão do Cartão v6, riscos R18 e R19). Em dúvida se um campo é dado de cartão, trate como se fosse.
6. **Sem segredo no código.** Nada de credencial, token, endereço interno de servidor ou identificador de conta no código, no commit ou no pull request.
7. **Não escreva no Jira** e não altere parâmetros de estimativa ou de priorização.

---

## 3. Antes de escrever código

1. Identifique a chave do card (`DS-n`). Sem chave, pergunte qual é.
2. Leia, nesta ordem: o card; o PRD de origem em `docs/prd/` (a versão citada no bloco 1 do card); os ADRs com status Aceito em `docs/adr/` que tratem do assunto; o Plano em `docs/planos/` do épico.
3. Confira se o card passa no DoR (bloco 3). Se algum item estiver em aberto e bloquear o caminho principal, pare e informe.
4. Liste, antes de começar, quais cenários BDD (bloco 5) e quais cenários de teste (bloco 7) a mudança vai cobrir. Se o card tiver mais de sete cenários ou o título precisar de "e", aponte que o card pode precisar de quebra (guia "Como escrever um card", seção 06) em vez de implementar tudo de uma vez.
5. Se a implementação exigir decisão técnica que nenhum ADR cobre (biblioteca nova, padrão de integração, mudança de formato de dado ou de log), proponha um ADR com o modelo do kit e não implemente até o ADR ser aceito.
6. Se o PRD, o card e o código divergirem, não escolha sozinho: descreva a divergência e pergunte.

---

## 4. Testes

- Todo comportamento novo ou alterado tem teste automatizado que cobre os cenários do card: caminho feliz, alternativo, borda e falha.
- Serviço externo (parceiro, banco, processadora) é simulado no teste; o teste não chama o serviço real.
- Rode os testes e o linter com os comandos da seção 1 antes de declarar a tarefa pronta e informe o resultado real. Não declare "testes passando" sem tê-los executado.
- Sem pipeline de CI/CD (caso do Konsig, US-43), o resultado dos testes vai descrito no pull request, com o comando usado.
- O QA executa os cenários de teste do card na etapa QA Teste; seus testes não substituem essa etapa.

---

## 5. Commits

Formato **[ALÉM DA FONTE — decisão do usuário]**:

```
<DS-n> <verbo no imperativo> <o que muda, em português>

<por que muda, quando não for óbvio pelo card>
Refs: <PRD vX.Y, seção> · <ADR-nnnn, se houver>
```

Exemplo: `DS-501 Captura propostas em AND - AGUARD QUITACAO para o motor` (ilustrativo).

- Um commit por mudança lógica. Não misture refatoração com comportamento novo.
- Sem dado pessoal, segredo ou nome de pessoa na mensagem.

---

## 6. Pull requests

Título: `<DS-n> <título do card>`.

Corpo:

```
## Card
<DS-n> · <link>

## O que muda
<duas a cinco linhas, em linguagem de negócio>

## Referências
PRD: docs/prd/<arquivo> (vX.Y), seções <n>
ADR: <ADR-nnnn ou "nenhum">

## Cenários cobertos
- [ ] <Cenário BDD 1> · teste <nome>
- [ ] <Cenário BDD 2> · teste <nome>

## Como testar
<comandos e massa fictícia>

## Fora deste PR
<o que o card prevê e ficou para outro PR, se houver>

## Riscos e rollback
<o que pode quebrar; como reverter>

## Conferência
- [ ] Sem dado pessoal, dado de cartão ou segredo
- [ ] Testes executados localmente: <resultado>
- [ ] Documentação em docs/ atualizada, se o comportamento mudou
```

O pull request vai para Code Review com revisor preenchido no card (regra 2 do experimento em vigor desde a Sprint 19). Código gerado por IA passa pela mesma revisão que qualquer outro código.

---

## 7. Documentação

- Se a mudança alterar regra, integração, formato de dado ou de log, atualize o documento correspondente em `docs/` no mesmo pull request, ou registre no PR por que não atualizou.
- Use os modelos do kit (PRD, ADR, Plano, Card). Não crie formatos novos de documento.
- Documentos em português do Brasil, linguagem formal, pessoas citadas pelo papel (PO, tech lead, dev, QA), nunca pelo nome.
- Não use o documento "Melhorias Scrum TI V2" como descrição do processo atual: são sugestões não aplicadas. Não afirme que o time usa Fibonacci ou planning poker.

---

## 8. Quando parar e perguntar

- O pedido toca o outro sistema (Konsig ↔ NeoKonsig).
- O comportamento pedido não está no PRD nem no card.
- A tarefa exige decisão técnica sem ADR.
- Aparece dado pessoal real, dado de cartão ou segredo.
- Um teste existente precisa ser removido ou enfraquecido para a mudança passar.
