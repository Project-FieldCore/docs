# Monitoramento, Controle e Encerramento — FieldCore

Define como o projeto é acompanhado, como as mudanças são tratadas e como ele é encerrado, e registra os dados reais de execução coletados nos repositórios da organização [Project-FieldCore](https://github.com/orgs/Project-FieldCore/repositories) e no board do backlog do produto ([projeto 9](https://github.com/orgs/Project-FieldCore/projects/9)) até 27/11/2026.

## 1. Indicadores de acompanhamento

| Indicador | Fonte | Frequência | Responsável | Limite para ação |
|---|---|---|---|---|
| PBIs concluídos / planejados na sprint | Board (campos Status e Sprint) e labels `sprint/N` | Semanal (planejamento de segunda) | GP | Menos de 80% da sprint concluída na revisão |
| Velocidade (pontos concluídos por sprint) | Board (campo Pontos) | Fim da sprint | GP/PO | Queda de mais de 20% em relação à média |
| Conclusão dos itens P0 | Labels `priority/P0` | Semanal | PO | Qualquer P0 aberto no fim da sprint planejada |
| Data real × data da linha de base dos marcos | Cronograma (doc. 03) e fechamento dos épicos | Por marco | GP | Marco do caminho crítico atrasado |
| Taxa de sucesso da validação de PR | GitHub Actions | Contínua, consolidada por semana | DevOps/QA | Abaixo de 90% na semana |
| Taxa de sucesso do deploy de desenvolvimento | GitHub Actions | Contínua, consolidada por semana | DevOps | Três falhas seguidas |
| Defeitos por severidade | Issues e revisão de PR (Notion 18.7) | A cada ciclo de teste | QA | Qualquer defeito crítico ou alto aberto |
| Riscos de prioridade alta | Registro de riscos (doc. 08) | Semanal | GP | Gatilho acionado |
| Custo realizado × orçamento | Orçamento (doc. 04) | Por aquisição | GP | Qualquer gasto não aprovado pelo sponsor |

## 2. Rotina de controle

Cadência definida no planejamento de sprints do repositório `docs` (`RULES/SPRINT_PLANNING.md`):

- **Segunda-feira:** planejamento semanal — revisão do board, dos indicadores e dos riscos altos.
- **Daily assíncrona** nos dias úteis, com **daily síncrona** às terças e quintas.
- **Sexta-feira:** demonstração do incremento.
- **Fim da sprint:** revisão e retrospectiva, com ao menos uma ação de melhoria registrada.

O desvio que ameaça o caminho crítico é comunicado ao GP no mesmo dia útil e, se afetar escopo, prazo ou custo, segue o controle de mudanças.

## 3. Controle integrado de mudanças

1. Quem identifica a necessidade registra a solicitação (issue ou proposta de ADR) com motivo e impacto em escopo, prazo, custo e qualidade.
2. GP e arquiteto analisam o impacto; o PO avalia a prioridade frente ao backlog.
3. Mudanças de escopo do MVP são aprovadas pelo sponsor (TAP, FCS 2); decisões técnicas são registradas como ADR.
4. Aprovada a mudança, atualizam-se backlog, cronograma, riscos e documentação; a equipe é informada no planejamento seguinte.
5. Se houver atraso, o escopo é reduzido na ordem do roadmap (Notion 16.7): dashboard avançado, tipos de resposta, galeria, construtor simplificado, conflitos, notificações/PDF/assinatura — preservando autenticação, planejamento, checklist, foto, offline, sincronização e revisão.

Mudanças registradas na execução:

| Data | Mudança | Registro | Motivo e impacto |
|---|---|---|---|
| 20/10/2026 | Reinício dos boards e das issues no GitHub | ADR 0001 | Auditoria de 19–20/10 encontrou 8 boards, 327 issues e 39 milestones sem referência aos PBIs do backlog e nenhum PBI concluído de ponta a ponta. O backlog foi recriado com 177 issues ligadas aos PBIs do Notion, com backup do histórico anterior. |
| 26/10/2026 | Painel web em Next.js no lugar de Angular | ADR 0002 | Alinha a especificação ao código já existente no `web-react`; sem impacto de escopo. |

## 4. Acompanhamento realizado (dados em 27/11/2026)

### 4.1 Execução por sprint

O backlog recriado em 20/10 foi executado em 8 sprints e acompanhado no board do projeto, com as colunas Backlog, Ready, In progress, In review, Done e Blocked. O backlog tem 177 itens: os 82 PBIs do Notion e as sub-issues por componente (API, web e mobile). A tabela abaixo mostra as datas de fechamento.

| Sprint | Itens | Concluídos | Fechamentos |
|---:|---:|---:|---|
| 1 | 12 | 12 | 22/10 a 29/10 |
| 2 | 19 | 19 | 26/10 a 04/11 |
| 3 | 21 | 21 | 27/10 a 05/11 |
| 4 | 23 | 23 | 05/11 |
| 5 | 17 | 17 | 05/11 |
| 6 | 15 | 15 | 05/11 a 10/11 |
| 7 | 29 | 29 | 08/11 a 11/11 |
| 8 | 40 | 40 | 08/11 a 27/11 |
| **Total** | **177** | **177 (100%)** | |

- Itens P0: 151 de 151 concluídos (100%). O último foi o **PBI-0069 — Versão publicada do painel administrativo**, finalizado em 27/11.
- Itens P1: 26 de 26 concluídos (100%). O último foi o **PBI-0080 — Biometria para reabertura local**, finalizado em 27/11.
- Pull requests integrados: 143 (`api-java` 65, `web-react` 41, `mobile-react` 26, `docs` 11).
- Situação no board no encerramento (27/11): todos os 177 itens finalizados; nenhum item em **Blocked**.

Velocidade registrada no board (campo Pontos):

| Sprint | Itens com pontos | Pontos planejados | Pontos concluídos |
|---:|---:|---:|---:|
| 1 | 12 | 35 | 35 |
| 2 | 19 | 73 | 73 |
| 3 | 21 | 69 | 69 |
| 4 a 8 | 0 | — | — |

Os campos Sprint e Pontos do board foram preenchidos apenas nas sprints 1 a 3 (53 dos 177 itens). A partir da sprint 4, o planejamento ficou registrado só nos labels `sprint/N`, sem estimativa, o que impede medir a velocidade nesse período. A média das sprints 1 a 3 foi de 59 pontos por sprint.

### 4.2 Marcos: linha de base × realizado

As datas realizadas correspondem ao fechamento dos PBIs dos épicos relacionados. Como as issues foram recriadas em 20/10, trabalho feito antes dessa data aparece com fechamento posterior.

| Marco da linha de base | Previsto | Realizado (evidência) | Desvio |
|---|---|---|---|
| 3.9 Infraestrutura base | 18/09 | EP-01 Fundação técnica: 22/10 a 29/10 | ~6 semanas |
| 4.14 / 5.12 / 6.10 Backend, web e mobile funcionais | 09/10 a 13/10 | EP-02 a EP-05: 26/10 a 05/11; EP-06 e EP-07: 05/11 | ~3 semanas |
| 7.5 Sistema integrado | 22/10 | EP-08 Offline e sincronização: 05/11 a 10/11 | ~19 dias |
| 8.6 Testes internos | 04/11 | PBI-0065 Testes dos fluxos críticos: 11/11 | 7 dias |
| 9.5 Homologação | 13/11 | EP-09 Revisão: 10/11 a 11/11; PBI-0072 demonstração ponta a ponta: 23/11 | 10 dias |
| 10.7 Go-live | 19/11 | Build Android (PBI-0068): 22/11; API por container (PBI-0070): 26/11; painel publicado (PBI-0069): 27/11 | ~8 dias |
| 11.5 Encerramento | 27/11 | Este documento e o relatório final: 27/11 | No prazo |

Desempenho de prazo por contagem de itens do backlog em 27/11: valor agregado de 177 de 177 itens planejados, o que dá um índice de desempenho de prazo (SPI = EV / PV) de **1,00** no encerramento. O índice de custo (CPI) não se aplica, pois não houve gasto financeiro registrado.

### 4.3 Qualidade técnica (GitHub Actions)

| Pipeline | Execuções concluídas | Sucesso |
|---|---:|---:|
| Validação de PR e CI (três repositórios) | 205 | 199 (97,1%) |
| Deploy de desenvolvimento — API | 64 | 23 (35,9%) |
| Deploy de desenvolvimento — web | 24 | 23 (95,8%) |

O deploy de desenvolvimento da API falhou em todas as execuções de 04/11 a 20/11, com exceção de uma em 13/11, e estabilizou em 26/11 (21 de 23 com sucesso). Esse foi o principal desvio de qualidade técnica do período e coincide com o atraso do go-live.

### 4.4 Custos

Não há registro de aquisição paga no repositório. Custo realizado: R$ 0,00, dentro do custo obrigatório previsto. Os itens opcionais (R$ 2.570,00) não foram acionados.

## 5. Ações corretivas adotadas

| Desvio | Ação |
|---|---|
| Atraso detectado na auditoria de 19–20/10 | Reinício do backlog com rastreabilidade (ADR 0001), sprints curtas e cadência semanal de controle |
| Divergência entre especificação e código do painel | Registro da decisão em ADR 0002 |
| Falhas contínuas do deploy da API | Ajustes do ambiente de nuvem (como o CORS do profile `postgres`) e execução da API por container (PBI-0070); o pipeline estabilizou em 26/11 |
| Publicação do painel no fim do prazo | Build executável mantida como alternativa aceita pela DoD do MVP até a publicação, concluída em 27/11 (PBI-0069) |

## 6. Encerramento

### 6.1 Verificação da DoD do MVP (Notion 18.6)

| Critério | Situação | Evidência |
|---|---|---|
| Fluxo AC-RELEASE funciona | Atendido | PBI-0065 (suite AC-RELEASE) e PBI-0072 (demonstração ponta a ponta) |
| Build Android instalável | Atendido | PBI-0068 |
| Painel com build executável ou publicada | Atendido | CI do `web-react` e publicação (PBI-0069) |
| API executável por instruções | Atendido | PBI-0067 e PBI-0070 |
| Banco criado por migrações | Atendido | Flyway no `api-java` |
| Usuários e dados de demonstração | Atendido | PBI-0066 |
| Autenticação e autorização | Atendido | EP-02 |
| Checklist, foto, QR Code e localização | Atendido | EP-06 e EP-07 |
| Inspeção offline e sincronização sem duplicidade | Atendido | EP-08 (PBI-0052) |
| Aprovação e reprovação pelo supervisor | Atendido | PBI-0060 e PBI-0061 |
| Documentação principal atualizada | Atendido | READMEs, OpenAPI (PBI-0071) e repositório `docs` |
| Sem defeito crítico conhecido sem contenção | Atendido | Nenhum item aberto no board no encerramento |

### 6.2 Atividades de encerramento

1. Obter o aceite formal do sponsor (assinaturas do TAP e da declaração do escopo).
2. Arquivar a documentação final no repositório e manter os READMEs como guia de execução.
3. Realizar a retrospectiva final e registrar as lições aprendidas abaixo.

### 6.3 Lições aprendidas

| Tema | O que aconteceu | Recomendação |
|---|---|---|
| Rastreabilidade do backlog | Até 20/10 havia 327 issues sem vínculo com os PBIs, o que impediu medir o progresso real. | Criar o backlog no GitHub a partir dos PBIs desde a primeira sprint. |
| Controle do cronograma | O atraso só foi formalizado na auditoria de 19–20/10, depois de marcos da linha de base já vencidos. | Comparar previsto × realizado toda semana desde o início. |
| Atualização do board | Sprints 3 a 5 tiveram fechamentos concentrados em 05/11, sinal de atualização em lote, e os campos Sprint e Pontos ficaram vazios a partir da sprint 4. | Atualizar o status das issues ao fim de cada PR e estimar os pontos no planejamento de cada sprint. |
| Decisões técnicas | A troca de Angular por Next.js só foi registrada em 26/10. | Registrar ADR no momento da decisão. |
| Ambiente e implantação | O deploy da API falhou por cerca de três semanas, e a publicação do painel ficou para o fim. | Montar o pipeline de deploy no início (fase 3) e tratá-lo como entrega do caminho crítico. |
| Concentração de trabalho | 89 dos 143 PRs integrados foram de um único integrante. | Distribuir autoria e revisão para reduzir dependência de pessoa (risco R-05). |
| Nomenclatura | O produto recebeu nomes diferentes na especificação e na organização do GitHub, o que exigiu padronizar os documentos de gestão como FieldCore. | Definir um nome único no TAP e manter em todos os artefatos, repositórios e board. |
