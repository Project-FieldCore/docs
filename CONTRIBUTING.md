# Como contribuir com a documentação

Este repositório guarda dois tipos de documento, com regras diferentes:

| Tipo | Onde | Fonte da verdade |
|---|---|---|
| Especificação do produto | `NOTION/pages/` | **Notion** — este repo é um snapshot exportado |
| Gestão e governança | `PROJECT_MANAGEMENT/`, `DECISIONS/`, raiz | **Este repositório** |

## Regras por área

### `NOTION/`
- Não renomeie arquivos de `pages/` (o sufixo é o ID da página no Notion; links e futuras exportações dependem dele).
- Não corrija conteúdo só aqui: corrija no Notion e reexporte, senão a correção é sobrescrita.
- Reexportou? Atualize a tabela de índice em [`NOTION/README.md`](NOTION/README.md) no mesmo commit.

### `PROJECT_MANAGEMENT/` e demais arquivos
- Escritos e mantidos direto aqui, em Markdown.
- Datas em `dd/mm/aaaa`; prazos em dias úteis; responsáveis por papel (GP, PO, ARQ, Dev…) ou nome — seja consistente dentro do documento.
- Imagens (ex.: `EAP.jpeg`) devem vir acompanhadas da **fonte editável** quando existir (Mermaid/draw.io/planilha) na mesma pasta.

## Escrevendo um documento novo

1. Escolha a pasta certa: gestão → `PROJECT_MANAGEMENT/`; decisão → `DECISIONS/`; termo de domínio → [`GLOSSARIO.md`](GLOSSARIO.md); o resto da especificação nasce no Notion.
2. Nome de arquivo em maiúsculas para artefatos de gestão (`TAP.md`, `CRONOGRAMA.md`) e descritivo para os demais.
3. Comece com `# Título` + 1–2 linhas dizendo **o que é, para quem e quando atualizar** — quem abre o arquivo decide em 10 segundos se é o que procura.
4. Linke a partir do índice da pasta (`README.md` local) e, se for relevante, do [`README.md`](README.md) raiz. Documento sem link de entrada é documento perdido.

## Fluxo de trabalho (Git)

O histórico deste repo já segue gitmoji + Conventional Commits — mantenha:

```bash
git checkout -b docs/<assunto-curto>
# edite…
git commit -m ":books: docs: <resumo no imperativo>"
git push -u origin docs/<assunto-curto>
# abra PR para main
```

- **Branches:** `docs/<assunto>` para documentação, `fix/<assunto>` para correção de link/conteúdo errado.
- **Commits:** `:books: docs: …` (docs), `:sparkles: feat: …` (artefato novo relevante), `:bug: fix: …` (link quebrado). Um assunto por commit.
- **Pull Requests:** descreva o que mudou e por quê; se alterou prazo/escopo/marco, linke a decisão em `DECISIONS/`.

## Antes de abrir o PR — checklist

- [ ] Links relativos conferidos (clique em todos os que você criou/alterou)
- [ ] Índice da pasta atualizado (`README.md` local e/ou raiz)
- [ ] Sem informação duplicada: linke para a fonte em vez de copiar o conteúdo
- [ ] Nomes e termos conforme o [GLOSSARIO.md](GLOSSARIO.md) (produto = **FieldOps**)
- [ ] Nenhum dado sensível, senha ou dado pessoal real (use as personas Ana/Marina/Carlos)
