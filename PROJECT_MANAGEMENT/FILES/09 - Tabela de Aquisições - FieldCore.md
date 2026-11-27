# Tabela de Aquisições

Planejamento de recursos, serviços e possíveis compras do FieldCore. Nenhuma aquisição paga é autorizada por este documento; o sponsor deve aprovar previamente.

| ID | Item | Motivo | Urgência | Fornecedor possível | Tipo | Quantidade | Custo unitário (R$) | Custo total (R$) | Responsável | Situação/critério |
|---|---|---|---|---|---|---:|---:|---:|---|---|
| A-01 | GitHub (organização e Actions) | Código, issues e CI | Alta | GitHub (plano gratuito/educacional) | Serviço | 1 organização | 0,00 | 0,00 | GP | Em uso; manter acessos mínimos |
| A-02 | Notion | Backlog e especificação | Alta | Notion (plano educacional) | Serviço | 1 workspace | 0,00 | 0,00 | PO | Em uso; fonte dos requisitos |
| A-03 | Hospedagem DEV | API e demonstração | Alta | Ambiente acadêmico de nuvem | Serviço | 4 meses | 0,00 | 0,00 | DevOps | Em uso pelo deploy de desenvolvimento |
| A-04 | PostgreSQL | Persistência da API | Alta | Ambiente DEV (profile `postgres`) | Serviço | 4 meses | 0,00 | 0,00 | DevOps | Backup e acesso controlado |
| A-05 | Armazenamento de evidências | Fotos de inspeção | Média | Ambiente DEV/S3 compatível | Serviço | 20 GB | 0,00 | 0,00 | DevOps | Validar limite e segurança |
| A-06 | Domínio | URL de demonstração externa | Baixa | Registrador nacional (Registro.br) | Serviço | 1 unidade | 60,00 | 60,00 | DevOps | Opcional; aprovar antes de comprar |
| A-07 | Certificado TLS | Tráfego HTTPS | Baixa | Let's Encrypt | Serviço | 1 unidade | 0,00 | 0,00 | DevOps | Aplicável se usar domínio |
| A-08 | Smartphones Android | Testes de app e câmera | Média | Empréstimo da equipe/instituição ou varejo | Bem | 2 unidades | 900,00 | 1.800,00 | Dev Mobile | Preferir empréstimo; comprar só se faltar dispositivo |
| A-09 | Etiquetas QR | Identificar ativos no piloto | Baixa | Gráfica ou papelaria local | Material | 100 unidades | 0,50 | 50,00 | PO | Comprar somente para piloto presencial |
| A-10 | Dados móveis | Teste em área de baixa conexão | Baixa | Operadora de telefonia móvel (pré-pago) | Serviço | 2 chips | 30,00 | 60,00 | Dev Mobile | Opcional |
| **Total** | | | | | | | | **1.970,00** | | Todos os itens pagos são opcionais |

Urgência: **alta** quando o item é necessário desde o início do desenvolvimento; **média** quando é necessário antes dos testes de campo; **baixa** quando só se aplica a um piloto externo.

## Processo

1. Responsável confirma necessidade, alternativa gratuita e valor.
2. GP valida impacto no orçamento e risco.
3. Sponsor aprova compras pagas antes do pedido.
4. GP registra aquisição realizada, comprovante e aceite no acompanhamento semanal.

## Situação em 27/11/2026

Não há registro de aquisição paga no repositório. Os recursos em uso (A-01 a A-04) vêm de planos gratuitos, educacionais ou do ambiente acadêmico, sem contrato pago a encerrar. Os itens opcionais (A-06 a A-10) não foram acionados.
