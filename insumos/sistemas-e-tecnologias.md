# Sistemas e tecnologias · TI Neo Crédito

**Documento de insumo** para as três solicitações do Comitê de Agilidade (pool de projetos 2027, documentos para a IA e indicadores 2027).
**Data de elaboração:** 16/11/2026.
**Natureza:** mapa de sistemas e integrações levantado do Jira e dos documentos do pacote de fontes. **Não substitui o Inventário de Sistemas oficial.**

---

## 1. Escopo, fontes e limitações

### 1.1 O que este documento é

Este documento registra quais sistemas internos e quais parceiros externos aparecem nas fontes recebidas, qual o papel de cada um, em que estado se encontram e quais itens do Jira os tocam. Ele serve de entrada para:

- o pool de projetos 2027 (solicitação 1), ao indicar em qual sistema cada demanda cai;
- o conjunto de documentos para a IA (solicitação 2), em que o Inventário de Sistemas é candidato a documento de entrada **[ALÉM DA FONTE — decisão do usuário]**;
- os indicadores de 2027 (solicitação 3), ao indicar onde há ou não há pipeline, testes automatizados e observabilidade.

### 1.2 Fontes utilizadas

| Arquivo do pacote | Conteúdo | Data de extração ou versão |
|---|---|---|
| `contexto-mestre.md` | Decisões, regras e distinção Konsig × NeoKonsig | 16/11/2026 |
| `prompt-comite.md` | Prioridades de 2027 e pendências do pool | 16/11/2026 |
| `visao-cartao-v6.txt` | Visão do Cartão de Crédito v6: atores, macroetapas e riscos | 03/11/2026 |
| `pdti-2026-2028.txt` | Apresentação do PDTI 2026–2028 (16 slides) | modificada em 20/08/2026 |
| `gdp_16-11.csv` | Jira, board Gestão de Projetos, 90 itens | 16/11/2026, 9h51 |
| `upstream_16-11.csv` | Jira, board Upstream, 65 itens | 16/11/2026, 9h51 |
| `downstream_16-11.csv` | Jira, board Downstream (project = DS), 475 itens | 16/11/2026, 10h26 |
| `epicos_downstream_16-11.csv` | Cards por épico, calculado do Downstream | 16/11/2026, 10h26 |
| `review-sprint-18.txt` | Review da Sprint 18 | 06/11/2026, 16h46 |

### 1.3 Limitações

1. **O Inventário de Sistemas oficial (Drive `1LwSqMSxgldjHxNQmj34uDAI_refDOkWG`) não foi recebido.** O documento "Konsig Arquitetura" (Drive `1u3NsVaAXvnayi6I7eCJ4z41fC2yh1naP`) também não está no pacote.
2. Toda tecnologia (linguagem, banco de dados, infraestrutura) que as fontes não afirmam fica marcada como **"a confirmar no Inventário"**.
3. Quando a tecnologia aparece **somente** em descrição de card do Jira, ela é registrada como **"evidência no Jira"**, com a chave do item. Isso indica o uso, mas não é o registro oficial da arquitetura. Também precisa ser confirmada no Inventário.
4. A apresentação do PDTI recebida não traz padrões de mercado, as 47 ações nem indicadores por ação. Este documento não usa esse conteúdo.
5. Nomes de pessoas, endereços internos de servidores e identificadores de contas que constam nas descrições do Jira foram omitidos de propósito.

---

## 2. Situação: decidido, em aberto, bloqueado e obsoleto

| Situação | Item | Fonte |
|---|---|---|
| **Decidido** | Konsig (legado) e NeoKonsig (reescrita) são sistemas diferentes, com tecnologias diferentes. | contexto-mestre, seção 3 (16/11/2026) |
| **Decidido** | O cartão de crédito entra no **Konsig legado**, não no NeoKonsig (13/11/2026). | contexto-mestre, seção 6 |
| **Decidido** | A reestruturação da esteira entra no Konsig legado (13/11/2026). | Decisão de 13/11/2026 registrada nas regras da tarefa do comitê (16/11/2026). O contexto-mestre (seções 6 e 7) e o prompt-comite (seção 4) ainda não a registram como decidida e precisam ser atualizados. Ver ponto de atenção A4. |
| **Decidido** | O pagamento da Quitação usa o PagAuto com a API do Banco do Brasil (09/11/2026). | contexto-mestre, seção 10 |
| **Em aberto** | Delimitação de SSOT entre Konsig e NeoKonsig (quais dados e estados cada um mantém). | visao-cartao-v6, glossário (03/11/2026) |
| **Em aberto** | Escopo e sistema de destino das integrações com a Salesforce. | prompt-comite, seção 4 (16/11/2026) |
| **Em aberto** | Prioridade dos módulos do NeoKonsig no GDP (Low e Lowest). Não é reaberta aqui. | contexto-mestre, seção 7 |
| **Bloqueado** | Registro oficial de tecnologias por sistema: depende do Inventário de Sistemas, não recebido. | LEIA-ME (16/11/2026) |
| **Obsoleto** | Na Visão v6, a atribuição do NeoKonsig como responsável pelas macroetapas 13 (faturamento) e 15 (conciliação) e as dependências das macroetapas 18 (cobrança) e 21 (dados) que apontam para o NeoKonsig. Vale a decisão de 13/11/2026. | visao-cartao-v6 (03/11/2026); contexto-mestre, seções 3 e 6 (16/11/2026) |
| **Em aberto** | Responsável principal da macroetapa 21 (Dados, BI e gestão de carteira), registrado como "A definir" na Visão v6. | visao-cartao-v6 (03/11/2026) |

---

## 3. Sistemas internos

**Leitura da coluna "Itens que tocam o sistema":** são itens do GDP **não concluídos** em 16/11/2026 (candidatos ao pool de 2027) e as três prioridades de 2027 já definidas (cartão, integrações com a Salesforce e reestruturação da esteira). A lista não é o pool aprovado.

### 3.1 Tabela de sistemas

| Sistema | Papel | Estado | Itens que tocam o sistema (GDP não concluídos e prioridades 2027) | Tecnologia | Fonte |
|---|---|---|---|---|---|
| **Konsig** (legado) | Originação e ciclo de crédito e contrato: proposta, elegibilidade, KYC, decisão, oferta, contratação, averbação e orquestração da efetivação. Citado pelo PDTI como exemplo do portfólio de soluções internas mantido pelo núcleo Soluções (slide 10, 20/08/2026). | Produção (legado). Recebe em 2027 o cartão e a reestruturação da esteira. | **Prioridades:** cartão (GDP-38 Highest; GDP-112; US-92 a US-97), reestruturação da esteira (sem item no GDP). **Em andamento:** Quitação (GDP-76 Em Downstream; épico DS-500 Fase 2, 8 cards em Backlog), Xerox (GDP-107 Em Downstream), JUDIT (GDP-118 Em Downstream), Não me perturbe (GDP-132 Em Downstream). **Fila:** GDP-114 Crivo decisão (Highest), GDP-62 CRCP (Highest), GDP-83 Cobmais parte 2 (Highest), GDP-105 e GDP-106 Xerox score (High), GDP-72 Portal consignatárias (High), GDP-75 Tratativa interna (High), GDP-61 Retorno de pagamentos esteira (High), GDP-96 MCB, GDP-120 PLD, GDP-138 CAF ações judiciais, GDP-140, GDP-145 e GDP-77 Paradinha, GDP-139 OCR parte 3, GDP-80 Tipificação, GDP-117 Retorno BB, GDP-143 Crivo lista restritiva, GDP-65 CAF, GDP-55 D4Sign (Lowest), GDP-57 Nova esteira SIAPE (Lowest), GDP-100 Crivo cadastro (Lowest), GDP-58 Regras do convênio (Lowest), GDP-53, GDP-59, GDP-66, GDP-67, GDP-74, GDP-84, GDP-85, GDP-97, GDP-135, GDP-137. **Técnicos:** US-43 CI/CD (Backlog). | **A confirmar no Inventário.** Evidência no Jira: API em PHP, atualizada da versão 7.3 para a 8 (DS-399, DS-432, DS-412); módulos em Node (`node`, `node-v2`: DS-78, DS-221, DS-322); serviço de websocket com Redis (DS-214, DS-226); Elastic Stack e Elastic APM para observabilidade (log `konsig-api-v1` no formato ECS no DS-412; subtarefa DS-322 "Migrar konsig-api-php & konsig-node" do DS-305); SonarQube (DS-202, DS-231); contêineres Docker (DS-168). Banco de dados: a confirmar. | visao-cartao-v6 (03/11/2026); pdti-2026-2028, slide 10 (20/08/2026); gdp_16-11.csv e upstream_16-11.csv (16/11/2026, 9h51); downstream_16-11.csv e epicos_downstream_16-11.csv (16/11/2026, 10h26) |
| **NeoKonsig** (reescrita) | Nova plataforma de consignado, desenvolvida por módulos. No GDP (GDP-29 a GDP-36 e GDP-87; gdp_16-11.csv, 16/11/2026, 9h51): Parceiros, Convênio, Esteira, Admin, Contratos, Atendimento, Cobrança, Financeiro e Autorregulação. O PDTI, slide 16 (20/08/2026), lista outros módulos: Proposta, Auditoria, Cobrança, CRM, Relatório e Configuração. A divergência fica em aberto até a confirmação no Inventário de Sistemas. | Em construção. Módulo de Parceiros, Entrega 1, em desenvolvimento. | GDP-29 Parceiro ficha cadastro (High, Em Downstream; épico DS-251 com 83 cards, 59 concluídos e 24 abertos), GDP-111 Parceiro dashboard (Em Downstream), GDP-30 Convênio (High, Em Upstream), GDP-34 Esteira (Low), GDP-31 Admin (Low), GDP-33 Contratos, GDP-32 Atendimento, GDP-35 Cobrança, GDP-36 Financeiro (Lowest), GDP-87 Autorregulação (Medium). | **A confirmar no Inventário.** Evidência no Jira: PostgreSQL (DS-405), RabbitMQ na integração com o Konsig (DS-298, DS-541, DS-561), Node (DS-537), Keycloak para autenticação e autorização (US-40). A arquitetura foi definida em GDP-48 e US-21 (Concluídos): arquitetura, integrações, API para parceiros e barramento. | gdp_16-11.csv (16/11/2026, 9h51); epicos_downstream_16-11.csv (16/11/2026, 10h26); pdti-2026-2028, slide 16 (20/08/2026) |
| **CRM API** | Serviço de CRM associado ao Konsig. A fonte não detalha a função de negócio. | Produção. Migração para o novo GitLab em andamento (DS-487, 4 cards, 3 concluídos). | Nenhum item do GDP. | **A confirmar no Inventário.** Evidência no Jira: PHP (DS-317, DS-398); onboarding na AWS (DS-487). | downstream_16-11.csv e epicos_downstream_16-11.csv (16/11/2026, 10h26) |
| **Gatekeeper** | Controle de acesso ao Konsig (sessão, OTP e liberação de IP). | Produção. | Nenhum item do GDP. US-43 cita a "substituição da solução técnica para acesso de usuários extranet". A relação com o Gatekeeper é a confirmar. | A confirmar no Inventário. | downstream_16-11.csv: DS-38, DS-168, DS-289, DS-306 (16/11/2026, 10h26); upstream_16-11.csv: US-43 (16/11/2026, 9h51) |
| **PagAuto** | Componente de pagamentos e comprovantes. Usado na Quitação com a API do Banco do Brasil. | Produção. Migração do APM: tarefa DS-305 pausada; subtarefa do PagAuto (DS-323) em Backlog. | Quitação (GDP-76; DS-500). | A confirmar no Inventário. | contexto-mestre, seção 10 (16/11/2026); downstream_16-11.csv: DS-59, DS-323 (16/11/2026, 10h26) |
| **Keycloak** | Provedor de identidade (autenticação e autorização). | Produção. Migrado para o novo GitLab (DS-479, Concluído, 5 cards). Será o primeiro consumidor do padrão de release (DS-550, Backlog, 0 de 9 cards concluídos). | NeoKonsig (US-40). | Evidência no Jira: PostgreSQL de homologação e produção (DS-481, DS-482). Infraestrutura: a confirmar no Inventário. | upstream_16-11.csv (16/11/2026, 9h51); downstream_16-11.csv e epicos_downstream_16-11.csv (16/11/2026, 10h26) |
| **GitLab** (repositórios e CI/CD) | Repositórios e pipelines. | Em migração para GitLab gerenciado/SaaS: DS-175 (Em desenvolvimento, 6 sprints segundo a Review S18), DS-495 (Backlog). Padronização de release e deploy em DS-550 (Backlog, 9 cards). | US-43 Konsig CI/CD. | Evidência no Jira: GitLab CI/CD Component, versionamento SemVer, imagens Docker e deploy com Ansible por ambiente (DS-550). | downstream_16-11.csv e epicos_downstream_16-11.csv (16/11/2026, 10h26); review-sprint-18 (06/11/2026, 16h46) |
| **NeoFaz** | Sistema interno de compras e viagens. | Viagens implantado em estrutura própria (contexto-mestre). No Jira, o épico DS-125 (Viagens) segue Em desenvolvimento (3 cards, 1 concluído). Compras em construção (DS-159, 3 cards, 1 concluído). | GDP-27 Viagens e GDP-28 Compras (Em Downstream), GDP-88 Inventário corporativo, GDP-104 Documentoscopia e OCR. | A confirmar no Inventário. | contexto-mestre, seção 10 (16/11/2026); gdp_16-11.csv (16/11/2026, 9h51); epicos_downstream_16-11.csv (16/11/2026, 10h26) |
| **Site, blog e intranet** | Presença institucional e intranet. | Produção: GDP-21, GDP-6, GDP-50 e GDP-86 Concluídos. | GDP-94 Melhoria em layout e dados. | Evidência no Jira: CMS Craft (GDP-86, DS-344, DS-457); PHP (DS-404). | gdp_16-11.csv (16/11/2026, 9h51); downstream_16-11.csv (16/11/2026, 10h26) |
| **Observabilidade** | Logs e APM das aplicações. | Produção, com migração para ambiente compartilhado pausada (DS-201, DS-305). Épico DS-24 em Backlog, com 5 cards abertos: 3 em Backlog e 2 em Pausado. | Nenhum item do GDP. | Evidência no Jira: Elastic Stack e Elastic APM (DS-123, DS-305). | downstream_16-11.csv e epicos_downstream_16-11.csv (16/11/2026, 10h26) |
| **Data Lake corporativo** | Base de dados analíticos sob o núcleo Dados. | A fonte não informa. | Macroetapa 21 do cartão (Dados, BI e gestão de carteira). | A confirmar no Inventário. | pdti-2026-2028, slide 10 (20/08/2026); visao-cartao-v6 (03/11/2026) |

### 3.2 Volume de trabalho por sistema no Downstream

Fonte: `downstream_16-11.csv`, extração de 16/11/2026, 10h26. Contagem pelo campo **Categorias**, com todos os tipos de item (Tarefa, História, Bug, Subtarefa e Épico). "Não concluídos" = qualquer status diferente de Concluído.

| Categoria | Itens | Não concluídos |
|---|---|---|
| Konsig | 236 | 88 |
| NeoKonsig | 84 | 23 |
| NeoFaz | 8 | 6 |
| Cartão | 0 | 0 |

Existe ainda 1 item com a categoria "neo-konsig" (DS-559, Backlog), não somado à linha NeoKonsig.

Esta contagem não é vazão e não usa a mesma unidade da capacidade do pool (cards de épico concluídos). Ela serve apenas para mostrar onde o trabalho se concentra.

---

## 4. Integrações externas

| Parceiro | Finalidade | Sistema Neo que integra | Itens do Jira | Fonte |
|---|---|---|---|---|
| **Orbitall** (processadora e BIN Sponsor, sistema ATC) | Abertura de conta e cartão, autorização, antifraude, faturamento, arquivos de transações (TRANDIA via SFTP), relatórios e clearing (T140). | Konsig (originação e efetivação), pela decisão de 13/11/2026. A Visão v6 cita também o NeoKonsig (ver A2). | GDP-38, GDP-112; US-92 (originação e abertura de conta), US-93 (transacional dos arquivos). Nenhum card no Downstream. | visao-cartao-v6 (03/11/2026); gdp_16-11.csv e upstream_16-11.csv (16/11/2026, 9h51) |
| **Mastercard** | Bandeira: autorização, garantia ou colateral, liquidação (settlement) e aprovação do card design. | Sem integração direta. A Neo recebe as informações pela Orbitall. | GDP-38. | visao-cartao-v6 (03/11/2026) |
| **MBLabs** (aplicativo Bankeiro) | Canal do cliente do cartão: ativação, limite, fatura, boleto e comandos do cartão. Integra com a Neo por API. | Konsig. | GDP-113 Infraestrutura MBLabs – Bankeiro (Em Upstream). | visao-cartao-v6 (03/11/2026); gdp_16-11.csv (16/11/2026, 9h51) |
| **Atlanta** | Instituição financeira responsável pela operação regulada do cartão e pelas peças regulatórias (SCR, IOF, Decred). | A fonte não define a integração sistêmica. A Neo prepara o lote contábil. | DS-454 (JUDIT, conglomerado Neo/Atlanta); DS-355 e DS-384 (convênios da Atlanta). | visao-cartao-v6 (03/11/2026); downstream_16-11.csv (16/11/2026, 10h26) |
| **Salesforce** | Atendimento multicanal do cartão: protocolo, consulta e contestações. É uma das três prioridades de 2027. | **Não definido.** US-94 (Plataforma de Atendimento do cartão) pode estar relacionada; a relação é a confirmar. | **Nenhum item** com "Salesforce" no GDP, no Upstream ou no Downstream. | visao-cartao-v6 (03/11/2026); prompt-comite (16/11/2026); busca nos três CSVs (16/11/2026) |
| **Nuvidio** | Assinatura eletrônica e trilha de auditoria da contratação. | Konsig. | GDP-54 e épico DS-85 Receptivo Nuvidio (Concluídos, 12 cards). | gdp_16-11.csv (16/11/2026, 9h51); epicos_downstream_16-11.csv (16/11/2026, 10h26); visao-cartao-v6 (03/11/2026) |
| **Crivo** | Bureau e política de crédito, lista restritiva e decisão automática. | Konsig. | GDP-47 piloto, GDP-98 e GDP-101 (Concluídos); GDP-114 (Highest, Em Upstream), GDP-143, GDP-100. | gdp_16-11.csv (16/11/2026, 9h51) |
| **Xerox** | Documentoscopia, facematch e score. | Konsig. | GDP-56 (Concluído); GDP-107 (High, Em Downstream; épico DS-513 com 9 cards abertos: 8 em Backlog e 1 em Em desenvolvimento, nenhum concluído); GDP-105 e GDP-106 (High). | gdp_16-11.csv (16/11/2026, 9h51); epicos_downstream_16-11.csv (16/11/2026, 10h26) |
| **JUDIT** | Validação de ações judiciais e reprovação automática de propostas. | Konsig. | GDP-118 (Em Downstream); épicos DS-454 e DS-466 (5 cards cada, nenhum concluído). | gdp_16-11.csv (16/11/2026, 9h51); epicos_downstream_16-11.csv (16/11/2026, 10h26) |
| **CAF** | KYC de sócios e CNPJ; consulta de ações judiciais (contingente). | NeoKonsig (DS-354, Concluído). Konsig: GDP-65 (Backlog) e GDP-138 (Backlog). | DS-354, GDP-65, GDP-138. | gdp_16-11.csv (16/11/2026, 9h51); downstream_16-11.csv (16/11/2026, 10h26) |
| **D4Sign** | Assinatura de contrato. | NeoKonsig (DS-365, Concluído). Konsig: GDP-55 (Backlog, Lowest). | DS-365, GDP-55. | gdp_16-11.csv (16/11/2026, 9h51); downstream_16-11.csv (16/11/2026, 10h26) |
| **Cobmais** | Cobrança de inadimplentes (envio de templates e lotes). | Konsig. | GDP-102 (Concluído); GDP-83 Parte 2 (Highest, Priorização Upstream). | gdp_16-11.csv (16/11/2026, 9h51); downstream_16-11.csv: DS-121 (16/11/2026, 10h26) |
| **Celcoin** | KYC, DDA, catálogo de mensagens Pix e conta. | Konsig. | GDP-63 DDA (Concluído); DS-279, DS-366 (Concluídos); DS-79 (Pausado). | gdp_16-11.csv (16/11/2026, 9h51); downstream_16-11.csv (16/11/2026, 10h26) |
| **Serpro / SIAPE** | Consulta de CPF, certificados digitais e convênio SIAPE. | Konsig. | GDP-23 (Concluído); GDP-57 Nova esteira SIAPE (Lowest); DS-171, DS-237. | gdp_16-11.csv (16/11/2026, 9h51); downstream_16-11.csv (16/11/2026, 10h26) |
| **Receita Federal** | Situação cadastral de CPF e CNPJ. | Konsig (GDP-81, Concluído); NeoKonsig (DS-350, Concluído). | GDP-81, DS-350. | gdp_16-11.csv (16/11/2026, 9h51); downstream_16-11.csv (16/11/2026, 10h26) |
| **Núclea** (SCC, MCB, RCC, CRCP) | Registro e averbação no SCC, repasse mensal do MCB, certificado do SRCC, consulta de certificados de agentes (CRCP) e CNPJ alfanumérico. | Konsig. MCB também no NeoKonsig (DS-254, DS-443). | GDP-96 MCB, GDP-62 CRCP (Highest); US-37 CNPJ alfanumérico; DS-67, DS-283, DS-386, DS-387, DS-444. | gdp_16-11.csv e upstream_16-11.csv (16/11/2026, 9h51); downstream_16-11.csv (16/11/2026, 10h26) |
| **Base Não me perturbe** (arquivo SFTP, padrão ABR Telecom) | Importação diária da base de bloqueio de contato (autorregulação). | Konsig. | GDP-132 (Em Downstream); épico DS-97 (5 cards, 4 concluídos); DS-98. | gdp_16-11.csv (16/11/2026, 9h51); downstream_16-11.csv e epicos_downstream_16-11.csv (16/11/2026, 10h26) |
| **Banco do Brasil** | Retorno de pagamentos e pagamento da Quitação (API do BB via PagAuto). | Konsig. | GDP-60 (Concluído), GDP-117; DS-92, DS-93; GDP-61 "Retorno de pagamentos - esteira" (descrição no modelo em branco; relação com o BB a confirmar); Quitação (GDP-76). | gdp_16-11.csv (16/11/2026, 9h51); contexto-mestre, seção 10 (16/11/2026) |
| **OMIE** | API para o Financeiro. A fonte não detalha a finalidade. | **Não identificado.** | GDP-119 (Backlog Upstream; descrição ainda é o modelo em branco). | gdp_16-11.csv (16/11/2026, 9h51) |
| **Portal de consignatárias / ConsigFácil Maranhão** | Integração com portais de convênio e anexação de CCB. | Konsig. | GDP-72 (High), GDP-85 (Low). | gdp_16-11.csv (16/11/2026, 9h51) |
| **RD** | Pesquisa de satisfação e contato. | Konsig. | GDP-22 (Concluído); DS-239. | gdp_16-11.csv (16/11/2026, 9h51); downstream_16-11.csv (16/11/2026, 10h26) |
| **GLPI** | Chamados de suporte, com bot de respostas. | Bot associado ao Konsig. Integração com o Jira em Backlog. | DS-170, DS-203, DS-409, DS-414. | downstream_16-11.csv (16/11/2026, 10h26) |
| **Slack** | Ferramenta de comunicação em migração. A fonte não informa o destino. | Não se aplica (ferramenta corporativa). | GDP-95, US-34. | gdp_16-11.csv e upstream_16-11.csv (16/11/2026, 9h51) |
| **AWS** | Catálogo de bancos e onboarding de aplicações. Também é infraestrutura do Bankeiro, segundo a MBLabs. | Keycloak, CRM API; Bankeiro (MBLabs). | DS-482, DS-487. | downstream_16-11.csv (16/11/2026, 10h26); visao-cartao-v6 (03/11/2026) |
| **Printer, embossadora e logística** (Digital Dados) | Impressão e envio de fatura e boleto; plástico e entrega do cartão físico. | A fonte não define. | Nenhum. | visao-cartao-v6 (03/11/2026) |
| **Compupack** | Atendimento de infraestrutura N1, N2 e N3. | Não se aplica (serviço). | Nenhum. | pdti-2026-2028, slide 11 (20/08/2026) |

---

## 5. Pontos de atenção

| Nº | Ponto | Evidência | Consequência para 2027 | Recomendação |
|---|---|---|---|---|
| A1 | **O Konsig não tem CI/CD**, e é nele que entram o cartão e a reestruturação da esteira. | US-43 "Konsig: CI/CD" em Backlog, prioridade Medium (upstream_16-11.csv, 16/11/2026, 9h51). Regressão automatizada DS-53: 12 cards, 3 concluídos e 9 em Backlog. Padronização de release DS-550: 9 cards em Backlog, começando pelo Keycloak (epicos_downstream_16-11.csv, 16/11/2026, 10h26). DS-175 (migrar repositórios do Konsig) está há 6 sprints em aberto (review-sprint-18, 06/11/2026, 16h46). | Construção nova num sistema sem pipeline de CI/CD (US-43, Backlog) e com a regressão automatizada em andamento (DS-53: 3 de 12 cards concluídos, epicos_downstream_16-11.csv, 16/11/2026, 10h26). O PDTI traz a ação "Adotar pipeline CI/CD..." na diretriz "Definir padrões de desenvolvimento que garantam entregas ágeis e consistentes" (slide 6, 20/08/2026). | Tratar a US-43 e a adoção do DS-550 no Konsig como **pré-requisito do desenvolvimento do cartão**, no primeiro trimestre de 2027 do pool. **[ALÉM DA FONTE — decisão do usuário]** |
| A2 | **A Visão v6 diverge da decisão sobre o NeoKonsig.** | A Visão v6 põe o NeoKonsig como responsável pelo faturamento (macroetapa 13, junto com Orbitall e MbLabs) e pela conciliação (15) e o cita como dependência na cobrança (18) e nos dados (21, responsável "A definir"); no glossário, atribui ao NeoKonsig o ciclo financeiro pós-faturamento; e diz que a Orbitall "integra diretamente com Konsig e NeoKonsig" (visao-cartao-v6, 03/11/2026). A decisão de 13/11/2026 põe o cartão no Konsig legado (contexto-mestre, seção 6). | O pós-faturamento (conciliação, repasse e cobrança) passa a ser construção nova no Konsig, que hoje não cobre esse domínio (contexto-mestre, seção 7). Quem usar a Visão v6 como fonte vai dimensionar o trabalho no sistema errado. | Pedir à autora da Visão a versão v7, com a tabela de atores, as macroetapas 13 e 15 e as dependências das macroetapas 18 e 21 apontando para o Konsig, antes de detalhar os cards. |
| A3 | **Integrações com a Salesforce sem item no Jira.** | Nenhuma ocorrência de "Salesforce" nos três boards (gdp, upstream e downstream de 16/11/2026). O prompt-comite registra que essa prioridade "ainda não tem documento" (16/11/2026). | Uma das três prioridades de 2027 não pode ser dimensionada nem atribuída a um sistema. | Abrir o item no GDP com o modelo de solicitação antes de 30/11/2026, com o Konsig como sistema Neo de origem, porque o atendimento multicanal atende o cartão, que entra no Konsig legado (decisão de 13/11/2026). **[ALÉM DA FONTE — decisão do usuário]** |
| A4 | **A reestruturação da esteira não tem item no Konsig.** O único item de esteira no GDP é do NeoKonsig. | GDP-34 "[NEO-KON] ESTEIRA", prioridade Low (gdp_16-11.csv, 16/11/2026, 9h51). A decisão de 13/11/2026 põe a esteira no Konsig legado. O prompt-comite ainda lista a questão como pendência. | O pool pode contar a mesma demanda duas vezes (no Konsig e no GDP-34) ou deixar de contá-la. | Registrar a decisão sobre a esteira na tabela de decisões consolidadas (contexto-mestre, seção 6), abrir o item da esteira no Konsig e informar no GDP-34 que ele não é a prioridade de 2027. **[ALÉM DA FONTE — decisão do usuário]** |
| A5 | **Divergência tecnológica nos front-ends do Konsig.** | US-71: "Divergência tecnológica entre os frontends dos Módulos do Konsig impede a integração das novos módulos ao sistema existente" (Backlog, sem descrição). O US-71 é subtarefa do US-21 "[NEO-KON] DEFINIÇÃO DE ARQUITETURA PARCEIROS": o impedimento registrado é a integração dos módulos do NeoKonsig ao sistema existente. US-36: análise de componentes comuns do front entre Konsig e NeoKonsig (Backlog) (upstream_16-11.csv, 16/11/2026, 9h51). | Os novos módulos do cartão no Konsig podem enfrentar o mesmo impedimento. **[ALÉM DA FONTE — decisão do usuário]** | Fazer a US-71 junto com a especificação técnica do cartão (US-99). **[ALÉM DA FONTE — decisão do usuário]** |
| A6 | **SSOT entre Konsig e NeoKonsig sem delimitação**, com integração já implementada. | O NeoKonsig cria corban no Konsig via RabbitMQ: integração implementada (DS-298, Concluído) e ajustes em andamento (DS-529 em Aprovação POs; subtarefa DS-561 em Backlog); o ambiente de execução (homologação ou produção) não consta da fonte (downstream_16-11.csv, 16/11/2026, 10h26). A Visão v6 exige que domínios, dados e estados de cada sistema sejam "explicitamente delimitados" (glossário, 03/11/2026). | Risco de dado duplicado ou divergente entre os dois sistemas, que se agrava com o cartão no legado. | Registrar a matriz de SSOT por domínio no Inventário de Sistemas. **[ALÉM DA FONTE — decisão do usuário]** |
| A7 | **Segurança do Konsig com pendências abertas.** | Épico DS-65 Correção de vulnerabilidades: 20 cards, 12 concluídos e 8 abertos (epicos_downstream_16-11.csv, 16/11/2026, 10h26). DS-81 (token de usuário enviado em parâmetro de URL) em Backlog. A atualização para o PHP 8 gerou bugs de efeito colateral (DS-407, DS-409, DS-412, DS-432). | O cartão traz requisitos de PCI DSS e da Mastercard: não gravar CVV, mascarar PAN em logs, definir o escopo do ambiente de dados de cartão (riscos R18 e R19 da Visão v6). | Concluir o DS-65 e o DS-81 antes de o Konsig receber dados de cartão **[ALÉM DA FONTE — decisão do usuário]**, e definir cedo o escopo do ambiente de dados de cartão, como pede o R19. |
| A8 | **Observabilidade e certificados sem controle central.** | DS-24 (épico em Backlog) com 5 cards abertos: 3 em Backlog e 2 em Pausado (epicos_downstream_16-11.csv, 16/11/2026, 10h26); migração do APM pausada (DS-305). Certificados tratados por chamado: DS-237 (certificado do Serpro); DS-283 (certificado do SRCC, Núclea) e DS-444 (certificados do SCC, Núclea, adquiridos junto ao Serpro) (downstream_16-11.csv, 16/11/2026, 10h26). | O risco R16 da Visão v6 pede monitoramento de APIs e de arquivos no horário definido. Há 11 parceiros com item concluído no Konsig: Nuvidio, Crivo, Xerox, Cobmais, Celcoin, Serpro, Receita Federal, Núclea, Não me perturbe, Banco do Brasil e RD (gdp_16-11.csv, 16/11/2026, 9h51, e downstream_16-11.csv, 16/11/2026, 10h26; seção 4 deste documento). | Incluir no Inventário de Sistemas a lista de integrações, com certificado e validade de cada uma. **[ALÉM DA FONTE — decisão do usuário]** |
| A9 | **Cartão sem nenhum card no Downstream.** | A categoria Cartão tem 0 itens no Downstream (downstream_16-11.csv, 16/11/2026, 10h26). A Review S18 registra que "não estão previstas tarefas de desenvolvimento do Cartão" até a Sprint 22 (06/11/2026, 16h46). A Visão v6 indica prazo em novembro/2026. | Confirma que o desenvolvimento do cartão começa em 2027 (contexto-mestre, seção 7). | Nenhuma ação nova. O ponto é insumo para o pool. |

---

## 6. Uso deste documento nas três solicitações

| Solicitação | Como este documento entra |
|---|---|
| 1 · Pool de projetos | Classifica cada demanda por sistema (Konsig, NeoKonsig, NeoFaz ou integração). Os pontos A1, A3 e A4 são itens que o pool precisa tratar. |
| 2 · Documentos para a IA | É um rascunho de entrada até o Inventário de Sistemas oficial ser recebido. A IA não deve afirmar tecnologias marcadas como "a confirmar no Inventário". |
| 3 · Indicadores 2027 | A1 e A8 indicam onde ainda não há base para medir a frequência de deploy, a cobertura de testes automatizados e a disponibilidade das integrações. A definição desses indicadores depende dos indicadores do PDTI, que a apresentação recebida não traz. |
