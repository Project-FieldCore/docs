# Registro e Análise de Riscos

Registro vivo de riscos do FieldOps. GP revisa semanalmente, atualiza respostas e comunica riscos altos ao sponsor.

Escala: probabilidade (P) e impacto (I) de 1 a 5; exposição = P × I. Prioridade: alta (15–25), média (6–14), baixa (1–5).

| ID | Risco | P | I | Exposição | Prioridade | Dono | Resposta preventiva | Contingência/gatilho |
|---|---|---:|---:|---:|---|---|---|---|
| R-01 | Atraso no caminho crítico e perda da margem de 1 dia útil | 4 | 5 | 20 | Alta | GP | Acompanhar semanalmente; proteger fases 3, 4, 7–10 | Replanejar escopo P1/P2 ao primeiro atraso crítico |
| R-02 | Divergência do contrato API entre aplicações | 3 | 5 | 15 | Alta | ARQ | OpenAPI versionado, revisão e testes de contrato | Congelar versão e corrigir adaptadores/mocks |
| R-03 | Perda ou duplicidade na sincronização offline | 3 | 5 | 15 | Alta | Dev Mobile | Outbox, idempotência e testes de reenvio | Bloquear publicação, recuperar fila e investigar logs |
| R-04 | Mudança de escopo sem aprovação | 3 | 4 | 12 | Média | PO/GP | Backlog priorizado e aceite do sponsor | Registrar mudança e revisar prazo/custo |
| R-05 | Indisponibilidade de integrante-chave | 3 | 4 | 12 | Média | GP | Documentação, pares e divisão por componente | Redistribuir PBIs e reduzir escopo não essencial |
| R-06 | Ambiente/cloud indisponível | 2 | 4 | 8 | Média | DevOps | Backup de configurações e execução local | Usar ambiente local e reagendar homologação |
| R-07 | Dados/evidências inadequados para homologação | 3 | 3 | 9 | Média | QA | Massa de testes revisada e anonimizada | Criar massa complementar antes do reteste |
| R-08 | Falha de segurança ou exposição de segredo | 2 | 5 | 10 | Média | ARQ/DevOps | Variáveis de ambiente, revisão de PR e CI | Revogar segredo, corrigir e registrar incidente |

## Fluxo de tratamento

1. Identificar e registrar risco/incidente.
2. GP atribui dono e confirma avaliação.
3. Dono executa prevenção e atualiza a evidência.
4. Risco alto ou gatilho acionado é escalado ao sponsor no mesmo dia útil.
