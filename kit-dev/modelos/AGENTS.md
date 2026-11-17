<!--
MODELO · AGENTS.md para repositório de sistema da Neo Crédito · Kit de documentação TI · v2.0 · 17/11/2026 · proposta
Substitui o modelo CLAUDE.md do kit v1 (142 linhas, 16/11/2026). Tudo abaixo da linha "COPIE A PARTIR DAQUI" vai para a raiz do repositório.

QUANDO USAR
- Um AGENTS.md por repositório de sistema, na raiz. O Konsig vem primeiro: é para onde o time inteiro vai em 2027.
- Ao criar ou migrar o repositório (DS-175/DS-495), e sempre que um dev novo ou um agente de IA começar a trabalhar no sistema.
- Ao mudar comando de build/teste, armadilha conhecida ou regra da constituição: atualize no mesmo PR.

QUANDO NÃO USAR
- Não é documentação do sistema: arquitetura, contexto e integrações ficam em docs/SISTEMA.md. Aqui só se aponta para lá.
- Não é lugar de regra de negócio: ela fica no PRD e no card.
- Nunca um arquivo para Konsig e NeoKonsig juntos, nem regra compartilhada entre os dois. Cada repositório tem o seu, e cada um diz "este não é o outro".

REGRAS DE ESCRITA DESTE ARQUIVO
1. Escrito e revisado por humano. Nunca gerado por /init (ou equivalente) sem revisão linha a linha. Motivo: Gloaguen et al.
   (ETH Zurich/LogicStar.ai, arXiv 2602.11988, fev/2026, https://arxiv.org/abs/2602.11988): arquivos de contexto tendem a não melhorar
   a taxa de sucesso e sobem o custo de inferência em mais de 20%. Os escritos por humanos se saem um pouco melhor que os gerados por LLM,
   e o arquivo ajuda quando traz prática não padrão. Percentuais de ganho ou perda por tipo de arquivo: [A CONFIRMAR no artigo].
2. Menos de 200 linhas no arquivo copiado (recomendação da documentação do Claude Code: https://code.claude.com/docs/en/memory).
3. Só o que o modelo não sabe: comandos exatos, regras sem exceção, nomes de status, armadilhas do legado. Nada de "escreva código limpo".
4. Regras concretas e verificáveis ("ao integrar com o CRM, envie CPF como string", não "cuidado com tipos").
5. O que não foi confirmado fica [A CONFIRMAR]. Proposta sem fonte fica [ALÉM DA FONTE — decisão do usuário].

ARQUIVOS DE OUTRAS FERRAMENTAS (apontam, nunca repetem regra)
- CLAUDE.md na raiz contém uma linha só:  @AGENTS.md
  Motivo: o Claude Code lê o AGENTS.md sozinho só quando não existe CLAUDE.md (v2.1.277+). Se existir, lê só o CLAUDE.md. A linha
  @AGENTS.md garante a leitura nos dois casos e em versões antigas (https://code.claude.com/docs/en/memory, seção AGENTS.md, conferida
  em 17/11/2026). O CLAUDE.md é contexto, não configuração: o que não pode depender de obediência vai para hook (abaixo).
- .github/copilot-instructions.md contém só: "Siga o AGENTS.md na raiz deste repositório." O Copilot lê AGENTS.md, e diante de instruções
  em conflito a escolha dele é não determinística (https://docs.github.com/en/copilot/how-tos/configure-custom-instructions/add-repository-instructions).
- .cursor/rules/agents.mdc (Always Apply) contém só o apontador para o AGENTS.md, e só se o time usar Cursor [A CONFIRMAR].
- Quais agentes o time usa e com que aprovação: [A CONFIRMAR]. A regra de uso de IA (D2, documento 1) ainda não foi aprovada
  (D2-documentos-ia/D2-documentos-para-a-IA.md, seção 4).

HOOK PARA O QUE NÃO PODE DEPENDER DE OBEDIÊNCIA [ALÉM DA FONTE — decisão do usuário]
- Instrução em markdown é pedido, não bloqueio. Para regra da constituição que pode ser checada por máquina, use hook de pre-commit
  (e, no Claude Code, hook PreToolUse) que barre: padrão de CPF/CNPJ formatado, sequência de 13 a 19 dígitos com cara de PAN, chave privada,
  token e senha. O hook vale para humano e agente. Enquanto o Konsig não tiver CI/CD (US-43, Backlog, upstream_16-11.csv, 16/11/2026 9h51),
  o hook local é a barreira automática antes do commit. Se a análise do SonarQube (DS-202, DS-231) roda no Konsig e em que momento:
  [A CONFIRMAR].

SKILLS DE IA
- DS-546 ("skill genérica de workflow da Neocrédito", Code Review, downstream_16-11.csv, 16/11/2026 10h26) nasceu no NeoKonsig e, pela própria
  descrição, vale para qualquer repositório. Candidata a ser levada ao Konsig [A CONFIRMAR]. Se for, o AGENTS.md aponta para ela; não a copia.

Apague este comentário depois de preencher.
======================================== COPIE A PARTIR DAQUI ========================================
-->

# AGENTS.md · <Konsig>

Instruções para agentes de código (Claude Code, Copilot, Cursor e outros) e para dev novo neste repositório. Leia inteiro antes de qualquer tarefa. Se um pedido conflitar com este arquivo, pare e pergunte.

## 1. Este repositório

- **Sistema:** <Konsig, o sistema legado de consignado da Neo Crédito>. Referência completa: `docs/SISTEMA.md`.
- **Este não é o NeoKonsig.** <No arquivo do NeoKonsig: "Este não é o Konsig.">. São sistemas diferentes, em repositórios diferentes, sem regra compartilhada. Não traga código, biblioteca ou padrão de um para o outro sem ADR aceito.
- **Práticas que este repositório não tem:** <Konsig: CI/CD e versionamento de banco (migrations), os dois pendentes na US-43 em Backlog, upstream_16-11.csv, 16/11/2026 9h51; jornadas automatizadas na pipeline, que existem no NeoKonsig (DS-471, Code Review, downstream_16-11.csv, 16/11/2026 10h26)>. Não suponha que existem.
- **Stack:** [A CONFIRMAR no Inventário de Sistemas]. Evidência do Jira, não confirmada (`insumos/sistemas-e-tecnologias.md`, 16/11/2026): API em PHP, atualizada da 7.3 para a 8 (DS-399, DS-412, DS-432); módulos em Node (DS-78, DS-221, DS-322); websocket com Redis (DS-214, DS-226); Elastic Stack/APM, log konsig-api-v1 em ECS (DS-412); SonarQube (DS-202, DS-231); Docker (DS-168). ORM Doctrine citado como provável no DS-407 [A CONFIRMAR]. Banco: [A CONFIRMAR]. A fonte da stack é o Inventário de Sistemas (Drive `1LwSqMSxgldjHxNQmj34uDAI_refDOkWG`, não recebido), com a versão consultada citada; evidência do Jira não o substitui.
- **Responsáveis (papel):** <tech lead do sistema; PO do sistema>.

## 2. Constituição (regras sem exceção)

Regras propostas pelo kit v2 [ALÉM DA FONTE — decisão do usuário], exceto onde há fonte citada. Todo PR cita a constituição no bloco "Conferência" (seção 6). Mudar uma regra exige ADR.

1. **Konsig não é NeoKonsig** (contexto-mestre.md, seção 3, 16/11/2026). Não sugira código, biblioteca, padrão ou solução de um no outro sem ADR aceito. Se a tarefa tocar o outro sistema (por exemplo, a integração NeoKonsig–Konsig via RabbitMQ no cadastro de corban: DS-298, card do NeoKonsig, downstream_16-11.csv, 16/11/2026 10h26; contrato em `docs/integracoes/`), declare isso e pare para confirmação.
2. **Não invente requisito.** O comportamento esperado está no PRD, no card e nos ADRs. O que não estiver lá, pergunte. Proposta além disso leva [ALÉM DA FONTE — decisão do usuário] e não é implementada sem confirmação.
3. **Não invente tecnologia.** Não afirme versão, biblioteca ou infraestrutura que não esteja neste arquivo, em `docs/SISTEMA.md` ou no código. Use [A CONFIRMAR].
4. **Nenhum dado pessoal.** Não escreva CPF, CNPJ, nome de cliente, e-mail, telefone, número de contrato, de proposta ou de cartão em código, teste, fixture, log de exemplo, commit, PR ou documento. Massa de teste é sintética: fictícia no conteúdo e válida no formato. Se encontrar dado pessoal real no repositório, não o reproduza; informe o caminho do arquivo ao revisor.
5. **Dado de cartão.** CVV nunca é gravado. PAN e CVV são mascarados ou bloqueados em log e mensagem de erro, e não entram em teste (Visão do Cartão v6, risco R18, 03/11/2026). Dado completo da trilha também fica fora [ALÉM DA FONTE — decisão do usuário]. O escopo do ambiente de dados de cartão (R19) é decisão de Segurança & Conformidade, não do dev. Na dúvida se um campo é dado de cartão, trate como se fosse.
6. **Sem segredo no código.** Nada de credencial, token, endereço interno de servidor ou identificador de conta no código, no commit ou no PR.
7. **Não escreva no Jira** (D2-documentos-para-a-IA.md §4.2, controle 6, proposta [ALÉM DA FONTE — decisão do usuário]) e não altere os parâmetros da calculadora de estimativa e priorização (D2, decisão de 10/11/2026).
8. **Processo real, não sugerido** (contexto-mestre.md, seções 3 e 11, 16/11/2026). Não afirme que o time usa Fibonacci ou planning poker: não usa. Não use o documento "Melhorias Scrum TI V2" como descrição do processo atual: são sugestões não aplicadas. Tamanho de projeto é PP/P/M/G/GG pela régua (`D1-pool/regua-tamanho-tempo.md`, v1, 16/11/2026), proposta sem decisão do comitê.

Mais duas, que o kit v2 torna explícitas [ALÉM DA FONTE — decisão do usuário]:
- **Um sistema por documento.** PRD, ADR, contrato, runbook e SISTEMA.md tratam de um sistema só.
- **Teste por cenário.** Todo cenário Dado/Quando/Então do card e toda linha de tabela de decisão do PRD tem um teste com nome rastreável.

## 3. Comandos

Comando exato, copiável. Sem comando confirmado, deixe [A CONFIRMAR no Inventário] e não deixe o agente adivinhar.

| Para quê | Comando |
|---|---|
| Instalar dependências | [A CONFIRMAR no Inventário] |
| Subir o sistema local, sem depender de ambiente compartilhado | [A CONFIRMAR]. A US-43 lista como pendente "estação de trabalho executa sistema de forma auto suficiente" (upstream_16-11.csv, 16/11/2026 9h51) |
| Rodar os testes | [A CONFIRMAR no Inventário] |
| Rodar um teste só | [A CONFIRMAR no Inventário] |
| Linter / formatação | [A CONFIRMAR no Inventário] |
| Aplicar mudança de banco | Não há migrations (US-43). Ver armadilha 4 |
| Deploy | Manual. Seguir `docs/runbooks/` (RUNBOOK.md de deploy e rollback). O agente não faz deploy [ALÉM DA FONTE — decisão do usuário] |

Rode testes e linter antes de declarar a tarefa pronta e informe o resultado real, com o comando usado. Nunca declare "testes passando" sem executá-los. Serviço externo (banco, bureau, processadora, parceiro) é simulado no teste. O QA executa os cenários do card na etapa QA Teste; os testes do agente não substituem essa etapa.

## 4. Armadilhas do legado

Cada uma tem card de origem (downstream_16-11.csv, 16/11/2026 10h26). Quando uma nova armadilha custar um Bug, acrescente aqui com a chave.

1. **Quebras da atualização PHP 7.3 → 8** (depois da análise DS-399). Três padrões: tipo diferente vindo do banco/ORM (DS-407); função que agora recusa null, como array_merge (DS-412); acesso por offset de string vira erro (DS-432). O efeito chegou ao bot do GLPI (DS-409). Cubra cada padrão com teste no código que tocar.
2. **Token do usuário na URL** (DS-81). Não crie rota nova que receba token por query string. Não mude a autenticação existente sem ADR: afeta bots, painel swagger, terceiros que usam o Konsig e o gatekeeper.
3. **Lock da ficha por websocket** (DS-28). Mudança na movimentação da proposta ou na ficha considera concorrência entre usuários. Descreva no PR como testou o acesso simultâneo.
4. **DDL manual, sem migrations** (DS-93: "SE FOR SUBIR, TEM QUE ATUALIZAR O DB"). Toda mudança de esquema vai em script SQL versionado em <pasta [A CONFIRMAR]>, com script de reversão, e é citada no PR e no runbook de deploy.
5. **Erro de SQL no front** (DS-157). Nunca devolva mensagem de exceção ou SQL ao usuário. Logue o detalhe (sem dado pessoal) e devolva mensagem genérica.
6. **CPF como string.** No CRM API, CPF enviado como número quebrou a pesquisa (DS-544, Code Review, downstream_16-11.csv, 16/11/2026 10h26). Ao integrar com o CRM, envie CPF como string. Estender para "string de 11 dígitos, com zero à esquerda, em todo o Konsig" é [ALÉM DA FONTE — decisão do usuário].

## 5. Onde está a especificação

Leia antes de codar. Atualize no mesmo PR quando o comportamento mudar (nível spec-anchored: o documento vive ao lado do código). Use os modelos do kit de documentação; não crie formato novo de documento.

| O quê | Onde |
|---|---|
| Referência do sistema (contexto, integrações, riscos) | `docs/SISTEMA.md` |
| O que e por quê (RN em EARS, tabela de decisão, critérios) | `docs/prd/` |
| Como entregar, deploy, rollback, corte | `docs/planos/` |
| Decisões e ideias abandonadas (não reabra sem fato novo) | `docs/adr/` |
| Contratos com parceiros e entre sistemas | `docs/integracoes/` |
| Rotinas, deploy manual, falhas conhecidas | `docs/runbooks/` |
| Checklist de dados e regulação (obrigatório no PR que toca dado pessoal) | `docs/` ou corpo do PR |
| Postmortems e passagens | `docs/postmortems/`, `docs/passagem/` |

Repositório definitivo que recebe `docs/`: [A CONFIRMAR] (migração DS-175/DS-495). Até a definição, vale a pasta provisória definida no README do kit, seção 4 (três passos: `docs/` do repositório do Konsig em que o card abre o MR; antes de haver MR, o Drive onde a área solicitante aprova; depois da definição, `git mv` pelo tech lead) [ALÉM DA FONTE — decisão do usuário].

## 6. Roteiro antes do código e modelo de PR

Regras propostas pelo kit v2 [ALÉM DA FONTE — decisão do usuário], exceto onde há fonte citada.

**Antes do código**
1. Identifique a chave do card (`DS-n`). Sem chave, pergunte.
2. Leia, nesta ordem: card, PRD citado no card, ADRs aceitos do assunto, Plano do épico, contrato da integração tocada.
3. Item em aberto na lista de refinamento do card que bloqueie o caminho principal: pare e informe.
4. Liste os cenários que a mudança vai cobrir. Mais de sete cenários, ou título com "e": aponte que o card pode precisar de quebra.
5. Decisão técnica sem ADR (biblioteca nova, padrão de integração, formato de dado ou de log): proponha o ADR e não implemente até ser aceito.
6. PRD, card e código divergem: descreva a divergência e pergunte.
7. Toca dinheiro (pagamento, liquidação, repasse, decisão de crédito): exija ADR e um teste por linha da tabela de decisão antes de codar.

**Commit, branch e MR** seguem a convenção da organização (regras do terraform-gitlab; skill do DS-546, em Code Review, downstream_16-11.csv, 16/11/2026 10h26) [A CONFIRMAR o texto final]. Até lá, cite a chave DS-n no commit. Um commit por mudança lógica; não misture refatoração com comportamento novo.

**PR** · título `<DS-n> <título do card>`:

```
## Card
<DS-n> · <link>
## O que muda
<duas a cinco linhas, em linguagem de negócio>
## Referências
PRD: docs/prd/<arquivo> (vX.Y), seções <n> · ADR: <ADR-nnnn ou "nenhum"> · Contrato: <arquivo ou "nenhum">
## Cenários cobertos
- [ ] <Cenário ou linha da tabela de decisão> · teste <nome>
## Como testar
<comandos executados e resultado; massa fictícia>
## Fora deste PR
<o que o card prevê e ficou para outro PR>
## Riscos e rollback
<o que pode quebrar; como reverter; script de banco e reversão, se houver>
## Conferência (constituição)
- [ ] Regras 1 a 8 e "um sistema por documento" / "teste por cenário" respeitadas
- [ ] Sem dado pessoal, dado de cartão ou segredo (checklist de dados no PR, se tocou dado pessoal)
- [ ] docs/ atualizado no mesmo PR, ou motivo registrado
```

Revisor preenchido em Code Review (contexto-mestre.md §4, regra 2, experimento vigente desde a Sprint 19). Código gerado por IA tem revisão humana como qualquer outro [ALÉM DA FONTE — decisão do usuário].

## 7. Quando parar e perguntar

- O pedido toca o outro sistema (Konsig ↔ NeoKonsig).
- O comportamento pedido não está no PRD nem no card.
- A tarefa exige decisão técnica sem ADR.
- Aparece dado pessoal real, dado de cartão ou segredo.
- Um teste existente precisa ser removido ou enfraquecido para a mudança passar.

<!--
======================================== FIM DO QUE SE COPIA ========================================

REFERÊNCIAS DE MERCADO (conferir o original antes de citar em documento oficial: parte foi lida via busca em 17/11/2026)
- AGENTS.md, formato aberto: https://agents.md/
- Agentic AI Foundation (Linux Foundation, 09/12/2025), que recebeu o AGENTS.md da OpenAI: https://openai.com/index/agentic-ai-foundation/
- Claude Code, memória: CLAUDE.md é contexto, não configuração; menos de 200 linhas; bloqueio se faz com hook; lê AGENTS.md quando não há CLAUDE.md:
  https://code.claude.com/docs/en/memory
- GitHub Copilot, instruções de repositório (AGENTS.md mais próximo prevalece; conflito é não determinístico):
  https://docs.github.com/en/copilot/how-tos/configure-custom-instructions/add-repository-instructions
- Cursor rules (.mdc, modos de ativação): https://cursor.com/docs/context/rules
- Adoção: 1,6% de 10.000 repositórios abertos têm AGENTS.md; 4,7% têm algum arquivo de agente: https://arxiv.org/abs/2510.21413
- Eficácia: arquivos de contexto tendem a não melhorar a taxa de sucesso e sobem o custo em mais de 20%; ajudam quando trazem prática não padrão
  (Gloaguen et al., ETH Zurich/LogicStar.ai, fev/2026): https://arxiv.org/abs/2602.11988
- "Constitution" do GitHub Spec Kit, inspiração para a seção 2 sem adotar a ferramenta: https://github.com/github/spec-kit
- Spec-driven development em Assess no Thoughtworks Radar: https://www.thoughtworks.com/radar/techniques/spec-driven-development
-->
