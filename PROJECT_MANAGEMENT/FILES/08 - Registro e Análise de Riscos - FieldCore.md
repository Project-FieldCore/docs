# Registro e Análise de Riscos

Registro vivo de riscos do FieldCore. O GP revisa semanalmente, atualiza respostas e comunica riscos altos ao sponsor.

Escala: probabilidade (P) e impacto (I) de 1 a 5; exposição = P × I. Prioridade: alta (15–25), média (6–14), baixa (1–5). Estratégias para ameaças: **evitar** (eliminar a causa), **mitigar** (reduzir probabilidade ou impacto), **transferir** (passar parte do impacto a terceiros) e **aceitar** (acompanhar sem ação preventiva significativa).

## Análise qualitativa e respostas

| ID | Risco | P | I | Exposição | Prioridade | Estratégia | Dono | Resposta preventiva | Contingência/gatilho |
|---|---|---:|---:|---:|---|---|---|---|---|
| R-01 | Atraso no caminho crítico e perda da margem de 1 dia útil | 4 | 5 | 20 | Alta | Mitigar | GP | Acompanhar semanalmente; proteger fases 3, 4, 7–10 | Replanejar escopo P1/P2 ao primeiro atraso crítico |
| R-02 | Divergência do contrato API entre aplicações | 3 | 5 | 15 | Alta | Mitigar | ARQ | OpenAPI versionado, revisão e testes de contrato | Congelar versão e corrigir adaptadores/mocks |
| R-03 | Perda ou duplicidade na sincronização offline | 3 | 5 | 15 | Alta | Mitigar | Dev Mobile | Outbox, idempotência e testes de reenvio | Bloquear publicação, recuperar fila e investigar logs |
| R-04 | Mudança de escopo sem aprovação | 3 | 4 | 12 | Média | Evitar | PO/GP | Backlog priorizado e aceite do sponsor | Registrar mudança e revisar prazo/custo |
| R-05 | Indisponibilidade de integrante-chave | 3 | 4 | 12 | Média | Mitigar | GP | Documentação, pares e divisão por componente | Redistribuir PBIs e reduzir escopo não essencial |
| R-06 | Ambiente/cloud indisponível | 2 | 4 | 8 | Média | Transferir | DevOps | Ambiente gerenciado de nuvem, backup de configurações e execução local | Usar ambiente local e reagendar homologação |
| R-07 | Dados/evidências inadequados para homologação | 3 | 3 | 9 | Média | Mitigar | QA | Massa de testes revisada e anonimizada | Criar massa complementar antes do reteste |
| R-08 | Falha de segurança ou exposição de segredo | 2 | 5 | 10 | Média | Evitar | ARQ/DevOps | Variáveis de ambiente, revisão de PR e CI | Revogar segredo, corrigir e registrar incidente |

## Causa, risco e consequência

| ID | Causa | Risco | Consequência |
|---|---|---|---|
| R-01 | Cronograma comprimido, com margem de 1 dia útil e equipe com dedicação parcial | Atividades do caminho crítico terminarem depois do previsto | Demonstração do fluxo offline e da sincronização comprometida no fim do semestre |
| R-02 | Três aplicações desenvolvidas em paralelo por pessoas diferentes | Mobile, web e API implementarem versões diferentes do contrato | Retrabalho na integração e atraso do marco de sistema integrado |
| R-03 | Reenvio automático da outbox após falha de rede | Operações perdidas ou registradas em duplicidade | Dados de inspeção inconsistentes e reprovação no critério AC-RELEASE |
| R-04 | Pedidos de novas funcionalidades durante a execução | Escopo ampliado sem análise de impacto | Esforço desviado de itens P0 e risco ao prazo |
| R-05 | Equipe pequena e conhecimento concentrado por componente | Integrante-chave indisponível em período crítico | Componente parado e atraso das dependências |
| R-06 | Dependência de ambiente de nuvem e de pipeline de deploy | Ambiente ou deploy indisponível | Homologação e go-live sem ambiente publicado |
| R-07 | Falta de dados reais de inspeção | Massa de teste insuficiente ou irreal | Defeitos não detectados antes da homologação |
| R-08 | Credenciais necessárias para API, banco e deploy | Segredo exposto em código, log ou canal | Incidente de segurança e necessidade de revogação |

## Situação em 27/11/2026

| ID | Situação | Evidência |
|---|---|---|
| R-01 | **Ocorreu.** Atraso registrado na auditoria de 19–20/10; contingência acionada com reinício do backlog e replanejamento em 8 sprints. | `SPRINT_PLANNING.md` e ADR 0001; marcos realizados no documento 12 |
| R-02 | Controlado. OpenAPI publicado e mocks do contrato usados pelo web. | PBI-0071; `src/data/openapi` no `web-react` |
| R-03 | Controlado. Outbox, envio em lote e proteção contra duplicidade concluídos. | PBI-0050 a PBI-0055 |
| R-04 | Controlado. Mudanças registradas como ADR; P1 executado só após o fluxo P0. | ADR 0001 e ADR 0002 |
| R-05 | Atenção. Autoria de PRs concentrada (89 de 143 em um integrante). | Pull requests integrados |
| R-06 | **Ocorreu parcialmente.** Deploy da API falhou de 04/11 a 20/11 e estabilizou em 26/11; a publicação do painel foi concluída em 27/11. | GitHub Actions; PBI-0069 |
| R-07 | Controlado. Dados de demonstração reproduzíveis. | PBI-0066 |
| R-08 | Sem incidente registrado. Segredos por variáveis de ambiente. | README da API (`JWT_SECRET`) e DoD |

## Fluxo de tratamento

1. Identificar e registrar risco/incidente com causa, risco e consequência.
2. GP atribui dono e confirma avaliação e estratégia.
3. Dono executa prevenção e atualiza a evidência.
4. Risco alto ou gatilho acionado é escalado ao sponsor no mesmo dia útil.
5. Na revisão semanal, o GP atualiza a situação, identifica riscos novos e registra riscos residuais.
