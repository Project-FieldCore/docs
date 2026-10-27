# Glossário — FieldOps

Termos do domínio usados na especificação ([`NOTION/`](NOTION/README.md)), no código e nas reuniões. Ao escrever um documento novo, use estes termos com estes significados.

| Termo | Significado |
|---|---|
| **Inspeção** | Atividade de campo atribuída a um técnico, gerada a partir de um modelo, com ciclo de vida próprio: agendada → em execução → concluída → sincronizada → em revisão → aprovada/reprovada. |
| **Modelo de inspeção** | Gabarito reutilizável de uma inspeção: seções e itens de checklist configurados pelo admin/supervisor. É **versionado** — ao publicar, gera uma versão imutável. |
| **Versão do modelo** | Cópia imutável e publicada de um modelo. Inspeções já criadas continuam ligadas à versão original, mesmo que o modelo evolua. |
| **Snapshot do checklist** | Cópia das perguntas do modelo no momento da criação/agendamento da inspeção. Garante que a execução em campo não muda se o modelo for editado depois. |
| **Ficha de inspeção** | Registro completo de uma inspeção executada: respostas, evidências, localização e não conformidades. Exemplo em [Anexo C](NOTION/pages/21%20-%20Anexo%20C%20-%20Exemplo%20de%20Ficha%20de%20Inspe%C3%A7%C3%A3o%20c093130b4ab7825695a8015d140a8375.md). |
| **Não conformidade (NC)** | Desvio registrado durante a execução (item reprovado, problema no equipamento etc.), acompanhado pela supervisão até a resolução. |
| **Evidência** | Foto (e metadados como localização/data) capturada pelo técnico para comprovar um item do checklist. |
| **Cliente / Local / Equipamento** | Hierarquia de cadastros: um cliente possui locais; cada local possui equipamentos (identificáveis por QR Code) que são inspecionados. |
| **Técnico / Supervisor / Administrador** | Perfis de usuário: técnico executa em campo (mobile); supervisor agenda, atribui e revisa (web); administrador gerencia cadastros e modelos (web). Personas: Carlos, Marina e Ana — ver [04 - Personas](NOTION/pages/04%20-%20Personas%204353130b4ab78359aad101e637a5e19a.md). |
| **Operação offline** | Capacidade do app mobile de executar inspeções sem internet, salvando tudo localmente (SQLite) até sincronizar. |
| **Sincronização (sync)** | Envio/recebimento de dados entre app e API ao recuperar conexão: *push* das inspeções concluídas e *pull* de novas atribuições. |
| **Outbox** | Fila local de operações pendentes de envio no app. Preserva os dados mesmo se o app for fechado antes de sincronizar. |
| **Idempotência** | Propriedade de uma operação que pode ser repetida (ex.: reenvio após falha de rede) sem duplicar dados no servidor. Requisito central da sincronização. |
| **Revisão** | Etapa em que o supervisor aprova ou reprova uma inspeção sincronizada, com base em respostas e evidências. Reprovação pode gerar correção pelo técnico. |
| **MVP** | Escopo mínimo do produto para a primeira entrega — definido no [Backlog](NOTION/pages/15%20-%20Backlog%20do%20Produto%20add3130b4ab783848042818065d5e111.md) e protegido pelo [TAP](PROJECT_MANAGEMENT/TAP.md) (mudanças só com o sponsor). |
| **Definition of Done (DoD)** | Critérios que definem quando uma entrega está pronta — ver [18 - DoD](NOTION/pages/18%20-%20Defini%C3%A7%C3%A3o%20de%20Pronto%20-%20Definition%20of%20Done%2027d3130b4ab7839c917f816f80bc8201.md). |
| **EAP** | Estrutura Analítica do Projeto: decomposição do escopo em pacotes de trabalho; base do cronograma. Ver [`PROJECT_MANAGEMENT/EAP.jpeg`](PROJECT_MANAGEMENT/EAP.jpeg). |
| **TAP** | Termo de Abertura do Projeto: documento que autoriza formalmente o projeto. Ver [`PROJECT_MANAGEMENT/TAP.md`](PROJECT_MANAGEMENT/TAP.md). |
| **Marco (milestone)** | Ponto de controle de duração zero no cronograma (ex.: 7.5 — Sistema integrado). Lista completa no [Cronograma](PROJECT_MANAGEMENT/CRONOGRAMA.md#4-marcos-do-projeto-resumo). |
| **Caminho crítico** | Sequência de atividades que determina a data final do projeto; atrasos nele atrasam a entrega. No FieldOps: Infra → Backend → Integração → Testes → Homologação → Implantação. |

> Faltou um termo ou a definição diverge de uma RN? Corrija a fonte (Notion ou RN correspondente) e ajuste aqui — o glossário reflete a especificação, não a substitui.
