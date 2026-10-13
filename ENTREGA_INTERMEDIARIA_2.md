# Startellite — Entrega Intermediária 2

**Entrega intermediária — 12/10/2026**  
**Apresentação final — 27/10/2026**  
**Insper Code Jr. — 2026.2**

## 1. Identificação da equipe

| Integrante | Responsabilidade atual |
|---|---|
| Wesley Lima Silva | Orbitinho no servidor, integrações seguras, homologação, CI/CD e testes |
| Guilherme Kenzo Taba Nakamura | Orbitinho na interface, conhecimento, texto, voz, acessibilidade e testes |
| Pedro Pereira | Conclusão da página pública de Espaçonaves, proposta e Design System |
| Victor Barbosa Viana | Product Owner e Scrum Master: priorização, alinhamento e aceite funcional, sem implementação |

## 2. Objetivo desta entrega

Esta entrega registra o estado do Startellite no marco intermediário do projeto. O recorte foi definido a partir da reunião com o cliente em 06/10/2026 e do registro consolidado em [`docs/IMPLEMENTADO.md`](docs/IMPLEMENTADO.md).

O cliente priorizou duas experiências:

1. uma página pública de Espaçonave que funcione como portfólio compartilhável; e
2. o Orbitinho como assistente para explicar o uso da plataforma, indicar páginas e consultar somente informações autorizadas do usuário.

No marco de 12/10, somente a primeira frente possui uma implementação parcial documentada. **Nada do Orbitinho foi implementado.** Portanto, o produto apresentado nesta etapa deve ser classificado como **protótipo parcial da página pública de Espaçonaves**, e não como o MVP completo planejado com o cliente.

## 3. Atendimento aos itens da Entrega Intermediária 2

| Item solicitado | Situação no marco | Evidência documental |
|---|---|---|
| MVP ou protótipo parcial funcional | **Parcial** | Página pública de Espaçonave implementada na `stage`; Portfólio e Tripulação sem integração; controle público/privado fora da `stage`; Orbitinho não iniciado |
| README refletindo as mudanças | **Atendido** | [`README.md`](README.md) |
| Backlog atualizado | **Atendido** | [`docs/BACKLOG_ENTREGA_FINAL.md`](docs/BACKLOG_ENTREGA_FINAL.md) |
| Funcionalidades concluídas e critérios de aceite | **Atendido documentalmente** | Seções 5 e 6 deste relatório e [`docs/FUNCIONALIDADES_E_ACEITE.md`](docs/FUNCIONALIDADES_E_ACEITE.md) |
| Feedback do cliente e alterações realizadas | **Atendido documentalmente** | Seção 7 deste relatório e [`docs/FEEDBACK_CLIENTE.md`](docs/FEEDBACK_CLIENTE.md) |

## 4. MVP apresentado no marco intermediário

### 4.1 Página pública de Espaçonaves

A página pública é o recorte demonstrável do projeto. Conforme o registro [Implementado](docs/IMPLEMENTADO.md), a implementação relatada inclui:

- rota pública `/spaceships/[slug]`, renderizada no servidor;
- capa, avatar, nome, localização, indicadores, apresentação e especialidades;
- metadados, URL canônica, OpenGraph, Twitter Card e JSON-LD;
- temas claro e escuro;
- leitura da view `public_spaceship_profiles` por chave anônima;
- tratamento uniforme com página 404 para slug inválido, Espaçonave inexistente ou privada;
- validação das URLs de avatar e banner para aceitar somente o Storage autorizado;
- componentes compartilhados do Design System;
- mock de desenvolvimento habilitado somente de forma explícita e ignorado em produção.

O protótipo permanece parcial porque:

- as abas **Portfólio** e **Tripulação** possuem interface, mas não estão integradas aos dados reais;
- o controle para tornar uma Espaçonave pública ou privada está no commit `512705e`, fora da `stage` e sem PR integrado;
- o botão **Fazer Proposta** direciona provisoriamente para `/register`;
- o ambiente Sandbox permanece bloqueado por erro da Vercel;
- ainda faltam evidências anexadas de execução em ambiente acessível e aceite funcional do Product Owner.

### 4.2 Orbitinho

**Estado: não iniciado.**

Nenhuma das funcionalidades do Orbitinho possui implementação, integração, teste ou demonstração registrada:

| Funcionalidade planejada | Estado em 12/10 |
|---|---|
| Responder dúvidas sobre o uso da plataforma | Não iniciada |
| Indicar em qual página uma tarefa deve ser realizada | Não iniciada |
| Navegação por comandos de texto | Não iniciada |
| Navegação por comandos de voz | Não iniciada |
| Consultar projetos, pedidos ou novidades do próprio usuário | Não iniciada |
| Impedir consultas sobre dados de outras pessoas | Não iniciada |
| Perguntas sugeridas na abertura | Não iniciada; item considerado bônus pelo cliente |

A existência anterior de algum mecanismo de navegação mencionada durante a reunião não foi considerada implementação desta entrega, pois não há commit, integração ou demonstração documentada.

## 5. Funcionalidades concluídas e critérios de aceite

Os estados abaixo representam o que está documentado nos relatórios da equipe. A classificação “implementada” indica presença registrada em commit ou na `stage`; o aceite funcional ainda depende de demonstração e validação do Product Owner.

| Funcionalidade | Critério de aceite | Evidência registrada | Estado |
|---|---|---|---|
| Rota pública de Espaçonave | Uma URL com slug válido renderiza o perfil no servidor; slug inválido, inexistente ou privado retorna 404 sem expor dados | Commit `e0974a9` | Implementada na `stage` |
| Campos públicos `is_public` e `slug` | Slug é válido, único e estável; os campos existem sem abrir as tabelas internas ao visitante | Commit `f6edeac` | Implementada na `stage` |
| View pública segura | Acesso anônimo recebe somente os campos permitidos; dados internos e pessoais ficam fora da resposta | Commit `eeb58da`; resposta 200 com lista vazia registrada | Implementada na `stage` |
| Conteúdo e identidade visual do perfil | A página apresenta capa, avatar, nome, localização, indicadores, descrição e especialidades de forma responsiva | Commits `e0974a9`, `005c7ba` e `ba9dad7`; merge `7c08c06` | Implementada na `stage` |
| Segurança de imagens e metadados | Imagens externas ao Storage autorizado são rejeitadas; JSON-LD não permite fechamento indevido da tag de script | [Implementado](docs/IMPLEMENTADO.md) | Relatada como implementada |
| Componentes do Design System usados na página | Página utiliza componentes compartilhados; abas podem ser operadas pelo teclado; temas usam tokens | Commit `610e9b9` | Implementada parcialmente |
| CI dividida em verificações | PR para `stage` executa lint, typecheck, testes e build em jobs separados | [Implementado](docs/IMPLEMENTADO.md); link da execução ainda não anexado | Relatada como implementada |
| Mock local seguro | Execução local funciona sem credenciais de produção e o mock não é habilitado em produção | [Implementado](docs/IMPLEMENTADO.md) | Relatada como implementada |
| Testes da superfície pública | Testes cobrem perfis público, privado, inexistente, slug inválido, campos proibidos, anonimização e imagens | [Implementado](docs/IMPLEMENTADO.md) registra 36 testes aprovados | Relatada como implementada |

## 6. Funcionalidades parciais ou não aceitas

| Funcionalidade | Situação | Condição necessária para conclusão |
|---|---|---|
| Controle público/privado | Implementado no commit `512705e`, mas fora da `stage` | Abrir PR, integrar à `stage`, executar testes e validar com um comandante e um usuário sem permissão |
| Portfólio | Interface pronta, sem integração | Exibir projetos e missões autorizados, anonimizar clientes quando necessário e tratar carregamento, vazio e erro |
| Tripulação | Interface pronta, sem integração | Exibir somente integrantes com consentimento e tratar estados de carregamento, vazio e erro |
| Fazer Proposta | Botão provisório para `/register` | Implementar o fluxo real ou registrar a limitação no escopo final |
| Sandbox | Deploy bloqueado por `User not found (404)` | Corrigir token, organização ou projeto na Vercel e registrar uma execução bem-sucedida |
| Lint completo | Somente lint direcionado foi relatado como aprovado | Registrar o resultado do job completo na CI |
| Aceite funcional | Não registrado | Demonstrar os fluxos, anexar evidências e registrar nome, data e resultado da validação de Victor |
| Orbitinho | Nada implementado | Executar os itens do backlog final destinados ao assistente |

## 7. Feedback do cliente e efeito no projeto

O feedback foi coletado na reunião de 06/10/2026 com Pedro Antonio Silva e Victor Barbosa Viana. A transcrição local foi usada como fonte, com os pontos abaixo registrados por paráfrase.

| Feedback do cliente | Alteração no projeto | Resultado até o marco |
|---|---|---|
| O Orbitinho deve explicar como usar a plataforma e indicar a página correta para cada tarefa | A frente foi priorizada e dividida em conhecimento, interface, navegação e autorização | Nenhuma implementação realizada |
| Navegação por texto e voz deve reaproveitar o mecanismo já existente, se viável | Texto e voz receberam critérios separados no backlog | Nenhuma integração realizada |
| Consultas pessoais não podem mostrar projetos ou informações de terceiros | Autenticação e autorização no servidor foram incluídas nos critérios e no backlog | Regra ainda não implementada no Orbitinho |
| A página pública deve funcionar como portfólio compartilhável, com capa, perfil, descrição e trabalhos | A página pública por slug, seu perfil e sua identidade visual foram implementados | Página parcial; Portfólio e Tripulação ainda sem dados integrados |
| A identidade visual deve usar linguagem escura, azul e espacial | A página passou a usar temas, tokens e componentes compartilhados | Implementação registrada; validação visual do cliente ainda pendente |
| Problemas de acesso, convites e permissões estavam bloqueando o trabalho | Acessos e dependências externas foram tratados como bloqueios prioritários | Resolução não confirmada; Sandbox ainda bloqueado |

## 8. Backlog atualizado para a entrega final

O backlog completo está em [`docs/BACKLOG_ENTREGA_FINAL.md`](docs/BACKLOG_ENTREGA_FINAL.md). Ele reúne todo o trabalho restante entre a entrega intermediária de 12/10 e a apresentação final de 27/10/2026.

### Wesley — Orbitinho, homologação, CI/CD e testes

- reconstruir homologação, seed, Storage e policies sem dados de produção;
- consolidar CI/CD, preview, testes unitários, integração e pgTAP;
- implementar consultas, ações, autorização e confirmação no servidor do Orbitinho;
- implementar o recorte aprovado de assistência por IDE;
- proteger custos, logs, telemetria e dados sensíveis;
- concluir a documentação técnica e as evidências dessas frentes.

### Guilherme — Orbitinho, experiência e testes

- mapear arquitetura, intents, rotas e fontes do Orbitinho;
- preparar base de conhecimento e avaliação;
- implementar interface, dúvidas e navegação por texto;
- implementar voz em desktop e mobile suportados;
- concluir a experiência hands-free, acessibilidade e personalidade;
- integrar a experiência dos clientes de IDE;
- automatizar a matriz de testes e produzir evidências.

### Pedro — Espaçonaves e Design System

- validar e integrar a rota pública, campos, view e controle de visibilidade;
- concluir cabeçalho, Portfólio e Tripulação;
- implementar o fluxo completo de proposta;
- concluir sitemap, SEO e performance da página;
- finalizar componentes, tokens e Storybook/equivalente;
- estabilizar responsividade, acessibilidade e evidências de Espaçonaves.

Pedro concentra integralmente a conclusão das frentes de Espaçonaves e Design System; Wesley e Guilherme concentram Orbitinho e as fundações de qualidade.

### Coordenação de Victor

- fechar com o cliente as decisões de conteúdo, consentimento e proposta;
- manter o backlog e os aceites atualizados;
- congelar o escopo e conduzir o aceite final;
- consolidar backlog, documentação, evidências e apresentação.

## 9. Próximos passos prioritários

1. Integrar o controle público/privado à `stage`.
2. Conectar Portfólio e Tripulação somente a dados autorizados.
3. Implementar do zero o recorte mínimo do Orbitinho, começando por respostas de uso e navegação por texto.
4. Aplicar autenticação e autorização no servidor às consultas pessoais do Orbitinho.
5. Resolver a publicação do Sandbox ou fornecer execução local reproduzível.
6. Executar CI, regressão e testes das rotas e ações críticas.
7. Anexar PRs, commits, capturas, URL ou instruções de execução.
8. Registrar o aceite funcional do Product Owner e as validações do cliente.

## 10. Conclusão

A equipe chegou ao marco intermediário com uma base parcial da página pública de Espaçonaves, incluindo rota, perfil, contrato público de dados, proteções de acesso e parte do Design System. CI, mocks e testes também foram relatados, embora ainda faltem links de execução e uma demonstração reproduzível.

O Orbitinho não teve nenhuma implementação até este marco. Portfólio e Tripulação permanecem somente na interface, o controle público/privado aguarda integração e o Sandbox continua bloqueado. Assim, a entrega representa **um protótipo parcial funcional da frente de Espaçonaves**, acompanhado de um backlog replanejado para concluir as integrações, iniciar o Orbitinho e preparar a entrega final.

## 11. Documentos de apoio

- [`README.md`](README.md)
- [`docs/MVP_E_DEMONSTRACAO.md`](docs/MVP_E_DEMONSTRACAO.md)
- [`docs/FUNCIONALIDADES_E_ACEITE.md`](docs/FUNCIONALIDADES_E_ACEITE.md)
- [`docs/FEEDBACK_CLIENTE.md`](docs/FEEDBACK_CLIENTE.md)
- [`docs/BACKLOG_ENTREGA_FINAL.md`](docs/BACKLOG_ENTREGA_FINAL.md)
- [`docs/IMPLEMENTADO.md`](docs/IMPLEMENTADO.md)

