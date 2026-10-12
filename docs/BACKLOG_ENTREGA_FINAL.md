# Backlog replanejado — Entrega final

**Período:** 12–29/10/2026.

**Apresentação prevista:** 30/10/2026.

**Base:** backlog e requisitos da Entrega 1, reunião com o cliente em 06/10, relatório de Wesley e changelog de Guilherme.

Este backlog contém somente o trabalho que ainda falta para a entrega final. A rota pública, os campos e a view de Espaçonaves, o layout inicial, parte do Design System, a estrutura de CI, mocks e testes já relatados formam a base existente e não foram recriados como tarefas.

## Equipe e distribuição

| Pessoa | Papel neste backlog | Quantidade de itens técnicos principais |
|---|---|---:|
| Wesley Lima Silva | Homologação, backend, segurança, testes, CI e deploy | 10 |
| Guilherme Kenzo Taba Nakamura | Espaçonaves, proposta, frontend do Orbitinho, Design System e experiência | 10 |
| Pedro Pereira | Arquitetura do Orbitinho, conhecimento, revisão de segurança e revisão do legado | 4 |
| Victor Barbosa Viana | Produto, alinhamento, aceite e artefatos da apresentação | 6 itens de coordenação |

Pedro possui menos tarefas que Wesley e Guilherme. Seus itens têm foco em decisões técnicas e revisão transversal. Victor continua sem responsabilidade de implementação ou revisão de código.

## Convenções

- **P0:** obrigatório para fechar o produto ou um artefato da entrega final.
- **P1:** necessário para qualidade, continuidade e apresentação segura.
- **P2:** melhoria que pode ser registrada como trabalho futuro se o P0 estiver atendido.
- **Size:** esforço relativo na sequência Fibonacci, conforme o backlog da Entrega 1.
- **S6:** 12–18/10; **S7:** 19–25/10; **S8:** 26–29/10.
- Todos os itens começam em **A fazer**, exceto bloqueios já comprovados.

## Wesley — 10 itens

| ID | Sprint | Pri. | Size | Entrega | Critério de conclusão | Dependências | Status |
|---|---:|---:|---:|---|---|---|---|
| EF-W01 | S6 | P0 | 3 | Desbloquear o deploy do Sandbox na Vercel | Deploy da `stage` termina no projeto correto ou o impedimento recebe responsável, prazo e alternativa local documentada | Token, organização e projeto Vercel do cliente | Bloqueado externamente |
| EF-W02 | S6 | P0 | 5 | Tornar a homologação reconstruível | Comando documentado recria schema, migrations, funções, triggers e RLS sem intervenção manual oculta | Dump estrutural e acesso ao Supabase de homologação | A fazer |
| EF-W03 | S6 | P0 | 5 | Criar seed fictício, buckets e policies de homologação | Seed cobre empresas, satélites, Espaçonaves, missões e consentimentos; buckets e policies necessários são reproduzidos sem dados reais | EF-W02 | A fazer |
| EF-W04 | S6 | P0 | 3 | Consolidar CI e proteção da `stage` | Lint completo, typecheck, testes e build rodam em PR; falha obrigatória impede integração; execução fica anexada | Workflow já criado | A fazer |
| EF-W05 | S6 | P0 | 3 | Preparar contrato de dados para Portfólio e Tripulação | Consultas retornam somente projetos e integrantes autorizados, com anonimização e opt-in verificáveis | Decisão de consentimento do cliente | A fazer |
| EF-W06 | S6 | P0 | 5 | Implementar backend de “Fazer Proposta” | Fluxos autenticado e anônimo validam entrada no servidor, associam identidade quando houver e limitam abuso | Destino e retenção aprovados pelo cliente | A fazer |
| EF-W07 | S7 | P0 | 8 | Implementar consultas e ações seguras do Orbitinho | Usuário recebe somente os próprios projetos, pedidos ou novidades; tentativa sobre terceiros é negada; “Criar tarefa” só executa após confirmação | EF-P01, autenticação e APIs existentes | A fazer |
| EF-W08 | S7 | P0 | 5 | Cobrir regras críticas com testes automatizados | Testes cobrem rota pública, `setSpaceshipPublic`, RLS, consentimento, proposta, autorização e campos proibidos | EF-W03, EF-W05, EF-W06 e EF-W07 | A fazer |
| EF-W09 | S7 | P1 | 5 | Consolidar testes unitários, integração e pgTAP | Suite acordada roda localmente e na CI; falhas e limitações conhecidas ficam documentadas | EF-W04 e EF-W08 | A fazer |
| EF-W10 | S8 | P0 | 3 | Documentar setup, deploy, testes e CI/CD finais | Comandos, variáveis sem secrets, Sandbox, estratégia de deploy e execução dos testes entram no README ou documentação técnica | EF-W01 a EF-W09 | A fazer |

## Guilherme — 10 itens

| ID | Sprint | Pri. | Size | Entrega | Critério de conclusão | Dependências | Status |
|---|---:|---:|---:|---|---|---|---|
| EF-G01 | S6 | P0 | 2 | Abrir e integrar o PR do controle público/privado | Commit `512705e` entra na `stage`; comandante ativa/desativa e não comandante recebe erro | Revisão e CI verdes | A fazer |
| EF-G02 | S6 | P0 | 5 | Integrar a aba Portfólio | Projetos e missões autorizados aparecem; clientes sem consentimento são anonimizados; loading, vazio e erro funcionam | EF-W05 | A fazer |
| EF-G03 | S6 | P0 | 5 | Integrar a aba Tripulação | Avatar, especialidade e nível aparecem somente com opt-in; loading, vazio e erro funcionam | EF-W05 | A fazer |
| EF-G04 | S6 | P0 | 8 | Implementar interface completa de “Fazer Proposta” | Visitante e empresa autenticada têm campos, validação, sucesso e erro claros; botão deixa de apontar apenas para `/register` | EF-W06 | A fazer |
| EF-G05 | S7 | P0 | 5 | Implementar interface do Orbitinho para dúvidas, orientação e confirmação | Usuário recebe resposta fundamentada, entende incerteza/erro e confirma os dados antes de ações como “Criar tarefa” | EF-P01, EF-P02 e EF-W07 | A fazer |
| EF-G06 | S7 | P0 | 5 | Integrar navegação do Orbitinho por texto | Comandos priorizados abrem a rota correta; entrada ambígua pede esclarecimento; entrada inválida não navega | EF-G05 | A fazer |
| EF-G07 | S7 | P1 | 5 | Integrar navegação do Orbitinho por voz | Voz usa as mesmas intenções do texto; falha de reconhecimento não executa rota errada | EF-G06 e suporte do navegador | A fazer |
| EF-G08 | S7 | P1 | 5 | Fechar responsividade, acessibilidade, SEO e performance | Teclado, foco, leitor de tela e mobile são verificados; sitemap e metadata faltantes entram; medição de performance é registrada | Página e integrações concluídas | A fazer |
| EF-G09 | S7 | P1 | 3 | Finalizar e documentar o Design System necessário | Componentes usados, estados, tokens de tipografia/espaçamento e equivalente ao Storybook ficam documentados; escopo não usado vai para melhorias futuras | Design System existente | A fazer |
| EF-G10 | S8 | P0 | 3 | Estabilizar interface e produzir evidências visuais | Mock é removido ou delimitado, acentuação é corrigida, bugs visuais P0 são fechados e capturas finais são entregues | EF-G01 a EF-G09 | A fazer |

## Pedro — 4 itens

| ID | Sprint | Pri. | Size | Entrega | Critério de conclusão | Dependências | Status |
|---|---:|---:|---:|---|---|---|---|
| EF-P01 | S6 | P0 | 3 | Mapear arquitetura, intents e fontes do Orbitinho | Documento registra fluxo atual, páginas suportadas, consultas pessoais, confirmação de ações e fontes aprovadas | Acesso ao código e alinhamento do cliente | A fazer |
| EF-P02 | S6 | P0 | 5 | Preparar conhecimento e avaliação do Orbitinho | Respostas e sugestões de próximo passo têm fonte/data; avaliação mede acurácia, incerteza, recusas e exposição de dados | EF-P01 | A fazer |
| EF-P03 | S7 | P0 | 5 | Revisar arquitetura, privacidade e segurança das integrações | Página pública, proposta e Orbitinho têm revisão registrada de autorização, consentimento, rate limiting, logs, custo e dados sensíveis | Implementações de Wesley e Guilherme | A fazer |
| EF-P04 | S8 | P1 | 3 | Revisar documentação técnica e handoff | Arquitetura, APIs, modelo de dados, autenticação, segurança, riscos e continuidade correspondem ao produto entregue | Documentação consolidada pela equipe | A fazer |

## Victor — coordenação e entrega

| ID | Sprint | Pri. | Entrega | Critério de conclusão | Apoio | Status |
|---|---:|---:|---|---|---|---|
| EF-V01 | S6 | P0 | Fechar decisões com o cliente | Intents do Orbitinho, campos públicos, consentimentos, proposta, retenção e destino de contato estão registrados | Pedro, Wesley e Guilherme | A fazer |
| EF-V02 | S6–S7 | P0 | Manter backlog e aceite incremental | Cada item ativo tem responsável, evidência, status e critério; funcionalidades visíveis recebem aceite funcional | Todos | A fazer |
| EF-V03 | S8 | P0 | Congelar escopo e executar aceite final | Nenhuma feature grande entra após o congelamento; pendências e bugs ficam classificados | Wesley e Guilherme | A fazer |
| EF-V04 | S8 | P0 | Consolidar backlog final | Documento distingue concluído, não concluído, removido do escopo e melhoria futura | Todos | A fazer |
| EF-V05 | S8 | P0 | Gravar vídeo de demonstração de 1–3 minutos | Vídeo mostra ao menos um caso de uso e os fluxos relevantes não cobertos por ele | Todos | A fazer |
| EF-V06 | S8 | P0 | Preparar apresentação de 5–7 minutos | Apresentação segue Problema → Solução → Demonstração → Aprendizados/próximos passos e é ensaiada | Todos | A fazer |

## Artefatos finais obrigatórios

| ID | Pri. | Artefato | Conteúdo mínimo | Responsável pela consolidação | Status |
|---|---:|---|---|---|---|
| EF-D01 | P0 | README final | Contexto, funcionalidades, stack, arquitetura, pré-requisitos, instalação, variáveis sem secrets, execução, estrutura, deploy e autores | Wesley + Guilherme | A fazer |
| EF-D02 | P0 | Documentação técnica | Arquitetura e diagrama, APIs, modelo de dados, autenticação, segurança, deploy, testes e CI/CD | Wesley; revisão Pedro | A fazer |
| EF-D03 | P0 | Backlog final | Concluído, não concluído, removido e melhorias futuras | Victor | A fazer |
| EF-D04 | P0 | HANDOFF.md | O que não funciona, bugs, pendências, serviços usados e próximos passos | Guilherme + Wesley; revisão Pedro | A fazer |
| EF-D05 | P0 | Evidências | PRs/commits, checks, URL ou setup, capturas, resultados de testes e aceite | Wesley + Guilherme | A fazer |
| EF-D06 | P0 | Vídeo de 1–3 minutos | Caso de uso principal e fluxos complementares | Victor + equipe | A fazer |
| EF-D07 | P0 | Apresentação de 5–7 minutos | Problema, solução, demonstração, aprendizados e próximos passos | Victor + equipe | A fazer |

## Planejamento por sprint

### S6 — 12 a 18/10: integrações essenciais

- resolver ou documentar o bloqueio do Sandbox;
- reconstruir homologação e dados fictícios;
- integrar visibilidade, Portfólio, Tripulação e proposta;
- definir arquitetura, conhecimento e decisões do Orbitinho;
- manter CI obrigatória na `stage`.

**Saída da sprint:** página pública completa em homologação, proposta funcional e Orbitinho pronto para integração de frontend.

### S7 — 19 a 25/10: Orbitinho e qualidade

- concluir consultas pessoais e navegação por texto/voz;
- fechar testes de autorização, RLS, proposta e Orbitinho;
- revisar segurança, custo e logs;
- executar acessibilidade, responsividade, SEO e performance;
- consolidar Design System e CI.

**Saída da sprint:** produto integrado, verificações verdes e riscos conhecidos registrados.

### S8 — 26 a 29/10: congelamento e legado

- congelar escopo e executar regressão final;
- corrigir somente bugs bloqueadores;
- fechar README, documentação técnica, backlog final e HANDOFF;
- reunir evidências;
- gravar vídeo e ensaiar apresentação.

**Saída da sprint:** pacote final reproduzível, demonstrável e pronto para continuidade.

## Dependências críticas

```text
EF-V01 → EF-P01/P02 → EF-W07 → EF-G05/G06/G07
EF-W02 → EF-W03 → EF-W05 → EF-G02/G03
EF-W06 → EF-G04
EF-G01/G02/G03/G04 + EF-W07 + EF-G05/G06 → EF-P03
EF-W04/W08/W09 + EF-G08/G09/G10 → EF-V03
EF-V03 → EF-D01/D02/D03/D04/D05 → EF-D06/D07
```

## Definition of Done

Um item só pode mudar para concluído quando:

- seus critérios de aceite estão atendidos;
- existe PR ou commit vinculado;
- typecheck, lint, testes relevantes e build estão verdes;
- não há secrets, dados reais ou logs sensíveis;
- privacidade, RLS, migrations e autorização foram revisadas quando aplicável;
- documentação e `.env.example` foram atualizados;
- existe evidência reproduzível;
- limitações restantes foram registradas no backlog final e no handoff;
- Victor realizou o aceite funcional e o cliente validou decisões de negócio aplicáveis.

## Itens explicitamente fora de escopo

- separar frontend e backend em repositórios;
- migrar genericamente Server Actions para REST;
- migrar arquivos para AWS/S3;
- alterar pagamentos, faturamento, webhooks, cron jobs ou OAuth existentes;
- migrar todas as telas antigas para o novo Design System;
- executar DDL diretamente em produção;
- adicionar funcionalidades P2 enquanto houver item P0 bloqueado.
