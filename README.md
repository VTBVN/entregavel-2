# Startellite — Entrega intermediária 2

**Entrega intermediária: 12/10/2026 · Apresentação final: 27/10/2026 · Insper Code Jr. · semestre 2026.2**

Este repositório reúne a documentação e as evidências da segunda entrega do case Startellite. O [material didático da Insper Code Jr.](https://inspercodejr.github.io/material-didatico-26-2/reunioes/#1110-entrega-intermediaria-2-marco-da-metade-do-projeto) pede:

1. MVP ou protótipo parcial funcional;
2. README refletindo as mudanças no projeto;
3. backlog atualizado;
4. funcionalidades concluídas com seus critérios de aceite;
5. registro do feedback do cliente e das alterações realizadas a partir dele.

## Situação documentada

Os arquivos disponíveis da Entrega 1 e a reunião com Pedro Antonio Silva em 06/10/2026 documentam prioridades e decisões de escopo. O documento [Implementado](docs/IMPLEMENTADO.md) consolida os registros de CI, Sandbox, mocks, testes, documentação, segurança, página pública, campos, view, Design System e controle de visibilidade, sem atribuição individual. Esses itens permanecem **a validar** no backlog final até que branch ou PR, checks e demonstração estejam disponíveis. As abas Portfólio e Tripulação foram criadas, mas ainda não possuem integração.

| Item exigido | Documento ou evidência | Situação |
|---|---|---|
| MVP/protótipo parcial funcional | [Implementado versus faltante no MVP](docs/MVP_E_DEMONSTRACAO.md) | Espaçonave parcial; Orbitinho faltante |
| README atualizado | Este arquivo | Preparado para a Entrega 2 |
| Backlog da Entrega 2 | [Backlog intermediário](docs/BACKLOG_ENTREGAVEL_2.md) | Histórico do marco intermediário |
| Backlog da entrega final | [Backlog final replanejado](docs/BACKLOG_ENTREGA_FINAL.md) | Wesley e Guilherme em Orbitinho/qualidade; Pedro em Espaçonaves/Design System |
| Funcionalidades e critérios de aceite | [Aceite funcional](docs/FUNCIONALIDADES_E_ACEITE.md) | Implementações registradas; Portfólio e Tripulação parciais |
| Feedback e alterações | [Feedback do cliente](docs/FEEDBACK_CLIENTE.md) | Reunião de 06/10 registrada |
| Implementado | [Registro consolidado](docs/IMPLEMENTADO.md) | Implementações relatadas; validação técnica e integrações pendentes |

## Projeto e recorte para 12/10

A Startellite conecta profissionais de desenvolvimento (“Satélites”) a projetos e missões. A Entrega 1 organizou cinco frentes: homologação, página pública de Espaçonaves, testes e CI, componentes visuais e Orbitinho. Na reunião de 06/10, o cliente pediu foco imediato em:

- **Orbitinho:** orientar o uso da plataforma com respostas corretas, indicar onde realizar tarefas e, se viável, aproveitar a navegação já existente por texto e voz;
- **Página pública de Espaçonave:** primeiro recorte visual de portfólio com capa, perfil, descrição e projetos/missões, em tema escuro com azul e elementos de constelação;
- **Acessos:** resolver permissões de quadros, épicos e convites para que a equipe consiga executar e atualizar o trabalho.

Consultas do Orbitinho sobre projetos ou pedidos de uma pessoa devem depender de autenticação e autorização. A página pública precisa de seleção explícita de dados e consentimento antes de expor nomes ou clientes. Esses cuidados constam no [backlog](docs/BACKLOG_ENTREGAVEL_2.md) e nos [critérios de aceite](docs/FUNCIONALIDADES_E_ACEITE.md).

## O que mudou desde a Entrega 1

O plano anterior distribuía entregas de homologação, CI, página pública e Orbitinho entre as sprints. A reunião de 06/10 registrou perda de tempo por problemas de acesso e recesso. Para o marco de 12/10, o backlog passa a destacar as duas experiências que o cliente quer ver na demonstração e os bloqueios que impedem validá-las. A distinção entre **proposto**, **implementado** e **aceito** é mantida nos documentos.

## Responsabilidades atuais

A equipe técnica da entrega final é formada por Wesley Lima Silva, Guilherme Kenzo Taba Nakamura e Pedro Pereira. Wesley e Guilherme concentram o Orbitinho, homologação, CI/CD e testes: Wesley atua principalmente no servidor, integrações e segurança; Guilherme, na interface, conhecimento, texto, voz e acessibilidade. Pedro concentra a conclusão da página pública de Espaçonaves, do fluxo de proposta e do Design System. A distribuição completa e sua rastreabilidade com o PDF estão no [backlog da entrega final](docs/BACKLOG_ENTREGA_FINAL.md).

Victor Barbosa Viana permanece como Product Owner e Scrum Master, responsável por priorização, alinhamento, facilitação e aceite funcional, sem implementação. 




## Fontes

- Reunião com Pedro Antonio Silva e Victor Barbosa Viana em 06/10/2026. A transcrição bruta não foi copiada para este repositório por conter dados de reunião.
- Documentos da Entrega
- [Implementado](docs/IMPLEMENTADO.md), registro consolidado das implementações relatadas, sem atribuição individual.
- [Orientações oficiais de entregáveis da Insper Code Jr.](https://inspercodejr.github.io/material-didatico-26-2/reunioes/#1110-entrega-intermediaria-2-marco-da-metade-do-projeto).
