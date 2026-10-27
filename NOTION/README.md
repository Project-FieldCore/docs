# Especificação do Produto — FieldOps (export do Notion)

Especificação completa do produto exportada do Notion: visão, requisitos, arquitetura, backlog e critérios de qualidade.
Ponto de entrada do repositório: [`../README.md`](../README.md) · Gestão do projeto: [`../PROJECT_MANAGEMENT/`](../PROJECT_MANAGEMENT/README.md)

📺 **Vídeo do projeto:** https://youtu.be/4UAVJdNgx-s

> ⚠️ **Antes de editar:** estes arquivos são um *snapshot* exportado do Notion (repare o hash no nome de cada arquivo — é o ID da página no Notion).
> - **Não renomeie** os arquivos em `pages/`: os links deste índice e de outros documentos quebram, e a próxima exportação recria os nomes com hash.
> - Correções de conteúdo devem ser feitas **na fonte (Notion)** e reexportadas; editar só aqui cria uma divergência que será sobrescrita.
> - Se uma página passar a ser mantida definitivamente neste repositório, remova-a da exportação, renomeie para um nome limpo e registre a decisão em [`../DECISIONS/`](../DECISIONS/README.md).

## Produto e requisitos

| # | Página | Conteúdo |
|---|---|---|
| 01 | [Visão Geral](pages/01%20-%20Vis%C3%A3o%20Geral%2020e3130b4ab782b393d481b43725c522.md) | Nome do produto, resumo executivo, visão e componentes da solução |
| 02 | [Objetivos](pages/02%20-%20Objetivos%207283130b4ab7835fa16b8189b75a172c.md) | Objetivos do produto e do projeto |
| 03 | [Problema](pages/03%20-%20Problema%20b913130b4ab7835a9a29012200ee4700.md) | Problema que o FieldOps resolve e contexto atual |
| 04 | [Personas](pages/04%20-%20Personas%204353130b4ab78359aad101e637a5e19a.md) | Ana (admin), Marina (supervisora) e Carlos (técnico) |
| 05 | [Perfis de Usuário](pages/05%20-%20Perfis%20de%20Usu%C3%A1rio%209d73130b4ab782bc90ee01bb9dffe5f6.md) | Perfis de acesso e permissões |
| 06 | [Casos de Uso](pages/06%20-%20Casos%20de%20Uso%20ebb3130b4ab78391961a01aa3ae9c022.md) | Casos de uso do sistema |
| 07 | [Fluxo Geral](pages/07%20-%20Fluxo%20Geral%209ea3130b4ab782e88b55016ed5e2fa12.md) | Fluxo ponta a ponta: planejar → executar → sincronizar → revisar |
| 08 | [Funcionalidades](pages/08%20-%20Funcionalidades%2039d3130b4ab783d49fa401ca1cd4abd3.md) | Funcionalidades por componente |
| 09 | [Regras de Negócio](pages/09%20-%20Regras%20de%20Neg%C3%B3cio%205323130b4ab7822ca2a1819b0b118cfa.md) | Regras de negócio (RNs) que a API deve garantir |

## Arquitetura e dados

| # | Página | Conteúdo |
|---|---|---|
| 10 | [Modelo de Dados](pages/10%20-%20Modelo%20de%20Dados%20eb43130b4ab7824f85b881c97289b28f.md) | Entidades, ciclo de vida da inspeção, PostgreSQL (central) × SQLite (local) |
| 11 | [Arquitetura](pages/11%20-%20Arquitetura%202fa3130b4ab7820094b201c65aae2822.md) | Visão arquitetural, princípios e contextos funcionais |
| 12 | [API REST](pages/12%20-%20API%20REST%20a003130b4ab78345a637819a01fe1fc4.md) | Contrato da API entre mobile, web e backend |

## Aplicações

| # | Página | Conteúdo |
|---|---|---|
| 13 | [Aplicativo Mobile](pages/13%20-%20Aplicativo%20Mobile%20ac83130b4ab783f9a98781d7b86ce1d7.md) | App do técnico: checklist, QR Code, evidências, offline e sincronização |
| 14 | [Interface Administrativa Web](pages/14%20-%20Interface%20Administrativa%20Web%201663130b4ab782babf8781b030596ced.md) | Painel do admin/supervisor: cadastros, modelos, agenda e revisão |

## Planejamento e qualidade

| # | Página | Conteúdo |
|---|---|---|
| 15 | [Backlog do Produto](pages/15%20-%20Backlog%20do%20Produto%20add3130b4ab783848042818065d5e111.md) | Backlog e escopo do MVP |
| 16 | [Roadmap](pages/16%20-%20Roadmap%2030f3130b4ab783af82b781172c6cb245.md) | 16 semanas em 8 sprints de 2 semanas |
| 17 | [Critérios de Aceitação](pages/17%20-%20Crit%C3%A9rios%20de%20Aceita%C3%A7%C3%A3o%208a43130b4ab782038a7f81a1eb087644.md) | Critérios de aceitação por entrega |
| 18 | [Definição de Pronto (DoD)](pages/18%20-%20Defini%C3%A7%C3%A3o%20de%20Pronto%20-%20Definition%20of%20Done%2027d3130b4ab7839c917f816f80bc8201.md) | Quando uma entrega é considerada pronta |
| 19 | [Critérios de Avaliação](pages/19%20-%20Crit%C3%A9rios%20de%20Avalia%C3%A7%C3%A3o%208983130b4ab7839089fc815b3b0f3ff9.md) | Rubricas de avaliação do produto e das disciplinas |

## Anexos

| Anexo | Página | Conteúdo |
|---|---|---|
| A | [Checklist executivo do projeto](pages/20%20-%20Anexo%20A%20-%20Checklist%20executivo%20do%20projeto%207123130b4ab7823ea9ae0116836d28a2.md) | Checklist executivo de acompanhamento |
| B | [Decisões de escopo consolidadas](pages/20%20-%20Anexo%20B%20-%20Decis%C3%B5es%20de%20escopo%20consolidadas%2070f3130b4ab7822898ce810f4a289296.md) | Decisões de escopo já fechadas |
| C | [Exemplo de Ficha de Inspeção](pages/21%20-%20Anexo%20C%20-%20Exemplo%20de%20Ficha%20de%20Inspe%C3%A7%C3%A3o%20c093130b4ab7825695a8015d140a8375.md) | Exemplo preenchido de ficha de inspeção |
| D | [Diagrama de Classe](pages/22%20Anexo%20D%20-%20Diagrama%20de%20Classe%203c63130b4ab782fe962c018b0adf27b3.md) | Diagrama de classes do domínio (imagem em `pages/22 Anexo D - Diagrama de Classe/`) |
