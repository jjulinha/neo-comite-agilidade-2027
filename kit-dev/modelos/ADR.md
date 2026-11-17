# Modelo · Registro de Decisão (ADR) · kit-dev v2 · 17/11/2026 · proposta

**Tipo (Diátaxis):** explicação. Um ADR registra uma decisão e o porquê dela. Também serve de memória para o agente de IA e para o dev novo: o que está aqui como descartado não se reabre sem fato novo (regra do contexto-mestre: "Não reabrir decisão consolidada sem fato novo").

**Quando usar.** ADR independe do tamanho (PP a GG). Abra um quando houver:
1. escolha de tecnologia, biblioteca, padrão de integração ou de dados que outro time terá de seguir;
2. decisão que afeta os dois sistemas (Konsig e NeoKonsig), como a delimitação de fonte única de verdade entre eles;
3. mudança de documentação ou de padrão de processo (Fluxo V3, Políticas Explícitas V1, guia de cards, régua de tamanho ou este kit);
4. decisão que inverte ou substitui um ADR anterior.
Com o gatilho de dinheiro do kit (pagamento, liquidação, repasse, remuneração de correspondente, decisão automática de crédito), o ADR é obrigatório.

**Quando não usar.** Escolha local que se desfaz dentro de um card: escreva só o Y-statement no card ou no PR. Plano de execução vai para o Plano de Implementação, e não para o ADR.

**Onde fica.** `docs/adr/ADR-<nnnn>_<chave do item>_<assunto>.md` no repositório do sistema, com numeração por repositório (mesmo caminho do v1, lido pelo agente de IA conforme o AGENTS.md). Exemplo: `docs/adr/ADR-0001_GDP-76_pagamento-quitacao-pagauto-api-bb.md`. Enquanto o repositório do Konsig que recebe `docs/` estiver [A CONFIRMAR] (DS-175/DS-495), use a pasta provisória do README. ADR de processo (sem sistema) fica no repositório do Comitê de Agilidade **[ALÉM DA FONTE — decisão do usuário]**. Ferramenta: nenhuma obrigatória (adr-tools opcional) **[ALÉM DA FONTE — decisão do usuário]**.

**Regras.** ADR aceito não se edita: escreve-se outro que o substitui, e o antigo passa a "Substituído por ADR-n". As consequências de um ADR viram o contexto do próximo. Um sistema por ADR: se valer para Konsig e NeoKonsig, abra um em cada repositório, com referência cruzada.

## Cópia em branco

```markdown
# ADR-NNNN · <decisão em uma frase, no infinitivo>

> Y-statement (opcional): No contexto de <caso>, diante de <força ou requisito>, decidimos por <opção>, descartando <alternativas>, para atingir <benefício>, aceitando <custo>.

| Status | Proposto · Aceito · Rejeitado · Substituído por ADR-n · Obsoleto |
|---|---|
| Data | dd/mm/aaaa (proposta) · dd/mm/aaaa (decisão) |
| Sistema (um só) | Konsig · NeoKonsig · outro do Inventário · Processo da TI (sem sistema) |

## Contexto
<!-- A situação, a força que obriga a decidir agora e as restrições. Cada fato com fonte e data. Sem opinião sem fato. -->

## Decisão
<!-- "Decidimos <ação>." No presente, com alcance: onde vale, a partir de quando, para quem. -->

## Alternativas consideradas
<!-- Pelo menos duas reais, além de "não fazer nada". Se só existe uma opção viável, registre a lacuna, e não como alternativa inventada. -->
### A · <escolhida> — Prós: … · Contras: …
### B · <alternativa> — Prós: … · Contras: …
### Ideias abandonadas
<!-- Caminho descartado + motivo do abandono. É o que impede a IA ou o dev novo de propor de novo. -->
- <ideia> — abandonada porque <motivo, com fonte>.

## Consequências
<!-- Uma decisão sem consequência negativa registrada quase sempre foi mal analisada. -->
- Positivas: … · Negativas ou custo: …
- Reversão: como desfazer e quanto custa (ou "não há rollback; contingência: …").
- Dados e regulação (obrigatório em qualquer ADR): CHECKLIST-DADOS-E-REGULACAO.md respondido? (link) · aciona DPO? sim/não

## Links
Card: DS-n · PRD: docs/… · ADR substituído: ADR-n · PR que aplicou: <link>
```

**Status, o que cada um quer dizer:** *Proposto*: escrito e em discussão, não autoriza implementação. *Aceito*: decidido pelo responsável, passa a valer. *Rejeitado*: discutido e recusado; o registro fica para que a discussão não recomece do zero. *Substituído por ADR-n*: outro ADR tomou o lugar. *Obsoleto*: deixou de se aplicar sem substituto, por exemplo porque o componente foi desativado.

**Exemplo de lacuna bem registrada:** no ADR-0001 da Quitação (PagAuto + API BB), "Só uma alternativa ativa aparece nas fontes; a B fica como lacuna, e não como alternativa inventada" (`exemplos/quitacao/ADR-0001_GDP-76_pagamento-quitacao-pagauto-api-bb.md`).

## Anexo opcional · só para ADR de processo ou de documentação

Acrescente ao final do ADR. Não use em decisão técnica dentro de um sistema.

1. **Impacto em documentos:** tabela com documento, seção afetada, o que muda, papel responsável, prazo e feito [ ]. Entra todo documento que passaria a dizer algo falso. O ADR só passa a Aceito com a lista completa.
2. **DACI:** Driver (quem escreve), Approver (um só: tech lead para decisão técnica; Comitê de Agilidade, com a gestão da TI, para processo **[ALÉM DA FONTE — decisão do usuário]**), Contributors, Informed.
Modelo preenchido: `exemplos/processo/ADR-0001_CHAVE-A-CONFIRMAR_nota-vigencia-fluxo-v3.md`.

## Decisões reais que pedem ADR (só a lista; os ADRs não estão escritos)
- JUDIT → CAF: contingência e critério de failover (GDP-138, DS-272).
- Cartão: SSOT Konsig × fornecedores; arquivo × API Conta Nova; CVV nunca gravado nos sistemas da Neo; PAN e CVV mascarados em logs e mensagens (R18 da Visão v6, 03/11/2026).
- Autenticação por header em vez de token na URL (DS-81).
- Padrão de release (DS-550).
- Encerramento do NeoKonsig na Entrega 1 [A CONFIRMAR registro formal].
- Modo sombra e critério de corte da Quitação (DS-500/DS-507).

## Referências de mercado
- Nygard, *Documenting Architecture Decisions* (2011): https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions
- MADR (variante mínima): https://github.com/adr/madr
- Fowler, bliki: https://www.martinfowler.com/bliki/ArchitectureDecisionRecord.html
- Zimmermann, Y-statements: https://medium.com/olzzio/y-statements-10eb07b5a177
- HashiCorp, RFC template (abandoned ideas): https://www.hashicorp.com/how-hashicorp-works/articles/rfc-template
