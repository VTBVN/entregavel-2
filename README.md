# Startellite — Entrega intermediária 2

**Marco de 12/10/2026 · Insper Code Jr. · semestre 2026.2**

Este repositório reúne a documentação e as evidências da segunda entrega do case Startellite. O [material didático da Insper Code Jr.](https://inspercodejr.github.io/material-didatico-26-2/reunioes/#1110-entrega-intermediaria-2-marco-da-metade-do-projeto) pede:

1. MVP ou protótipo parcial funcional;
2. README refletindo as mudanças no projeto;
3. backlog atualizado;
4. funcionalidades concluídas com seus critérios de aceite;
5. registro do feedback do cliente e das alterações realizadas a partir dele.

## Situação documentada

Os arquivos disponíveis da Entrega 1 e a reunião com Pedro Antonio Silva em 06/10/2026 comprovam prioridades e decisões de escopo. O relatório entregue por Wesley documenta alterações em CI, Sandbox, mocks, testes, documentação e segurança. O changelog de Guilherme registra a implementação da página pública, campos, view, Design System e controle de visibilidade. As abas Portfólio e Tripulação foram criadas, mas ainda não possuem integração.

| Item exigido | Documento ou evidência | Situação |
|---|---|---|
| MVP/protótipo parcial funcional | [Implementado versus faltante no MVP](docs/MVP_E_DEMONSTRACAO.md) | Espaçonave parcial; Orbitinho faltante |
| README atualizado | Este arquivo | Preparado para a Entrega 2 |
| Backlog da Entrega 2 | [Backlog intermediário](docs/BACKLOG_ENTREGAVEL_2.md) | Histórico do marco intermediário |
| Backlog da entrega final | [Backlog final replanejado](docs/BACKLOG_ENTREGA_FINAL.md) | Wesley e Guilherme com maior carga; Pedro em revisão e Orbitinho |
| Funcionalidades e critérios de aceite | [Aceite funcional](docs/FUNCIONALIDADES_E_ACEITE.md) | Implementações registradas; Portfólio e Tripulação parciais |
| Feedback e alterações | [Feedback do cliente](docs/FEEDBACK_CLIENTE.md) | Reunião de 06/10 registrada |
| Modificações de Wesley | [Relatório de modificações](docs/RELATORIO_MODIFICACOES_WESLEY.md) | Alterações relatadas; links técnicos pendentes |
| Modificações de Guilherme | [Changelog](docs/CHANGELOG_GUILHERME.md) | Página pública implementada; abas ainda sem integração |

## Projeto e recorte para 11/10

A Startellite conecta profissionais de desenvolvimento (“Satélites”) a projetos e missões. A Entrega 1 organizou cinco frentes: homologação, página pública de Espaçonaves, testes e CI, componentes visuais e Orbitinho. Na reunião de 06/10, o cliente pediu foco imediato em:

- **Orbitinho:** orientar o uso da plataforma com respostas corretas, indicar onde realizar tarefas e, se viável, aproveitar a navegação já existente por texto e voz;
- **Página pública de Espaçonave:** primeiro recorte visual de portfólio com capa, perfil, descrição e projetos/missões, em tema escuro com azul e elementos de constelação;
- **Acessos:** resolver permissões de quadros, épicos e convites para que a equipe consiga executar e atualizar o trabalho.

Consultas do Orbitinho sobre projetos ou pedidos de uma pessoa devem depender de autenticação e autorização. A página pública precisa de seleção explícita de dados e consentimento antes de expor nomes ou clientes. Esses cuidados constam no [backlog](docs/BACKLOG_ENTREGAVEL_2.md) e nos [critérios de aceite](docs/FUNCIONALIDADES_E_ACEITE.md).

## O que mudou desde a Entrega 1

O plano anterior distribuía entregas de homologação, CI, página pública e Orbitinho entre as sprints. A reunião de 06/10 registrou perda de tempo por problemas de acesso e recesso. Para o marco de 11/10, o backlog passa a destacar as duas experiências que o cliente quer ver na demonstração e os bloqueios que impedem validá-las. A distinção entre **proposto**, **implementado** e **aceito** é mantida nos documentos.

## Responsabilidades atuais

A equipe técnica da entrega final é formada por Wesley Lima Silva, Guilherme Kenzo Taba Nakamura e Pedro Pereira. Wesley concentra homologação, CI, backend, segurança, testes e deploy. Guilherme concentra Espaçonaves, proposta, frontend do Orbitinho, Design System e experiência. Pedro retorna com menos tarefas, voltadas à arquitetura e ao conhecimento do Orbitinho, revisão de segurança e revisão do legado. A distribuição completa está no [backlog da entrega final](docs/BACKLOG_ENTREGA_FINAL.md).

Victor Barbosa Viana permanece como Product Owner e Scrum Master, responsável por priorização, alinhamento, facilitação e aceite funcional, sem implementação. Thiago Brasileiro de Sousa permanece sem atribuição no backlog atual.

## Como completar as evidências

Antes da apresentação, a equipe deve adicionar links de PRs, commits ou ambiente de demonstração em [MVP e demonstração](docs/MVP_E_DEMONSTRACAO.md), atualizar o status de cada item no [backlog](docs/BACKLOG_ENTREGAVEL_2.md) e registrar o resultado de cada critério em [aceite funcional](docs/FUNCIONALIDADES_E_ACEITE.md). Use capturas sem dados pessoais ou segredos. Não marque “concluído” apenas porque o código existe: registre a reprodução e a validação funcional.

## Fontes

- Reunião com Pedro Antonio Silva e Victor Barbosa Viana em 06/10/2026, transcrita localmente em `consulta_startellite/startellite.txt`. A transcrição bruta não foi copiada para este repositório por conter dados de reunião.
- Documentos da Entrega 1 em `consulta_startellite/docs/`, especialmente `REQUISITOS.md`, `BACKLOG.md`, `ALINHAMENTO_CLIENTE.md` e `DEFINITION_OF_DONE.md`.
- [Relatório de modificações de Wesley](docs/RELATORIO_MODIFICACOES_WESLEY.md), copiado do arquivo fornecido pela equipe.
- [Changelog de Guilherme](docs/CHANGELOG_GUILHERME.md), consolidado a partir do arquivo fornecido pela equipe.
- [Orientações oficiais de entregáveis da Insper Code Jr.](https://inspercodejr.github.io/material-didatico-26-2/reunioes/#1110-entrega-intermediaria-2-marco-da-metade-do-projeto).
