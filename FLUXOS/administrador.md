# Administrador

Ana entra no painel web, mantém quem acessa o sistema e o cadastro operacional que o supervisor usa para agendar.
Corte: 05/11/2026. Papel `ADMIN`. Canal: web.

O supervisor faz o mesmo cadastro de cliente, local e equipamento. Não faz a gestão de usuários.

```mermaid
flowchart TD
  login[Abre o login] --> cred{E-mail e senha validos?}
  cred -->|Nao| erro[Mensagem unica, sem dizer qual campo falhou]
  cred -->|Usuario inativo| bloqueio[Acesso negado]
  cred -->|Sim| painel[Painel web]
  painel --> usuarios[Usuarios]
  painel --> clientes[Clientes]
  painel --> modelos[Modelos - ver fluxo do supervisor]
  painel --> agenda[Agendar e acompanhar - ver fluxo do supervisor]
```

## UC-01 — Entrar e sair

Disponível no web (PBI-0009, 0010) e no mobile do técnico (PBI-0008, 0010).

```mermaid
sequenceDiagram
  actor Ana
  participant Web
  participant API
  Ana->>Web: e-mail e senha
  Web->>API: POST /auth/login
  API-->>Web: access token e refresh token
  Web->>Web: guarda a sessao
  Note over Web,API: access token vencido
  Web->>API: POST /auth/refresh
  API-->>Web: novo access token
  Ana->>Web: sair
  Web->>API: POST /auth/logout
  Web->>Web: apaga a sessao
```

## UC-02 — Usuários

Disponível (PBI-0011, 0012). Só `ADMIN`.

```mermaid
flowchart TD
  lista[Lista usuarios] --> novo[Cria usuario com papel e senha inicial]
  lista --> edita[Edita nome, e-mail e papel]
  lista --> status[Ativa ou inativa]
  status --> efeito[Inativo nao abre sessao nova]
  efeito --> historico[Historico do usuario permanece]
```

Papéis que ele pode atribuir: `ADMIN`, `SUPERVISOR`, `TECHNICIAN`.

## UC-03 — Cliente, local e equipamento

Disponível (PBI-0013 a 0017). `ADMIN` e `SUPERVISOR`.

```mermaid
flowchart TD
  cliente[Cadastra ou edita o cliente] --> local[Abre os locais desse cliente]
  local --> equipa[Cadastra equipamento no local]
  equipa --> qr[Sistema guarda o QR do equipamento]
  equipa --> regra{Equipamento de outro local?}
  regra -->|Sim| bloqueia[Nao entra no agendamento]
  regra -->|Nao| segue[Pode ser escolhido no agendamento daquele local]
```

Lista de clientes, locais e equipamentos é paginada, com busca e filtro (PBI-0017).

## Ainda não entra neste fluxo

- Redefinir senha por e-mail. Há tela de "esqueci a senha" no web e no mobile; o contrato entregue até o PBI-0012 não fecha esse caso.
- Consulta de auditoria e indicadores (UC-18, UC-19).
- Papel de cliente somente leitura (UC-20).
