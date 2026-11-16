# Demanda 2 · Conjunto de documentos de que a IA precisa para apoiar a TI

**Comitê de Agilidade · TI Neo Crédito**
**Solicitação nº 2 da reunião inicial de 12/11/2026:** "Conjunto de documentos que a IA precisa para nos auxiliar · padrões de mercado"
**Versão:** 1.0 · **Data:** 16/11/2026 · **Situação:** proposta para deliberação em reunião própria do comitê (regra de um tema por reunião, decisão de 10/11/2026)

**Convenções deste documento**

- Todo número traz a fonte entre parênteses, com o arquivo do pacote e a data de extração ou de versão. A lista completa está na seção 7.
- O que vai além do documento-fonte está marcado como **[ALÉM DA FONTE — decisão do usuário]**.
- Konsig (sistema legado) e NeoKonsig (reescrita) são tratados como sistemas distintos.
- Nenhum trecho de norma ou publicação de mercado foi transcrito; as referências de mercado aparecem apenas como base conceitual.

---

## 1. Reformulação do pedido

### 1.1 Problema real

O pedido não é uma lista de leitura para a IA. É a definição de **quais tarefas da TI a IA vai apoiar e qual documento oficial cada tarefa exige como entrada**, para que a IA produza resultado aderente ao processo da Neo e não ao "padrão genérico" do modelo. Sem esse conjunto, a IA preenche lacunas com suposições, e o primeiro exemplo concreto disso já está no acervo: o Fluxo de Desenvolvimento TI V3 ainda cita Fibonacci, prática que o time não adota hoje (contexto-mestre.md, seção 3, 16/11/2026). Uma IA alimentada com esse documento sem ressalva recomendaria uma prática inexistente.

O segundo problema é de conformidade: parte do que alimentaria a IA (descrições do Jira, documentos de cartão) contém ou pode conter dado pessoal, dado protegido por sigilo bancário e dado de cartão. Por isso o conjunto começa por uma regra de uso e anonimização, e não por um modelo de documento (seção 4).

### 1.2 Tarefas que a IA vai apoiar

Recomenda-se limitar o apoio inicial a oito tarefas, todas ligadas a um ponto fraco medido no Jira ou a um artefato já previsto no processo.

| Nº | Tarefa | Por que entra (evidência) |
|---|---|---|
| T1 | Redigir documento de visão ou de requisito a partir da demanda | O Upstream tem as etapas Análise funcional, Prototipação e Especificação técnica + testes, com 11, 4 e 6 itens nessas etapas (upstream_16-11.csv, 16/11/2026 9h51). 62 de 90 itens do GDP já usam o mesmo roteiro de abertura ("Solicitante / Área solicitante / Contexto da solicitação…"), contados como descrições que começam com "Solicitante:" (gdp_16-11.csv, 16/11/2026 9h51): há padrão de entrada para a IA seguir. |
| T2 | Escrever o card no padrão do guia "Como escrever um card" | O guia é o tutorial oficial desde 13/11/2026 (contexto-mestre.md, seção 6). Entre os 363 cards (Tarefa, História e Bug) do Downstream, 80 estão sem descrição, 32 sem Categorias, 6 sem Natureza e 15 sem Classe de serviço (downstream_16-11.csv, extração de 16/11/2026 10h26). Épicos e subtarefas ficam fora da contagem porque não usam esses campos. |
| T3 | Apoiar o refinamento e a quebra de cards | A seção 06 do guia traz os sinais de card grande e os critérios de quebra (guia-como-escrever-card.txt, v1.0, set/2026). As Políticas Explícitas V1 exigem divisão em unidades de trabalho (seção 3.6) mas não definem como dividir (contexto-mestre.md, seção 3). Na S18, a mediana da História foi 118h para uma sprint de 75h úteis (review-sprint-18.txt, 06/11/2026 16h46). |
| T4 | Redigir RFC (requisição de mudança) e nota de implantação | O Downstream tem o status Waiting for deploy, com 4 itens abertos (metricas_downstream_16-11.json, 16/11/2026 10h26). O padrão de release e deploy ainda está em backlog (DS-550) e o Konsig não tem CI/CD (US-43, backlog) (downstream_16-11.csv, 16/11/2026 10h26; upstream_16-11.csv, 16/11/2026 9h51). Não há modelo de mudança localizado. |
| T5 | Registrar incidente e classificar prioridade | A tabela de prioridade P1 a P4, com tempos de resposta por nível N1, N2 e N3, está no PDTI (pdti-2026-2028.txt, slide 14, modificada 20/08/2026). O SLA está ligado a bônus semestral, com gatilho de 70% (slide 15). |
| T6 | Redigir análise de causa raiz (RCA) e postmortem | O guia exige, para Bug, card de origem, causa raiz e fase de detecção (guia-como-escrever-card.txt, seção 07). Dos 31 Bugs do Downstream, 1 menciona "causa raiz" na descrição (downstream_16-11.csv, 16/11/2026 10h26). |
| T7 | Analisar indicadores de fluxo e de serviço | Há linha de base da S18 e vazão das S15 a S18 (contexto-mestre.md, seção 5); a Demanda 3 depende dessa análise. |
| T8 | Apoiar a priorização do pool de projetos | A Demanda 1 (pool 2027) exige leitura recorrente do GDP, da capacidade e das prioridades já definidas (prompt-comite.md, seção 4). |

### 1.3 O que a IA não fará

Estes limites decorrem de decisões já registradas e não estão em discussão:

- **Não decide prioridade nem altera parâmetros.** Os parâmetros da calculadora são editáveis apenas pelo responsável (decisão de 10/11/2026); a IA apoia a análise, a decisão segue o DACI do comitê.
- **Não propõe mudança em indicador ligado à remuneração.** O SLA está vinculado a bônus (pdti-2026-2028.txt, slide 15); qualquer alteração vai à Dani e ao RH (prompt-comite.md, seção 4, Demanda 3).
- **Não avalia pessoas.** Dados de concentração por pessoa (por exemplo, testes e revisões feitos pela mesma pessoa na S18) entram apenas como indicador agregado do processo.
- **Não acrescenta conteúdo aos cards além do documento de requisito.** Tudo o que for além deve ser sinalizado para decisão (contexto-mestre.md, seção 2, item 4).

---

## 2. Matriz tarefa × documento de entrada

Legenda da coluna "Existe? Onde": **Sim** (o conteúdo está no pacote de fontes); **Existe (ID), não recebido** (há ID no Drive informado no contexto-mestre.md, seção 3, mas o arquivo não chegou no pacote e o conteúdo não pôde ser verificado; quando há problema já conhecido pelo contexto-mestre.md, ele é indicado); **Parcial** (existe no pacote, mas com problema identificado); **Não localizado** (não há arquivo rastreável nas fontes); **Não recebido** (o documento é citado, sem ID, e não chegou no pacote).

### 2.1 Documentos transversais (valem para todas as tarefas)

| Documento de entrada | Existe? Onde | Lacuna |
|---|---|---|
| Regra de uso de IA e de anonimização do que alimenta a IA | **Não localizado.** Há base interna: o item US-80 ("Revisar segurança, LGPD, auditoria e retenção da tipificação", status Concluído Upstream) lista os portões exigidos antes de usar fornecedor externo de IA, como retenção zero, não treinamento, região, suboperadores e prompt injection (upstream_16-11.csv, 16/11/2026 9h51). O item pai, US-25, está Despriorizado. | Converter os portões do US-80 em regra aprovada pelo DPO, aplicável a toda a TI e não apenas à tipificação. |
| Modelo de documentos da Neo Crédito | **Não localizado.** O contexto-mestre.md (seção 2, item 1) exige segui-lo, mas não informa ID. | Localizar o modelo e registrar o ID no Drive. |
| Inventário de Sistemas | **Existe (ID), não recebido.** Drive `1LwSqMSxgldjHxNQmj34uDAI_refDOkWG`. Consta como não recebido no LEIA-ME.md (16/11/2026). | Confirmar se o inventário separa Konsig e NeoKonsig, se registra o cartão no Konsig legado (decisão de 13/11/2026) e qual é a data da última atualização. |

### 2.2 Documentos por tarefa

| Tarefa | Documento de entrada | Existe? Onde | Lacuna |
|---|---|---|---|
| T1 Visão / requisito | Modelo de documento de visão | **Parcial.** Há um exemplar preenchido, a Visão do Cartão de Crédito v6 (03/11/2026), com cabeçalho "Dados do Projeto" e tabela de versionamento (visao-cartao-v6.txt). O modelo em branco não foi localizado. | Extrair o modelo em branco do exemplar. A Visão v6 põe o pós-faturamento no NeoKonsig, o que diverge da decisão de 13/11/2026 (cartão no Konsig legado); o exemplar precisa ser corrigido antes de servir de referência. |
| T1 | Roteiro de abertura de demanda | **Parcial.** O roteiro existe só como texto nas descrições: 62 de 90 itens do GDP e 8 de 65 do Upstream, contados como descrições que começam com "Solicitante:" (gdp_16-11.csv e upstream_16-11.csv, 16/11/2026 9h51). Arquivo-modelo não localizado. | Formalizar o roteiro como modelo. |
| T1 | Konsig Arquitetura | **Existe (ID), não recebido.** Drive `1u3NsVaAXvnayi6I7eCJ4z41fC2yh1naP`. | Atualidade não verificada. É pré-requisito da T1 para o cartão e a reestruturação da esteira, que entram no Konsig legado (decisão de 13/11/2026). |
| T1 | Arquitetura do NeoKonsig | **Não localizado.** | Sem documento, a IA não distingue o impacto no NeoKonsig do impacto no Konsig. |
| T2 Card | Guia "Como escrever um card" (InnoviaX, v1.0, set/2026) | **Sim**, como arquivo do projeto; sem ID no Drive (contexto-mestre.md, seção 3). | Publicar no Drive com ID e controle de versão. O guia cita um "teto combinado pelo time" (seção 06), que não existe: depende da decisão em aberto sobre PP a GG e a regra "cabe ou quebra". |
| T2 | Políticas Explícitas V1 (DoR, tags CR e QA-REJECTED) | **Existe (ID), não recebido.** Drive `14vzbIjpsUxObg8uha21YlUS6DtBTTqf7`. | Não incorpora as três regras do experimento em vigor desde a S19 (contexto-mestre.md, seção 4). O DS-71 (Concluído) registra que será necessária revisão das políticas conforme o novo processo amadurecer (downstream_16-11.csv, 16/11/2026 10h26). |
| T2 | Glossário dos campos do Jira (Categorias, Natureza, Classe de serviço, Tipo) | **Não localizado.** As classes de serviço estão listadas no contexto-mestre.md (seção 3), sem definição. | A regra 3 do experimento exige esses campos para concluir o card. Sem definição, a IA classifica por suposição. |
| T3 Refinamento e quebra | Guia InnoviaX, seções 06 e 07 | **Sim** (ver T2). | Ver T2. |
| T3 | Fluxo de Desenvolvimento TI V3 | **Existe (ID), não recebido.** Drive `14F0QqrDgqEmAxzHdrdtLYhWNYrJiKdsr`. Problema conhecido pelo contexto-mestre.md. | Cita Fibonacci, que não descreve a prática atual; a decisão vigente (10/11/2026) prevê o uso somente depois do refinamento e está em revisão no Comitê de Agilidade (contexto-mestre.md, seções 3 e 6). Sem nota de vigência, a IA reproduz a prática inexistente. |
| T3 | Calculadora de Tamanho PP a GG (parâmetros) | **Sim**, como artefato (contexto-mestre.md, seção 9). | O uso do modelo PP a GG no lugar do Fibonacci está em aberto e depende do comitê. A IA só pode usar as faixas como proposta, não como regra. |
| T4 RFC / mudança | Modelo de RFC e política de mudança e release | **Não localizado.** | O padrão de release ainda é item de backlog (DS-550, 9 cards em Backlog) (epicos_downstream_16-11.csv, 16/11/2026 10h26). |
| T4 | Descrição do pipeline de CI/CD por sistema | **Não localizado.** O Konsig não tem CI/CD (US-43, Backlog) (upstream_16-11.csv, 16/11/2026 9h51). | Sem isso, a IA não sabe que passos manuais a RFC do Konsig precisa prever. |
| T5 Incidente | Tabela de prioridade e SLA | **Sim**, na apresentação do PDTI (pdti-2026-2028.txt, slides 14 e 15, modificada 20/08/2026). Sem ID no Drive. | Registrar o ID do PDTI no Drive. |
| T5 | Modelo de registro de incidente | **Não localizado.** | — |
| T5 | Política de Segurança da Informação | **Não localizado.** O PDTI cita sua implantação como responsabilidade do núcleo de Segurança & Conformidade (slide 10). | Sem a política, a IA não sabe classificar um incidente de segurança nem a quem escalar. |
| T5 | Relatório de metas TI · SLA 1º semestre/2026 | **Não recebido** (LEIA-ME.md, 16/11/2026). | Sem histórico de atendimento, não há base de comparação. |
| T6 RCA / postmortem | Regras de Bug do guia (card de origem, causa raiz, fase de detecção) | **Sim** (guia-como-escrever-card.txt, seção 07). | Na prática, a regra quase não é seguida (1 de 31 Bugs, ver T6 na seção 1.2). |
| T6 | Modelo de RCA / postmortem | **Não localizado.** | — |
| T7 Indicadores | Linha de base S18 e vazão S15 a S18 | **Sim** (review-sprint-18.txt, 06/11/2026 16h46; contexto-mestre.md, seção 5). | — |
| T7 | Painel Indicadores Neo · Requisitos (28/09/2026) | **Não recebido** (LEIA-ME.md, 16/11/2026). A tabela de KPIs está vazia (prompt-comite.md, seção 4). | Depende da Demanda 3. |
| T7 | Indicadores por ação do PDTI | **A fonte não traz.** A apresentação recebida não contém indicadores por ação (LEIA-ME.md, 16/11/2026). | Obter o documento do PDTI que contenha os indicadores. |
| T7 | Dicionário de indicadores (fórmula, fonte, unidade) | **Não localizado.** | Sem dicionário, a IA pode recalcular a capacidade numa unidade diferente da usada nos tamanhos, erro já corrigido na auditoria de 13/11/2026 (contexto-mestre.md, seção 5). |
| T8 Priorização do pool | Exportação do GDP | **Sim** (gdp_16-11.csv, 90 itens, 16/11/2026 9h51). | — |
| T8 | Princípios de priorização e roteiro de 47 ações (Comitê PDTI julho/2026) | **Não recebido**; a apresentação do PDTI recebida não traz as 47 ações (LEIA-ME.md, 16/11/2026). | Sem critério formal, a IA reproduz o campo Prioridade do GDP, que diverge das prioridades declaradas para o NeoKonsig (contexto-mestre.md, seção 7). |
| T8 | Pilares e diretrizes do PDTI | **Sim** (pdti-2026-2028.txt, slides 3 a 8). | — |

---

## 3. Documentos internos e referências de mercado

### 3.1 Documentos internos da Neo

| Documento | Situação | Papel no conjunto |
|---|---|---|
| Modelo de documentos da Neo | Não localizado | Forma de qualquer documento gerado (T1, T4, T5, T6). |
| Políticas Explícitas V1 | Existe (ID), não recebido · `14vzbIjpsUxObg8uha21YlUS6DtBTTqf7` | Regras de entrada (DoR) e tags do fluxo (T2, T3). |
| Inventário de Sistemas | Existe (ID), não recebido · `1LwSqMSxgldjHxNQmj34uDAI_refDOkWG` | Impede que a IA confunda sistemas e tecnologias (T1, T4, T5). |
| Guia "Como escrever um card" (InnoviaX v1.0) | Sim · arquivo do projeto, sem ID | Padrão de card, quebra e Bug (T2, T3, T6). |
| Fluxo de Desenvolvimento TI V3 | Existe (ID), não recebido; cita Fibonacci · `14F0QqrDgqEmAxzHdrdtLYhWNYrJiKdsr` | Status e agrupamentos do fluxo, seção 6.4 (T3, T4, T7). |
| Konsig Arquitetura | Existe (ID), não recebido · `1u3NsVaAXvnayi6I7eCJ4z41fC2yh1naP` | Análise de impacto no legado (T1, T4); pré-requisito da T1 para o cartão e a esteira. |
| Manual de Marca | Sim · `1pJxLx_aWDkzcmTQ5WwTRkEfgZy9gSX3D` | Só para artefatos visuais; fora do conjunto mínimo. |
| Melhorias Scrum TI V2 | Sim · `1VHKIDjuAW6Vdezh1uOgxgrpCHPoAILmX` | **Fora da base da IA.** São sugestões não aplicadas e não descrevem a prática atual; alimentá-las levaria a IA a tratá-las como processo vigente. |

### 3.2 Referências de mercado

**Divergência registrada.** O contexto-mestre.md (seção 8) e o prompt-comite.md (seção 4, Demanda 2) informam que os padrões adotados estão na "seção 1 do PDTI": COBIT 2019, ITIL 4, ISO/IEC 27001, NIST CSF, DAMA-DMBOK, LGPD, ISO 27701 e OWASP SAMM. A apresentação do PDTI recebida (pdti-2026-2028.txt, 16 slides, modificada 20/08/2026) **não tem essa seção** e não cita nenhum desses padrões (LEIA-ME.md, 16/11/2026). O prompt menciona um "PDTI 2026–2028 v1.3", que pode ser um documento diferente da apresentação. Até que esse documento chegue, a lista abaixo vale como lista **informada**, e não como lista verificada na fonte.

A apresentação do PDTI traz apenas referências próximas: práticas ágeis (Scrum, Kanban, OKRs; slide 4), CI/CD e SecDevOps (slides 6 e 13) e a tabela de SLA por prioridade (slide 14). A Visão do Cartão v6 traz outra lista de normas aplicáveis ao cartão, entre elas a LGPD, a Resolução CMN nº 4.893/2021 (segurança cibernética e contratação de processamento e nuvem) e o PCI DSS v4.0.1 (visao-cartao-v6.txt, 03/11/2026), e ressalva que a aplicabilidade de cada uma depende do enquadramento jurídico da empresa, da natureza do cartão, da consignação e do contrato com a Orbitall (visao-cartao-v6.txt, seção 1.1, 03/11/2026).

A correspondência abaixo é análise deste documento, não conteúdo das normas nem do PDTI. Por isso toda a tabela está marcada como **[ALÉM DA FONTE — decisão do usuário]**.

| Referência | Base conceitual para a tarefa | Documento interno que ela deveria orientar |
|---|---|---|
| ITIL 4 | T4 (habilitação de mudança), T5 (gestão de incidentes), T6 (gestão de problemas) e níveis de serviço | Modelo de RFC, modelo de incidente, modelo de RCA e a tabela de SLA do PDTI (slide 14) |
| COBIT 2019 | T8 (governança de portfólio e de prioridades) e T7 (desempenho e conformidade da TI) | Critérios de priorização do pool e dicionário de indicadores; também a regra de uso de IA, como peça de governança |
| ISO/IEC 27001 | Classificação da informação, controle de acesso e gestão de fornecedores: base da regra de uso de IA e de T5 para incidentes de segurança | Política de Segurança da Informação (citada no PDTI, slide 10, não localizada) e regra de uso de IA |
| NIST CSF | T5 e T6 para incidentes de segurança: identificar, proteger, detectar, responder e recuperar | Modelo de incidente de segurança e postmortem |
| DAMA-DMBOK | T7 (definição, qualidade e linhagem do dado) e qualidade dos campos do Jira usados como fonte | Dicionário de indicadores e glossário dos campos do Jira |
| LGPD | Base legal, minimização e anonimização do que alimenta a IA (todas as tarefas) | Regra de uso de IA e de anonimização |
| ISO 27701 | Registro do tratamento de dados pessoais feito pela IA e papéis de controlador e operador | Regra de uso de IA (seção de registro de tratamento) |
| OWASP SAMM | T2 e T3 (requisitos não funcionais de segurança, bloco 8 do guia) e T4 (verificação antes da implantação) | Fluxo de Desenvolvimento (etapa de Code Review) e DoD das Políticas Explícitas; dá base ao épico de correção de vulnerabilidades (DS-65, 20 cards, 12 concluídos) (epicos_downstream_16-11.csv, 16/11/2026 10h26) |

**Recomendação [ALÉM DA FONTE — decisão do usuário]:** incluir o PCI DSS v4.0.1 e a Resolução CMN nº 4.893/2021 entre as referências da Demanda 2. As duas já constam da Visão v6 e são as que mais restringem o uso de IA: a primeira por causa dos dados de cartão, a segunda por causa da contratação de processamento em nuvem, que é o caso de um fornecedor de IA.

---

## 4. Riscos de LGPD e sigilo no que alimenta a IA

### 4.1 Riscos identificados

| Nº | Risco | Evidência | Gravidade |
|---|---|---|---|
| R1 | **Anonimização do Jira imperfeita.** O pacote de 16/11/2026 informa 306 ocorrências de dado pessoal removidas (LEIA-ME.md). Nos três CSVs foram localizados 195 marcadores de remoção: 179 de telefone, 10 de e-mail, 3 de CPF e 3 de CNPJ (downstream 167, GDP 18, Upstream 10). Não foi possível reconciliar 306 com 195 a partir das fontes. | Contagem nos arquivos gdp_16-11.csv, upstream_16-11.csv e downstream_16-11.csv (16/11/2026). | Alta |
| R2 | **Falsos positivos.** 177 dos 179 marcadores de telefone estão dentro de nomes de arquivo de imagem anexada; os marcadores de CPF e de CNPJ no GDP e no Upstream (2 de cada) estão dentro de um identificador de link. A regra apaga informação que não é pessoal. | gdp_16-11.csv e upstream_16-11.csv (16/11/2026 9h51); downstream_16-11.csv (16/11/2026 10h26). | Média: degrada o contexto que a IA recebe. |
| R3 | **Falsos negativos.** Restaram 4 ocorrências de um mesmo endereço de e-mail corporativo codificado em URL ("%40"): 2 no Downstream, 1 no GDP e 1 no Upstream (CSVs de 16/11/2026). A regra não reconhece dado pessoal em formato codificado. | Mesmos arquivos e data. | Alta: prova que o pacote "anonimizado" ainda contém dado pessoal. |
| R4 | **Dado pessoal de colaboradores em campos estruturados.** Os campos Solicitante, Responsável, DEVs, Revisor, Testador e PO trazem nomes; um item do Upstream (US-43) traz identificadores de conta. Cruzados com tempo de ciclo, permitem avaliação individual. | Cabeçalhos dos CSVs (16/11/2026). | Média |
| R5 | **Sigilo bancário.** Demandas de crédito consignado tratam de proposta, margem, contrato e pagamento. A Visão v6 exige avaliar as regras de sigilo bancário. | visao-cartao-v6.txt (03/11/2026), seção de normas. | Alta |
| R6 | **Dados de cartão (PCI DSS).** A Visão v6 proíbe guardar o CVV nos sistemas da Neo, inclusive em logs e mensagens (risco R18), e registra que o escopo do ambiente de dados de cartão ainda precisa ser definido (risco R19). Por extensão do R18 **[ALÉM DA FONTE — decisão do usuário]**, texto colado em ferramenta de IA deve ser tratado como dado fora do ambiente certificado. | visao-cartao-v6.txt (03/11/2026), riscos R18 e R19. | Crítica |
| R7 | **Documentos reais como corpus.** O US-80 registra que o corpus da tipificação "aparenta conter documentos pessoais reais" e que não foram comprovados base legal, retenção, região nem cláusula de não treinamento do fornecedor. | upstream_16-11.csv (16/11/2026 9h51), US-80. | Alta |
| R8 | **Dado concreto nos cenários de teste.** O guia pede cenário de teste "com dado concreto" e usa CPF como exemplo de campo (seções 03 e 08; a exigência de dado concreto aparece também na seção 04). Se a IA gerar ou receber cenários com dado real, ele passa ao card. | guia-como-escrever-card.txt (v1.0, set/2026). | Média |
| R9 | **Conexão direta com o Jira.** O conector Atlassian (Rovo MCP) não está conectado; a conexão exige validação prévia com o responsável pelo Atlassian ou pela segurança, porque fica registrada em log. | contexto-mestre.md, seção 9 (16/11/2026). | Alta, se conectado sem a regra da seção 4.2. |

### 4.2 Controles recomendados

1. **Classificar a entrada antes de alimentar a IA, em três níveis:**
   - **Livre:** documentos de processo (guia, políticas, fluxo, modelos em branco) e indicadores agregados.
   - **Somente após anonimização validada:** descrições do Jira, documentos de visão e requisitos com exemplos.
   - **Proibido:** dado de cartão (PAN, CVV, trilha), documentos pessoais digitalizados, extratos, contratos assinados e qualquer conteúdo do ambiente da processadora.

   **[ALÉM DA FONTE — decisão do usuário]**
2. **Anonimização em duas camadas.** Aplicar primeiro a substituição automática, depois uma verificação que cubra formatos codificados (como "%40") e dígitos com e sem máscara. Antes de liberar o pacote, revisar por amostragem e registrar, no próprio pacote, as contagens de remoção e de falsos positivos. Critério de aceite: zero ocorrência residual na amostra e contagem reconciliada com o número declarado (hoje 306 declaradas contra 195 marcadores; LEIA-ME.md, 16/11/2026; contagem nos CSVs de 16/11/2026). **[ALÉM DA FONTE — decisão do usuário]**
3. **Pseudonimizar pessoas.** Substituir nomes de colaboradores por papel (Dev, Revisor, Testador, PO) antes de qualquer análise de fluxo. Indicadores saem apenas agregados por etapa, nunca por pessoa. **[ALÉM DA FONTE — decisão do usuário]**
4. **Exigir do fornecedor de IA os portões do US-80:** retenção zero, não uso para treinamento, região e transferência de dados declaradas, lista de suboperadores, descarte e notificação de incidente. Sem esses itens em contrato, a ferramenta não recebe nada além do nível "livre". O US-80 trata apenas da tipificação de documentos (upstream_16-11.csv, 16/11/2026 9h51); aplicá-lo a qualquer fornecedor de IA e a toda a TI é proposta deste documento. **[ALÉM DA FONTE — decisão do usuário]**
5. **Massa de teste sintética.** Os cenários de teste gerados pela IA usam dado fictício e válido em formato, nunca dado copiado de produção. **[ALÉM DA FONTE — decisão do usuário]**
6. **Não conectar a IA diretamente ao Jira** enquanto os controles 1 a 4 não forem aprovados e a validação exigida no contexto-mestre.md (seção 9) não for feita. A IA também não escreve no Jira. A validação prévia vem do contexto-mestre.md; a condição dos controles 1 a 4 e a proibição de escrita são propostas deste documento. **[ALÉM DA FONTE — decisão do usuário]**
7. **Trilha de uso.** Registrar o que foi submetido à IA, por quem, com que finalidade e em que data, para atender a eventual pedido de titular ou auditoria. **[ALÉM DA FONTE — decisão do usuário]**

### 4.3 Quem aprova

O PDTI atribui ao núcleo de Segurança & Conformidade a implantação da Política de Segurança da Informação e o suporte à conformidade regulatória; a equipe é composta por um DPO terceiro e um assistente ainda não definido (pdti-2026-2028.txt, slide 10, modificada 20/08/2026).

**Recomendação [ALÉM DA FONTE — decisão do usuário]:** o DPO emite parecer escrito sobre a regra de uso de IA (controles 1 a 7), e a Dani a aprova como gestora, com registro DACI no comitê. Os itens que tocam dado de cartão (controle 1, nível "proibido") também passam por Compliance.

---

## 5. Conjunto mínimo para começar

O critério de escolha foi este: entram os documentos sem os quais a IA erraria de forma previsível nas tarefas de maior volume (T1, T2 e T3) e o documento que torna seguro alimentá-la. Seis documentos, nesta ordem **[ALÉM DA FONTE — decisão do usuário]**:

| Ordem | Documento | Situação | Dono sugerido **[ALÉM DA FONTE — decisão do usuário]** | Critério de pronto **[ALÉM DA FONTE — decisão do usuário]** |
|---|---|---|---|---|
| 1 | **Regra de uso de IA e de anonimização** | Novo, com base no US-80 | Núcleo de Segurança & Conformidade, com parecer do DPO terceiro | Controles 1 a 7 da seção 4.2 aprovados por escrito (parecer do DPO e decisão registrada em DACI). Rotina de anonimização testada contra os falsos positivos e negativos da seção 4.1, com zero resíduo na amostra. |
| 2 | **Guia "Como escrever um card" (InnoviaX v1.0)** | Existe, sem ID no Drive | PO do núcleo de Soluções | Arquivo publicado no Drive com ID e versão. Nota explícita de que o "teto" da seção 06 ainda depende da decisão do comitê sobre PP a GG. |
| 3 | **Políticas Explícitas V1 + adendo do experimento S19 + glossário de campos** | Existe (ID), não recebido (`14vzbIjpsUxObg8uha21YlUS6DtBTTqf7`); adendo e glossário são novos | Gestão do processo de desenvolvimento | Versão vigente identificada. Adendo com as três regras da S19 marcadas como experimento até a retro. Definição de Categorias, Natureza, Classe de serviço (Expedite, Fixed Date, Standard, Intangible) e Tipo. |
| 4 | **Fluxo de Desenvolvimento TI V3 com nota de vigência** | Existe (ID), não recebido (`14F0QqrDgqEmAxzHdrdtLYhWNYrJiKdsr`) | Gestão do processo de desenvolvimento | Nota no início do documento: "O Fibonacci citado aqui não descreve a prática atual. Decisão vigente (10/11/2026): uso somente depois do refinamento, em revisão no Comitê de Agilidade." Os status do Fluxo V3 conferidos com os status em uso no Jira, inclusive PAUSADO (12 itens abertos; metricas_downstream_16-11.json, 16/11/2026 10h26). |
| 5 | **Inventário de Sistemas** | Existe (ID), não recebido (`1LwSqMSxgldjHxNQmj34uDAI_refDOkWG`) | Arquiteto do núcleo de Soluções (posição ainda não preenchida no PDTI, slide 10); até lá, o gerente do núcleo | Konsig e NeoKonsig em linhas separadas, com tecnologia e data de atualização. O cartão registrado no Konsig legado. Indicação de quais sistemas têm CI/CD. |
| 6 | **Modelo de documento de visão e requisito + roteiro de abertura de demanda** | Novo, derivado de exemplares existentes | PO do núcleo de Processos de Negócio | Modelo em branco no Drive, derivado do cabeçalho da Visão v6 e do roteiro usado em 62 de 90 itens do GDP (gdp_16-11.csv, 16/11/2026 9h51). Referência cruzada com o guia de cards (bloco 1, "Cabeçalho e referência"). O exemplar da Visão v6 só passa a servir de referência depois de corrigido para Konsig legado. |

**Ordem de execução.** O documento 1 vem antes de qualquer uso, porque sem ele nenhum conteúdo do Jira pode entrar. Os documentos 2 a 4 podem ser preparados em paralelo, porque são ajustes de arquivos que já existem. O 5 depende do recebimento e da conferência do inventário. O 6 é o único que exige redação nova de conteúdo.

**Pré-requisito da T1 no Konsig legado.** A Konsig Arquitetura (`1u3NsVaAXvnayi6I7eCJ4z41fC2yh1naP`, existe com ID, não recebida) é entrada obrigatória da T1 sempre que a demanda for do cartão ou da reestruturação da esteira, que entram no Konsig legado (decisão de 13/11/2026). Ela não ocupa posição no conjunto mínimo porque não exige redação, apenas o recebimento e a conferência da atualidade, mas a T1 para esses dois temas não começa sem ela **[ALÉM DA FONTE — decisão do usuário]**.

### Fica para depois, e por quê

| Documento | Motivo |
|---|---|
| Modelo de RFC e política de release (T4) | Depende do padrão de release em backlog (DS-550) e da ausência de CI/CD no Konsig (US-43). Um modelo agora descreveria um processo que vai mudar. |
| Modelos de incidente e de RCA (T5, T6) e Política de Segurança da Informação | A política não foi localizada, e o relatório de SLA do 1º semestre não foi recebido. A tabela de SLA do PDTI basta para a IA classificar a prioridade enquanto isso. |
| Dicionário de indicadores e Painel Indicadores Neo (T7) | É o produto da Demanda 3; criá-lo aqui criaria um conjunto paralelo, o que o prompt-comite.md proíbe. |
| Critérios de priorização do pool (T8) | Dependem da entrega da Demanda 1 (30/11/2026) e do material do Comitê PDTI de julho/2026, não recebido. |
| Arquitetura do NeoKonsig | Não localizada. Entra quando for produzida ou localizada; até lá, a IA não faz análise de impacto no NeoKonsig. |
| Manual de Marca | Só se aplica a artefatos visuais. |
| Referências de mercado como documentos de entrada | Servem para orientar a redação dos documentos internos, não para alimentar a IA. Além disso, a fonte que as lista (PDTI, seção 1) não foi recebida. |
| Melhorias Scrum TI V2 | Fica fora da base da IA, e não apenas para depois. |

---

## 6. Decidido, em aberto, bloqueado e obsoleto

### Decidido (não reabrir)

| Data | Decisão | Efeito nesta demanda |
|---|---|---|
| 10/11/2026 | Fibonacci só depois do refinamento, não na planning direta | Em revisão desde 13/11 (proposta PP a GG + cabe ou quebra, pendente do comitê). Define a nota de vigência do documento 4 e o teto da seção 06 do guia. |
| 10/11/2026 | Parâmetros da calculadora editáveis só pelo responsável; calculadora não integrada ao Jira | A IA não altera os parâmetros da calculadora. |
| 10/11/2026 | Regras do Downstream em vigor desde a S19 | Entram como adendo de experimento (documento 3). |
| 10/11/2026 | Comitê com um tema por reunião e decisão em DACI | A Demanda 2 tem reunião própria. |
| 13/11/2026 | O guia InnoviaX é o tutorial de cards da TI | É o documento 2 do conjunto mínimo. |
| 13/11/2026 | Projeto = épico no pool de 2027 | O glossário do documento 3 deve refletir isso. |
| 13/11/2026 | Cartão no Konsig legado | O Inventário (documento 5) e o exemplar da Visão v6 (documento 6) precisam refletir isso. |

### Em aberto

- Quem aprova a regra de uso de IA. Recomendação: parecer do DPO e decisão da Dani em DACI (seção 4.3).
- Inclusão do PCI DSS v4.0.1 e da Resolução CMN nº 4.893/2021 entre as referências (seção 3.2).
- Donos dos seis documentos (seção 5).
- Teto de tamanho do card: depende da decisão sobre PP a GG e a regra "cabe ou quebra", que reverte a decisão de 10/11/2026 e ainda não foi aprovada.
- Ferramenta e fornecedor de IA: nenhuma fonte do pacote define qual será usada.
- Reconciliação entre as 306 ocorrências declaradas (LEIA-ME.md, 16/11/2026) e os 195 marcadores localizados (contagem nos CSVs de 16/11/2026) (seção 4.1).

### Bloqueado

- **Verificação da lista de padrões de mercado:** depende do documento do PDTI com a seção 1 (possivelmente a v1.3), não recebido.
- **Conferência do Inventário de Sistemas e do Painel Indicadores Neo:** não recebidos (LEIA-ME.md, 16/11/2026).
- **Alimentação da IA com conteúdo do Jira:** bloqueada até a aprovação do documento 1 e a validação do conector Atlassian (contexto-mestre.md, seção 9).
- **Uso de qualquer material com dado de cartão:** bloqueado até a definição do escopo do ambiente de dados de cartão (visao-cartao-v6.txt, risco R19).
- **Pré-análise técnica com IA sobre os repositórios do Konsig (DS-69):** pausada no Jira (downstream_16-11.csv, 16/11/2026 10h26).

### Obsoleto

- Calculadora de story points (substituída em 13/11/2026): não entra na base da IA.

### Decisões necessárias para a reunião da Demanda 2

1. Aprovar o conjunto mínimo de seis documentos e a ordem da seção 5.
2. Definir os donos de cada documento.
3. Definir o fluxo de aprovação da regra de uso de IA (DPO e gestora).
4. Solicitar o documento do PDTI com a seção 1 e as 47 ações, ou confirmar a lista de padrões informada.
5. Incluir ou não o PCI DSS v4.0.1 e a Resolução CMN nº 4.893/2021 entre as referências.
6. Manter o conector Atlassian desconectado até a aprovação da regra de uso de IA.

---

## 7. Fontes

| Arquivo do pacote | Conteúdo usado | Data de extração ou versão |
|---|---|---|
| LEIA-ME.md | Inventário do pacote, 306 ocorrências removidas, documentos não recebidos, ausência da seção de padrões no PDTI | 16/11/2026 |
| contexto-mestre.md | Documentos de referência e IDs do Drive (seção 3), regras da S19 (seção 4), linha de base (seção 5), decisões (seção 6), em aberto (seção 7), Demanda 2 (seção 8), conector Atlassian (seção 9) | 16/11/2026 |
| prompt-comite.md | Pedido da Demanda 2 (seção 4) e regras obrigatórias (seção 5) | 16/11/2026 |
| pdti-2026-2028.txt | Pilares e ações (slides 3 a 8), núcleos e DPO terceiro (slides 10 e 11), Scrum, CI/CD e SecDevOps (slides 12 e 13), SLA e bônus (slides 14 e 15) | Modificada 20/08/2026 |
| visao-cartao-v6.txt | Normas aplicáveis (LGPD, CMN 4.893/2021, PCI DSS v4.0.1, sigilo bancário), riscos R18 e R19, estrutura do documento de visão | 03/11/2026 |
| guia-como-escrever-card.txt | Anatomia do card (seção 02), CPF como exemplo de campo (seções 03 e 08) e exigência de dado concreto (seção 04), quebra (seção 06), regras por tipo (seção 07) | v1.0, set/2026 |
| gdp_16-11.csv | 90 itens; roteiro de abertura em 62 itens (critério: descrição que começa com "Solicitante:"; "Contexto da solicitação:" aparece em 66); marcadores de remoção | 16/11/2026 9h51 |
| upstream_16-11.csv | 65 itens; status do Upstream; US-25, US-43 e US-80; marcadores de remoção | 16/11/2026 9h51 |
| downstream_16-11.csv | 475 itens; preenchimento de descrição e campos nos 363 cards (Tarefa, História e Bug); Bugs; DS-65, DS-69, DS-71 e DS-550; marcadores de remoção | 16/11/2026 10h26 |
| epicos_downstream_16-11.csv | Épicos DS-65 (20 cards, 12 concluídos) e DS-550 (9 cards em Backlog) | 16/11/2026 10h26 |
| metricas_downstream_16-11.json | Abertos por status (4 em Waiting for deploy, 12 em Pausado) | 16/11/2026 10h26 |
| review-sprint-18.txt | Mediana de 118h para História e sprint de 75h úteis | 06/11/2026 16h46 |

**Contagens calculadas neste documento** (preenchimento de campos, marcadores de remoção, falsos positivos e negativos, Bugs com causa raiz, uso do roteiro de abertura): leitura direta dos CSVs acima, em 16/11/2026. A contagem não substitui o número de 306 declarado no LEIA-ME.md; a diferença está registrada como ponto em aberto.
