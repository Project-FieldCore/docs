# FieldOps (FieldCore) — Documentação

> Repositório central de documentação da plataforma **FieldOps** — sistema de inspeção técnica em campo com operação offline.
> Aqui vivem a especificação do produto (exportada do Notion) e os artefatos de gestão do projeto. O código fica nos repositórios irmãos (links abaixo).

**Assistentes de IA / agentes:** comece em [`AGENTS.md`](AGENTS.md) (agnóstico de ferramenta). Índice de convenções: [`PROJECT_MANAGEMENT/CONVENTIONS.md`](PROJECT_MANAGEMENT/CONVENTIONS.md).

📺 **Vídeo do projeto:** https://youtu.be/4UAVJdNgx-s

---

## O que é o FieldOps

Plataforma que substitui formulários impressos, planilhas e fotos sem identificação por um fluxo digital único: **planejar → executar em campo (mesmo offline) → sincronizar → revisar → auditar**.

| Persona | Quem é | O que faz na plataforma |
|---|---|---|
| **Ana** | Administradora | Cadastra clientes, locais, equipamentos, usuários e modelos de inspeção |
| **Marina** | Supervisora | Agenda e atribui inspeções, acompanha a execução, aprova/reprova resultados |
| **Carlos** | Técnico de campo | Executa checklists no app mobile, lê QR Code, captura evidências — inclusive sem internet |

Visão completa: [01 - Visão Geral](NOTION/pages/01%20-%20Vis%C3%A3o%20Geral%2020e3130b4ab782b393d481b43725c522.md) · [03 - Problema](NOTION/pages/03%20-%20Problema%20b913130b4ab7835a9a29012200ee4700.md) · [04 - Personas](NOTION/pages/04%20-%20Personas%204353130b4ab78359aad101e637a5e19a.md)

## Componentes e repositórios

| Componente | Stack | Repositório |
|---|---|---|
| API REST | Java + Spring Boot + PostgreSQL | [api-java](https://github.com/Project-FieldCore/api-java) |
| Interface administrativa web | Next.js + TypeScript ([ADR 0002](DECISIONS/0002-web-nextjs-instead-of-angular.md)) | [web-react](https://github.com/Project-FieldCore/web-react) |
| Aplicativo mobile | Expo + React Native + SQLite | [mobile-react](https://github.com/Project-FieldCore/mobile-react) |
| Documentação | Markdown | [docs](https://github.com/Project-FieldCore/docs) — *você está aqui* |

Quem já tinha clone com o nome antigo: [REPO_RENAME_GUIDE.md](PROJECT_MANAGEMENT/REPO_RENAME_GUIDE.md).

> ⚠️ **Divergências a resolver (não esconda, decida):**
> 1. **Nome:** os documentos oscilam entre *FieldOps* e *FieldCore*. Convenção adotada aqui: **FieldOps é o produto**, **FieldCore é o nome da organização** no GitHub; os repositórios usam nomes curtos em inglês (`api-java`, `web-react`, `mobile-react`, `docs`).
> 2. **Frontend web:** stack oficial = **Next.js** ([ADR 0002](DECISIONS/0002-web-nextjs-instead-of-angular.md)). As páginas Notion 11/14 ainda citam Angular até o próximo reexport.

## Estrutura deste repositório

```
docs/
├── README.md                  # ← este arquivo (ponto de entrada humano)
├── AGENTS.md                  # ponto de entrada para IAs / agentes (agnóstico)
├── CONTRIBUTING.md            # como escrever, nomear e aprovar mudanças na doc
├── GLOSSARIO.md               # termos do domínio (inspeção, snapshot, outbox…)
├── FLUXOS/                    # uso real por papel e caso de uso (Mermaid; evolui com os PBIs)
│   └── README.md              # índice, situação e como atualizar
├── NOTION/                    # especificação do produto (export do Notion)
│   ├── README.md              # índice comentado das 22 páginas
│   └── pages/                 # páginas 01–22 (não renomear — ver CONTRIBUTING)
├── PROJECT_MANAGEMENT/        # gestão do projeto (PMBOK)
│   ├── README.md              # índice + marcos + como manter os artefatos
│   ├── TAP.md                 # Termo de Abertura do Projeto
│   ├── CRONOGRAMA.md          # cronograma (89 atividades, 11 fases, 11 marcos)
│   └── EAP.jpeg               # Estrutura Analítica do Projeto (imagem)
└── DECISIONS/                 # registro de decisões de arquitetura (ADR)
    └── README.md              # índice + template
```

## Índice da documentação

### 1. Como cada papel usa o sistema — [`FLUXOS/`](FLUXOS/README.md)

[Jornada](FLUXOS/jornada.md) · [Administrador](FLUXOS/administrador.md) · [Supervisor](FLUXOS/supervisor.md) · [Técnico](FLUXOS/tecnico.md)

O que está no código até o PBI corrente. A especificação completa continua no Notion.

### 2. Produto e requisitos — [`NOTION/pages/`](NOTION/README.md)

Visão geral · Objetivos · Problema · Personas · Perfis de usuário · Casos de uso · Fluxo geral · Funcionalidades · Regras de negócio

### 3. Arquitetura e dados

[10 - Modelo de Dados](NOTION/pages/10%20-%20Modelo%20de%20Dados%20eb43130b4ab7824f85b881c97289b28f.md) · [11 - Arquitetura](NOTION/pages/11%20-%20Arquitetura%202fa3130b4ab7820094b201c65aae2822.md) · [12 - API REST](NOTION/pages/12%20-%20API%20REST%20a003130b4ab78345a637819a01fe1fc4.md)

### 4. Aplicações

[13 - Aplicativo Mobile](NOTION/pages/13%20-%20Aplicativo%20Mobile%20ac83130b4ab783f9a98781d7b86ce1d7.md) · [14 - Interface Administrativa Web](NOTION/pages/14%20-%20Interface%20Administrativa%20Web%201663130b4ab782babf8781b030596ced.md)

### 5. Planejamento e qualidade

[15 - Backlog](NOTION/pages/15%20-%20Backlog%20do%20Produto%20add3130b4ab783848042818065d5e111.md) · [16 - Roadmap](NOTION/pages/16%20-%20Roadmap%2030f3130b4ab783af82b781172c6cb245.md) · [17 - Critérios de Aceitação](NOTION/pages/17%20-%20Crit%C3%A9rios%20de%20Aceita%C3%A7%C3%A3o%208a43130b4ab782038a7f81a1eb087644.md) · [18 - Definition of Done](NOTION/pages/18%20-%20Defini%C3%A7%C3%A3o%20de%20Pronto%20-%20Definition%20of%20Done%2027d3130b4ab7839c917f816f80bc8201.md) · [19 - Critérios de Avaliação](NOTION/pages/19%20-%20Crit%C3%A9rios%20de%20Avalia%C3%A7%C3%A3o%208983130b4ab7839089fc815b3b0f3ff9.md)

### 6. Gestão do projeto — [`PROJECT_MANAGEMENT/`](PROJECT_MANAGEMENT/README.md)

[TAP — Termo de Abertura](PROJECT_MANAGEMENT/TAP.md) · [Cronograma](PROJECT_MANAGEMENT/CRONOGRAMA.md) · [EAP](PROJECT_MANAGEMENT/EAP.jpeg)

### 7. Anexos

Checklist executivo · Decisões de escopo · Exemplo de ficha de inspeção · Diagrama de classes — ver índice completo em [`NOTION/README.md`](NOTION/README.md).

## Consultar OpenAPI e diagramas principais

Para quem avalia a entrega (AC-RELEASE): onde ver o contrato da API e onde estão os diagramas.

### OpenAPI (Swagger UI e `/v3/api-docs`)

Swagger UI e o JSON do OpenAPI são públicos (sem token); as rotas protegidas pedem login (`POST /api/v1/auth/login`, depois **Authorize** com o `accessToken`).

| Onde | Swagger UI | OpenAPI (JSON) |
|---|---|---|
| Local (`./mvnw spring-boot:run`) | http://localhost:8080/swagger-ui.html | http://localhost:8080/v3/api-docs |
| Container (Docker Compose) | porta publicada (padrão 8080): `/swagger-ui.html` | `/v3/api-docs` — build/run em [`DEPLOY_CONTAINER.md`](https://github.com/Project-FieldCore/api-java/blob/develop/docs/DEPLOY_CONTAINER.md); URLs e diagramas também na seção [Consultar OpenAPI e diagramas](https://github.com/Project-FieldCore/api-java/blob/develop/README.md#consultar-openapi-e-diagramas) do README do api-java |
| DEV (EC2) | http://34.196.177.92/swagger-ui.html | http://34.196.177.92/v3/api-docs |

> O IP do DEV pode mudar no Learner Lab; confirme o endereço atual com a equipe (Environment `development` do api-java).

Contrato versionado: [`openapi/fieldops-v1.yaml`](https://github.com/Project-FieldCore/api-java/blob/develop/openapi/fieldops-v1.yaml) (repo api-java, branch `develop`). Erros usam o formato padronizado da [12 - API REST](NOTION/pages/12%20-%20API%20REST%20a003130b4ab78345a637819a01fe1fc4.md): `timestamp`, `status`, `code`, `message`, `path`, `requestId`, `fieldErrors`.

### Diagramas principais

| Diagrama | Onde | Formato | Observação |
|---|---|---|---|
| Classes do domínio | [22 Anexo D - Diagrama de Classe](NOTION/pages/22%20Anexo%20D%20-%20Diagrama%20de%20Classe%203c63130b4ab782fe962c018b0adf27b3.md) ([imagem](NOTION/pages/22%20Anexo%20D%20-%20Diagrama%20de%20Classe/image.png)) | Imagem (PlantUML exportado) | Sem fonte editável no repo |
| Modelo de dados | [10 - Modelo de Dados](NOTION/pages/10%20-%20Modelo%20de%20Dados%20eb43130b4ab7824f85b881c97289b28f.md) (seção 10.3) | Texto/ASCII | Sem diagrama gráfico (ER) |
| Fluxos por papel | [FLUXOS](FLUXOS/README.md) · [jornada](FLUXOS/jornada.md) · [técnico](FLUXOS/tecnico.md) · [supervisor](FLUXOS/supervisor.md) · [administrador](FLUXOS/administrador.md) | Mermaid | Corte 05/11/2026 (até o PBI-0050) |
| Arquitetura | [11 - Arquitetura](NOTION/pages/11%20-%20Arquitetura%202fa3130b4ab7820094b201c65aae2822.md) | Texto | Sem diagrama visual; ainda cita Angular (ver divergência acima) |
| API REST | [12 - API REST](NOTION/pages/12%20-%20API%20REST%20a003130b4ab78345a637819a01fe1fc4.md) | Texto | O contrato executável é o OpenAPI acima |

A descrição do Swagger UI do api-java (PBI-0071.1) também lista esses links.

**Pendências (diagramas ainda parciais):**

- Diagrama de classes só existe como imagem; falta a fonte editável (CONTRIBUTING pede PlantUML/Mermaid ao lado da imagem).
- O diagrama de classes diverge do código: `UserRole` usa `ADMIN/MANAGER/INSPECTOR/REVIEWER`, enquanto a API usa `ADMIN/SUPERVISOR/TECHNICIAN/CLIENT_VIEWER`; e o diagrama prevê `EquipmentType`, que não existe nas migrations. Corrigir na fonte (Notion) e reexportar.
- Não há diagrama gráfico do modelo de dados (ER) nem de arquitetura (componentes/implantação).
- Os fluxos estão com corte em 05/11/2026; atualizar conforme [`FLUXOS/README.md`](FLUXOS/README.md#como-evoluir).

### Como avaliar em 5 passos

1. Abra o **Swagger UI** (local, container ou DEV — tabela acima) e confirme que carrega sem token.
2. Abra `/v3/api-docs` e confira `info` (título **FieldOps API**, versão) e a lista de rotas; compare com o contrato versionado `fieldops-v1.yaml`.
3. Faça login em `POST /api/v1/auth/login`. Use o usuário **de demonstração** `admin@fieldcore.com` / `DemoPass123!` (válido no DEV, no container de demo e local; lista completa em [`DEMO_SEED.md`](https://github.com/Project-FieldCore/api-java/blob/develop/docs/DEMO_SEED.md)). São credenciais de demo, não segredos de produção. Use **Authorize** com o `accessToken` e chame uma rota protegida (ex.: `GET /api/v1/inspections`).
4. Provoque um erro (senha errada → `401 INVALID_CREDENTIALS`; sem token → `401`) e confira o corpo padronizado (`code`, `message`, `requestId`, `fieldErrors`).
5. Percorra os diagramas na ordem: **classes (22) → modelo de dados (10) → fluxos por papel ([FLUXOS](FLUXOS/README.md))** e registre divergências em relação ao código.

## Por onde começar

| Se você é… | Comece por |
|---|---|
| Novo no projeto | [FLUXOS](FLUXOS/README.md) (o que cada papel faz hoje) → [01 - Visão Geral](NOTION/pages/01%20-%20Vis%C3%A3o%20Geral%2020e3130b4ab782b393d481b43725c522.md) → [GLOSSARIO.md](GLOSSARIO.md) |
| Desenvolvedor(a) | [11 - Arquitetura](NOTION/pages/11%20-%20Arquitetura%202fa3130b4ab7820094b201c65aae2822.md) → [10 - Modelo de Dados](NOTION/pages/10%20-%20Modelo%20de%20Dados%20eb43130b4ab7824f85b881c97289b28f.md) → [12 - API REST](NOTION/pages/12%20-%20API%20REST%20a003130b4ab78345a637819a01fe1fc4.md) → README do seu repositório |
| Gestão / acompanhamento | [PROJECT_MANAGEMENT/](PROJECT_MANAGEMENT/README.md) (TAP, cronograma e marcos) |
| Avaliador(a) | [Consultar OpenAPI e diagramas](#consultar-openapi-e-diagramas-principais) → [19 - Critérios de Avaliação](NOTION/pages/19%20-%20Crit%C3%A9rios%20de%20Avalia%C3%A7%C3%A3o%208983130b4ab7839089fc815b3b0f3ff9.md) → [16 - Roadmap](NOTION/pages/16%20-%20Roadmap%2030f3130b4ab783af82b781172c6cb245.md) → este README |

## Marcos (resumo)

Prazo final: **30/11/2026** · Encerramento previsto: **27/11/2026** (margem de 1 dia útil — trate 27/11 como data-limite real).

| Marco | Data | Descrição |
|---|:---:|---|
| 1.7 | 27/08/2026 | Plano de projeto aprovado |
| 2.9 | 10/09/2026 | Documentação de requisitos aprovada |
| 3.9 | 18/09/2026 | Infraestrutura base disponível |
| 7.5 | 22/10/2026 | Sistema integrado (build candidato a homologação) |
| 9.5 | 13/11/2026 | Sistema homologado pelo cliente |
| 10.7 | 19/11/2026 | Go-live |
| 11.5 | 27/11/2026 | Encerramento formal |

Tabela completa (11 marcos) no [Cronograma](PROJECT_MANAGEMENT/CRONOGRAMA.md#4-marcos-do-projeto-resumo).

## Equipe

Giovana Rafaela · Gustavo Sousa · Juliana Nascimento · Maria Eduarda · Milenna Portella — detalhes e papéis no [TAP](PROJECT_MANAGEMENT/TAP.md).

## Como manter esta documentação

- **Fonte da especificação:** as páginas em `NOTION/pages/` foram exportadas do Notion. Ao reexportar, substitua os arquivos e atualize [`NOTION/README.md`](NOTION/README.md) — não edite correções só no export, ou elas serão perdidas na próxima exportação. Corrija na fonte (Notion) ou migre a página para cá de forma definitiva e registre a decisão.
- **Gestão do projeto:** `PROJECT_MANAGEMENT/` é mantido direto neste repositório.
- Regras de nomeação, branches, commits e revisão: [`CONTRIBUTING.md`](CONTRIBUTING.md).
- Decisões relevantes (troca de stack, mudança de escopo, contrato de API): registe em [`DECISIONS/`](DECISIONS/README.md) antes de sair alterando vários documentos.
