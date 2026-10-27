# Registro de Decisões (ADR)

Decisões relevantes de arquitetura, stack e escopo — registradas **quando são tomadas**, para que ninguém precise reconstruir o "porquê" meses depois a partir de commits e conversas.

## Índice

| ADR | Decisão | Status |
|---|---|---|
| 0001 | [Reset do GitHub (boards/issues/milestones) e backlog canônico por PBI do Notion](0001-reset-github-notion-pbi.md) | aceita |
| 0002 | [Interface web em Next.js (em vez de Angular)](0002-web-nextjs-instead-of-angular.md) | aceita |

## Decisões pendentes de registro

1. **Nome canônico: FieldOps × FieldCore** — adotado provisoriamente no [README raiz](../README.md): produto = FieldOps, organização = FieldCore; repos com nomes curtos em inglês.
2. ~~**Frontend web: Angular × Next.js**~~ — **resolvido** na ADR 0002 (Next.js oficial para o MVP); falta reexport/atualização das páginas Notion 11/14 e do TAP.
3. ~~**Repositório `fieldcore_cloud`**~~ — **resolvido:** repositório removido; nomes padronizados em `api-java` / `web-react` / `mobile-react` / `docs` (ver [REPO_RENAME_GUIDE.md](../PROJECT_MANAGEMENT/REPO_RENAME_GUIDE.md)).

## Como registrar uma decisão

Copie o template abaixo para `NNNN-titulo-curto.md` (numeração sequencial) e adicione a linha no índice acima.

```markdown
# ADR NNNN — <título da decisão>

- **Status:** proposta | aceita | substituída pela ADR XXXX
- **Data:** aaaa-mm-dd
- **Decisores:** <quem decidiu>

## Contexto
<o problema, as restrições e as alternativas consideradas>

## Decisão
<o que foi decidido, em uma ou duas frases>

## Consequências
<o que fica mais fácil, o que fica mais difícil, o que precisa mudar em outros documentos/repos>
```

Decisão mudou? Não edite a ADR antiga: crie uma nova, marque a antiga como *substituída* e linke as duas.
