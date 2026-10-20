# Planejamento de sprints — FieldOps (fiel ao Notion)

Estrutura de sprints, backlog e cadência do time. **A fonte é o Notion**:
backlog PBI-001…082 (doc. 15), roadmap de 8 sprints × 2 semanas (doc. 16),
critérios de aceitação (doc. 17) e DoD (doc. 18). Este arquivo não cria um
planejamento paralelo: ele operacionaliza o do Notion no GitHub e registra
o estado real. Estamos atrasados em relação ao cronograma
([CRONOGRAMA.md](CRONOGRAMA.md)); a resposta é avançar sobre o que está
atrasado **sem mudar a estrutura ideal** — mesmos épicos, mesma ordem de
dependência, mesma ordem de corte de escopo (doc. 16 §16.7).

## 1. Mapa Notion → GitHub

| Notion | GitHub |
|---|---|
| Épico EP-01…EP-10 | Campo `Épico` do Project + label `epic/EP-XX` |
| PBI-XXXX (doc. 15 §15.3) | Issue pai no repo do componente principal |
| Componente `Mobile/Admin/API` do PBI | Issues filhas `PBI-XXXX.N` nos repos afetados |
| Sprint 1…8 (docs. 15/16) | Campo `Sprint` do Project + label `sprint/N` |
| Critérios (doc. 17) | Seção "Critérios de aceitação" no corpo da issue |
| DoD (doc. 18) | Checklist final da issue/PR; sem DoD, não vai para `Done` |

Convenções de nome/branch/commit: [BRANCH_COMMIT_CONVENTION.md](BRANCH_COMMIT_CONVENTION.md).

## 2. Estado real (auditoria de 19–20/10/2026)

Resumo das auditorias por camada (backend, dados, front, UI, segurança):

- **Backend**: scaffold da Sprint 1 (PR #76). `AuthController`/`UserController`
  são stubs que lançam `501 NOT_IMPLEMENTED`; `V1__baseline.sql` é placeholder
  (`SELECT 1`) com a lista de tabelas só em comentário; OpenAPI skeleton com
  6 paths (doc. 12 pede ~40). JWT sem biblioteca definida e segredo dev
  versionado (`change-me-dev-only`) — corrigir no PBI-0007.
- **Frontend web**: protótipo **mock** completo em Next.js (telas de modelos,
  inspeções, agenda, revisão sobre Zustand/`mock-data.ts`, zero chamada de
  API). Divergência aberta: docs. 11/14/TAP dizem **Angular** — vira ADR
  antes dos cards web (ver [DECISIONS](../DECISIONS/README.md)).
- **Mobile**: projeto Expo criado, mas `App.tsx` é o template padrão — sem
  Expo Router, features, SQLite ou design system. O README do repo marca
  auth/offline como `[x]` sem implementação: **não** usar como evidência.
- **Conclusão**: nenhum PBI está "FEITO" de ponta a ponta; o que existe é
  fundação (Sprint 1 parcial) + protótipo web mock. O planejamento abaixo
  estima o trabalho **restante**, não o trabalho total.

## 3. Sprints 1–3 — PBIs, estimativas e dependências

Pontos em Fibonacci por PBI (soma de todos os componentes; filhos recebem
estimativa própria na criação e a pai é recalculada). Estimativa inicial
do Orquestrador a partir da auditoria — o time confirma/altera no
refinamento (doc. 15 §15.5: sem critério de aceitação e contrato, não entra).

### Sprint 1 — EP-01 Fundação técnica (22 pts)

| PBI | História (resumo) | Comp. | Pts | Estado real | Depende de |
|---|---|---|---|---|---|
| PBI-0001 | Repositórios e convenções | Todos | 3 | Parcial (repos ok; convenções neste doc) | — |
| PBI-0002 | Projeto Expo + TS + rotas/features | Mobile | 5 | Parcial (template) | 0001 |
| PBI-0003 | Projeto web + layout/rotas | Web | 3 | Parcial (Next mock; ADR Angular×Next) | 0001 |
| PBI-0004 | API Spring + PostgreSQL + migrações | API | 5 | Parcial (scaffold; DDL real é V2/V3) | 0001 |
| PBI-0005 | Lint, tipos e fluxo de PR | Todos | 3 | Ausente | 0001 |
| PBI-0006 | Contrato OpenAPI inicial + mocks | API/Integ. | 3 | Parcial (6 paths) | 0004 |

Marco M1: três aplicações executáveis com contrato inicial.

### Sprint 2 — EP-02 Identidade e EP-03 Cadastros (57 pts)

| PBI | História (resumo) | Comp. | Pts | Estado real | Depende de |
|---|---|---|---|---|---|
| PBI-0007 | Login e-mail/senha (API) | API | 8 | Ausente (stub 501) | 0004, 0006 |
| PBI-0008 | Sessão no mobile (login/logout) | Mobile | 5 | Ausente | 0002, 0007 |
| PBI-0009 | Sessão na web (login/logout) | Web | 5 | Mock apenas | 0003, 0007 |
| PBI-0010 | Renovação de sessão (refresh) | Mobile/Web/API | 5 | Ausente | 0007 |
| PBI-0011 | CRUD de usuários (admin) | Web/API | 8 | Ausente (stub) | 0007, 0012 |
| PBI-0012 | Autorização por perfil na API | API | 5 | Parcial (skeleton de segurança) | 0007 |
| PBI-0013 | Gerenciar clientes | Web/API | 5 | Mock (web) | 0004 |
| PBI-0014 | Gerenciar locais do cliente | Web/API | 5 | Mock (web) | 0013 |
| PBI-0015 | Gerenciar equipamentos do local | Web/API | 5 | Mock (web) | 0014 |
| PBI-0016 | QR Code único do equipamento | Web/API | 3 | Mock (web) | 0015 |
| PBI-0017 | Pesquisa, filtros e paginação | Web/API | 3 | Ausente (sem API) | 0013–0015 |

Marco M2: login integrado nos dois clientes; cadastros reais na API.
Critérios de segurança obrigatórios já na Sprint 2 (auditoria): segredo JWT
só por ambiente (≥256 bits), refresh com rotação + hash, BCrypt, matriz
perfil×endpoint testada (PBI-0012), Swagger/H2 só em dev.

### Sprint 3 — EP-04 Modelos e EP-05 Planejamento (53 pts)

| PBI | História (resumo) | Comp. | Pts | Estado real | Depende de |
|---|---|---|---|---|---|
| PBI-0018 | Modelo em rascunho | Web/API | 5 | Mock (web) | 0013 |
| PBI-0019 | Seções ordenáveis | Web/API | 5 | Mock sem ordenação | 0018 |
| PBI-0020 | Itens por tipo de resposta | Web/API | 8 | Mock parcial (sem opções SINGLE_CHOICE) | 0019 |
| PBI-0021 | Obrigatoriedade e regras de evidência | Web/API | 3 | Mock parcial | 0020 |
| PBI-0022 | Prévia do checklist | Web | 3 | Mock (fidelidade por tipo pendente) | 0020 |
| PBI-0023 | Publicar versão imutável | Web/API | 8 | Mock permissivo (publica inválido) | 0018–0021 |
| PBI-0024 | Snapshot da inspeção | API/Banco | 5 | Ausente | 0023 |
| PBI-0025 | Agendar a partir de modelo publicado | Web/API | 5 | Mock (web) | 0023, 0024 |
| PBI-0026 | Seleção encadeada cliente→local→equip. | Web/API | 3 | Mock | 0013–0015, 0025 |
| PBI-0027 | Atribuir a técnico ativo | Web/API | 3 | Mock | 0011, 0025 |
| PBI-0028 | Prioridade, prazo e instruções | Web/API | 2 | Mock | 0025 |
| PBI-0029 | Cancelar com justificativa | Web/API | 3 | Ausente | 0025 |

Marco M3: supervisor cria, publica, agenda e atribui — ponta a ponta na API.

### Sprints 4–8 (estrutura mantida, estimar no refinamento de cada sprint)

| Sprint | Épicos/PBIs | Marco |
|---|---|---|
| 4 | EP-05 (PBI-0030) + EP-06 Execução (PBI-0031…0040) | M4 — técnico executa online |
| 5 | EP-07 Nativos/evidências (PBI-0041…0047) | M5 — foto, QR e GPS |
| 6 | EP-08 Offline/sync (PBI-0048…0055) | M6 — offline concluído e sincronizado |
| 7 | EP-09 Revisão (PBI-0056…0063) + EP-10 (PBI-0064…0065) | M7 — aprovar/reprovar com correção |
| 8 | EP-10 Entrega (PBI-0066…0072) | M8 — release e demo final |

P1 (PBI-0073…0082: dashboard avançado, push, PDF, assinatura desenhada…)
só entra se o P0 da sprint fechar; ordem de corte oficial: doc. 16 §16.7.

## 4. Estimativas e capacidade

- Pontos medem **esforço restante relativo**, não horas. Filho estimado
  separadamente; tarefa acima de 8 pts deve ser dividida.
- Capacidade inicial: desconhecida (sem histórico confiável — as issues
  antigas não mediam nada). A velocidade da Sprint 1 vira a base; a partir
  dela recalculamos quantos pontos cabem por sprint até a apresentação
  final (marcos do CRONOGRAMA: homologação 13/11, go-live 19/11,
  encerramento 27/11/2026).
- Se a velocidade não comportar o P0, corta-se pela ordem do doc. 16 §16.7
  (dashboard avançado → tipos de resposta → galeria → drag-and-drop →
  conflito simplificado → notificações/PDF/assinatura), nunca auth,
  planejamento, checklist, foto, offline, sync ou revisão.

## 5. Cadência do time

Alinhada à rotina de aulas do doc. 16 §16.2 (refino no meio da semana,
integração/demo no fim) e aos artefatos sugeridos no README desta pasta:

| Ritual | Quando | Duração | Saída |
|---|---|---|---|
| Weekly (planning + review) | Segunda | 45 min | Sprint revisada, próxima sprint refinada (DoR doc. 15 §15.5), `STATUS.md` atualizado |
| Daily assíncrona | Seg–Sex | — | Cada um move seus cards e comenta bloqueio/progresso no board até o fim do dia |
| Daily síncrona | Terça e Quinta | 15 min | Só bloqueios e integração entre componentes |
| Demo/Review | Sexta (Aula 5 do doc. 16) | 30 min | Incremento demonstrável + evidência anexada às issues (DoD doc. 18) |
| Retrospectiva | Fim de cada sprint | 30 min | 1–3 ações registradas em `STATUS.md` |

`STATUS.md` (previsto × realizado, desvios do CRONOGRAMA, decisões da
semana) é a evidência do controle do cronograma — criar na primeira weekly.
