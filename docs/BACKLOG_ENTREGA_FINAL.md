# Backlog replanejado — Entrega final

**Período de execução:** 12–27/10/2026.

**Entrega intermediária:** 12/10/2026.

**Apresentação final:** 27/10/2026.

## 1. Fontes e precedência

Este backlog usa como linha de base o PDF `Case Startellite 2026.2 - Insper Code 1.pdf`. O feedback do cliente registrado na reunião de 06/10 detalha o comportamento esperado do Orbitinho e as regras de privacidade. As datas de 12 e 27/10 são atualizações posteriores informadas pela coordenação e substituem somente o cronograma de 29 e 30/10 impresso no PDF.

Em caso de conflito:

1. segurança, privacidade e restrições de produção do PDF não podem ser reduzidas;
2. decisões posteriores do cliente podem detalhar ou priorizar o escopo, desde que fiquem registradas;
3. retirada de requisito do PDF exige aceite explícito do cliente e registro no backlog final;
4. relato de implementação não equivale a conclusão sem branch ou PR, checks, demonstração e aceite.

## 2. Organização da equipe

| Pessoa | Frentes principais |
|---|---|
| Wesley Lima Silva | Orbitinho no servidor, integrações seguras, homologação, CI/CD e testes |
| Guilherme Kenzo Taba Nakamura | Orbitinho na interface, conhecimento, texto, voz, acessibilidade e testes |
| Pedro Pereira | Página pública de Espaçonaves, proposta, Design System, SEO e acabamento visual |
| Victor Barbosa Viana | Produto, alinhamento com o cliente, priorização, aceite e apresentação; sem implementação |

Wesley e Guilherme trabalham juntos na frente do Orbitinho e nas fundações de qualidade. Pedro conclui o que resta da frente de Espaçonaves e do Design System. Revisões cruzadas são permitidas, mas não alteram o responsável pela entrega.

## 3. Convenções

- **P0:** requisito obrigatório do PDF, segurança ou condição da apresentação.
- **P1:** expectativa importante do PDF que depende de validação técnica ou recorte com o cliente.
- **P2:** bônus; só começa após todos os P0 estarem demonstráveis.
- **S6:** 12–18/10 — validação da base e fundações.
- **S7:** 19–24/10 — integrações e conclusão funcional.
- **S8:** 25–27/10 — congelamento, aceite e apresentação.
- **A validar:** há relato de implementação, mas ainda falta comprovação reproduzível.
- **A fazer:** ainda não há implementação comprovada.
- **Bloqueado:** existe dependência externa identificada, com responsável e alternativa registrados.
- **Concluído:** Definition of Done atendida e aceite funcional registrado.

## 4. Rastreabilidade com o PDF

| Frente e peso no PDF | Resultado obrigatório | Tasks |
|---|---|---|
| Orbitinho — 30% | Texto, voz em desktop/mobile, dúvidas, ações sem mãos e recorte de programação/gestão de tarefas | EF-W05–W08; EF-G01–G08 |
| Espaçonaves — 20% | SSR, OpenGraph, privacidade, Portfólio, Tripulação, proposta e sitemap | EF-P01–P08; EF-W04 |
| Testes e CI — 20% | Checks em PR, testes unitários, pgTAP e documentação | EF-W03, EF-W04, EF-W08, EF-G07 e EF-G08 |
| Homologação — 15% | Reset reproduzível, migrations, seed fictício, Storage e setup | EF-W01, EF-W02 e EF-W03 |
| Design System — 15% | Componentes reutilizáveis, documentação visual, tokens e uso real | EF-P02, EF-P07 e EF-P08 |
| Entrega | Código revisável, ambiente reproduzível, documentação e demonstração final | EF-W08, EF-G08, EF-P08 e EF-V03–V05 |

## 5. Wesley — Orbitinho, homologação, CI/CD e testes

| ID | Sprint | Pri. | Size | Entrega | Critério de conclusão | Dependências | Status |
|---|---:|---:|---:|---|---|---|---|
| EF-W01 | S6 | P0 | 5 | Tornar homologação reconstruível | `supabase db reset` ou comando aprovado recria schema, funções, triggers, índices, RLS e migrations saneadas usando `supabase/config.toml`, sem acesso a produção | Dump estrutural e credenciais exclusivas de homologação | A fazer |
| EF-W02 | S6 | P0 | 5 | Criar seed, Storage e policies de homologação | Seed versionado contém empresas, Satélites, Espaçonaves e missões fictícias em estados representativos; buckets e policies necessários são recriados sem dados reais | EF-W01 | A fazer |
| EF-W03 | S6 | P0 | 5 | Consolidar CI/CD e preview seguro | PR executa typecheck, lint e testes em jobs obrigatórios; integração falha se um check falhar; preview/Sandbox usa somente credenciais de homologação; execução e bloqueios ficam anexados | Acesso ao GitHub e à Vercel/Supabase de homologação | A validar |
| EF-W04 | S6–S7 | P0 | 5 | Implementar testes unitários, integração e pgTAP | Suite cobre regras puras acordadas, RLS da superfície pública, consentimento, proposta e campos proibidos; roda localmente e na CI com documentação | EF-W01, EF-W02 e contratos de EF-P01–P05 | A fazer |
| EF-W05 | S7 | P0 | 8 | Implementar consultas e ações seguras do Orbitinho | Servidor autentica o usuário, retorna somente seus projetos, pedidos e novidades, nega consultas sobre terceiros e confirma dados antes de “Criar tarefa” ou outra ação sensível | EF-G01, autenticação e APIs existentes | A fazer |
| EF-W06 | S7 | P1 | 8 | Implementar recorte seguro de assistência por IDE | Integração aprovada permite ao Orbitinho apoiar programação ou gestão de tarefas por um protocolo/connector compatível; ao menos um cliente é demonstrado e VS Code, Claude, Antigravity e Cursor têm suporte ou limitação documentados; nenhuma ação ocorre sem autorização e confirmação | Decisão EF-V01 e arquitetura EF-G01 | A fazer |
| EF-W07 | S7 | P0 | 3 | Proteger custo, logs e dados do Orbitinho | Rate limiting, timeout e limites de uso são aplicados; logs e telemetria não armazenam prompts, documentos, segredos ou dados pessoais; tokens e latência são medidos sem conteúdo sensível | EF-W05; EF-W06 se o P1 for executado | A fazer |
| EF-W08 | S8 | P0 | 3 | Consolidar documentação e evidências técnicas | README e documentação registram setup, `.env.example`, homologação, CI/CD, testes, integrações do Orbitinho, variáveis sem valores secretos, riscos e comandos reproduzíveis | EF-W01–W07 | A fazer |

## 6. Guilherme — Orbitinho, experiência e testes

| ID | Sprint | Pri. | Size | Entrega | Critério de conclusão | Dependências | Status |
|---|---:|---:|---:|---|---|---|---|
| EF-G01 | S6 | P0 | 3 | Mapear arquitetura, intents e rotas existentes do Orbitinho | Documento versionado lista fluxo atual, mecanismo de navegação, rotas suportadas, consultas pessoais, ações, permissões, fontes de conhecimento e integrações reutilizáveis | Acesso ao código e decisão EF-V01 | A fazer |
| EF-G02 | S6 | P0 | 5 | Preparar base de conhecimento e avaliação | Base usa somente fontes não confidenciais aprovadas, com versão/data; conjunto de avaliação mede correção, incerteza, recusas, vazamento de dados e orientação de página | EF-G01 e validação do cliente | A fazer |
| EF-G03 | S6–S7 | P0 | 5 | Implementar interface e comandos escritos | Modal aceita texto, responde dúvidas de uso, indica a página correta e navega para intents priorizadas; entrada inválida ou ambígua pede esclarecimento e não executa ação | EF-G01, EF-G02 e EF-W05 | A fazer |
| EF-G04 | S7 | P0 | 5 | Implementar voz em desktop e mobile | Entrada e resposta por voz reutilizam as mesmas intents do texto em navegadores suportados; permissão negada, ruído ou falha de reconhecimento não navegam nem executam ações; suporte desktop/mobile é registrado | EF-G03 | A fazer |
| EF-G05 | S7 | P1 | 3 | Fechar experiência hands-free e personalidade | Fluxo principal pode ser executado sem mouse quando tecnicamente suportado; respostas usam termos da plataforma, linguagem natural e personalidade aprovada; teclado, foco e leitor de tela funcionam | EF-G03 e EF-G04 | A fazer |
| EF-G06 | S7 | P1 | 5 | Integrar experiência dos clientes de IDE | Usuário entende conexão, permissões, confirmação, resultado e erro da assistência de programação/gestão de tarefas; clientes suportados e limitações ficam visíveis e documentados | EF-W06 | A fazer |
| EF-G07 | S7 | P0 | 5 | Automatizar matriz de testes do Orbitinho | Testes cobrem intenção, texto, voz quando automatizável, autorização, confirmação, ambiguidade, recusa, falha de API e tentativa de acesso a terceiros | EF-W05, EF-G03 e EF-G04 | A fazer |
| EF-G08 | S8 | P0 | 3 | Integrar, estabilizar e produzir evidências do Orbitinho | CI fica verde; bugs P0 são fechados; demonstração comprova dúvida, navegação, voz, consulta própria, recusa de terceiro e ação confirmada; limitações P1 ficam registradas | EF-W03, EF-W05, EF-W07, EF-G01–G04 e EF-G07; P1 se executados | A fazer |

## 7. Pedro — Espaçonaves e Design System

| ID | Sprint | Pri. | Size | Entrega | Critério de conclusão | Dependências | Status |
|---|---:|---:|---:|---|---|---|---|
| EF-P01 | S6 | P0 | 5 | Validar e integrar a base da página pública | Branch ou PR comprova `is_public` com padrão `false`, slug, view/DTO com lista branca, rota SSR `/spaceships/[slug]`, 404 uniforme e ausência de leitura anônima nas tabelas base | Acesso às branches e migrations relatadas | A validar |
| EF-P02 | S6 | P0 | 3 | Concluir cabeçalho e dados principais | Página apresenta banner, avatar/logo, nome, bio, contagem de tripulantes, autoridade e stacks com dados autorizados; componentes compartilhados são usados | EF-P01 | A validar |
| EF-P03 | S6–S7 | P0 | 5 | Integrar Portfólio | Projetos internos e externos autorizados são exibidos; clientes sem consentimento são anonimizados; loading, vazio e erro funcionam | EF-P01 e regra de consentimento aprovada | A fazer |
| EF-P04 | S6–S7 | P0 | 5 | Integrar Tripulação | Avatar, especialidade e nível são exibidos; nome real aparece somente com opt-in compatível com as regras existentes; loading, vazio e erro funcionam | EF-P01 e regra de opt-in aprovada | A fazer |
| EF-P05 | S7 | P0 | 8 | Implementar “Fazer Proposta” | Modal atende empresa autenticada e visitante anônimo, valida dados, limita abuso, registra/envia ao destino aprovado e apresenta sucesso/erro sem expor dados | Decisões de destino e retenção em EF-V01 | A fazer |
| EF-P06 | S7 | P0 | 3 | Concluir sitemap, SEO e performance | Somente páginas públicas entram no sitemap; SSR, canonical, OpenGraph e metadados são validados; assets e carregamento recebem medição de performance | EF-P01–P04 | A fazer |
| EF-P07 | S7 | P0 | 5 | Concluir Design System aditivo | Componentes necessários ficam em `/components/ui` ou estrutura aprovada; Storybook/equivalente executa; tokens de cores, tipografia e espaçamento são documentados; página usa os componentes | Inventário e componentes relatados | A fazer |
| EF-P08 | S8 | P0 | 3 | Estabilizar Espaçonaves e produzir evidências | Página funciona em mobile, teclado e leitor de tela; regressão não altera fluxos legados; PRs, capturas, URL/setup e aceite dos fluxos ficam anexados | EF-P01–P07 e testes EF-W04 | A fazer |

## 8. Victor — coordenação, aceite e apresentação

| ID | Sprint | Pri. | Entrega | Critério de conclusão | Apoio | Status |
|---|---:|---:|---|---|---|---|
| EF-V01 | S6 | P0 | Fechar decisões de escopo com o cliente | Ficam registrados: intents e rotas do Orbitinho, recorte de assistência por IDE, fontes de conhecimento, dados públicos, consentimentos, proposta, retenção e critérios de aceite | Todos | A fazer |
| EF-V02 | S6–S7 | P0 | Conduzir alinhamento e aceite incremental | Há ao menos um alinhamento semanal; cada item ativo possui responsável, evidência, status e critério; mudanças de prioridade são registradas | Todos | A fazer |
| EF-V03 | S8 | P0 | Congelar escopo em 25/10 e executar aceite final | Nenhuma funcionalidade grande entra após o congelamento; P0 são demonstrados; pendências P1/P2, bugs e riscos ficam classificados | Todos | A fazer |
| EF-V04 | S8 | P0 | Consolidar pacote final | Código/PRs, setup, `.env.example`, documentação, backlog final, evidências e limitações estão organizados para continuidade | Todos | A fazer |
| EF-V05 | S8 | P0 | Preparar e conduzir apresentação de 27/10 | Apresentação demonstra as cinco frentes, relaciona resultados aos pesos do PDF e registra decisões, riscos e próximos passos | Todos | A fazer |

## 9. Artefatos finais

| ID | Pri. | Artefato | Conteúdo mínimo | Responsável |
|---|---:|---|---|---|
| EF-D01 | P0 | Código e PRs | Mudanças pequenas, revisáveis, vinculadas às tasks e sem checks falhando | Responsável de cada task |
| EF-D02 | P0 | Homologação e setup | Reset, migrations, seed, Storage, `.env.example` e instruções reproduzíveis | Wesley |
| EF-D03 | P0 | Página pública | URL/execução, SSR, privacidade, Portfólio, Tripulação, proposta e sitemap | Pedro |
| EF-D04 | P0 | CI e testes | Workflow, unitários, integração, pgTAP, resultados e instruções | Wesley + Guilherme |
| EF-D05 | P0 | Orbitinho | Texto, voz, dúvidas, consultas autorizadas, ações e decisão/recorte de IDE documentado | Wesley + Guilherme |
| EF-D06 | P0 | Design System | Componentes, tokens, Storybook/equivalente e uso real | Pedro |
| EF-D07 | P0 | Documentação final | README, arquitetura, segurança, deploy, limitações e continuidade | Todos; consolidação Victor |
| EF-D08 | P0 | Apresentação | Demonstração funcional e síntese das decisões técnicas | Victor + equipe |

## 10. Planejamento por sprint

### S6 — 12 a 18/10: validar e reconstruir a base

- validar branches, PRs e migrations relatados para Espaçonaves e Design System;
- reconstruir homologação, seed, Storage e policies;
- consolidar os checks obrigatórios da CI;
- mapear o Orbitinho, suas intents, rotas e fontes;
- fechar com o cliente o recorte de assistência por IDE, consentimentos e proposta;
- iniciar Portfólio, Tripulação e interface escrita do Orbitinho.

**Saída:** base comprovada, ambiente reproduzível, decisões fechadas e integrações prontas para conclusão.

### S7 — 19 a 24/10: concluir as cinco frentes

- concluir Portfólio, Tripulação, proposta, sitemap e Design System;
- integrar dúvidas, texto, voz, consultas pessoais e ações do Orbitinho;
- implementar ou registrar formalmente o recorte aprovado de assistência por IDE;
- executar testes unitários, integração, RLS/pgTAP e matriz do Orbitinho;
- revisar segurança, produção, custos, logs, acessibilidade e performance.

**Saída:** todos os P0 integrados, demonstráveis e com checks verdes.

### S8 — 25 a 27/10: congelar, aceitar e apresentar

- congelar escopo em 25/10;
- executar regressão e aceite final;
- corrigir somente bugs bloqueadores;
- consolidar documentação, evidências e limitações;
- ensaiar em 26/10;
- apresentar em 27/10.

**Saída:** pacote final reproduzível, demonstrado e pronto para continuidade.


## 11. Definition of Done

Uma task só pode mudar para **Concluído** quando:

- seus critérios de conclusão estão atendidos;
- existe branch e PR ou commit rastreável;
- o PR é pequeno o suficiente para revisão prática;
- typecheck, lint, testes relevantes e build estão verdes;
- migrations e SQL estão versionados e nenhuma DDL foi executada em produção;
- não foram usados dados reais, credenciais de produção ou chaves `service_role`/live;
- nenhum segredo, prompt, documento ou dado pessoal sensível aparece em código, evidência ou log;
- não foi criado custo recorrente sem aprovação do cliente;
- autorização, RLS, consentimento, rate limiting e privacidade foram revisados quando aplicável;
- a branch foi sincronizada com a evolução paralela do produto antes da integração;
- documentação e `.env.example` foram atualizados sem valores secretos;
- existe evidência reproduzível e Victor registrou o aceite funcional;
- limitações restantes foram registradas no backlog final.

## 12. Fora de escopo

- separar frontend e backend em repositórios;
- converter genericamente Server Actions em REST;
- migrar arquivos ou infraestrutura para AWS/S3;
- alterar pagamentos, faturamento, webhooks, cron jobs, callbacks OAuth ou APIs públicas existentes;
- executar DDL ou deploy diretamente em produção;
- migrar todas as telas legadas para o novo Design System;
- iniciar P2 enquanto houver P0 não demonstrável.


