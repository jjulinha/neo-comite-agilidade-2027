# RUNBOOK · [rotina, falha ou deploy] · [Konsig | NeoKonsig]

> Tipo Diátaxis: **how-to**. Um arquivo por rotina ou falha, em `docs/runbooks/` do repositório do sistema (enquanto o repositório do Konsig estiver [A CONFIRMAR], DS-175/DS-495, use a pasta provisória do README). Um sistema por arquivo.

## Quando usar / quando não usar
- **Use** quando houver: rotina recorrente (agendada ou por evento); falha que já ocorreu duas vezes; deploy manual (Konsig sem CI/CD: US-43 em Backlog, `upstream_16-11.csv`, 16/11/2026 9h51); integração com rotina agendada ou falha conhecida (ligue ao CONTRATO-DE-INTEGRACAO.md da contraparte). [ALÉM DA FONTE — decisão do usuário: gatilhos]
- **Não use** para: decisão (ADR.md), análise de incidente (POSTMORTEM.md), dados da contraparte como layout e certificado (CONTRATO-DE-INTEGRACAO.md, que aponta para cá), deploy de uma entrega só (Plano §5).
- **Por que existe:** há rotinas e procedimentos que se repetem e hoje dependem de quem lembra: a importação diária do NMP, com 3 tentativas antes das 07h e aviso no Teams (DS-98); a recepção diária do TRANDIA por SFTP (Visão do Cartão v6); o deploy manual do Konsig (US-43 em Backlog, `upstream_16-11.csv`, 16/11/2026 9h51); a renovação de certificados, feita de forma reativa (DS-295: "temos atuado de forma reativa"; DS-237, DS-283, DS-444; `downstream_16-11.csv`, 16/11/2026 10h26).

## Modelo
**1. Gatilho ou sintoma.** O que dispara: horário, alerta, mensagem de erro literal, pedido da área. Ex.: "importação ABR não concluída às 07h".
**2. Pré-requisitos e acessos.** Por papel (dev, tech lead, infraestrutura). Diga *qual* acesso, nunca o segredo, host ou conta.
**3. Passos numerados.** Um passo por linha, com o comando ou a tela exata e o que conferir depois dele. Sem "verificar se está ok".
**4. Como verificar que resolveu.** Evidência observável: contagem de registros, status, log, tela. Sem CPF ou dado real no exemplo.
**5. Rollback.** Por passo, ou "não há rollback" com a contingência. Pagamento enviado ao banco não se desfaz por rollback de código (ADR-0001 da Quitação).
**6. Escalonamento.** Por papel e em ordem (dev → tech lead → infraestrutura/fornecedor), com o tempo de cada nível pela tabela de SLA do PDTI, slide 14 (P1 a P4). Prazo diferente do PDTI só com justificativa [ALÉM DA FONTE — decisão do usuário].
**7. Quem é avisado e por qual canal.** Papel + canal (grupo do Teams, card no Downstream). Falha que vira incidente P1/P2 (PDTI, slide 14) abre POSTMORTEM.md.
**8. Última execução:** dd/mm/aaaa · **Última revisão:** dd/mm/aaaa · **Dono:** papel. Runbook não executado nem revisado em 6 meses é suspeito. [ALÉM DA FONTE — decisão do usuário]

## Variante · Deploy e rollback do Konsig (sem CI/CD)
Esta variante substitui o exemplo do Plano §5 quando o deploy se repete igual a cada entrega, como o próprio Plano §5 orienta; o Plano passa a apontar para cá, com as diferenças da entrega.

Sequência manual, ilustrativa até o Inventário de Sistemas e o DS-550 (Plano §5) [ALÉM DA FONTE — decisão do usuário]:
1. Tech lead gera o pacote a partir do branch principal revisado e cria a tag da versão.
2. Infraestrutura aplica em [ambiente A CONFIRMAR]; scripts de banco na ordem e com a reversão da tabela do Plano §8.4.
3. QA executa a regressão manual dos fluxos críticos afetados.
4. PO libera para produção; dev confere o passo 4 do modelo e registra a linha abaixo.

**Registro de release** (uma linha por deploy, mais recente em cima). Evidência: o épico DS-286 teve 4 cards "Deploy dd/mm" (DS-287, DS-343, DS-344, DS-367), todos sem descrição, e nenhum dos 31 Bugs cita versão ou deploy de origem na descrição (`downstream_16-11.csv`, 16/11/2026 10h26) [A CONFIRMAR: sistema de cada deploy].

| Data | Versão ou tag | Cards (DS-) | Quem liberou (papel) | Rollback? (sim/não, motivo) |
|---|---|---|---|---|
| dd/mm/aaaa | vX.Y.Z | DS-nnn, DS-nnn | PO | não |

Quando o DS-550 (SemVer, tags protegidas, Ansible; 9 cards em Backlog, `downstream_16-11.csv`, 16/11/2026 10h26) for adotado no Konsig, este runbook segue o padrão dele [A CONFIRMAR: relação do DS-550 com a US-43, sem vínculo no Jira]. O Bug cita a versão desta tabela no campo "versão ou deploy" do CARD.md.

## Runbooks prioritários (Konsig, salvo indicação)
- **NMP:** importação ABR antes das 07h, falha nas 3 tentativas, aviso no Teams (DS-98). Canal e destinatários [A CONFIRMAR] (DS-341).
- **Cartão:** recepção diária do TRANDIA por SFTP e conferência da liquidação [A CONFIRMAR, Plano de Atividades não recebido].
- **Quitação:** execução agendada do motor e "Reavaliar" (PC-05; horário não definido, DS-501).
- **JUDIT:** indisponibilidade ou 401 (DS-272: 401 após mudança do fornecedor, tratado como Expedite).
- **Certificados:** renovação (DS-295, pausado; hoje um card avulso a cada renovação: DS-237, DS-283, DS-444, natureza Arquitetura; o DS-295 registra atuação reativa).
- **NeoKonsig em produção após a Entrega 1** (DS-421, DS-566): runbook do lado NeoKonsig, entregue com PASSAGEM.md; dono em 2027 [A CONFIRMAR].
- **Deploy e rollback do Konsig:** a variante acima.

## Referências de mercado
Não há norma para runbook; as definições vêm de fornecedores e os termos variam.
- PagerDuty, "What is a runbook": o playbook cobre o quadro geral; o runbook, a tarefa. https://www.pagerduty.com/resources/learn/what-is-a-runbook/
- Rootly, "Runbook vs playbook": o glossário usa os dois termos de forma intercambiável, o que reforça que os termos variam. https://docs.rootly.com/glossary/runbook-vs-playbook
- Diátaxis (how-to): https://diataxis.fr/
