# Análise de Qualidade — Sete Ferramentas

Aplicação das sete ferramentas básicas de qualidade ao FieldCore. Destina-se à equipe, ao QA e ao sponsor; revisar a cada ciclo de testes e homologação.

> Os números das seções 2 a 5 são uma linha de base didática estimada, pois o GitHub não registra defeitos classificados por tipo. Os dados reais disponíveis — execuções de CI e de deploy — estão na seção 8.

## Padrões e critérios de qualidade

- **Planejar a qualidade (8.1):** cada história segue a Definition of Done do Notion (página 18), com itens gerais e específicos de mobile, web e API; a versão final segue o AC-RELEASE (Notion 17.19).
- **Garantir a qualidade (8.2):** revisão obrigatória por pull request, convenção de branches e commits e validação automática (lint, tipos, build e testes) nos três repositórios.
- **Controlar a qualidade (8.3):** taxa de sucesso dos pipelines, defeitos por severidade e evidências anexadas às issues.

| Severidade | Definição | Conduta |
|---|---|---|
| Crítico | Perda de dados, falha de segurança, impossibilidade de executar o fluxo principal ou duplicidade grave | Bloqueia a entrega |
| Alto | Funcionalidade P0 indisponível sem alternativa aceitável | Corrigir antes da release |
| Médio | Problema com alternativa conhecida, sem perda de dados | Aceitar com registro e plano |
| Baixo | Problema visual ou melhoria não essencial | Pode permanecer no backlog |

## 1. Fluxograma

```mermaid
flowchart LR
 A[Planejar inspeção] --> B[Executar checklist offline]
 B --> C{Há conexão?}
 C -- Não --> D[Guardar operação na outbox]
 D --> C
 C -- Sim --> E[Sincronizar API]
 E --> F{Resposta válida e sem duplicidade?}
 F -- Não --> G[Registrar falha e retentar/revisar]
 G --> E
 F -- Sim --> H[Revisão do supervisor]
 H --> I[Relatório e auditoria]
```

Ponto crítico: a transição entre outbox e API deve preservar idempotência e evidências.

## 2. Folha de verificação

A folha abaixo simula 30 ocorrências encontradas em testes de integração; a coluna “real” deve ser preenchida no próximo ciclo.

| Tipo de não conformidade | Ocorrências estimadas | Campo para ocorrência real |
|---|---:|---|
| Falha de sincronização/reenvio | 9 |  |
| Contrato API divergente | 7 |  |
| Validação de formulário | 5 |  |
| Permissão/autorização | 4 |  |
| Evidência fotográfica | 3 |  |
| Desempenho/consulta | 2 |  |
| **Total** | **30** |  |

## 3. Diagrama de Pareto

| Ordem | Categoria | Ocorrências | % acumulado |
|---:|---|---:|---:|
| 1 | Sincronização/reenvio | 9 | 30,0% |
| 2 | Contrato API | 7 | 53,3% |
| 3 | Validação de formulário | 5 | 70,0% |
| 4 | Permissão | 4 | 83,3% |
| 5 | Evidência | 3 | 93,3% |
| 6 | Desempenho | 2 | 100,0% |

Prioridade: atacar sincronização, contrato e validações, que concentram 70% das ocorrências estimadas.

## 4. Diagrama de causa e efeito

**Efeito analisado: inspeção não sincronizada ou inconsistente.**

| Categoria | Causas potenciais |
|---|---|
| Método | Retentativa sem regra definida; conflito sem tratamento |
| Máquina/tecnologia | Rede instável; versão incompatível do app ou API |
| Mão de obra | Uso incorreto do fluxo; revisão insuficiente do contrato |
| Material/dados | Payload incompleto; foto grande; identificador duplicado |
| Medição | Ausência de métricas de fila, falha e tempo de sincronização |
| Ambiente | Área sem conectividade; bateria insuficiente do dispositivo |

## 5. Histograma

Distribuição estimada de 20 tempos de sincronização bem-sucedida (segundos).

| Faixa | Frequência |
|---|---:|
| 0–2 s | 5 |
| 3–5 s | 8 |
| 6–8 s | 4 |
| 9–11 s | 2 |
| 12 s ou mais | 1 |

Critério inicial: investigar amostras acima de 8 s e definir meta após medição real em campo.

## 6. Diagrama de dispersão

Variáveis a registrar: tamanho total das evidências (MB) × tempo de sincronização (s). A hipótese é correlação positiva: arquivos maiores elevam o tempo. Cada teste deve registrar os dois valores; se a tendência se confirmar, aplicar compressão/limite de upload e envio em etapas.

## 7. Gráfico de controle

Indicador: percentual de sincronizações com sucesso por execução diária. Linha central inicial: 95%; limite de alerta inferior: 90%; meta: ≥ 98% após estabilização. Pontos abaixo do limite, sete pontos consecutivos em queda ou qualquer alteração relevante no contrato devem abrir investigação e ação corretiva.

## 8. Dados reais de execução (GitHub Actions)

Execuções concluídas por semana até 27/11/2026, nos repositórios `api-java`, `web-react` e `mobile-react`.

| Semana (início) | Validação de PR/CI | Sucesso | Deploy DEV da API | Sucesso |
|---|---:|---:|---:|---:|
| 26/10 | 46 | 45 (97,8%) | 3 | 1 |
| 02/11 | 84 | 83 (98,8%) | 19 | 0 |
| 09/11 | 42 | 41 (97,6%) | 15 | 1 |
| 16/11 | 9 | 9 (100%) | 4 | 0 |
| 23/11 | 24 | 21 (87,5%) | 23 | 21 |
| **Total** | **205** | **199 (97,1%)** | **64** | **23 (35,9%)** |

Leitura como gráfico de controle: a validação de PR ficou acima do limite de alerta de 90% em quatro das cinco semanas; a semana de 23/11, com 87,5%, coincide com o maior volume de entregas P1 e deve ser investigada. O deploy de desenvolvimento da API ficou fora de controle de 02/11 a 20/11 (1 sucesso em 38 execuções) e voltou ao padrão em 26/11. Pela análise de Pareto, a falha de deploy concentrou 41 das 48 falhas de pipeline do período (85%), o que a torna a principal causa a tratar. O deploy de desenvolvimento do web teve 23 sucessos em 24 execuções.

## Ações e acompanhamento

| Ação | Responsável | Evidência |
|---|---|---|
| Executar testes de reenvio/idempotência | QA e Dev Mobile/Backend | Casos automatizados e relatório |
| Validar OpenAPI antes da integração | ARQ e Devs | Contrato versionado e CI verde |
| Medir falhas e tempo de sincronização | QA | Folha de verificação preenchida |
| Revisar Pareto e limites | GP/QA | Ata semanal e atualização deste documento |
| Estabilizar o pipeline de deploy da API | DevOps | Execuções verdes consecutivas (alcançado em 26/11) |
