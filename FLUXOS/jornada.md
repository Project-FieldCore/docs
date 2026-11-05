# Jornada entre os papéis

Como uma inspeção atravessa administrador, supervisor e técnico com o que está entregue até o PBI-0040.
Corte: 05/11/2026, até o PBI-0050. Atualizar quando um PBI mudar estado, canal ou ator.

O equipamento escolhido no agendamento fica registrado na tela. A API de agendamento ainda não recebe `equipmentId` (PBI-0026).

```mermaid
flowchart TD
  subgraph admin [Administrador - web]
    A1[Entra com e-mail e senha] --> A2[Cadastra usuarios ativos]
    A2 --> A3[Cadastra cliente, local e equipamento]
  end

  subgraph sup [Supervisor - web]
    S1[Cria modelo em rascunho] --> S2[Monta secoes e itens]
    S2 --> S3[Confere a previa]
    S3 --> S4[Publica versao imutavel]
    S4 --> S5[Agenda a partir da versao publicada]
    S5 --> S6[Escolhe cliente, local e equipamento compativel]
    S6 --> S7[Atribui tecnico ativo, prazo, prioridade e instrucoes]
    S7 --> S8[Acompanha a lista filtrada]
    S8 --> S9[Cancela com justificativa, se ainda couber]
  end

  subgraph tec [Tecnico - mobile]
    T1[Entra e baixa as inspecoes atribuidas] --> T2[Filtra por estado, data e prioridade]
    T2 --> T3[Le o detalhe antes de comecar]
    T3 --> T4[Inicia e registra o horario]
    T4 --> T5[Responde o checklist do snapshot]
    T5 --> T6[Salva cada resposta no aparelho]
    T6 --> T7[Ve progresso e pendencias]
    T7 --> T8[Conclui se as regras do item passaram]
  end

  A3 --> S1
  S7 --> T1
  T8 --> S8
```

## Estado da inspeção hoje

Estados que a API já grava. Revisão, aprovação e reprovação existem no modelo, mas o fluxo do supervisor que os aciona ainda é PBI-0056 em diante.

```mermaid
stateDiagram-v2
  [*] --> ATRIBUIDA: agendar com versao publicada
  ATRIBUIDA --> EM_ANDAMENTO: tecnico inicia
  EM_ANDAMENTO --> ENVIADA: tecnico conclui com as regras ok
  ATRIBUIDA --> CANCELADA: supervisor cancela com justificativa
  EM_ANDAMENTO --> CANCELADA: supervisor cancela com justificativa
  ENVIADA --> EM_REVISAO: previsto UC-16
  EM_REVISAO --> APROVADA: previsto UC-17
  EM_REVISAO --> REPROVADA: previsto UC-17
  APROVADA --> [*]: nao cancela pelo fluxo comum
  CANCELADA --> [*]
```

## O que esta jornada ainda não desenha

| Depois de | Entra quando |
|---|---|
| Conclusão enviada | UC-14 sincronizar fila offline (PBI-0048 a 0055) |
| Inspeção enviada | UC-16 revisar e UC-17 aprovar ou reprovar (PBI-0056 a 0061) |
| Reprovação | Técnico recebe a correção no mobile (PBI-0062) |
