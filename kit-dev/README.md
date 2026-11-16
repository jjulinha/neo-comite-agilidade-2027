# Kit de documentação para desenvolvimento · TI Neo Crédito

| Item | Valor |
|---|---|
| Documento | Kit de modelos de documentação de demanda (PRD, ADR, Plano de Implementação, Card, CLAUDE.md) |
| Versão | 1.0 · proposta para o Comitê de Agilidade |
| Data | 16/11/2026 |
| Situação | **Proposta.** Nenhum modelo deste kit está aprovado. A adoção depende de decisão registrada em DACI no comitê (decisão de 10/11/2026: um tema por reunião). |
| Relação com as demandas do comitê | Concretiza o documento 6 do conjunto mínimo da Demanda 2 ("Modelo de documento de visão e requisito", `D2-documentos-ia/D2-documentos-para-a-IA.md`, seção 5) e alimenta indicadores da Demanda 3 (seção 9 deste README). |

**Convenções usadas em todo o kit**

- **[A CONFIRMAR]**: informação que deveria existir em documento oficial da Neo, mas que não foi recebida (por exemplo, o Inventário de Sistemas).
- **[ALÉM DA FONTE — decisão do usuário]**: proposta deste kit que não está em nenhuma fonte e precisa de decisão.
- Todo número traz a fonte e a data de extração. As contagens desta pasta foram feitas sobre as exportações do Jira de 16/11/2026 (GDP e Upstream às 9h51; Downstream às 10h26).
- **Konsig** (legado) e **NeoKonsig** (reescrita) são sistemas distintos, com tecnologias distintas. Todo documento do kit declara um, e só um, sistema. Uma demanda que toque os dois gera documentos separados, ligados por referência cruzada.
- Exemplos usam papéis (PO, tech lead, dev, revisor, QA, área solicitante), nunca nomes de pessoas.

---

## 1. Para que serve o kit

O kit resolve um problema medido, não estético. Na exportação do Downstream de 16/11/2026, 10h26 (`downstream_16-11.csv`), entre os 363 cards (Tarefa, História e Bug):

| O que o card traz na descrição | Cards | Critério de contagem |
|---|---|---|
| Nenhuma descrição | 80 de 363 | campo vazio |
| História no formato "eu quero" | 23 de 363 | texto "eu quero" |
| Critério de aceite | 21 de 363 | "critério(s) de aceite" |
| Cenário com "Dado" e "Então" | 4 de 363 | as duas palavras no texto |
| DoR | 14 de 363 | "DoR" ou "Definition of Ready" |
| DoD | 0 de 363 | "DoD" ou "Definition of Done" |
| Bug com causa raiz | 1 de 31 Bugs | "causa raiz" |

E a rastreabilidade entre os boards é parcial: 15 dos 35 épicos do Downstream têm item do GDP associado (`downstream_16-11.csv`, 16/11/2026 10h26), e o GDP-76 (Quitação), em Downstream, não aponta para nenhum épico (`gdp_16-11.csv`, 16/11/2026 9h51).

O guia "Como escrever um card" (InnoviaX v1.0, set/2026) é o tutorial oficial de cards desde 13/11/2026 (`contexto-mestre.md`, seção 6). Ele define o card, mas não define o documento de onde o card sai. A referência obrigatória do bloco 1 do card ("referência ao documento de origem, com versão") pressupõe que esse documento exista. Este kit fornece o documento de origem (PRD), o registro das decisões técnicas e de padrão (ADR) e o plano que transforma o PRD em épicos e cards (Plano de Implementação).

**O que o kit não faz:** não substitui o Fluxo de Desenvolvimento TI V3, as Políticas Explícitas V1 nem o Documento de Visão de projetos grandes. Ele se encaixa neles. Onde um modelo do kit conflitar com um desses documentos, o conflito vira um ADR de mudança de documentação (seção 4.3), e não uma regra silenciosa.

---

## 2. O fluxo de documentação de uma demanda

```
GDP ──► Upstream ──────────────────────────────► Downstream ─────────────────────────► Registro
 item    PRD (+ ADR se houver decisão)            Plano de Implementação → cards
 GDP-n   US-n                                     épico DS-n → cards DS-n
                                                  Em desenvolvimento → Code Review → QA Teste →
                                                  Aprovação POs → Waiting for deploy → Concluído
```

| Etapa | Board e status no Jira | Documento do kit | Quem escreve | Quem aprova | Saída que libera a etapa seguinte |
|---|---|---|---|---|---|
| 1. Entrada da demanda | Gestão de Projetos (GDP), Backlog Upstream → Priorização Upstream | Nenhum. Usa o roteiro de abertura do GDP (Solicitante, Área solicitante, Contexto da solicitação, Descrição do problema ou necessidade, Como o processo funciona atualmente, Consequências do cenário atual), já usado em 62 de 90 itens (`gdp_16-11.csv`, 16/11/2026 9h51) | Área solicitante | Gestão da TI (priorização) | Item GDP priorizado |
| 2. Análise funcional | Upstream: Análise funcional | **PRD** (seções 1 a 8) | Analista funcional / PO | — | PRD em revisão |
| 3. Prototipação | Upstream: Prototipação | PRD, seção 9 (fluxo proposto) com link do protótipo | Analista / UX | Área solicitante | Protótipo validado |
| 4. Especificação técnica + testes | Upstream: Especificação técnica + testes | PRD completo + **ADR** quando houver decisão técnica, de padrão ou de documentação | PO + tech lead | PO (PRD); tech lead e comitê, conforme o caso (ADR) | PRD aprovado; ADR aceito |
| 5. Aprovação | Upstream: Aprovação solicitantes → Concluído Upstream | PRD com seção de aprovações preenchida e **tamanho estimado pela régua** (Políticas Explícitas V1, seção 3.8: dimensionamento inicial obrigatório ao concluir no Upstream) | PO | Área solicitante | Demanda pronta para o Downstream |
| 6. Planejamento | Downstream: criação do épico (projeto = épico, decisão de 13/11/2026) | **Plano de Implementação** | Tech lead + PO | PO | Épico e cards criados no Jira |
| 7. Cards | Downstream: Backlog | **Card** no padrão do guia, um por unidade verificável | PO (Histórias, regra 1 do experimento S19); time (Tarefas) | Refinamento | Card que passa no DoR |
| 8. Construção e teste | Em desenvolvimento → Code Review → QA Teste → Aprovação POs | Card (cenários de teste e DoD); Plano (plano de teste) | Dev, revisor, QA, PO, com responsável obrigatório em cada etapa (regra 2 do experimento S19) | PO | Card aprovado |
| 9. Implantação | Waiting for deploy → Concluído | Plano (ambientes, deploy e rollback) | Tech lead / infraestrutura | Tech lead | Em produção |
| 10. Registro | Concluído (com Categorias, Descrição, Classe de serviço e Tipo, regra 3 do experimento S19) | PRD e Plano com status final; ADR com status atualizado; realizado × estimado registrado na régua | PO + tech lead | — | Documentos fechados |

Os status do Upstream e do Downstream acima são os presentes nas exportações de 16/11/2026 (`upstream_16-11.csv`, 9h51; `downstream_16-11.csv`, 10h26) e no fluxo do `contexto-mestre.md`, seção 3. A coluna "Documento do kit" é proposta **[ALÉM DA FONTE — decisão do usuário]**.

---

## 3. Qual documento usar, por tamanho

O tamanho é o da régua de tamanho × tempo (`D1-pool/regua-tamanho-tempo.md`, versão 1, 16/11/2026), medido em cards de épico. As faixas PP a GG **são proposta, sem decisão do comitê** (`contexto-mestre.md`, seção 7).

| Tamanho | Cards de épico | Documentos | Tempo de referência no Downstream (dias úteis, típico / conservador) | Observação |
|---|---|---|---|---|
| **PP** | 1–2 | **Só o card**, com o bloco 1 apontando para o item GDP ou US de origem | 16 / 29 (faixa PP–M agregada) | Ajuste pequeno sem tela nem integração: Upstream de referência 5 / 10 dias úteis (proposta da régua) |
| **P** | 3–4 | **Só os cards**, todos com a mesma referência de origem | 16 / 29 | Se houver regra de negócio nova que vale para mais de um card, sobe para PRD curto |
| **M** | 5–9 | **PRD curto + Plano curto** | 16 / 29 | PRD curto: seções 1, 2, 3, 4, 7, 10, 11, 14 e 15 do modelo obrigatórias; as demais com "não se aplica" e o motivo |
| **G** | 10–20 | **PRD completo + Plano com entregas + ADR se houver decisão** | 66 (piso) / 86 | A régua recomenda avaliar a quebra de todo G em entregas M, porque os três G abertos já passaram de 66 dias úteis |
| **GG** | > 20 | **Quebrar antes de documentar.** Um PRD-mãe (visão do todo, regras comuns, fora de escopo) e **um Plano por entrega** (cada entrega G ou M, com seu épico) | não estimar | Regra proposta da régua: GG não entra no pool sem quebra |

Referência do Upstream para todas as classes (da criação à conclusão no Upstream): 29 dias úteis típico, 44 conservador. O tamanho não prevê o tempo do Upstream; o que pesa é a espera por aprovação e priorização (`D1-pool/regua-tamanho-tempo.md`, seção 3).

**Exemplos da realidade da Neo (épicos do Downstream, `epicos_downstream_16-11.csv`, 16/11/2026 10h26):**

- Quitação Fase 1 (DS-418, Konsig, 2 cards) → PP: só os cards.
- Quitação Fase 2 (DS-500, Konsig, 8 cards) → M: PRD curto, já existente na prática como "Documento de Requisitos V04", e Plano curto.
- Correção de vulnerabilidades (DS-65, Konsig, 20 cards) → G: PRD + Plano + ADR para cada mudança de padrão de segurança.
- Parceiros, Entrega 1 (DS-251, NeoKonsig, 83 cards) → GG: o modelo pede PRD-mãe do Módulo de Parceiros e um Plano por entrega.
- Cartão de crédito consignado (GDP-38, Konsig legado, decisão de 13/11/2026) → GG: a Visão do Cartão v6 (03/11/2026) faz o papel de PRD-mãe, depois de corrigida para o Konsig legado; cada bloco do estimador vira uma entrega com Plano próprio.

**ADR independe do tamanho.** Um card PP que muda um padrão (por exemplo, o formato de log ou a versão do PHP do Konsig) gera ADR. Um G sem decisão técnica nova não gera.

**Quando abrir um ADR (qualquer tamanho):**

1. Escolha de tecnologia, biblioteca, padrão de integração ou de dados que outro time terá de seguir.
2. Decisão que afeta os dois sistemas (Konsig e NeoKonsig), como a delimitação de fonte única de verdade entre eles.
3. **Mudança de documentação ou de padrão de processo**: alteração em Fluxo de Desenvolvimento V3, Políticas Explícitas V1, guia de cards, régua de tamanho ou neste kit.
4. Decisão que inverte ou substitui um ADR anterior.

---

## 4. Onde guardar, nomes, versionamento e status

### 4.1 Local **[ALÉM DA FONTE — decisão do usuário]**

Os documentos ficam no repositório do sistema afetado, na pasta `docs/`, para que versão do código e versão do documento andem juntas e a IA leia os documentos no mesmo lugar do código:

```
<repositório do sistema>/
├── CLAUDE.md                         ← instruções para assistentes de IA (modelo em modelos/CLAUDE.md)
└── docs/
    ├── prd/        GDP-76_quitacao-fase-2-motor.md
    ├── adr/        ADR-0001_DS-412_log-no-formato-ecs.md
    ├── planos/     DS-500_plano-quitacao-fase-2.md
    └── README.md   índice: chave do Jira, título, status, versão
```

- Demanda do Konsig: repositório do Konsig. Demanda do NeoKonsig: repositório do NeoKonsig. Nunca um documento único para os dois.
- O Konsig está em migração de repositórios para o GitLab gerenciado (DS-175, há 6 sprints em aberto segundo a Review da Sprint 18, 06/11/2026 16h46). Até a conclusão, qual repositório do Konsig recebe a pasta `docs/` é **[A CONFIRMAR]**.
- O Documento de Visão de projetos grandes e os documentos de requisito hoje guardados no Drive continuam no Drive. O PRD do repositório aponta para eles pelo ID do Drive; não os copia.

### 4.2 Nomes de arquivo

| Documento | Padrão do nome | Exemplo |
|---|---|---|
| PRD | `<chave GDP>_<assunto-em-minúsculas>.md`. Sem item GDP (demanda técnica): `<chave US>_...` | `GDP-76_quitacao-fase-2-motor.md` |
| PRD de entrega de um GG | `<chave GDP>_E<n>_<assunto>.md` | `GDP-29_E1_parceiros-ficha-cadastro.md` |
| ADR | `ADR-<número sequencial de 4 dígitos por repositório>_<chave do item que motivou>_<assunto>.md` | `ADR-0003_US-43_pipeline-ci-konsig.md` |
| Plano | `<chave do épico DS>_plano-<assunto>.md` | `DS-500_plano-quitacao-fase-2.md` |

### 4.3 Versionamento e status

Cada documento tem, no cabeçalho, a tabela de versionamento no mesmo formato da Visão do Cartão v6 (data, responsável, descrição), com o responsável registrado pelo **papel** (PO, tech lead).

- Versão `0.x` enquanto o status for Rascunho ou Em revisão; `1.0` na aprovação; `1.1`, `1.2` para ajustes que não mudam escopo; `2.0` para mudança de escopo, que exige nova aprovação e revisão dos cards afetados (é pelo bloco 1 do card que se acham os cards que citam a versão anterior).
- Toda alteração entra por commit e por pull request; o histórico do Git é a trilha de auditoria. A tabela de versionamento do documento resume as versões que contam para o negócio.

| Documento | Status possíveis |
|---|---|
| PRD | Rascunho · Em revisão · Aprovado · Em execução · Concluído · Substituído |
| ADR | Proposto · Aceito · Rejeitado · Substituído (por ADR-nnnn) · Obsoleto |
| Plano | Rascunho · Aprovado · Em execução · Concluído · Cancelado |

### 4.4 Ligação com o Jira

| Board | Prefixo | O que o documento registra | O que o item do Jira registra |
|---|---|---|---|
| Gestão de Projetos | `GDP-` | PRD: chave GDP no cabeçalho e no nome do arquivo | Link para o PRD no campo de descrição ou em link remoto |
| Upstream | `US-` | PRD: chaves US das subtarefas de análise, prototipação e especificação | Link para o PRD e para os ADRs |
| Downstream | `DS-` | Plano: chave do épico e lista das chaves dos cards; ADR: chave que motivou | Card: bloco 1 com "Referência: <seção do PRD>, em <arquivo> (<versão>)" |

Regra mínima de rastreabilidade: **GDP ↔ US ↔ épico DS** associados no Jira e citados no PRD. Hoje esse vínculo falta em casos de projeto prioritário: o GDP-76 não aponta para o US-69, o DS-418 nem o DS-500 (`insumos/quitacao-estado-e-faseamento.md`, seção 4.3).

---

## 5. Como a IA usa o kit

### 5.1 O que fornecer de entrada

| Para produzir | Entregue à IA | Não entregue |
|---|---|---|
| PRD | Descrição do item GDP já anonimizada; anotações da análise funcional; o modelo `modelos/PRD.md`; o `CLAUDE.md` do repositório | Planilhas operacionais com dados de clientes; contratos; prints de tela com CPF ou nome |
| ADR | Contexto técnico escrito pelo tech lead; ADRs anteriores do repositório; trecho do Inventário de Sistemas | Credenciais, endereços internos de servidores, identificadores de contas |
| Plano | PRD aprovado; ADRs aceitos; régua de tamanho; o modelo `modelos/PLANO-DE-IMPLEMENTACAO.md` | — |
| Cards | PRD aprovado; Plano; o modelo `modelos/CARD.md`; o guia InnoviaX | Massa de produção para os cenários de teste |
| Código | PRD, ADR, Plano e card; `CLAUDE.md` do repositório | — |

### 5.2 O que a IA devolve

- Rascunho do documento no modelo, com cada lacuna marcada **[A CONFIRMAR]** e cada acréscimo marcado **[ALÉM DA FONTE — decisão do usuário]**.
- Lista de perguntas abertas, cada uma com quem responde (papel).
- Sugestão de quebra dos cards pela seção 06 do guia, com o critério usado.
- Cenários de teste com **massa sintética**, válida no formato e fictícia no conteúdo.

### 5.3 O que exige revisão humana, sempre

| Item | Quem revisa |
|---|---|
| Regras de negócio e critérios de aceite do PRD e dos cards | PO e área solicitante |
| Decisão do ADR e alternativas descartadas | Tech lead; comitê quando for mudança de padrão ou de documentação |
| Tamanho estimado e datas do Plano | PO e tech lead, contra a régua (os parâmetros da régua são editados só pelo responsável, decisão de 10/11/2026) |
| Sistema afetado (Konsig ou NeoKonsig) | Tech lead |
| Ausência de dado pessoal no texto final | Autor do documento, antes do commit |
| Código gerado | Revisor no Code Review e QA no QA Teste, como qualquer código |

A IA não decide prioridade, não altera parâmetros da régua, não escreve no Jira e não é conectada a ele enquanto a regra de uso de IA (documento 1 da Demanda 2) não estiver aprovada e o conector Atlassian não tiver sido validado com a segurança (`contexto-mestre.md`, seção 9; `D2-documentos-ia/D2-documentos-para-a-IA.md`, seção 4.2).

---

## 6. Regra de LGPD para todos os documentos do kit

1. **Nenhum dado pessoal** em PRD, ADR, Plano, card ou `CLAUDE.md`: nada de CPF, CNPJ de pessoa física empresária, nome de cliente, e-mail, telefone, matrícula, número de contrato ou de proposta real, nem número de cartão. Isso vale também para exemplos, cenários de teste, prints e anexos.
2. **Pessoas da Neo por papel**, não por nome: "PO", "tech lead", "dev", "revisor", "QA", "área Financeiro".
3. **Massa de teste sintética.** O guia pede dado concreto nos cenários de teste (seção 04) e usa CPF como exemplo de campo (seção 03). Dado concreto aqui significa um valor fictício que exercita a regra (por exemplo, "CPF com dígito verificador inválido", "proposta fictícia na situação AND - AGUARD QUITACAO"), nunca um valor copiado de produção.
4. **Dado de cartão nunca entra**, nem mascarado: PAN, CVV e trilha ficam fora de qualquer documento, log de exemplo ou prompt de IA (Visão do Cartão v6, riscos R18 e R19, 03/11/2026).
5. **O PRD declara o tratamento de dado pessoal da demanda** (seção 12 do modelo): quais categorias de dado a funcionalidade trata, a finalidade, o mascaramento por perfil e a retenção. Declarar o tratamento é diferente de expor o dado.
6. **Antes do commit**, o autor confere o documento contra os itens 1 a 4. A anonimização automática das exportações do Jira já deixou resíduos (quatro ocorrências de e-mail codificado em URL; `D2-documentos-ia/D2-documentos-para-a-IA.md`, seção 4.1, risco R3), por isso a conferência humana não é opcional.

Os itens 1 a 6 são proposta **[ALÉM DA FONTE — decisão do usuário]** e devem ser conciliados com a regra de uso de IA e de anonimização, que depende de parecer do DPO.

---

## 7. Conteúdo da pasta

| Arquivo | Para quê | Quando usar |
|---|---|---|
| `README.md` | Este guia de uso | Antes do primeiro uso |
| `modelos/PRD.md` | Documento de Requisitos de Produto | M, G e GG (PRD-mãe) |
| `modelos/ADR.md` | Registro de decisão técnica, de padrão ou de documentação | Sempre que houver decisão, em qualquer tamanho |
| `modelos/PLANO-DE-IMPLEMENTACAO.md` | Do PRD ao épico e aos cards, com teste, deploy e rollback | M, G e cada entrega de um GG |
| `modelos/CARD.md` | Card no padrão do guia InnoviaX (dez blocos) | Todo card |
| `modelos/CLAUDE.md` | Instruções para assistentes de IA no repositório do sistema | Uma vez por repositório (Konsig e NeoKonsig têm arquivos distintos) |

---

## 8. Decidido, em aberto, bloqueado

| Situação | Item |
|---|---|
| **Decidido** | Guia InnoviaX como tutorial de cards (13/11/2026). Projeto = épico (13/11/2026). Regras do Downstream da S19 (10/11/2026). Konsig e NeoKonsig distintos; cartão no Konsig legado (13/11/2026). |
| **Em aberto** | Adoção deste kit. Faixas PP a GG e referências de tempo da régua. Teto de tamanho do card ("cabe ou quebra"), que o guia cita na seção 06 e que ainda não existe. Repositório que recebe `docs/` no Konsig. Status e numeração propostos na seção 4. |
| **Bloqueado** | Tecnologias por sistema no `CLAUDE.md`: dependem do Inventário de Sistemas, não recebido. Uso da IA com conteúdo do Jira: depende da regra de uso de IA (Demanda 2, documento 1). |

---

## 9. Como medir a adoção do kit (insumo para a Demanda 3)

Os indicadores abaixo podem ser medidos já com as exportações do Jira, sem ferramenta nova. A linha de base é a da seção 1 (`downstream_16-11.csv`, 16/11/2026 10h26). As metas são **[meta é proposta — decisão da gestora]** e devem ser conciliadas com `D3-indicadores/D3-indicadores-2027.md` para não criar conjunto paralelo.

| Indicador | Fórmula | Linha de base (16/11/2026) | Meta proposta para o fim do 1º trimestre de 2027 |
|---|---|---|---|
| Cards com descrição | cards com descrição ÷ cards (Tarefa, História, Bug) criados no período | 283 de 363 (78,0%) | 100% (já exigido para concluir pela regra 3 da S19) |
| Cards com critério de aceite | cards com bloco de critérios ÷ cards criados no período | 21 de 363 (5,8%) | 80% das Histórias |
| Cards com cenário BDD | cards com "Dado … Então" ÷ cards criados no período | 4 de 363 (1,1%) | 60% das Histórias |
| Bugs com card de origem e causa raiz | Bugs com os dois ÷ Bugs criados no período | 1 de 31 (3,2%) | 70% |
| Épicos ligados ao GDP | épicos com item GDP associado ÷ épicos criados no período | 15 de 35 (42,9%) | 100% dos épicos de projeto (épicos técnicos sem GDP registrados como tal) |
| Demandas M ou maiores com PRD | épicos M+ com link para PRD ÷ épicos M+ abertos no período | não medido (o PRD não existe ainda) | 100% dos novos |

Contagem por busca de texto na descrição, sem leitura manual; pode haver falso positivo ou negativo. A medição recorrente deve usar o mesmo critério para manter a comparação.
