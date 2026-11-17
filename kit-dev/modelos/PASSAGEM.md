# PASSAGEM · modelo (how-to, Diátaxis)

Pacote de transferência de conhecimento. Tem duas variantes no mesmo arquivo: **(A) encerramento de sistema ou entrega** e **(B) saída de pessoa**. Use só papéis (PO, tech lead, dev, revisor, QA, área solicitante), sem nome de pessoa e sem segredo. Toda a regra de uso deste modelo é [ALÉM DA FONTE — decisão do usuário].

## Quando usar / quando não usar
- **Usar (A):** quando um sistema ou entrega para de receber time. Uso imediato: NeoKonsig ao fim da Entrega 1 (épico DS-251), com o time indo para o Konsig em 2027.
- **Usar (B):** antes de férias, ausência ou troca de time de quem concentra trabalho. Evidência: na S18, 11 de 14 testes com testador identificado foram feitos pela mesma pessoa, e 11 de 23 revisões com revisor identificado também se concentraram em uma pessoa. Os números são parciais: testador e revisor estão preenchidos em menos de um terço dos itens (`review-sprint-18.txt`, slide 14, extração de 06/11/2026 16h46). Há ausências previstas no time até a Sprint 22 (`review-sprint-18.txt`, planejamento).
- **Não usar:** para passar um card de etapa (Dev→Revisor→QA→PO). Nesse caso use a nota de passagem do CARD.md. Também não use para incidente (POSTMORTEM.md) nem para rotina recorrente (RUNBOOK.md); este pacote só aponta para eles.
- **Onde fica:** `docs/passagem/<chave>_<assunto>.md` no repositório do sistema que está sendo deixado (README do kit, seção 5), um arquivo por sistema ou pessoa-papel. Konsig e NeoKonsig nunca no mesmo arquivo. Variante B de férias ou ausência: depois do retorno, apagar ou mover o conteúdo para RUNBOOK/ADR [ALÉM DA FONTE — decisão do usuário].

## (A) Encerramento de sistema ou entrega · estado de parada
**A1. Identificação.** Sistema, épico, versão em produção, data de parada e papel que assina.
**A2. Matriz RF/RN × card × estado.** Uma linha por RF/RN. Estado: implementado, pendente ou descartado. Numeração incerta fica marcada, não corrigida de memória.

| RF/RN | Card(s) | Estado | Observação |
|---|---|---|---|
| RN??? aprovação manual de integração | DS-411 | [A CONFIRMAR] | Resumo traz "[RN???]" |
| RF3? validação de cadastro existente | DS-314 | [A CONFIRMAR] | Número incerto no resumo |

**A3. Pendências abertas com chave.** Exemplo: DS-251 tem 83 cards, 59 concluídos e 24 abertos (`epicos_downstream_16-11.csv`, 16/11/2026 10h26). Liste os 24 com status e destino: fecha, vai para backlog com dono ou é cancelado.
**A4. Dívidas.** Dívida técnica e de documentação, com o card ou o motivo de não haver card.
**A5. Integrações e mocks por ambiente.** Uma linha por integração × ambiente (dev, homolog, produção): real ou mock, e o card que tira o mock.
**A6. Contratos de integração ativos na parada.** Aponte o CONTRATO-DE-INTEGRACAO.md de cada contraparte, com os dois lados: produtor e consumidor, repositório de cada um e papel dono depois da parada (o mesmo de A7, [A CONFIRMAR]). Exemplo: fila RabbitMQ NeoKonsig→Konsig que cria corban (DS-298), com o erro aberto DS-529, Tarefa em Aprovação POs (subtarefa DS-561, ajuste do logger RabbitMQ e da fila q.corban-created-into-konsig) (`downstream_16-11.csv`, 16/11/2026 10h26).
**A7. Dono da sustentação.** Papel responsável por Bug de produção depois da parada: [A CONFIRMAR]. O NeoKonsig está em produção (DS-421) e já tem Bug de produção (DS-566) (`downstream_16-11.csv`, 16/11/2026 10h26).
**A8. Runbook de produção.** Link para o RUNBOOK.md: subir, verificar, reiniciar, rollback, a quem escalar (por papel).
**A9. ADRs retroativos.** Uma linha por decisão já tomada e não registrada (ex.: arquitetura do GDP-48/US-21). Cada uma vira ADR.md curto, com "ideias abandonadas".
**A10. Skills e arquivos de IA reaproveitáveis.** Arquivo, onde está e se serve a outro sistema (ex.: DS-546, skill genérica de workflow, em Code Review, `downstream_16-11.csv`, 16/11/2026 10h26).
**A11. Explicitamente cancelado.** O que não será feito, com quem decidiu (papel) e onde está registrado. Exemplo: gestão, rescisão e manutenção de parceiros do GDP-29 não têm item no Jira (`gdp_16-11.csv`, 16/11/2026 9h51); o US-20 está concluído com "ESCOPO: em andamento" (`upstream_16-11.csv`, 9h51). Sem esta linha, o escopo fica sem dono e sem registro.
**A12. Retrospectiva de encerramento.** Data, o que levar ao sistema de destino, o que não repetir. Hoje há um card genérico de retrospectiva, o DS-374, em Backlog e sem descrição (`downstream_16-11.csv`, 16/11/2026 10h26). Confirmar se é ele ou abrir um próprio [A CONFIRMAR].

## (B) Saída de pessoa · férias, ausência ou troca de time
**B1. Papel e janela de cobertura:** a partir de quando quem assume responde e até quando vale a passagem. Não registrar motivo da saída nem nome.
**B2. Em andamento, por card.** Chave, status, próximo passo, branch ou PR, bloqueio.
**B3. Onde está cada coisa.** Repositório, pasta, documento, ambiente, quadro. Link, não descrição.
**B4. Acessos e rotinas só desta pessoa.** O que executa, com que frequência e qual acesso exige. Nunca senha, token ou chave: diga onde o acesso é concedido.
**B5. Quem assume, por papel.** Uma linha por card ou rotina: papel que assume, a partir de quando.
**B6. Conhecimento não escrito.** Armadilhas, decisões de cabeça, "por que é assim". Cada item vira RUNBOOK.md (como fazer) ou ADR.md (por que), com card.

## Quem chega ao sistema de destino
Quem chega ao sistema de destino segue o guia de entrada do SISTEMA.md dele.

## Pronto quando
- (A) todas as linhas A2–A12 preenchidas ou marcadas [A CONFIRMAR] com papel responsável; (B) revisado por quem assume antes da saída.
- Revisão no mesmo PR que cria os RUNBOOK/ADR/CONTRATO derivados.

## Referências de mercado
- Diátaxis, tipos de documento (este modelo é how-to): https://diataxis.fr/ (via busca)
