# ADR 0001 — Reset do GitHub (boards/issues/milestones) e backlog canônico por PBI do Notion

- **Status:** aceita
- **Data:** 2026-10-20
- **Decisores:** Gustavo Sousa (Orquestrador), a partir de auditoria completa via `gh`

## Contexto

A organização `Project-FieldCore` acumulou 8 GitHub Projects (dois chamados
"Backend", boards com issues de outro repositório, boards fechados e vazios),
327 issues e 39 milestones criados em rajadas a partir de decomposições por
componente/disciplina — **nenhuma** issue referenciava os PBIs do backlog do
produto (Notion doc. 15, PBI-001…082). Títulos de governança estavam
triplicados nos três repos de código, os estados não refletiam o código
(ex.: Sprint 1 do backend com 34 issues abertas após o merge do scaffold,
PR #76) e três esquemas de nomenclatura coexistiam (`Sprint N —`, telas do
frontend, `MOB-NN`).

## Decisão

Apagar os 8 Projects, as 327 issues e os 39 milestones; manter branches,
pull requests, commits e o código. O backlog passa a ser criado **somente**
a partir dos PBIs do Notion (doc. 15), um Project canônico da organização,
issues nos repositórios dos componentes com sub-issues por componente —
convenção em [PROJECT_MANAGEMENT/BRANCH_COMMIT_CONVENTION.md](../PROJECT_MANAGEMENT/BRANCH_COMMIT_CONVENTION.md)
e planejamento em [PROJECT_MANAGEMENT/SPRINT_PLANNING.md](../PROJECT_MANAGEMENT/SPRINT_PLANNING.md).

Antes da exclusão foi exportado backup integral (issues com corpo/labels/
milestones/comentários, itens e campos dos 8 boards) para
`.cursor/orchestration/backup-gh/20261019-211347/` no workspace do
orquestrador (fora dos repositórios).

## Consequências

- Perde-se o histórico de issues como evidência de processo no GitHub
  (frontend/mobile não têm PRs); o backup exportado é a referência desse
  período e o código/commits permanecem como evidência do que foi entregue.
- Busca, milestones e board nascem limpos e rastreáveis ao Notion;
  qualquer card novo sem `PBI-XXXX` no título está fora da convenção.
- As divergências Angular×Next.js e nome do produto continuam pendentes
  de ADR própria (ver índice em [README.md](README.md)).
