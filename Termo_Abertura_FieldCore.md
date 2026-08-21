# Termo de Abertura de Projeto — Field Core

**Desenvolvimento e implantação da plataforma FieldCore — Sistema de Inspeção Técnica em Campo**

---

## Objetivo geral e objetivos específicos

Desenvolver e disponibilizar a plataforma FieldCore, capaz de planejar, executar, sincronizar, revisar e auditar inspeções técnicas em campo, com operação offline nativa.

Como metas intermediárias, têm-se:

- Definição e publicação de modelos de inspeção versionados;
- Construção integrada do app mobile, da interface administrativa web e da API REST;
- Validação da sincronização offline sem duplicidade de dados;
- Realização de testes que garantam a consistência das informações entre os três componentes da solução.

## Justificativa do projeto (benefícios)

Atualmente, as inspeções de campo dependem de formulários impressos, planilhas isoladas e fotografias sem identificação, gerando retrabalho, perda de dados e baixa rastreabilidade. A plataforma FieldCore substituirá esse processo fragmentado por um fluxo digital único, conectando planejamento, execução e revisão.

Isto resultará em:

- Maior padronização das inspeções;
- Redução do retrabalho e do tempo entre a execução em campo e a disponibilidade do resultado;
- Facilidade na identificação e acompanhamento de não conformidades;
- Auditoria de todo o processo.

## Premissas

- O Android será a plataforma mobile prioritária da primeira versão;
- O sistema será utilizado inicialmente por uma organização operadora que presta inspeções para vários clientes;
- Cada inspeção terá um único técnico responsável no MVP;
- As inspeções serão baseadas em modelos previamente configurados;
- O aplicativo deverá preservar dados não sincronizados mesmo após ser fechado.

## Breve descrição do projeto

Desenvolvimento de uma plataforma composta por três aplicações integradas:

- **Aplicativo mobile** (Expo/React Native)
- **Interface administrativa web** (Angular)
- **API REST** (Java/Spring Boot)

Que permitem planejar, executar e revisar inspeções técnicas em campo, inclusive em locais sem conectividade com a internet, com sincronização confiável e idempotente ao retorno da conexão.

## Patrocinador (sponsor)

Coordenação acadêmica das disciplinas integradoras (Mobile, Web, Governança de TI e CiberSegurança).

## Estimativa de investimentos

Não há investimento financeiro direto — projeto acadêmico. O principal investimento é a carga horária das disciplinas integradoras (80 aulas de 50 minutos ao longo de 16 semanas) e o esforço da equipe nas atividades de desenvolvimento.

## Estimativa de prazo

16 semanas efetivas de aula, organizadas em 8 sprints de 2 semanas, conforme o roadmap do projeto, com marco final de apresentação e defesa técnica ao término do período.

## Fatores Críticos de Sucesso (FCS)

1. Equipe dedicada, com papéis definidos nas três frentes do produto (mobile, interface administrativa web e API);
2. Após a definição do escopo do MVP, somente o sponsor poderá alterá-lo, com as devidas revisões de cronograma e prazo;
3. Cumprimento dos marcos obrigatórios (M1 a M8) definidos no roadmap de 16 semanas;
4. Contrato de API definido e documentado antes da integração entre os três componentes, viabilizando o uso de mocks pelas equipes de mobile e web enquanto o backend está em desenvolvimento;
5. Comunicação constante entre as disciplinas de Expo, Spring Boot e Interface Web para manter o contrato de dados sincronizado.

## Principais riscos

1. Atraso no cronograma de 16 semanas, comprometendo a demonstração do fluxo offline e de sincronização;
2. Inconsistência do contrato de API entre mobile, web e backend, gerando retrabalho de integração;
3. Perda ou duplicidade de dados durante a sincronização offline, caso a idempotência das operações não seja implementada corretamente.

## Restrições

O projeto deverá ser concluído dentro do calendário de 16 semanas efetivas de aula, mesmo que o calendário institucional possua 20 semanas — as semanas adicionais (avaliações, feriados, eventos institucionais) não poderão ser utilizadas como dependência para a conclusão do MVP.

## Interessados no projeto (stakeholders)

- Equipe de desenvolvimento (mobile, web administrativa e API);
- Corpo docente das disciplinas integradoras;
- Técnicos de campo e supervisores (usuários finais representados pelas personas Carlos e Marina);
- Administradores do sistema (persona Ana);
- Avaliadores acadêmicos do projeto.

## Comitê Executivo

Professores responsáveis pelas disciplinas de Expo, Spring Boot e Interface Web administrativa (avaliação integrada do produto).

## Gerente do Projeto

A definir pela equipe (revezamento por sprint) — integrantes:

- Giovana Rafaela
- Gustavo Sousa
- Juliana Nascimento
- Maria Eduarda
- Milenna Portella

---

## Aprovações

| | Nome | Data | Assinatura |
|---|---|---|---|
| **Elaborado por** | Juliana Fernandes do Nascimento | 14/08/2026 | Juliana Nascimento |
| **Aprovado por** | | ___/___/___ | |
