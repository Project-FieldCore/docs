# Registro de Decisões (ADR)

Decisões relevantes de arquitetura, stack e escopo — registradas **quando são tomadas**, para que ninguém precise reconstruir o "porquê" meses depois a partir de commits e conversas.

## Índice

| ADR | Decisão | Status |
|---|---|---|
| 0001 | [Reset do GitHub (boards/issues/milestones) e backlog canônico por PBI do Notion](0001-reset-github-notion-pbi.md) | aceita |

## Decisões pendentes de registro

Estas divergências já existem entre documentos e código e devem virar as primeiras ADRs:

1. **Frontend web: Angular (especificação) × Next.js (repositório atual)** — qual fica, e a especificação ([11](../NOTION/pages/11%20-%20Arquitetura%202fa3130b4ab7820094b201c65aae2822.md)/[14](../NOTION/pages/14%20-%20Interface%20Administrativa%20Web%201663130b4ab782babf8781b030596ced.md)) precisa ser atualizada.
2. **Nome canônico: FieldOps × FieldCore** — adotado provisoriamente no [README raiz](../README.md): produto = FieldOps, organização/repos = FieldCore.
3. **Repositório `fieldcore_cloud`** — citado no [Cronograma](../PROJECT_MANAGEMENT/CRONOGRAMA.md), ainda inexistente: criar ou remover da EAP/cronograma.

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
