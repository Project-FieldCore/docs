# Declaração do Escopo do Projeto — FieldCore

Elaborada conforme o modelo *Anexo 2 — Declaração do escopo* (`Templates/Anexo 2 - Declaracao do escopo.doc`), a partir do Termo de Abertura (documento 01) e da especificação do produto no repositório `docs` (Notion, páginas 02, 08, 15–18 e Anexo B).

## Controle de versões

| Versão | Data | Autor | Notas da revisão |
|---|---|---|---|
| 1.0 | 27/11/2026 | Equipe FieldCore | Versão inicial, derivada do TAP de 14/08/2026 e das decisões de escopo consolidadas (Anexo B). |

## Objetivo do projeto

Desenvolver e disponibilizar a plataforma FieldCore, que permite configurar, planejar, executar, sincronizar, revisar e auditar inspeções técnicas em campo de forma padronizada, segura e rastreável, inclusive em locais sem conectividade. O resultado esperado é um MVP demonstrável de ponta a ponta — da criação do modelo de inspeção à aprovação pelo supervisor — dentro das 16 semanas efetivas das disciplinas integradoras.

## Justificativa do projeto

As inspeções de campo dependem hoje de formulários impressos, planilhas isoladas e fotografias sem identificação. Isso gera retrabalho, perda e preenchimento incompleto de informações, demora entre a execução e a disponibilidade do resultado e baixa rastreabilidade das não conformidades.

Foram consideradas três alternativas: manter o processo manual, adotar um formulário digital genérico (sem operação offline nem vínculo com equipamentos) ou desenvolver uma plataforma própria. A escolha recaiu sobre a plataforma própria com três aplicações integradas (app mobile, painel web e API REST), porque é a única que atende simultaneamente à operação offline em campo, ao vínculo de cada resposta com evidência, equipamento, usuário e localização, e ao objetivo acadêmico de integrar as disciplinas de Mobile, Web e Backend.

## Requisitos do produto

Detalhamento do que o produto acabado deve atender, com base nos objetivos do TAP e nas funcionalidades P0 (Notion, página 08) e nos indicadores de sucesso do MVP (página 02, item 2.7).

| Requisito | Descrição |
|---|---|
| RP-01 Autenticação e perfis | Login por e-mail e senha com token renovável; perfis ADMIN, SUPERVISOR e TÉCNICO; autorização validada na API; sessão do mobile em armazenamento seguro. |
| RP-02 Cadastros administrativos | Usuários, clientes, locais e equipamentos (com QR Code único) cadastrados pelo painel web, com pesquisa, paginação, filtros e inativação lógica, sem acesso direto ao banco. |
| RP-03 Modelos de inspeção versionados | Criação de modelo em rascunho com seções, itens ordenados, tipo de resposta, obrigatoriedade e exigência de evidência; publicação de versão sem alterar versões já utilizadas. |
| RP-04 Planejamento | Inspeção criada a partir de modelo publicado, com cliente, local, equipamento, técnico, prioridade e data prevista; cancelamento exige justificativa. |
| RP-05 Execução em campo | App Android com lista de inspeções atribuídas, checklist dinâmico, validação de itens obrigatórios, fotografia por item, leitura de QR Code e localização no início e na conclusão (quando autorizada). |
| RP-06 Operação offline | Após o download, a inspeção pode ser executada e concluída sem rede; respostas e referências de evidências persistem em SQLite, inclusive após fechar o app. |
| RP-07 Sincronização idempotente | Outbox com envio em lote e repetição controlada; o reenvio da mesma operação não cria registros duplicados; conflitos de versão são detectados sem perda de dados. |
| RP-08 Revisão e auditoria | Supervisor visualiza respostas, fotos, localização e não conformidades; aprova ou reprova (motivo obrigatório); inspeção aprovada fica protegida; mudanças de estado ficam registradas. |
| RP-09 API documentada | Contrato REST versionado em OpenAPI, erros padronizados (`ErrorResponse`), validação de entrada e migrações de banco. |
| RP-10 Estados de interface | Telas tratam carregamento, vazio, erro e sucesso; o mobile apresenta o estado de sincronização e a última sincronização. |

## Requisitos do projeto

| Requisito | Descrição |
|---|---|
| RJ-01 Prazo | O MVP deve ser concluído dentro das 16 semanas efetivas de aula; as semanas institucionais restantes não são reserva de desenvolvimento (Anexo B, itens 15 e 16). |
| RJ-02 Contrato antes da integração | O contrato da API deve estar definido e documentado antes da integração, permitindo que web e mobile avancem com mocks. |
| RJ-03 Rastreabilidade do backlog | Toda issue de implementação deve referenciar um PBI do backlog (Notion, página 15) e seguir a convenção de branches, commits e PRs do repositório `docs`. |
| RJ-04 Definição de pronto | Cada história só é concluída quando atende à DoD (Notion, página 18): revisão por PR, lint e tipos verdes, testes dos critérios de aceitação, documentação e evidência anexada. |
| RJ-05 Segurança | Nenhum segredo, credencial ou dado pessoal real em código, logs ou canais do projeto; configuração por variáveis de ambiente. |
| RJ-06 Integração contínua | Os três repositórios de código devem executar validação automática (lint, tipos, build e testes) a cada pull request. |
| RJ-07 Execução reproduzível | API, painel e app devem ser executáveis a partir do README, com dados de demonstração reproduzíveis. |
| RJ-08 Evidências de avaliação | A entrega final deve comprovar o fluxo AC-RELEASE (Notion, 17.19) com evidências, para avaliação combinada da equipe e do domínio individual. |

## Escopo do projeto

Entregas do TAP detalhadas conforme a EAP (documento 02) e os épicos do backlog:

1. **Gestão do projeto** — TAP, declaração do escopo, EAP, cronograma, orçamento, análise de qualidade, organograma e RACI, plano de comunicação, riscos, aquisições, matriz de partes interessadas e relatório final.
2. **Fundação técnica (EP-01)** — três repositórios executáveis, convenções, CI e base de integração.
3. **Identidade e acesso (EP-02)** — autenticação JWT, perfis e rotas protegidas na web e no mobile.
4. **Cadastros operacionais (EP-03)** — usuários, clientes, locais e equipamentos com QR Code.
5. **Modelos de inspeção (EP-04)** — construtor de checklist versionado e publicação.
6. **Planejamento (EP-05)** — agendamento, atribuição e acompanhamento por estado.
7. **Execução de campo (EP-06)** — checklist dinâmico no app com salvamento automático.
8. **Recursos nativos e evidências (EP-07)** — câmera, QR Code e localização.
9. **Offline e sincronização (EP-08)** — SQLite, outbox, envio idempotente, cursor de download e tratamento de conflitos.
10. **Revisão e decisão (EP-09)** — fila de revisão, aprovação, reprovação e histórico.
11. **Qualidade e entrega (EP-10)** — testes dos fluxos críticos, dados de demonstração, build Android, painel publicado, API executável por container, OpenAPI e demonstração ponta a ponta.
12. **Funcionalidades P1**, implementadas somente após a estabilidade do fluxo principal: dashboard, notificações, assinatura, relatório PDF, histórico detalhado, comentários por item, tema escuro, exportação CSV e biometria.

## Exclusão do escopo do projeto

Mantidas as exclusões do TAP e das decisões de escopo (Notion 2.8, 8.4 e Anexo B):

- portal do cliente (fora do MVP);
- iOS como plataforma de validação (o mobile é prioritariamente Android);
- múltiplas organizações (multi-tenancy) e mais de um técnico por inspeção;
- edição colaborativa simultânea da mesma inspeção;
- fluxo de tratamento de não conformidades, planos de ação, ordens de serviço e manutenção preventiva;
- geofencing, rastreamento contínuo e controle de equipes em tempo real;
- áudio, vídeo, OCR e análise de imagens por inteligência artificial;
- integrações com ERP, sensores IoT, webhooks e armazenamento corporativo;
- relatórios regulatórios específicos e painéis analíticos avançados;
- substituição de sistemas corporativos de manutenção, diagnóstico automático e escala corporativa de milhões de inspeções.

## Estimativa de duração do projeto

16 semanas efetivas de aula, em 8 sprints de 2 semanas. Da aprovação do TAP (14/08/2026) ao encerramento previsto (27/11/2026), com prazo-limite em 30/11/2026. A linha de base do cronograma (documento 03) vai de 24/08/2026 a 27/11/2026, com 89 itens e 11 marcos; os marcos M1 a M8 do roadmap (Notion 16.6) servem como pontos de controle a cada duas semanas.

## Estimativas iniciais de custo

Não há investimento financeiro direto: o projeto é acadêmico e o principal recurso é a carga horária das disciplinas integradoras (80 aulas de 50 minutos) e o esforço da equipe. O orçamento (documento 04) fixa custo obrigatório de **R$ 0,00** e lista **R$ 2.570,00** em itens opcionais para um piloto externo (domínio, smartphones, etiquetas QR, dados móveis, deslocamentos e reservas), que só podem ser gastos com aprovação prévia do sponsor.

## Principais partes interessadas

Mantidas as do TAP, com a inclusão do responsável do cliente (persona Roberto), presente na especificação como usuário indireto:

- coordenação acadêmica das disciplinas integradoras (sponsor);
- professores de Expo, Spring Boot e Interface Web (comitê executivo e avaliação integrada);
- avaliadores acadêmicos;
- equipe de desenvolvimento: Giovana Rafaela, Gustavo Sousa, Juliana Nascimento, Maria Eduarda e Milenna Portella;
- técnicos de campo (persona Carlos) e supervisores (persona Marina);
- administradores do sistema (persona Ana);
- responsável do cliente (persona Roberto), que recebe resultados das inspeções fora do sistema no MVP.

## Premissas iniciais

| Premissa | Descrição |
|---|---|
| Plataforma mobile | Android é a plataforma prioritária de validação da primeira versão. |
| Organização usuária | O sistema é usado inicialmente por uma única organização operadora que presta inspeções a vários clientes. |
| Responsável único | Cada inspeção tem um único técnico responsável no MVP. |
| Modelos prévios | As inspeções partem de modelos configurados e publicados previamente. |
| Persistência local | O aplicativo preserva dados não sincronizados mesmo após ser fechado. |
| Ferramentas gratuitas | GitHub, GitHub Actions, Expo/EAS e contas educacionais estão disponíveis sem custo. |
| Desenvolvimento em paralelo | Web e mobile avançam com mocks do contrato OpenAPI enquanto a API é construída. |

## Restrições iniciais

| Restrição | Descrição |
|---|---|
| Calendário | 16 semanas efetivas; semanas de avaliações, feriados e eventos não são dependência para concluir o MVP. |
| Orçamento | Nenhuma despesa paga sem aprovação prévia do sponsor. |
| Equipe | Cinco integrantes, com dedicação acadêmica compartilhada com outras disciplinas. |
| Mudança de escopo | Após a definição do MVP, somente o sponsor pode alterá-lo, com revisão de prazo e custo. |
| Tecnologia | Expo/React Native, Next.js e Java/Spring Boot com PostgreSQL, conforme disciplinas e ADR 0002. |
| Ordem de corte | Se houver atraso, o escopo é reduzido na ordem do roadmap (Notion 16.7), preservando autenticação, planejamento, checklist, foto, offline, sincronização e revisão. |

## Critérios de aceitação das entregas

- **Histórias:** DoD geral e específica de mobile, web e API (Notion, página 18).
- **Versão final (AC-RELEASE, Notion 17.19):** fluxo sem edição manual do banco — login administrativo, cadastros, modelo publicado, agendamento, login do técnico, download, checklist, foto, QR Code, localização, perda de conexão, conclusão offline, sincronização sem duplicidade, revisão, aprovação ou reprovação, atualização no app e histórico.
- **Defeitos:** críticos bloqueiam a entrega; altos devem ser corrigidos antes da release; médios e baixos podem ser aceitos com registro e plano (Notion 18.7).

## Aprovações

| Participante | Assinatura | Data |
|---|---|---|
| Financiador do Projeto (coordenação acadêmica) | | ___/___/___ |
| Gerente do Projeto | | ___/___/___ |
