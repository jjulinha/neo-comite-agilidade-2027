<!--
MODELO · Card do Jira · Kit de documentação TI Neo Crédito · v1.0 · 16/11/2026
Fonte única deste modelo: guia "Como escrever um card" (InnoviaX, v1.0, setembro de 2026), tutorial oficial de cards da TI desde 13/11/2026.
Os dez blocos, a ordem e o modelo em branco são os do guia (seções 02, 03 e 10). Este arquivo não acrescenta blocos.
As únicas adaptações à Neo estão marcadas como "Nota Neo" e não mudam o padrão do guia.
-->

# Modelo de card · padrão do guia "Como escrever um card"

## 1. Como usar

- Dez blocos, **sempre na mesma ordem**. DoR e DoD são portões; o resto é conteúdo (guia, seção 02).
- Nem todo card precisa dos dez blocos com a mesma profundidade, mas todo card passa por todos conscientemente. Bloco que não se aplica: escrever que não se aplica, e por quê, em uma linha (guia, seção 02).
- O card nasce do PRD (tamanho M ou maior) ou diretamente do item de origem (PP e P). Ver `../README.md`, seção 3.
- O que muda por tipo de item (Story, Task, Bug, Spike, Teste, Subtask) está na seção 4 deste arquivo.

> **Nota Neo · tipos no Jira.** O Downstream tem os tipos Tarefa, História, Bug, Subtask e Epic (`downstream_16-11.csv`, 16/11/2026 10h26). Os tipos do guia correspondem a eles assim: Story = História, Task = Tarefa, Bug = Bug, Subtask = Subtask. Spike e Teste não têm tipo próprio: registrar como Tarefa, com a indicação "Spike:" ou "Teste:" no título ou no campo Categorias **[ALÉM DA FONTE — decisão do usuário]**; é o caso do DS-508, card de teste do motor da Quitação registrado como Tarefa. O campo "Iniciativa" do guia corresponde, na Neo, ao item do GDP de origem (por exemplo, GDP-76); card de épico técnico sem item GDP registra "sem item GDP" **[ALÉM DA FONTE — decisão do usuário]**. Pela regra 1 do experimento em vigor desde a Sprint 19, só o PO cria História; demanda nova entra como Tarefa e passa por triagem e refinamento (`contexto-mestre.md`, seção 4).
>
> **Nota Neo · dados pessoais.** O guia pede dado concreto nos cenários de teste (seção 04). Na Neo, dado concreto é um valor **fictício**, válido no formato, que exercita a regra. Nenhum CPF, nome, contato, contrato ou número de cartão real entra no card. Ver `../README.md`, seção 6.

---

## 2. Os dez blocos

| # | Bloco | Pergunta que responde | Leitor principal |
|---|---|---|---|
| 1 | Cabeçalho e referência | De onde veio esta regra, e a que ela pertence? | todos |
| 2 | Contexto | Por que este card existe, e o que acontece hoje sem ele? | dev · negócio |
| 3 | DoR · Definition of Ready | O que precisa existir antes de este card entrar na sprint? | portão de entrada |
| 4 | História (BDD) | Quem ganha o quê, e para quê? | negócio |
| 5 | Cenários BDD | Como o sistema se comporta em cada situação? | dev · QA |
| 6 | Critérios de aceite | O que precisa ser verdade para o card ser aceito? | negócio · QA |
| 7 | Cenários de teste | Como provar, com dado concreto, que está certo? | QA |
| 8 | Requisitos não funcionais | Sob quais condições de desempenho, segurança, volume e manutenção? | dev · arquitetura |
| 9 | Dependências e pendências | O que falta, com quem, até quando? | PO |
| 10 | DoD · Definition of Done | O que precisa estar feito para este card fechar? | portão de saída |

O guia chama o bloco 9 de "Dependências e pendências" na anatomia (seção 02) e de "Dependências, riscos e pendências" no detalhamento (seção 03). É o mesmo bloco.

---

## 3. Bloco a bloco: o que entra, o que não entra, exemplo da Neo

Os itens "entra" e "não entra" são os do guia (seção 03), com uma única adaptação, marcada como Nota Neo, na linha de validação do negócio da DoD (bloco 10). Os exemplos usam a Quitação no **Konsig** (legado), épico DS-500, e são **ilustrativos**: o card real deve ser fiel ao PRD e ao Documento de Requisitos de origem, e tudo o que for além deles é sinalizado para decisão.

### Bloco 1 · Cabeçalho e referência

| Entra | Não entra |
|---|---|
| Título no formato verbo + objeto | Responsável nomeado antes da planning |
| Tipo, iniciativa e épico pai | Solução técnica no título |
| Estimativa e componentes | Sigla solta sem verbo |
| Referência ao documento de origem, com versão | |

> **Exemplo Neo · caso a corrigir.** O título real do DS-501 é "Capturar as propostas em AND - AGUARD QUITACAO e executar o motor". Ele precisa de "e" para descrever o que faz, que é sinal de card grande (guia, seção 06) e reprova no checklist da seção 7 deste arquivo. Duas saídas: reescrever o título pelo resultado, "Executar o motor sobre as propostas em AND - AGUARD QUITACAO" **[ALÉM DA FONTE — decisão do usuário]**, ou quebrar o card, se a captura tiver valor verificável sozinha.
>
> **Exemplo Neo · cabeçalho corrigido.** Título: "Executar o motor sobre as propostas em AND - AGUARD QUITACAO". Referência: seção 7 (RN01) de `docs/prd/GDP-76_quitacao-fase-2-motor.md` (v0.1, rascunho; no kit, `exemplos/quitacao/GDP-76_quitacao-fase-2-motor.md`) e, como está hoje no DS-501, "ES 1, RF1, RF1.a, RF22 (caput), PRE 1, PRE 2; tabela de decisão, linhas 1 e 2" do Documento de Requisitos V04 (26/10/2026). Iniciativa: GDP-76. Tipo: História. Épico: DS-500. Enquanto o PRD estiver em 0.x, o card não passa no DoR: a referência precisa apontar para versão aprovada (1.0 ou posterior).
>
> **Nota Neo · estimativa.** O guia prevê o campo "Estimativa" em pontos (seção 10). Na Neo, a forma de estimar o card está **em aberto**: a decisão de 10/11/2026 (Fibonacci só depois do refinamento) está em revisão desde 13/11/2026, com a proposta de tamanho PP a GG por projeto e regra "cabe ou quebra" por card; o Fibonacci não é prática atual do time. Até a decisão do comitê: deixar o campo Estimativa do card **vazio** e registrar no épico a classe de tamanho (PP a GG) pela régua **[ALÉM DA FONTE — decisão do usuário]**. Não preencher pontos.

### Bloco 2 · Contexto

| Entra | Não entra |
|---|---|
| Como funciona hoje | Solução técnica e nome de tabela |
| Qual a limitação ou o risco atual | Descrição de tela |
| O que a entrega muda | Repetição do título em outras palavras |
| O recorte: o que este card cobre | |

Três a seis linhas bastam; contexto longo é sinal de que o card deveria ser dois (guia, seção 03).

> **Exemplo Neo.** Hoje o Financeiro identifica em planilha as propostas da esteira Cartão Consignado Compra que aguardam quitação e confere as regras manualmente. Este card faz o Konsig capturar essas propostas e submetê-las ao motor, em modo sombra: nada é alterado na proposta. Fica fora: a tela de visualização (DS-505, DS-506) e a exportação (DS-507).

### Bloco 3 · DoR

| Entra | Não entra |
|---|---|
| Documento, manual ou leiaute disponível | Tarefa de desenvolvimento |
| Decisão de arquitetura tomada | Item impossível de marcar como cumprido |
| Acesso, ambiente ou credencial liberados | Desejo genérico de entender melhor |
| Confirmação pendente de terceiro | |
| Dúvida de negócio respondida | |

Todo item precisa ser verificável com sim ou não por alguém que não escreveu o card (guia, seção 03).

> **Exemplo Neo.** Documento de Requisitos V04 (26/10/2026), seção da tabela de decisão, disponível para o time. Tela de Administração de Quitação com os ajustes apontados no teste de 09/11/2026 concluída (pré-requisito do DS-500). ADR do padrão de registro de auditoria em status Aceito [ALÉM DA FONTE — decisão do usuário: só se houver decisão técnica nova].
>
> **Nota Neo.** A DoR oficial da TI está nas Políticas Explícitas V1. Os itens do bloco 3 são os específicos deste card e não substituem a DoR das Políticas.

### Bloco 4 · História, no formato BDD

```
Como um <perfil>
Eu quero <ação ou capacidade>
Para que <benefício>
```

O "para que" não pode repetir a ação. Em card técnico sem usuário final direto, a história vira frase de objetivo, mantendo o "para que" (guia, seção 03).

> **Exemplo Neo (história real do DS-501, `downstream_16-11.csv`, 16/11/2026 10h26).** Como Financeiro, quero que o motor avalie automaticamente as propostas aguardando quitação, para não depender do download do relatório nem da planilha (D01). O código D01 vem do Documento de Requisitos V04 e não tem descrição nas fontes [A CONFIRMAR].

### Bloco 5 · Cenários BDD

```
Cenário: <título curto da situação>
Dado que <estado inicial verificável>
Quando <uma ação>
Então <resultado observável>
```

Seis regras (guia, seção 05): um comportamento por cenário; um Quando por cenário; o Então observável por quem lê o card; linguagem de negócio; o Dado descreve estado, não ação; cenário nomeado. Cobrir os quatro caminhos: feliz, alternativo, borda e falha. Entre três e sete cenários na maioria dos cards; mais de sete indica card grande (seção 06).

> **Exemplo Neo (caminho feliz).** Cenário: proposta elegível avaliada. Dado que existe uma proposta da esteira Cartão Consignado Compra na situação AND - AGUARD QUITACAO e há regras vigentes cadastradas, quando o motor é executado, então a avaliação da proposta fica registrada com a decisão final e a situação da proposta permanece a mesma.
>
> **Exemplo Neo (alternativo).** Cenário: proposta de outra situação. Dado que existe uma proposta da mesma esteira em situação diferente de AND - AGUARD QUITACAO, quando o motor é executado, então a proposta não é avaliada.

### Bloco 6 · Critérios de aceite

| Entra | Não entra |
|---|---|
| Regras gerais, limites e formatos | Advérbio: rapidamente, adequadamente, de forma intuitiva |
| Prazos, periodicidades e janelas | Critério que não vira teste |
| Exigências de registro e auditoria | Detalhe de implementação |
| Comportamento em falha | |

Teste rápido: o critério vira uma linha de teste com resposta sim ou não? (guia, seção 03).

> **Exemplo Neo.** O motor avalia apenas propostas da esteira Cartão Consignado Compra na situação AND - AGUARD QUITACAO (critério do DS-501). Nenhuma avaliação altera situação ou status da proposta (DS-500). Toda avaliação, com sucesso ou falha, fica registrada e pode ser consultada.

### Bloco 7 · Cenários de teste

| Ação (com dado concreto) | Resultado esperado |
|---|---|
| ... | ... |

O cenário BDD descreve a regra; o cenário de teste exercita a regra com valor concreto (guia, seção 03). Numerar T1, T2... para que bug e evidência possam citá-los (guia, seção 08).

> **Exemplo Neo (massa fictícia).** T1 · Executar o motor com uma proposta fictícia na situação AND - AGUARD QUITACAO e uma regra vigente com resultado PAGAR · avaliação registrada com decisão PAGAR; situação da proposta inalterada. T2 · Executar com uma proposta fictícia em outra situação · nenhuma avaliação registrada para ela.

### Bloco 8 · Requisitos não funcionais

Só o que for específico deste card: tempo máximo de resposta, volume esperado, trilha de auditoria, teste automatizado com simulação de serviço externo, retenção de dado. Repetir a política geral em todo card treina o time a pular o bloco (guia, seção 03).

> **Exemplo Neo.** Teste automatizado das regras do motor com a tabela de decisão e os exemplos do Anexo I do Documento de Requisitos V04 (DS-508). Volume por execução: [A CONFIRMAR com o Financeiro].

### Bloco 9 · Dependências e pendências

Toda pendência tem três partes: o que falta, quem responde e o prazo. "A DEFINIR" é aceitável no card que entra na sprint apenas se não bloquear o caminho principal, e sempre com dono e data; se bloquear, o card não passa no DoR (guia, seção 03).

> **Exemplo Neo.** A DEFINIR: horário da execução agendada (PC-05) não descrito · responsável: PO com o Financeiro · até [data] · não bloqueia o caminho principal, porque a execução pode ser verificada pelo botão "Reavaliar", que o próprio DS-501 já define.

### Bloco 10 · DoD

| Entra | Não entra |
|---|---|
| Código revisado e integrado | Repetição dos critérios de aceite |
| Testes automatizados implementados e passando | Item que depende de terceiro sem prazo |
| Cenários executados e evidenciados | |
| Validação do negócio, pela área e pelo papel (Nota Neo: o guia pede o nome de quem validou; na Neo, o nome fica no responsável da etapa Aprovação POs no Jira) | |
| Documentação e configuração atualizadas | |

Critério de aceite fala do comportamento do produto; DoD fala do estado do trabalho. Restrição de ambiente entra aqui explicitamente (guia, seção 03).

> **Nota Neo.** A validação do negócio registra no card a área e o papel; o nome de quem validou fica no responsável da etapa Aprovação POs do Jira, campo obrigatório pela regra 2 do experimento S19. Para ir a Concluído, o card precisa de Categorias, Descrição, Classe de serviço e Tipo (regra 3). A DoD oficial está nas Políticas Explícitas V1 [A CONFIRMAR o texto vigente].

---

## 4. O que muda por tipo de item (guia, seção 07)

| Tipo | O que muda | Cuidado principal |
|---|---|---|
| Story (História) | Padrão completo, com história, cenários e critérios | Garantir que existe usuário e benefício reais, e não uma tarefa técnica disfarçada |
| Task (Tarefa) | Trabalho técnico sem usuário final direto. A história vira frase de objetivo; critérios e cenários permanecem | Não deixar o card sem critério de aceite só porque é técnico |
| Bug | O contexto vira reprodução: passos, resultado esperado e resultado obtido. Obrigatórios o card de origem, a causa raiz e a fase em que foi detectado | Descrever o sintoma com dado real (na Neo: dado de reprodução fictício; nunca copiado de produção, nem mascarado) |
| Spike | Contexto, pergunta a responder, prazo máximo e formato da resposta. Critério de conclusão da investigação, não de comportamento | Spike sem prazo vira pesquisa infinita |
| Teste | Deriva dos cenários de um card de entrega e aponta para ele | Referenciar o card de origem, não reescrever o critério |
| Subtask (Subtarefa) | Herda o contexto do card pai e divide execução | Subtask divide trabalho, nunca entendimento |

> **Nota Neo · Bug.** Na exportação de 16/11/2026 10h26, 1 dos 31 Bugs do Downstream menciona causa raiz na descrição (`downstream_16-11.csv`). O bloco de Bug é o que mais falta na prática.

---

## 5. Quando quebrar (guia, seção 06)

**Sinais de card grande demais:** mais de sete cenários ou critérios de assuntos independentes; título que precisa de "e"; estimativa acima do teto combinado pelo time ou sem confiança; mais de um perfil de usuário na história; parte do card depende de decisão inexistente enquanto outra parte está pronta.

| Critério de quebra | Quando usar |
|---|---|
| Por regra de negócio | Cada regra tem valor próprio e pode ser validada sozinha. É a melhor quebra |
| Por tipo de documento ou fluxo | O card cobre vários artefatos com regras distintas |
| Por caminho | Caminho feliz primeiro, falha e contingência depois; só se o caminho feliz puder ir para produção com segurança |
| Por etapa do processo | Existe sequência clara, como enviar, receber retorno e tratar retorno |

**Como não quebrar:** por camada técnica (front e back), por pessoa que vai executar, ou em "parte 1" e "parte 2" sem que cada parte entregue algo verificável.

> **Nota Neo · teto.** O "teto combinado pelo time" citado pelo guia ainda não existe na Neo: depende da decisão do comitê sobre a regra "cabe ou quebra" **[A CONFIRMAR]**. Referência medida: na Sprint 18, a mediana da História foi 118h para uma sprint de 75h úteis (Review da Sprint 18, extração de 06/11/2026 16h46).

---

## 6. Modelo em branco (guia, seção 10)

Copie o bloco abaixo para a descrição do card no Jira.

```
TÍTULO: <verbo> <objeto>
Referência: <RF ou regra>, em <documento> (<versão>)
Tipo: <Story | Task | Bug | Spike | Teste>   (no Jira da Neo: Spike e Teste como Tarefa, ver Nota Neo da seção 1)
Iniciativa: <item GDP>      Épico: <nome>        Estimativa: <vazio; classe do épico pela régua — ver Nota Neo do bloco 1>

CONTEXTO
Como funciona hoje, qual a limitação, o que esta entrega muda
e o que fica fora do escopo. Três a seis linhas.

DoR
- <condição externa verificável>
- <decisão que precisa estar tomada>
- <acesso, ambiente ou dado necessário>

HISTÓRIA
Como um <perfil>
Eu quero <capacidade>
Para que <benefício, que não repete a ação>

CENÁRIOS
Cenário: <situação, caminho feliz>
Dado que <estado>, quando <uma ação>, então <resultado observável>.

Cenário: <situação alternativa>
Dado que ..., quando ..., então ...

Cenário: <borda ou limite>
Dado que ..., quando ..., então ...

Cenário: <falha ou indisponibilidade>
Dado que ..., quando ..., então ...

CRITÉRIOS DE ACEITE
- <afirmação binária com número, prazo ou formato>
- <comportamento exigido em falha>
- <exigência de registro ou auditoria>

CENÁRIOS DE TESTE
| Ação (com dado concreto) | Resultado esperado |
| ...                      | ...                |

REQUISITOS NÃO FUNCIONAIS
<somente o que é específico deste card>

DEPENDÊNCIAS E PENDÊNCIAS
- A DEFINIR: <o que falta> · responsável: <quem> · até <data>
  <bloqueia ou não o caminho principal>

DoD
- Código revisado e integrado
- Testes automatizados implementados e passando
- Cenários executados e evidenciados
- Validação do negócio por <área e papel>
- Documentação atualizada
```

> **Nota Neo · DoD do modelo em branco.** O guia traz "<nome ou área>"; na Neo o texto passa a "<área e papel>" (por exemplo, "área Financeiro, PO"), pela regra de não citar pessoas (`../README.md`, seção 6). Preencher "Validação do negócio" com a **área e o papel** (por exemplo, "área Financeiro, PO"); o nome de quem validou fica registrado no responsável da etapa Aprovação POs do Jira (regra 2 do experimento S19), e não na descrição do card.

As alterações em relação ao modelo do guia são quatro: o campo Estimativa (vazio, por causa da decisão em aberto descrita no bloco 1); o campo Iniciativa (item GDP); a observação do campo Tipo, porque o Jira da Neo não tem os tipos Spike e Teste; e "Validação do negócio por <área e papel>" no lugar de "<nome ou área>".

---

## 7. Checklist antes do refinamento (guia, seção 10)

- [ ] O título começa com verbo e não precisa de "e" para descrever o que faz.
- [ ] A referência ao documento de origem está escrita, com versão.
- [ ] O contexto diz como é hoje, o que muda e o que fica fora do escopo.
- [ ] Todo item do DoR é verificável com sim ou não por quem não escreveu o card.
- [ ] O "para que" da história não repete a ação em outras palavras.
- [ ] Cada cenário tem título, um único Quando e um Então observável.
- [ ] Os cenários cobrem caminho feliz, alternativo, borda e falha.
- [ ] Cada critério de aceite é binário e não usa advérbio.
- [ ] Os números (limites, prazos, janelas, formatos) estão nos critérios.
- [ ] Os cenários de teste têm dado concreto, e não descrição genérica.
- [ ] Os requisitos não funcionais são específicos deste card.
- [ ] Toda pendência tem o que falta, quem responde e até quando.
- [ ] Nenhum A DEFINIR bloqueia o caminho principal.
- [ ] O DoD fala do estado do trabalho, não do comportamento do produto.
- [ ] O card cabe numa sprint com folga, e tem entre três e sete cenários.
- [ ] Um leitor que não participou da conversa saberia o que construir e como provar.
- [ ] **Nota Neo:** nenhum dado pessoal real no card, inclusive nos cenários de teste.
