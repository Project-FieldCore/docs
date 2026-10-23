# Convenção de branches, commits e tarefas — FieldOps

Como nomear tasks (issues), branches e commits nos 4 repositórios
(`api-java`, `web-react`, `mobile-react`, `docs`). Mantido neste repositório;
(renomeados a partir de `fieldcore_*` — ver [REPO_RENAME_GUIDE.md](REPO_RENAME_GUIDE.md)).
mudou a convenção, mudou aqui primeiro e as issues abertas são renomeadas
na weekly.

## 1. Tarefas: hierarquia PBI → filho → tarefa

A fonte do backlog é o Notion (doc. 15): **PBI-XXXX** é o item pai.
A numeração abaixo carrega o caminho inteiro — ela é a estrutura,
não precisamos de barras extras para representar a árvore.

| Nível | Nome da issue | Exemplo |
|---|---|---|
| Pai (história do Notion) | `PBI-XXXX — <história curta>` | `PBI-0007 — Autenticar usuário com e-mail e senha` |
| Filho (por componente) | `PBI-XXXX.N [COMPONENTE] <entrega>` | `PBI-0007.1 [API] Login e emissão de tokens` |
| Tarefa (divisão técnica) | `PBI-XXXX.N.M <passo técnico>` | `PBI-0007.1.1 Emitir access token JWT` |

- Componentes: `API`, `WEB`, `MOBILE`, `DOCS`, `CLOUD`, `INTEGRACAO`.
- Numere os filhos na ordem da dependência (`.1` API antes de `.2` WEB/MOBILE
  quando o cliente depende do contrato).
- No GitHub, replique a árvore com **sub-issues nativas**: a issue filha é
  sub-issue da pai, a tarefa é sub-issue da filha. O board mostra o progresso
  pela árvore, não por texto no título.
- Filho de dev único e pequeno **não gera branch de tarefa**: vira checklist
  dentro da própria issue filha.

## 2. Branches: código numérico achatado, slug descritivo

Formato: `<tipo>/PBI-XXXX[-N[-M]]-<slug-curto>`

```text
feat/PBI-0007-autenticacao                 pai (branch de integração, só p/ PBI grande)
feat/PBI-0007-01-api-login                 filho
feat/PBI-0007-01-01-emitir-access-token    tarefa → PR para a branch do filho
feat/PBI-0007-01-02-refresh-rotation       tarefa → PR para a branch do filho
feat/PBI-0007-02-mobile-login              filho → PR para develop/main
docs/PBI-0001-branch-management            docs segue o mesmo padrão
fix/PBI-0052-corrigir-duplicidade-sync
```

Regras:

- **Nunca** `feat/PBI-0007/refresh`: se existir a branch `feat/PBI-0007`,
  o Git recusa `feat/PBI-0007/refresh` (conflito arquivo×diretório de ref).
  A hierarquia vive nos números (`-01`, `-01-01`), não em barras.
- Tipos: `feat`, `fix`, `docs`, `chore`, `test`, `refactor` (minúsculas,
  slug sem acento, palavras com `-`).
- Base e destino: tarefa → branch do filho (se existir) → `develop`
  (frontend/mobile) ou `main` (backend/docs/cloud, que não têm `develop`).
  PBI pequeno, sem branch pai: filho → `develop`/`main` direto.
- Uma branch por issue em andamento; branch mergeada é apagada no merge.

## 3. Commits e PRs

- Commit: `:gitmoji: type: descrição curta no infinitivo` (padrão já usado
  nos repos — ver [CONTRIBUTING.md](../CONTRIBUTING.md)). Sem trailers de
  co-autoria de IA.
- PR: título `[PBI-XXXX] <descrição>`; corpo com `Closes #<issue>` (ou
  `Part of #<pai>` para filho/tarefa), resumo e evidência conforme o DoD
  (Notion doc. 18): print/vídeo (UI), request/response (API), schema +
  verificação (dados). Docs-only não exige evidência de runtime.
- PR de tarefa referencia a issue **filha**; quem fecha a pai é o último
  filho, citando todos os `Closes`.

## 4. Board e campos (GitHub Projects da organização)

Um único Project canônico: **[FieldOps — Product Backlog (Notion)](https://github.com/orgs/Project-FieldCore/projects/9)** (org `Project-FieldCore`, #9).

| Campo | Valores |
|---|---|
| Status | Backlog · Ready · In progress · In review · Done · Blocked |
| Sprint | Sprint 1 … Sprint 8 (estrutura do Notion doc. 16) |
| Épico | EP-01 … EP-10 (Notion doc. 15) |
| Prioridade | P0 · P1 · P2 |
| Componente | API · WEB · MOBILE · DOCS · CLOUD · INTEGRACAO |
| Pontos | Fibonacci (1, 2, 3, 5, 8, 13) — ver [SPRINT_PLANNING.md](SPRINT_PLANNING.md) |

Labels nos repos (criar as que faltarem, apagar as genéricas auto-criadas):
`pbi`, `epic/EP-XX`, `sprint/N`, `priority/P0|P1|P2`,
`component/api|web|mobile|docs|cloud`.

Histórico: em 19–20/10/2026 os 8 Projects e as 327 issues anteriores foram
apagados (sem rastreabilidade PBI, triplicados, estados inválidos) e os
39 milestones removidos; branches, PRs e commits foram mantidos. Backup
integral exportado antes da exclusão e decisão registrada em
[DECISIONS/0001-reset-github-notion-pbi.md](../DECISIONS/0001-reset-github-notion-pbi.md).
