# Postmortem (análise pós-incidente sem culpa)

> Tipo: modelo de trabalho. Um arquivo por incidente, em `docs/postmortems/AAAA-MM-DD_<chave>_<assunto>.md`: um arquivo só, no repositório do sistema onde está a causa; o outro sistema recebe um link. Konsig e NeoKonsig nunca no mesmo campo "Sistema" sem dizer qual é a origem. Enquanto o repositório definitivo do Konsig que recebe `docs/` estiver [A CONFIRMAR] (DS-175, épico DS-495), use a pasta provisória definida no README do kit, seção 4 [ALÉM DA FONTE — decisão do usuário].
>
> Hoje não existe modelo de RCA ("Não localizado", `D2-documentos-ia/D2-documentos-para-a-IA.md`, T6). Dos 31 Bugs do Downstream, só 1 menciona "causa raiz" (DS-436), e é para dizer que a hipótese não foi confirmada (`downstream_16-11.csv`, 16/11/2026 10h26; `D2-documentos-para-a-IA.md`, T6).

## Quando usar / quando não usar
**Usar** quando bater **um** gatilho. A lista inteira é [ALÉM DA FONTE — decisão do usuário]:
- P1 (Crítica) ou P2 (Alta) da tabela de sustentação do PDTI (`pdti-2026-2028.txt`, slide 14, modificada em 20/08/2026): P2 = afeta 50% ou mais de um setor; P1 = afeta mais de um setor essencial, ou afeta severamente ou paralisa as operações;
- card de classe Expedite, ou Bug em produção. Bug em produção sem impacto P1/P2, sem dinheiro e sem perda de dado usa a **versão curta**: seções 1, 5, 7 e 8, em até meia página [ALÉM DA FONTE — decisão do usuário]. Alternativa a levar ao usuário: restringir este gatilho a "Bug em produção P1/P2";
- perda de dado, de qualquer tamanho;
- pagamento ou decisão de crédito errada (quitação, repasse, reprovação automática);
- incidente com dado pessoal: avaliar comunicação (LGPD, art. 48) e acionar o DPO. Fluxo do DPO [A CONFIRMAR]. Siga também o `CHECKLIST-DADOS-E-REGULACAO.md`.

Qualquer papel pode pedir um postmortem (dev, QA, PO, tech lead, área solicitante). Prazo: até **5 dias úteis** depois de normalizado [ALÉM DA FONTE — decisão do usuário].

**Não usar** no lugar do Bug card. O card (modelo de Bug do `CARD.md`) registra causa, versão ou deploy e card de origem de **todo** Bug; o postmortem é só para incidente com gatilho e aponta para o card. Não é avaliação de desempenho: sem nome de pessoa, sem ranking, sem placar.

---

## Modelo
**Incidente:** <título curto> · **Sistema (origem da causa):** Konsig | NeoKonsig · **Sistema afetado, se outro:** <link> · **Gatilho:** <qual da lista> · **Prioridade PDTI:** P1–P4 · **Cards:** <DS-…> · **Status:** rascunho | revisado | ações concluídas · **Autor (papel):** <…>

1. **Resumo.** Três a cinco frases: o que quebrou, por quanto tempo, como foi resolvido.
2. **Impacto.** Usuários (quantos perfis/setores), operações (o que parou), dinheiro (valor ou "não houve", com fonte), dado (perdido, exposto, corrigido). Número sem fonte vira [A CONFIRMAR].
3. **Linha do tempo.** Tabela `data hora | fato | fonte` (log, card, mensagem). Do primeiro sinal até a normalização. Fato, não opinião. Sem CPF, CNPJ, nome, e-mail ou telefone de cliente ou colaborador. Mascare o log e cite a fonte pelo identificador (card, horário, arquivo de log).
4. **Detecção.** Como soubemos: alerta, usuário, área solicitante, acaso. Quanto tempo entre o início e a detecção.
5. **Causas que contribuíram.** Separe **técnicas** (código, dado, infra, fornecedor) e **de processo** (teste, revisão, deploy manual, aviso que não chegou). Escreva sobre o sistema e o fluxo, nunca sobre pessoa: "o deploy subiu sem regressão do fluxo X", não "fulano não testou". Hipótese não confirmada fica marcada como hipótese.
6. **O que funcionou e o que não funcionou.** Duas listas curtas: o que ajudou a conter e o que atrasou.
7. **Origem do defeito.** Card, versão ou deploy que introduziu o problema. Se não há registro de release, escreva isso: é uma causa de processo.
8. **Ações.** Tabela `ação | tipo (prevenir, detectar, mitigar) | dono (papel) | prazo | card no Jira`. Ação sem card não entra.
9. **Teste de regressão ou monitoração adicionada.** Nome do teste ou do alerta e onde está. "Nenhuma" exige motivo.
10. **Documentos atualizados.** `CONTRATO-DE-INTEGRACAO.md`, `RUNBOOK.md`, seção "Armadilhas" do `AGENTS.md`, PRD, ADR. Link de cada um, no mesmo PR quando possível.

---

## Exemplos reais para preencher o modelo (fatos de `downstream_16-11.csv` e `epicos_downstream_16-11.csv`, 16/11/2026 10h26)
- **Série PHP 7.3→8 no Konsig.** A análise de impacto DS-399 foi concluída em 26/10/2026; entre 26/10 e 30/10 vieram os Bugs DS-407, DS-409, DS-412 e DS-432, todos citando o PHP. Seção 7: o upgrade. Seção 5, processo: épico de regressão automatizada DS-53 com 3 de 12 cards concluídos e 9 em Backlog (`epicos_downstream_16-11.csv`, 16/11/2026 10h26) e Konsig sem CI/CD (US-43, `upstream_16-11.csv`, 16/11/2026 9h51). Seção 9: regressão dos fluxos críticos.
- **DS-272, JUDIT 401 (Tarefa de classe Expedite, não Bug).** Em 18/09/2026 a JUDIT "subiu uma atualização de segurança, a qual nos barrou". Seção 5, técnica: atualização de segurança do fornecedor bloqueou a autenticação (401); se houve aviso prévio é hipótese [A CONFIRMAR]. Correção feita pelo fornecedor, sem mudança no código (DS-272, Tarefa Expedite, 18/09/2026). Seção 10: contrato de integração da JUDIT com autenticação e canal de aviso de mudança, mais runbook de indisponibilidade.

## Referências de mercado
- Google SRE Book, cap. 15, "Postmortem Culture: Learning from Failure": https://sre.google/sre-book/postmortem-culture/
- Google SRE Workbook, cap. 10, "Postmortem Culture" (modelos e exemplos): https://sre.google/workbook/postmortem-culture/
- [A CONFIRMAR] acesso às URLs.
