# Cronograma do Projeto FieldOps (FieldCore)

> Documento produzido para a atividade da disciplina **Gestão de Projetos** (Aula 04 — Planejamento do Projeto), aplicando os processos de Gerenciamento do Tempo (6.1 a 6.7) ao Projeto FieldOps/FieldCore.

## 1. Contexto

O **FieldOps (FieldCore)** é uma plataforma de gestão de inspeções de campo, composta por quatro repositórios:

- `api-java` — API central (clientes, locais, equipamentos, técnicos, modelos de inspeção, inspeções, não conformidades);
- `web-react` — painel web administrativo/supervisor (Next.js);
- `mobile-react` — aplicativo do técnico de campo (execução de checklists, leitura de QR Code, evidências, offline);
- `docs` — este repositório, com a documentação do projeto.

> Nomes antigos (`fieldcore_*`) e remoção de `fieldcore_cloud`: ver [REPO_RENAME_GUIDE.md](REPO_RENAME_GUIDE.md).

O cronograma abaixo foi elaborado a partir da EAP (Estrutura Analítica do Projeto) do FieldOps, considerando o modelo de domínio já mapeado no código (Cliente, Local, Equipamento, Técnico, Modelo de Inspeção, Inspeção, Não Conformidade) e as referências a documentos de Casos de Uso, Regras de Negócio e Funcionalidades citadas no projeto.

**Prazo final do projeto: 30/11/2026.** Para viabilizar a entrega dentro desse prazo, o cronograma foi deliberadamente comprimido em relação a uma estimativa "confortável" — ver estratégia de compressão no item 2.

## 2. Premissas, regras de contagem e estratégia de compressão do prazo

- **Data de início do projeto:** 24/08/2026 (segunda-feira). **Prazo final:** 30/11/2026.
- **Duração** é contada em **dias úteis** (segunda a sexta); feriados não foram considerados individualmente — vale revisar a agenda real do time (ex.: feriados de novembro) ao adotar este cronograma como linha de base.
- **Responsáveis** estão indicados por **papel/função** (ex.: Dev Backend, QA, PO), já que o repositório de documentação ainda não registra os nomes da equipe. Basta substituir cada papel pelo nome da pessoa correspondente quando o time estiver definido.
- Itens marcados como **Marco** têm duração zero — representam pontos de controle e não trabalho executado.
- **Tipos de dependência** utilizados (conforme slide "Dependências entre atividades"):
  - **FS** (Término → Início): a sucessora só inicia depois que a predecessora termina — a mais comum do cronograma;
  - **SS** (Início → Início): a sucessora inicia junto com a predecessora (trabalho em paralelo);
  - **FF** (Término → Término): as atividades terminam juntas — usada no marco de *Go-live* (10.7), que se encerra junto com a publicação do painel web e do aplicativo mobile;
  - **SF** (Início → Término) não foi utilizada por ser um tipo raro na prática — mantida apenas como referência conceitual.
- **Como o prazo de ~14 semanas (71 dias úteis) foi viabilizado — estratégia de compressão:**
  1. **Trilhas paralelas de desenvolvimento.** Backend (Fase 4), Frontend Web (Fase 5) e Mobile (Fase 6) são conduzidos por equipes/pessoas distintas **ao mesmo tempo**, logo após a Fase 3 (infraestrutura base), em vez de sequencialmente.
  2. **Front-end e mobile evoluem contra dados mockados primeiro** — mesma estratégia já usada hoje no `web-react` (arquivo `mock-data.ts`). Isso permite que as equipes de Web e Mobile avancem em paralelo ao Backend, sem esperar a API real ficar pronta; a integração com a API real do backend só ocorre na **Fase 7 (Integração)**.
  3. **Fases de curta duração no início** (Iniciação e parte da Documentação de Requisitos), já que boa parte do levantamento de casos de uso, regras de negócio e funcionalidades citadas no código já tem uma base de partida.
  4. **Plano de testes elaborado em paralelo** (item 8.1) desde a aprovação dos requisitos, e não apenas ao final do desenvolvimento.
  5. Mesmo com a compressão, o cronograma termina em **27/11/2026**, deixando apenas **1 dia útil de margem** antes do prazo final (30/11/2026). É uma folga mínima: qualquer atraso no caminho crítico (Fase 3 → 4 → 7 → 8 → 9 → 10) deve ser tratado como risco imediato ao prazo, e o ideal é a equipe já tratar **27/11/2026** como a data-limite real, reservando os últimos dias antes de 30/11 como contingência.

## 3. Estrutura Analítica do Projeto (EAP) e Cronograma

O cronograma contém **89 itens** (atividades e marcos), organizados em **11 fases**, com **11 marcos**.

> **Fases 4, 5 e 6 (Backend, Frontend Web e Mobile) rodam em paralelo** — todas iniciam logo após o marco 3.9 (Infraestrutura base disponível) e são conduzidas por pessoas/papéis diferentes ao mesmo tempo.


### Fase 1 - Iniciação e Planejamento

| ID | Atividade | Responsável | Duração (dias úteis) | Predecessoras (tipo) | Início | Término | Marco |
|----|-----------|-------------|:---:|-----------|:---:|:---:|:---:|
| 1.1 | Reunião de kickoff do projeto | GP | 1 | — | 24/08/2026 | 24/08/2026 |  |
| 1.2 | Elaborar termo de abertura (escopo, objetivos, premissas) | GP | 1 | 1.1 (FS) | 25/08/2026 | 25/08/2026 |  |
| 1.3 | Identificar e registrar stakeholders | GP | 1 | 1.1 (SS) | 24/08/2026 | 24/08/2026 |  |
| 1.4 | Definir ferramentas e repositórios do projeto (GitHub, board de tarefas) | GP | 1 | 1.1 (SS) | 24/08/2026 | 24/08/2026 |  |
| 1.5 | Elaborar plano de gerenciamento do cronograma | GP | 1 | 1.2 (FS) | 26/08/2026 | 26/08/2026 |  |
| 1.6 | Definir Estrutura Analítica do Projeto (EAP) | GP | 1 | 1.2 (SS) | 25/08/2026 | 25/08/2026 |  |
| 1.7 | **Plano de projeto aprovado** | GP | 0 | 1.3 (FS); 1.4 (FS); 1.5 (FS); 1.6 (FS) | 27/08/2026 | 27/08/2026 | ✅ |

### Fase 2 - Levantamento e Documentação de Requisitos

| ID | Atividade | Responsável | Duração (dias úteis) | Predecessoras (tipo) | Início | Término | Marco |
|----|-----------|-------------|:---:|-----------|:---:|:---:|:---:|
| 2.1 | Levantar necessidades do negócio com stakeholders | AR | 2 | 1.7 (FS) | 28/08/2026 | 31/08/2026 |  |
| 2.2 | Elaborar visão geral do produto e personas (Técnico, Supervisor, Gestor) | PO | 1 | 2.1 (FS) | 01/09/2026 | 01/09/2026 |  |
| 2.3 | Consolidar casos de uso | AR | 2 | 2.1 (FS) | 01/09/2026 | 02/09/2026 |  |
| 2.4 | Consolidar regras de negócio | AR | 2 | 2.3 (SS) | 01/09/2026 | 02/09/2026 |  |
| 2.5 | Consolidar funcionalidades do sistema | AR | 2 | 2.3 (FS) | 03/09/2026 | 04/09/2026 |  |
| 2.6 | Modelar entidades de domínio (Cliente, Local, Equipamento, Técnico, Modelo, Inspeção) | ARQ | 2 | 2.4 (FS); 2.5 (FS) | 07/09/2026 | 08/09/2026 |  |
| 2.7 | Elaborar wireframes de baixa fidelidade (painel web e app mobile) | UX/UI | 2 | 2.2 (FS); 2.5 (SS) | 03/09/2026 | 04/09/2026 |  |
| 2.8 | Validar requisitos e wireframes com stakeholders | PO | 1 | 2.6 (FS); 2.7 (FS) | 09/09/2026 | 09/09/2026 |  |
| 2.9 | **Documentação de requisitos aprovada** | PO | 0 | 2.8 (FS) | 10/09/2026 | 10/09/2026 | ✅ |

### Fase 3 - Arquitetura e Infraestrutura

| ID | Atividade | Responsável | Duração (dias úteis) | Predecessoras (tipo) | Início | Término | Marco |
|----|-----------|-------------|:---:|-----------|:---:|:---:|:---:|
| 3.1 | Definir arquitetura da solução (backend, cloud, web, mobile) | ARQ | 2 | 2.9 (FS) | 11/09/2026 | 14/09/2026 |  |
| 3.2 | Modelar banco de dados (DER) | ARQ | 2 | 3.1 (FS) | 15/09/2026 | 16/09/2026 |  |
| 3.3 | Definir stack tecnológica e padrões de código | ARQ | 1 | 3.1 (SS) | 11/09/2026 | 11/09/2026 |  |
| 3.4 | Configurar repositórios GitHub (backend, cloud, frontend, mobile, documentação) | DevOps | 1 | 3.1 (SS) | 11/09/2026 | 11/09/2026 |  |
| 3.5 | Provisionar ambiente de nuvem (fieldcore_cloud) | DevOps | 2 | 3.1 (FS) | 15/09/2026 | 16/09/2026 |  |
| 3.6 | Configurar armazenamento de evidências fotográficas | DevOps | 1 | 3.5 (FS) | 17/09/2026 | 17/09/2026 |  |
| 3.7 | Configurar pipeline de CI/CD | DevOps | 2 | 3.5 (SS) | 15/09/2026 | 16/09/2026 |  |
| 3.8 | Configurar ambientes de desenvolvimento e homologação | DevOps | 1 | 3.7 (FS) | 17/09/2026 | 17/09/2026 |  |
| 3.9 | **Infraestrutura base disponível** | ARQ | 0 | 3.2 (FS); 3.4 (FS); 3.6 (FS); 3.8 (FS) | 18/09/2026 | 18/09/2026 | ✅ |

### Fase 4 - Desenvolvimento Backend

| ID | Atividade | Responsável | Duração (dias úteis) | Predecessoras (tipo) | Início | Término | Marco |
|----|-----------|-------------|:---:|-----------|:---:|:---:|:---:|
| 4.1 | Criar schema e migrações do banco de dados | Dev Backend | 2 | 3.9 (FS) | 21/09/2026 | 22/09/2026 |  |
| 4.2 | Implementar autenticação e perfis de acesso (Técnico, Supervisor, Admin) | Dev Backend | 3 | 4.1 (FS) | 23/09/2026 | 25/09/2026 |  |
| 4.3 | Implementar CRUD de Clientes e Locais | Dev Backend | 2 | 4.1 (FS) | 23/09/2026 | 24/09/2026 |  |
| 4.4 | Implementar CRUD de Equipamentos com QR Code | Dev Backend | 2 | 4.3 (SS) | 23/09/2026 | 24/09/2026 |  |
| 4.5 | Implementar CRUD de Técnicos | Dev Backend | 1 | 4.2 (FS) | 28/09/2026 | 28/09/2026 |  |
| 4.6 | Implementar módulo de Modelos de Inspeção (seções, itens, versionamento) | Dev Backend | 4 | 4.1 (FS) | 23/09/2026 | 28/09/2026 |  |
| 4.7 | Implementar módulo de Inspeções (atribuição e execução) | Dev Backend | 4 | 4.4 (FS); 4.5 (FS); 4.6 (FS) | 29/09/2026 | 02/10/2026 |  |
| 4.8 | Implementar registro de não conformidades e evidências | Dev Backend | 3 | 4.7 (FS) | 05/10/2026 | 07/10/2026 |  |
| 4.9 | Implementar fluxo de revisão e aprovação pelo supervisor | Dev Backend | 2 | 4.7 (FS) | 05/10/2026 | 06/10/2026 |  |
| 4.10 | Implementar API de agenda de inspeções | Dev Backend | 2 | 4.7 (FS) | 05/10/2026 | 06/10/2026 |  |
| 4.11 | Implementar notificações do sistema | Dev Backend | 1 | 4.9 (FS) | 07/10/2026 | 07/10/2026 |  |
| 4.12 | Documentar API (OpenAPI/Swagger) | Dev Backend | 1 | 4.8 (FS); 4.10 (FS); 4.11 (FS) | 08/10/2026 | 08/10/2026 |  |
| 4.13 | Escrever testes unitários do backend | QA | 2 | 4.12 (SS) | 08/10/2026 | 09/10/2026 |  |
| 4.14 | **Backend com funcionalidades essenciais concluído** | Dev Backend | 0 | 4.12 (FS); 4.13 (FS) | 12/10/2026 | 12/10/2026 | ✅ |

### Fase 5 - Desenvolvimento Frontend Web

| ID | Atividade | Responsável | Duração (dias úteis) | Predecessoras (tipo) | Início | Término | Marco |
|----|-----------|-------------|:---:|-----------|:---:|:---:|:---:|
| 5.1 | Configurar projeto Next.js, Tailwind e Zustand | Dev Frontend | 1 | 3.9 (FS) | 21/09/2026 | 21/09/2026 |  |
| 5.2 | Implementar layout base e navegação (Sidebar) | Dev Frontend | 1 | 5.1 (FS) | 22/09/2026 | 22/09/2026 |  |
| 5.3 | Implementar tela de Dashboard | Dev Frontend | 2 | 5.2 (FS) | 23/09/2026 | 24/09/2026 |  |
| 5.4 | Implementar listagem e detalhe de Modelos de Inspeção | Dev Frontend | 3 | 5.2 (FS) | 23/09/2026 | 25/09/2026 |  |
| 5.5 | Implementar editor de Modelo de Inspeção (seções e itens) | Dev Frontend | 3 | 5.4 (FS) | 28/09/2026 | 30/09/2026 |  |
| 5.6 | Implementar listagem de Inspeções com filtros | Dev Frontend | 3 | 5.2 (FS) | 23/09/2026 | 25/09/2026 |  |
| 5.7 | Implementar detalhe de Inspeção (respostas e não conformidades) | Dev Frontend | 3 | 5.6 (FS) | 28/09/2026 | 30/09/2026 |  |
| 5.8 | Implementar fluxo de revisão/aprovação no painel | Dev Frontend | 2 | 5.7 (FS) | 01/10/2026 | 02/10/2026 |  |
| 5.9 | Implementar tela de Agenda/Cronograma de inspeções | Dev Frontend | 2 | 5.6 (SS) | 23/09/2026 | 24/09/2026 |  |
| 5.10 | Consolidar painel web com dados mockados (mock-data) | Dev Frontend | 2 | 5.3 (FS); 5.5 (FS); 5.8 (FS); 5.9 (FS) | 05/10/2026 | 06/10/2026 |  |
| 5.11 | Ajustes de responsividade e acessibilidade | Dev Frontend | 2 | 5.10 (FS) | 07/10/2026 | 08/10/2026 |  |
| 5.12 | **Painel web funcional (com dados mockados)** | Dev Frontend | 0 | 5.11 (FS) | 09/10/2026 | 09/10/2026 | ✅ |

### Fase 6 - Desenvolvimento Mobile

| ID | Atividade | Responsável | Duração (dias úteis) | Predecessoras (tipo) | Início | Término | Marco |
|----|-----------|-------------|:---:|-----------|:---:|:---:|:---:|
| 6.1 | Configurar projeto do aplicativo mobile | Dev Mobile | 1 | 3.9 (FS) | 21/09/2026 | 21/09/2026 |  |
| 6.2 | Implementar autenticação do técnico | Dev Mobile | 2 | 6.1 (FS) | 22/09/2026 | 23/09/2026 |  |
| 6.3 | Implementar agenda de inspeções do técnico | Dev Mobile | 2 | 6.2 (FS) | 24/09/2026 | 25/09/2026 |  |
| 6.4 | Implementar leitura de QR Code do equipamento | Dev Mobile | 2 | 6.2 (SS) | 22/09/2026 | 23/09/2026 |  |
| 6.5 | Implementar execução de checklist dinâmico | Dev Mobile | 4 | 6.3 (FS); 6.4 (FS) | 28/09/2026 | 01/10/2026 |  |
| 6.6 | Implementar captura de evidências fotográficas | Dev Mobile | 2 | 6.5 (FS) | 02/10/2026 | 05/10/2026 |  |
| 6.7 | Implementar registro de não conformidades em campo | Dev Mobile | 2 | 6.5 (FS) | 02/10/2026 | 05/10/2026 |  |
| 6.8 | Implementar funcionamento offline e sincronização | Dev Mobile | 3 | 6.6 (FS); 6.7 (FS) | 06/10/2026 | 08/10/2026 |  |
| 6.9 | Consolidar app mobile com API mockada | Dev Mobile | 2 | 6.8 (FS) | 09/10/2026 | 12/10/2026 |  |
| 6.10 | **Aplicativo mobile funcional (com API mockada)** | Dev Mobile | 0 | 6.9 (FS) | 13/10/2026 | 13/10/2026 | ✅ |

### Fase 7 - Integração

| ID | Atividade | Responsável | Duração (dias úteis) | Predecessoras (tipo) | Início | Término | Marco |
|----|-----------|-------------|:---:|-----------|:---:|:---:|:---:|
| 7.1 | Integrar painel web com a API real do backend | Dev Frontend | 3 | 4.14 (FS); 5.12 (FS) | 13/10/2026 | 15/10/2026 |  |
| 7.2 | Integrar app mobile com a API real do backend | Dev Mobile | 3 | 4.14 (FS); 6.10 (SS) | 13/10/2026 | 15/10/2026 |  |
| 7.3 | Testes de integração entre módulos | QA | 2 | 7.1 (FS); 7.2 (FS) | 16/10/2026 | 19/10/2026 |  |
| 7.4 | Ajustes de performance e otimização de consultas | Dev Backend | 2 | 7.3 (FS) | 20/10/2026 | 21/10/2026 |  |
| 7.5 | **Sistema integrado (build candidato a homologação)** | GP | 0 | 7.4 (FS) | 22/10/2026 | 22/10/2026 | ✅ |

### Fase 8 - Testes e Qualidade

| ID | Atividade | Responsável | Duração (dias úteis) | Predecessoras (tipo) | Início | Término | Marco |
|----|-----------|-------------|:---:|-----------|:---:|:---:|:---:|
| 8.1 | Elaborar plano de testes | QA | 2 | 2.9 (FS) | 11/09/2026 | 14/09/2026 |  |
| 8.2 | Executar testes funcionais (baseados nos casos de uso) | QA | 3 | 7.5 (FS); 8.1 (FS) | 23/10/2026 | 27/10/2026 |  |
| 8.3 | Executar testes de regressão | QA | 2 | 8.2 (FS) | 28/10/2026 | 29/10/2026 |  |
| 8.4 | Corrigir bugs identificados | Equipe de Desenvolvimento | 2 | 8.3 (FS) | 30/10/2026 | 02/11/2026 |  |
| 8.5 | Executar reteste de validação | QA | 1 | 8.4 (FS) | 03/11/2026 | 03/11/2026 |  |
| 8.6 | **Sistema aprovado em testes internos** | QA | 0 | 8.5 (FS) | 04/11/2026 | 04/11/2026 | ✅ |

### Fase 9 - Homologação

| ID | Atividade | Responsável | Duração (dias úteis) | Predecessoras (tipo) | Início | Término | Marco |
|----|-----------|-------------|:---:|-----------|:---:|:---:|:---:|
| 9.1 | Preparar ambiente e dados de homologação | DevOps | 1 | 8.6 (FS) | 05/11/2026 | 05/11/2026 |  |
| 9.2 | Treinar usuários-piloto (técnicos e supervisores) | GP | 1 | 9.1 (SS) | 05/11/2026 | 05/11/2026 |  |
| 9.3 | Executar homologação com cliente-piloto | PO | 3 | 9.1 (FS); 9.2 (FS) | 06/11/2026 | 10/11/2026 |  |
| 9.4 | Coletar feedback e implementar ajustes de homologação | PO | 2 | 9.3 (FS) | 11/11/2026 | 12/11/2026 |  |
| 9.5 | **Sistema homologado e aprovado pelo cliente** | PO | 0 | 9.4 (FS) | 13/11/2026 | 13/11/2026 | ✅ |

### Fase 10 - Implantação

| ID | Atividade | Responsável | Duração (dias úteis) | Predecessoras (tipo) | Início | Término | Marco |
|----|-----------|-------------|:---:|-----------|:---:|:---:|:---:|
| 10.1 | Elaborar plano de implantação e rollback | DevOps | 1 | 9.5 (FS) | 16/11/2026 | 16/11/2026 |  |
| 10.2 | Migrar dados iniciais (clientes, locais, equipamentos, técnicos) | Dev Backend | 1 | 10.1 (FS) | 17/11/2026 | 17/11/2026 |  |
| 10.3 | Publicar backend e cloud em produção | DevOps | 1 | 10.2 (FS) | 18/11/2026 | 18/11/2026 |  |
| 10.4 | Publicar painel web em produção | DevOps | 1 | 10.3 (SS) | 18/11/2026 | 18/11/2026 |  |
| 10.5 | Publicar aplicativo mobile nas lojas | Dev Mobile | 2 | 10.3 (SS) | 18/11/2026 | 19/11/2026 |  |
| 10.6 | Monitorar operação inicial (hypercare) | DevOps | 2 | 10.4 (FS); 10.5 (FS) | 20/11/2026 | 23/11/2026 |  |
| 10.7 | **Go-live do Projeto FieldOps** | GP | 0 | 10.4 (FF); 10.5 (FF) | 19/11/2026 | 19/11/2026 | ✅ |

### Fase 11 - Encerramento

| ID | Atividade | Responsável | Duração (dias úteis) | Predecessoras (tipo) | Início | Término | Marco |
|----|-----------|-------------|:---:|-----------|:---:|:---:|:---:|
| 11.1 | Elaborar relatório de lições aprendidas | GP | 1 | 10.6 (FS) | 24/11/2026 | 24/11/2026 |  |
| 11.2 | Atualizar documentação final do projeto | AR | 1 | 10.6 (SS) | 20/11/2026 | 20/11/2026 |  |
| 11.3 | Realizar reunião de encerramento com stakeholders | GP | 1 | 11.1 (FS); 11.2 (FS) | 25/11/2026 | 25/11/2026 |  |
| 11.4 | Encerrar recursos e formalizar entrega | GP | 1 | 11.3 (FS) | 26/11/2026 | 26/11/2026 |  |
| 11.5 | **Encerramento formal do Projeto FieldOps** | GP | 0 | 11.4 (FS) | 27/11/2026 | 27/11/2026 | ✅ |

## 4. Marcos do projeto (resumo)

| Marco | Data | Descrição |
|---|:---:|---|
| 1.7 | 27/08/2026 | Plano de projeto aprovado |
| 2.9 | 10/09/2026 | Documentação de requisitos aprovada |
| 3.9 | 18/09/2026 | Infraestrutura base disponível |
| 4.14 | 12/10/2026 | Backend com funcionalidades essenciais concluído |
| 5.12 | 09/10/2026 | Painel web funcional (com dados mockados) |
| 6.10 | 13/10/2026 | Aplicativo mobile funcional (com API mockada) |
| 7.5 | 22/10/2026 | Sistema integrado (build candidato a homologação) |
| 8.6 | 04/11/2026 | Sistema aprovado em testes internos |
| 9.5 | 13/11/2026 | Sistema homologado e aprovado pelo cliente |
| 10.7 | 19/11/2026 | Go-live do Projeto FieldOps |
| 11.5 | 27/11/2026 | Encerramento formal do Projeto FieldOps |

**Data prevista de encerramento do projeto:** 27/11/2026 — dentro do prazo final de 30/11/2026 (margem de 1 dia útil).

## 5. Observações finais

- Este cronograma cobre o ciclo completo do PMBOK aplicado ao Gerenciamento do Tempo (6.1 a 6.7): planejamento do gerenciamento do cronograma, definição e sequenciamento das atividades, estimativa de recursos e duração, desenvolvimento e controle do cronograma.
- As durações refletem um cenário **comprimido e otimista**, compatível com o prazo de 30/11/2026: pressupõem uma equipe dedicada em tempo integral a cada trilha (Backend, Frontend, Mobile, QA/DevOps) trabalhando simultaneamente, sem grandes bloqueios externos. Qualquer imprevisto relevante (indisponibilidade de pessoas, mudança de escopo, feriados não planejados) tende a consumir a margem de segurança de poucos dias úteis indicada acima.
- O controle do cronograma (processo 6.7) deve ser feito continuamente, atualizando datas reais de início/término e registrando desvios e mudanças na linha de base — se algum atraso surgir, priorize proteger o caminho crítico: Fase 3 → Fase 4 (Backend) → Fase 7 (Integração) → Fase 8 (Testes) → Fase 9 (Homologação) → Fase 10 (Implantação).

