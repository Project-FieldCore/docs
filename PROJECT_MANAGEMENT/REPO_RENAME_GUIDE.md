# Atualizar o clone após o rename dos repositórios

Os repositórios na org **Project-FieldCore** foram renomeados (sem o prefixo `fieldcore_`, nomes em inglês). O GitHub redireciona o URL antigo por um tempo, mas cada pessoa deve **atualizar o remote** e **renomear a pasta local**.

`fieldcore_cloud` foi **removido** — apague a pasta local se ainda existir.

## Mapa

| Pasta / remote antigo | Nome novo no GitHub | Pasta local nova |
|---|---|---|
| `fieldcore_backend` ou `backend` | `api-java` | `api-java` |
| `fieldcore_frontend` ou `frontend` | `web-react` | `web-react` |
| `fieldcore_mobile` ou `mobile` | `mobile-react` | `mobile-react` |
| `fieldcore_documentacao` ou `docs` | `docs` | `docs` |
| `fieldcore_cloud` | *(deletado)* | apagar a pasta |

## Antes de começar

1. Confirme no GitHub que os repos novos existem.
2. Feche a IDE e terminais abertos **dentro** das pastas que vai renomear.
3. Salve ou faça commit/stash de alterações pendentes (`git status` limpo).
4. Vá até a pasta **pai** dos clones (ex.: `fieldops/`).

## Por repositório (manual)

Repita para cada linha do mapa. Exemplo com o backend → `api-java`.

### 1. Atualizar o remote

Entre na pasta do clone (nome antigo) e rode:

**Linux / WSL / macOS / Git Bash**

```bash
cd backend
git remote set-url origin https://github.com/Project-FieldCore/api-java.git
git remote -v
git fetch origin
cd ..
```

**Windows (PowerShell)**

```powershell
cd backend
git remote set-url origin https://github.com/Project-FieldCore/api-java.git
git remote -v
git fetch origin
cd ..
```

Se o time usa SSH:

```text
git@github.com:Project-FieldCore/api-java.git
```

### 2. Renomear a pasta local

Ainda na pasta pai:

**Linux / WSL / macOS / Git Bash**

```bash
mv backend api-java
```

**Windows (PowerShell)**

```powershell
Rename-Item -Path backend -NewName api-java
```

### 3. Repetir para os outros

| Se a pasta se chama… | `set-url origin` | Depois renomeie para… |
|---|---|---|
| `frontend` ou `fieldcore_frontend` | `…/web-react.git` | `web-react` |
| `mobile` ou `fieldcore_mobile` | `…/mobile-react.git` | `mobile-react` |
| `docs` ou `fieldcore_documentacao` | `…/docs.git` | `docs` (se já for `docs`, só atualize o remote) |

### 4. Remover o cloud (se tiver)

**Linux / WSL / macOS / Git Bash:** `rm -rf fieldcore_cloud`  
**PowerShell:** `Remove-Item -Recurse -Force fieldcore_cloud`

## Clone novo (quem ainda não tinha)

```bash
git clone https://github.com/Project-FieldCore/api-java.git
git clone https://github.com/Project-FieldCore/web-react.git
git clone https://github.com/Project-FieldCore/mobile-react.git
git clone https://github.com/Project-FieldCore/docs.git
```

## Conferência rápida

Em cada pasta nova: `git remote -v` deve mostrar só o nome novo, e `git fetch` deve funcionar. Reabra o workspace na IDE.
