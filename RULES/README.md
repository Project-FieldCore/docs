# Regras e convenções — FieldCore

Regras de trabalho do time (e de qualquer assistente de IA): como abrir issues, branches, commits e PRs, o que a CI valida, como as sprints são planejadas e como atualizar clones após o rename dos repositórios. Entrada para IAs: [`../AGENTS.md`](../AGENTS.md).

A especificação do produto, exportada do Notion, fica em [`../NOTION/`](../NOTION/README.md).

## Conteúdo desta pasta

| Regra | Arquivo | O que define | Quando atualizar |
|---|---|---|---|
| Índice de convenções | [CONVENTIONS.md](CONVENTIONS.md) | Mapa de todas as convenções (humano + IA) | Quando criar ou renomear um artefato de governança |
| Branches, commits, issues e PRs | [BRANCH_COMMIT_CONVENTION.md](BRANCH_COMMIT_CONVENTION.md) | Hierarquia PBI → filho → tarefa e título de PR `[PBI-XXXX]` | Quando a convenção mudar (renomear issues abertas na weekly seguinte) |
| Integração contínua | [CI_CONVENTION.md](CI_CONVENTION.md) | O que roda na CI de `api-java`, `web-react` e `mobile-react`, branches e como repetir localmente | Quando mudar o baseline de qualidade (lint, tipos, build, testes) |
| Planejamento de sprints | [SPRINT_PLANNING.md](SPRINT_PLANNING.md) | PBIs do Notion (doc. 15) no GitHub, estimativas, dependências, cadência weekly/daily e ordem de corte | A cada refinamento e weekly |
| Rename de repositórios | [REPO_RENAME_GUIDE.md](REPO_RENAME_GUIDE.md) | Como atualizar o `origin` e a pasta local após o rename na org | Após qualquer rename; cada pessoa com clone antigo |

Regras relacionadas fora desta pasta:

- Templates de issue e PR: [`../.github/ISSUE_TEMPLATE/`](../.github/ISSUE_TEMPLATE/) · [`../.github/pull_request_template.md`](../.github/pull_request_template.md)
- Como contribuir na documentação: [`../CONTRIBUTING.md`](../CONTRIBUTING.md)
- Decisões de arquitetura e de processo (ADRs): [`../DECISIONS/`](../DECISIONS/README.md)
- Glossário de domínio: [`../GLOSSARIO.md`](../GLOSSARIO.md)

## Convenções gerais

- Datas sempre em `dd/mm/aaaa` e prazos em dias úteis, como no cronograma.
- Nomes conforme o [`../README.md`](../README.md) e o [`../GLOSSARIO.md`](../GLOSSARIO.md): produto **FieldOps**, organização e projeto de gestão **FieldCore**.
- Mudou escopo, prazo, marco ou uma regra desta pasta? Atualize o artefato correspondente **e** registre a decisão em [`../DECISIONS/`](../DECISIONS/README.md).
- Ao criar ou renomear uma regra, atualize esta tabela, o [CONVENTIONS.md](CONVENTIONS.md) e a tabela da §3 do [`../AGENTS.md`](../AGENTS.md) no mesmo PR.
