# ADR 0002 — Interface web em Next.js (em vez de Angular)

- **Status:** aceita
- **Data:** 2026-10-26
- **Decisores:** time FieldOps (ratificação Orchestrator / PBI-0003)
- **Relacionado:** [PBI-0003](https://github.com/Project-FieldCore/web-react/issues/140)

## Contexto

A especificação no Notion (docs 11 — Arquitetura e 14 — Interface Administrativa Web) e o TAP citam **Angular + TypeScript** para o painel administrativo. O repositório `web-react` foi iniciado e evoluiu em **Next.js (App Router) + TypeScript + Tailwind**, com layout, rotas, estados loading/vazio/erro e integração parcial com a API.

Manter Angular na especificação e Next.js no código gera divergência de avaliação, onboarding e critérios de aceite. Uma das duas linhas precisa ser a fonte da verdade para o MVP.

## Decisão

Adotar **Next.js** como stack oficial do painel web (`web-react`) para o MVP FieldOps.

- A especificação Notion (páginas 11/14) e o TAP devem ser atualizados em follow-up para refletir Next.js (ou nota explícita de desvio aceito até reexport).
- Novas telas e PRs web seguem a estrutura já existente em `app/` + `src/components/`.
- Não há plano de reescrever o painel em Angular nesta fase do projeto.

## Consequências

- **Prós:** alinha documentação de decisão com o código já entregue; evita retrabalho de migração Angular; aproveita App Router, estados padronizados (`States.tsx`) e fluxo de auth já mergeados em `develop`.
- **Contras:** critérios de avaliação acadêmicos que citam Angular (ex.: doc. 19) precisam de nota de equivalência Next.js; export Notion fica temporariamente defasado até reexport.
- **Não muda:** nome do produto (FieldOps) nem da org/repos (FieldCore).
