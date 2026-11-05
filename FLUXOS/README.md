# Fluxos de uso — FieldOps

O que a pessoa faz em cada papel, no canal em que o sistema já deixa fazer, caso de uso a caso de uso.
Quem atualiza: quem entrega um PBI que muda uma tela, um endpoint ou uma regra de passagem de estado.

Especificação de produto continua em [`NOTION/`](../NOTION/README.md) (perfis na página 05, casos de uso na 06, fluxo geral na 07).
Estes arquivos descrevem **o que os repositórios fazem hoje**. Quando os dois divergem, o diagrama diz o que está no código e a tabela aponta o PBI que ainda falta.

## Como evoluir

1. Ao fechar um PBI, atualize a coluna **Situação** na tabela abaixo.
2. Ajuste só o diagrama do caso de uso atingido. Não redesenhe os outros.
3. Tire o passo da seção "Ainda não entra neste fluxo" quando ele passar a existir na API e na tela.
4. Registre a data de corte no topo de cada arquivo (`Corte`).

Situação:

| Marca | Significado |
|---|---|
| Disponível | API e tela do canal principal fazem o fluxo |
| Parcial | A tela ou a API existe, mas o passo ainda não fecha o caso de uso |
| Previsto | Está no backlog (página 15) e ainda não deve aparecer como caminho feliz |

## Papéis

| Papel | Canal principal | Persona |
|---|---|---|
| `ADMIN` | Web | Ana |
| `SUPERVISOR` | Web | Marina |
| `TECHNICIAN` | Mobile | Carlos |
| Cliente somente leitura | — | Previsto (UC-20). Não há papel na API |

`ADMIN` e `SUPERVISOR` compartilham o painel. Gestão de usuários é só do administrador. Agendar, publicar modelo e acompanhar inspeção a API aceita dos dois.

## Corte: 05/11/2026 — PBIs 0001 a 0050

| Caso de uso | Papel | Canal | Situação | PBIs | Fluxo |
|---|---|---|---|---|---|
| UC-01 Autenticar | Todos | Web e mobile | Disponível | 0008, 0009, 0010 | [Jornada](jornada.md) |
| UC-02 Usuários | Administrador | Web | Disponível | 0011, 0012 | [Administrador](administrador.md) |
| UC-03 Clientes, locais, equipamentos | Administrador e supervisor | Web | Disponível | 0013–0017 | [Administrador](administrador.md) |
| UC-04 / UC-05 Modelo e publicação | Administrador e supervisor | Web | Disponível | 0018–0023 | [Supervisor](supervisor.md) |
| UC-06 Agendar e atribuir | Administrador e supervisor | Web | Disponível | 0024–0028 | [Supervisor](supervisor.md) |
| UC-15 Acompanhar | Administrador e supervisor | Web | Disponível | 0029, 0030, 0047 | [Supervisor](supervisor.md) |
| UC-07 Baixar atribuídas | Técnico | Mobile | Disponível | 0031 | [Técnico](tecnico.md) |
| UC-09 Iniciar | Técnico | Mobile | Disponível | 0033, 0034 | [Técnico](tecnico.md) |
| UC-10 Responder checklist | Técnico | Mobile | Disponível | 0035–0039 | [Técnico](tecnico.md) |
| UC-13 Concluir | Técnico | Mobile | Disponível | 0040, 0043, 0045 | [Técnico](tecnico.md) |
| UC-08 QR Code | Técnico | Mobile | Disponível | 0041 | [Técnico](tecnico.md) |
| UC-11 Evidência | Técnico | Mobile | Disponível | 0042–0044 | [Técnico](tecnico.md) |
| UC-12 Não conformidade | Técnico | Mobile | Disponível | 0046 | [Técnico](tecnico.md) |
| UC-14 Sincronizar | Técnico | Mobile e API | Parcial | 0048–0050 | [Técnico](tecnico.md) |
| UC-16 / UC-17 Revisão e decisão | Supervisor | Web | Previsto | 0056–0061 | [Supervisor](supervisor.md) |
| UC-18 / UC-19 Histórico e indicadores | Supervisor | Web | Previsto | 0063, 0073 | [Supervisor](supervisor.md) |

## Arquivos

- [Jornada entre os papéis](jornada.md) — do cadastro até a conclusão, com o estado da inspeção
- [Administrador](administrador.md) — sessão, usuários e cadastros
- [Supervisor](supervisor.md) — modelo, agendamento, acompanhamento e cancelamento
- [Técnico](tecnico.md) — lista, detalhe, checklist e conclusão
