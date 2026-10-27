# Convenção de CI — FieldOps

Expectativa mínima de Continuous Integration nos repositórios de código da org
[Project-FieldCore](https://github.com/Project-FieldCore). Mantido aqui (repo
`docs`); cada app pode ter um `docs/CI.md` / seção no README com detalhes
locais.

## Princípios

- Pipeline **verde em todo PR** (e em push para a branch de integração).
- Práticas simples da comunidade: install com lockfile, lint, typecheck; build
  só onde fizer sentido no dia a dia.
- Actions de terceiros **pinadas por SHA** (com comentário da tag).
- Cache de dependências quando o setup action suportar.
- Sem overengineering: sem matrix desnecessária, sem deploy neste estágio,
  sem EAS Build obrigatório no PR do mobile.

## Por repositório

| Repo | Branch base | Trigger | O que roda na CI | Como rodar local |
|---|---|---|---|---|
| [api-java](https://github.com/Project-FieldCore/api-java) | `develop` | `pull_request` + push `develop`/`main` | Build + testes (Maven/Gradle do repo) — ver PBI-0005.1 | Comando de build/test documentado no README do repo |
| [web-react](https://github.com/Project-FieldCore/web-react) | `develop` | `pull_request` + push `develop`/`main` | `npm ci` → `lint` → `typecheck` → `build` (Next.js) | `npm ci && npm run lint && npm run typecheck && npm run build` |
| [mobile-react](https://github.com/Project-FieldCore/mobile-react) | `develop` | `pull_request` + push `develop`/`main` | No diretório `fieldops-mobile/`: `npm ci` → `lint` → `typecheck` (sem EAS) | `cd fieldops-mobile && npm ci && npm run lint && npm run typecheck` |

Detalhes por app:

- Web: [web-react/docs/CI.md](https://github.com/Project-FieldCore/web-react/blob/develop/docs/CI.md)
- Mobile: [mobile-react/docs/CI.md](https://github.com/Project-FieldCore/mobile-react/blob/develop/docs/CI.md)

## Branches e proteção

- Código de produto: PRs para **`develop`** (integração). `main` recebe
  releases / promoção conforme o fluxo do repo.
- Recomendado: branch protection em `develop` (e `main` quando usado) exigindo
  o check `CI` verde antes do merge.
- Docs (`docs`): PRs para **`main`**; este repo não exige o mesmo pipeline Node —
  validação humana + links.

## Scripts npm esperados (web / mobile)

| Script | Comando típico | Obrigatório |
|---|---|---|
| `lint` | ESLint / `next lint` | Sim |
| `typecheck` | `tsc --noEmit` | Sim |
| `build` | `next build` (web) | Web sim; mobile não na CI de PR |

## Gaps conhecidos (baseline atual)

- **api-java:** CI de backend é entrega separada (PBI-0005.1); esta convenção
  descreve a expectativa mesmo antes do workflow existir.
- **mobile:** CI de PR **não** executa EAS Build nem testes em emulador —
  apenas lint e tipos.
- **web:** warnings de ESLint não falham o job por padrão (`next lint`); erros
  e falha de typecheck/build falham o pipeline.
- Testes unitários (`vitest` / Jest) podem entrar depois; não bloqueiam o
  baseline de PBI-0005.

## Referências

- Backlog: [PBI-0005](https://github.com/Project-FieldCore/docs/issues/2)
- Branches/commits: [BRANCH_COMMIT_CONVENTION.md](BRANCH_COMMIT_CONVENTION.md)
