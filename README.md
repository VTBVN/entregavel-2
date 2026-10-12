# Startellite — Entrega intermediária 2

**Marco de 11/10/2026 · Insper Code Jr. · semestre 2026.2**

Este repositório reúne a documentação e as evidências da segunda entrega do case Startellite. O [material didático da Insper Code Jr.](https://inspercodejr.github.io/material-didatico-26-2/reunioes/#1110-entrega-intermediaria-2-marco-da-metade-do-projeto) pede:

1. MVP ou protótipo parcial funcional;
2. README refletindo as mudanças no projeto;
3. backlog atualizado;
4. funcionalidades concluídas com seus critérios de aceite;
5. registro do feedback do cliente e das alterações realizadas a partir dele.

## Situação documentada

Os arquivos disponíveis da Entrega 1 e a reunião com Pedro Antonio Silva em 06/10/2026 comprovam **prioridades e decisões de escopo**, mas não comprovam que as funcionalidades foram implementadas ou aceitas. Por isso, o status técnico permanece **a confirmar com a equipe**. Este repositório não contém código do produto e não atribui conclusão sem evidência.

| Item exigido | Documento ou evidência | Situação |
|---|---|---|
| MVP/protótipo parcial funcional | [MVP e roteiro de demonstração](docs/MVP_E_DEMONSTRACAO.md) | Evidência técnica pendente |
| README atualizado | Este arquivo | Preparado para a Entrega 2 |
| Backlog atualizado | [Backlog da Entrega 2](docs/BACKLOG_ENTREGAVEL_2.md) | Priorizado; progresso a confirmar |
| Funcionalidades e critérios de aceite | [Aceite funcional](docs/FUNCIONALIDADES_E_ACEITE.md) | Critérios definidos; conclusão a confirmar |
| Feedback e alterações | [Feedback do cliente](docs/FEEDBACK_CLIENTE.md) | Reunião de 06/10 registrada |

## Projeto e recorte para 11/10

A Startellite conecta profissionais de desenvolvimento (“Satélites”) a projetos e missões. A Entrega 1 organizou cinco frentes: homologação, página pública de Espaçonaves, testes e CI, componentes visuais e Orbitinho. Na reunião de 06/10, o cliente pediu foco imediato em:

- **Orbitinho:** orientar o uso da plataforma com respostas corretas, indicar onde realizar tarefas e, se viável, aproveitar a navegação já existente por texto e voz;
- **Página pública de Espaçonave:** primeiro recorte visual de portfólio com capa, perfil, descrição e projetos/missões, em tema escuro com azul e elementos de constelação;
- **Acessos:** resolver permissões de quadros, épicos e convites para que a equipe consiga executar e atualizar o trabalho.

Consultas do Orbitinho sobre projetos ou pedidos de uma pessoa devem depender de autenticação e autorização. A página pública precisa de seleção explícita de dados e consentimento antes de expor nomes ou clientes. Esses cuidados constam no [backlog](docs/BACKLOG_ENTREGAVEL_2.md) e nos [critérios de aceite](docs/FUNCIONALIDADES_E_ACEITE.md).

## O que mudou desde a Entrega 1

O plano anterior distribuía entregas de homologação, CI, página pública e Orbitinho entre as sprints. A reunião de 06/10 registrou perda de tempo por problemas de acesso e recesso. Para o marco de 11/10, o backlog passa a destacar as duas experiências que o cliente quer ver na demonstração e os bloqueios que impedem validá-las. A distinção entre **proposto**, **implementado** e **aceito** é mantida nos documentos.

## Responsabilidades

Victor Barbosa Viana atua como Product Owner e Scrum Master, responsável por priorização, alinhamento, facilitação e aceite funcional. A implementação e revisão técnica ficam com os integrantes designados no backlog: Pedro Pereira, Wesley Lima Silva, Guilherme Kenzo Taba Nakamura e Thiago Brasileiro de Sousa. A atribuição operacional e o andamento ainda devem ser confirmados no quadro da equipe.

## Como completar as evidências

Antes da apresentação, a equipe deve adicionar links de PRs, commits ou ambiente de demonstração em [MVP e demonstração](docs/MVP_E_DEMONSTRACAO.md), atualizar o status de cada item no [backlog](docs/BACKLOG_ENTREGAVEL_2.md) e registrar o resultado de cada critério em [aceite funcional](docs/FUNCIONALIDADES_E_ACEITE.md). Use capturas sem dados pessoais ou segredos. Não marque “concluído” apenas porque o código existe: registre a reprodução e a validação funcional.

## Fontes

- Reunião com Pedro Antonio Silva e Victor Barbosa Viana em 06/10/2026, transcrita localmente em `consulta_startellite/startellite.txt`. A transcrição bruta não foi copiada para este repositório por conter dados de reunião.
- Documentos da Entrega 1 em `consulta_startellite/docs/`, especialmente `REQUISITOS.md`, `BACKLOG.md`, `ALINHAMENTO_CLIENTE.md` e `DEFINITION_OF_DONE.md`.
- [Orientações oficiais de entregáveis da Insper Code Jr.](https://inspercodejr.github.io/material-didatico-26-2/reunioes/#1110-entrega-intermediaria-2-marco-da-metade-do-projeto).
