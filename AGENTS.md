# FieldOps — contexto para assistentes de IA (agnóstico de ferramenta)

Este arquivo é o **ponto de entrada** para qualquer agente ou IDE com IA
(Cursor, Claude Code, Copilot, Codex, Windsurf, Aider, etc.). Não depende de
um produto específico: leia isto primeiro; depois siga os links.

Humanos: o mesmo mapa serve como índice de convenções. Detalhes longos ficam
nos arquivos linkados — **não duplique regras aqui**.

## 1. O que é este monorepo lógico

| Papel | Nome | Repo |
|---|---|---|
| Produto | **FieldOps** | — |
| Org GitHub | **FieldCore** (`Project-FieldCore`) | — |
| API | Java 25 + Spring Boot + PostgreSQL / Flyway | [api-java](https://github.com/Project-FieldCore/api-java) |
| Web admin | Next.js + TypeScript ([ADR 0002](DECISIONS/0002-web-nextjs-instead-of-angular.md)) | [web-react](https://github.com/Project-FieldCore/web-react) |
| Mobile técnico | Expo + React Native + TypeScript | [mobile-react](https://github.com/Project-FieldCore/mobile-react) |
| Documentação (você pode estar aqui) | Markdown + export Notion | [docs](https://github.com/Project-FieldCore/docs) |

Branch de integração atual dos apps: **`develop`** (release PRD/`main` ainda não é o fluxo diário).  
Repo `docs`: PRs para **`main`**.

Board canônico: [FieldOps — Product Backlog (Notion)](https://github.com/orgs/Project-FieldCore/projects/9) (Project #9).

## 2. Ordem de leitura (sessão nova)

1. Este `AGENTS.md`
2. [GLOSSARIO.md](GLOSSARIO.md) — termos do domínio
3. Convenções operacionais (abaixo)
4. Spec do produto em [`NOTION/`](NOTION/README.md) (export; fonte = Notion)
5. ADRs em [`DECISIONS/`](DECISIONS/README.md)
6. Só então o código do repo em que está trabalhando

## 3. Mapa de convenções (fonte da verdade)

| Tema | Onde | Resumo |
|---|---|---|
| Issues / branches / commits / **título de PR** | [PROJECT_MANAGEMENT/BRANCH_COMMIT_CONVENTION.md](PROJECT_MANAGEMENT/BRANCH_COMMIT_CONVENTION.md) | PBI → filho → tarefa; branch `tipo/PBI-XXXX-…`; commit `:gitmoji: type: …`; PR **`[PBI-XXXX]`** / `[PBI-XXXX.N]` |
| CI (lint, types, build, verify) | [PROJECT_MANAGEMENT/CI_CONVENTION.md](PROJECT_MANAGEMENT/CI_CONVENTION.md) | Pipeline verde no PR; actions pinadas por SHA; `permissions: contents: read`; sem `pull_request_target` / secrets |
| CI local por app | `api-java`/`web-react`/`mobile-react` → `docs/CI.md` | Como repetir a CI na máquina |
| Templates de issue/PR | [`.github/ISSUE_TEMPLATE/`](.github/ISSUE_TEMPLATE/) · [pull_request_template.md](.github/pull_request_template.md) | Formulários PBI / filho-tarefa; corpo de PR |
| Rename de repos | [PROJECT_MANAGEMENT/REPO_RENAME_GUIDE.md](PROJECT_MANAGEMENT/REPO_RENAME_GUIDE.md) | Atualizar `origin` + pasta local |
| Sprints / DoD / backlog | [SPRINT_PLANNING.md](PROJECT_MANAGEMENT/SPRINT_PLANNING.md) · Notion docs 15–18 | PBI, pontos, DoD |
| Contribuir neste repo `docs` | [CONTRIBUTING.md](CONTRIBUTING.md) | Notion vs gestão; fluxo Git da doc |
| Decisões de arquitetura | [DECISIONS/](DECISIONS/README.md) | ADR 0001 reset GitHub; ADR 0002 Next.js |
| Índice de gestão | [PROJECT_MANAGEMENT/README.md](PROJECT_MANAGEMENT/README.md) | TAP, cronograma, EAP |

Índice curto também em [PROJECT_MANAGEMENT/CONVENTIONS.md](PROJECT_MANAGEMENT/CONVENTIONS.md).

## 4. Regras não negociáveis (ao gerar código ou PRs)

1. **Não inventar stack** — web = Next.js; mobile = Expo; API = Spring Boot (ver ADRs).
2. **Não commitar segredos** — JWT/DB só por env; CI sem `secrets.*` no baseline de PR.
3. **Título de PR** começa com `[PBI-XXXX]` ou `[PBI-XXXX.N]` (ver convenção §3).
4. **Branch** no formato da convenção; base `develop` (apps) ou `main` (docs).
5. **Issue** via template (História, Critérios, Dependências, DoD); linkar PR com `Closes` / `Part of` / `Related to`.
6. **NOTION/** — não editar como fonte; corrigir no Notion e reexportar.
7. **Sem overengineering** — mudanças mínimas; CI/lint simples; sem refactors “de passagem”.
8. **Evidência no DoD** — UI print/vídeo; API request/response; dados schema; docs-only N/A runtime.
9. **Erros API** — envelope padronizado do projeto (`code`, `message`, `path`, …) quando tocar backend/clientes HTTP.
10. **Idioma** — produto e docs em português (BR) salvo código/ids em inglês (`api-java`, enums, paths).

## 5. Como trabalhar com backlog

- Item pai: `PBI-XXXX — …` (issue no repo do componente principal).
- Filho por componente: `PBI-XXXX.N [API|WEB|MOBILE|DOCS] …`.
- Não use issue-modelo fixa: use *New issue* → templates do GitHub.
- Status no Project #9: Backlog → Ready → In progress → In review → Done.

## 6. Por repositório (o que a IA deve abrir)

| Repo | Além deste guia |
|---|---|
| `docs` | [CONTRIBUTING.md](CONTRIBUTING.md), [NOTION/README.md](NOTION/README.md) |
| `api-java` | `README.md`, `docs/CI.md`, `src/main/resources/db/migration/`, OpenAPI em `openapi/` |
| `web-react` | `README.md`, `docs/CI.md`, `app/`, `src/components/States.tsx` |
| `mobile-react` | `README.md`, `docs/CI.md`, app em `fieldops-mobile/` (`src/app`, `src/features`, `src/design-system`) |

Cada repo de código deve ter um `AGENTS.md` **curto** que só aponta para
`https://github.com/Project-FieldCore/docs/blob/main/AGENTS.md` (este arquivo)
mais notas locais — evita divergência.

## 7. Ferramentas de IA — sem acoplamento

- **Canônico:** este `AGENTS.md` (+ links acima).
- Arquivos opcionais de um vendor (`.cursor/rules`, `CLAUDE.md`, `.github/copilot-instructions.md`, etc.) devem **apenas referenciar** este guia, não reescrever regras.
- Playbooks de orquestração multi-agente no workspace do time (ex.: Maestri / agent-playbook) são **host local** — não substituem estas convenções de produto no GitHub.

## 8. Checklist rápido antes de abrir PR

- [ ] Título `[PBI-XXXX] …` ou `[PBI-XXXX.N] …`
- [ ] Branch no padrão; base correta (`develop` / `main`)
- [ ] `Closes` / `Part of` / `Related to` no corpo
- [ ] CI local equivalente (`docs/CI.md` do repo) passando
- [ ] Sem segredo; docs/ADR atualizados se mudou decisão ou convenção
- [ ] Critérios da issue e DoD considerados

---

Mantenedor: time FieldOps. Mudou uma convenção? Atualize o arquivo canônico em
`PROJECT_MANAGEMENT/` (ou ADR) **e** revise a tabela da §3 deste guia no mesmo PR.
