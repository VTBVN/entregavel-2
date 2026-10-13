# MVP — implementado versus faltante

Esta comparação usa como fonte principal a reunião com Pedro Antonio Silva em 06/10/2026. O estado da implementação vem do registro consolidado em [`IMPLEMENTADO.md`](IMPLEMENTADO.md).

## Recorte pedido pelo cliente

Pedro indicou duas entregas principais para a semana:

1. **Orbitinho:** orientar o uso da plataforma, responder com precisão como realizar tarefas e indicar qual página acessar. A integração com a navegação existente por texto e voz era desejada. Consultas pessoais deveriam retornar somente dados do usuário autenticado (reunião, 30:32–35:31).
2. **Página pública de Espaçonave:** uma primeira versão de portfólio compartilhável, com identidade da equipe, capa/banner, imagem de perfil, descrição e projetos ou missões, seguindo uma linguagem escura, azul e espacial (reunião, 37:15–43:03).

As perguntas prontas na abertura do Orbitinho foram tratadas como bônus (32:23). O mapa de integrantes foi apresentado como exemplo criativo, sem caráter obrigatório (41:26). O fluxo completo de proposta não foi definido como parte do MVP nessa reunião.

## Resumo do estado

| Frente | Estado do MVP | Síntese |
|---|---|---|
| Página pública de Espaçonave | **Parcialmente implementada** | Estrutura pública, perfil, segurança e visual foram implementados; Portfólio e Tripulação ainda não estão integrados |
| Orbitinho | **Faltante** | Os documentos fornecidos não comprovam respostas sobre a plataforma, consulta do próprio usuário ou navegação integrada |
| CI, testes e Sandbox | **Suporte parcialmente pronto** | CI, mocks e testes foram implementados; o deploy do Sandbox continua bloqueado pela Vercel |

Com base nas evidências atuais, o conjunto ainda deve ser apresentado como **protótipo parcial**, pois uma das duas frentes principais do cliente, o Orbitinho, não possui implementação comprovada.

## Página pública de Espaçonave

| Pedido do cliente | Estado | O que foi implementado | O que falta |
|---|---|---|---|
| Página pública compartilhável | Implementado na `stage` | Rota SSR `/spaceships/[slug]`, canonical, OpenGraph, Twitter Card e JSON-LD; commit `e0974a9` | 
| Capa/banner e imagem de perfil | Implementado na `stage` | Layout com capa e avatar, ajustes nos commits `005c7ba` e `ba9dad7` | Confirmar visualmente 
| Nome, descrição e identidade da equipe | Implementado na `stage` | Nome, localização, números, apresentação e especialidades | Corrigir acentuação das especialidades e validar o texto final |
| Visual escuro, azul e espacial | Parcialmente comprovado | Página segue o guia visual e possui temas claro/escuro; Design System no commit `610e9b9` |
| Dados públicos seguros | Implementado | Campos `is_public` e `slug`, view `public_spaceship_profiles`, lista branca, 404 uniforme e restrição de imagens ao Storage | Anexar execução dos testes e validar os campos finais com o cliente |
| Ativação pública/privada pelo comandante | Implementado fora da `stage` | Branch `feat/st-019-spaceship-public-toggle`, commit `512705e`, com autorização por `commander_id` | Abrir PR, integrar à `stage` e validar; até isso ocorrer, a ativação depende do banco ou do mock |
| Projetos e missões no portfólio | Interface sem integração | Aba Portfólio foi criada | Integrar dados reais autorizados, anonimizar clientes e tratar carregamento, vazio e erro |
| Integrantes da Espaçonave | Interface sem integração | Aba Tripulação foi criada | Integrar somente integrantes com consentimento e tratar estados vazio e erro |
| Botão “Fazer Proposta” | Provisório | Botão leva a `/register` | Implementar o fluxo ST-027 ou documentar claramente a limitação |
| Mapa/localização de membros | Não implementado | Localização básica aparece no perfil | Item criativo opcional; não bloqueia o MVP definido na reunião |

## Orbitinho

| Pedido do cliente | Estado | Evidência encontrada | O que falta |
|---|---|---|---|
| Responder com precisão como usar a plataforma | Faltante | Nenhuma implementação foi registrada nos relatórios | Criar base revisada de respostas sobre projetos, Espaçonaves, épicos e fluxos da plataforma |
| Indicar qual página acessar para cada ação | Faltante | Nenhuma demonstração ou commit foi informado | Mapear intenções, páginas suportadas e respostas para destinos não encontrados ou ambíguos |
| Navegação por texto | Faltante | A reunião informa que a mudança de rota já existia, mas não há evidência de integração | Conectar comandos digitados ao mecanismo existente e validar rotas prioritárias |
| Navegação por voz | Faltante | Não há evidência técnica fornecida | Reutilizar as mesmas intenções do texto; falha de reconhecimento não pode abrir uma rota errada |
| Consultar informações do próprio usuário | Faltante | Não há implementação ou teste registrado | Validar identidade no servidor e limitar projetos, pedidos e novidades ao usuário autenticado |
| Recusar consulta sobre outras pessoas | Faltante | Requisito definido na reunião, sem evidência de teste | Adicionar autorização e teste de tentativa de acesso a dados de terceiros |


## Infraestrutura e qualidade que sustentam o MVP

| Item | Estado | Observação |
|---|---|---|
| CI com lint, typecheck, testes e build | Relatado como implementado | Ainda é necessário anexar PR, commit e execução completa da CI |
| Testes da superfície pública | Relatado como implementado | Relatório informa 36 testes aprovados, incluindo privacidade e anonimização |
| Mock sem produção | Implementado | Permite demonstração local; deve permanecer desativado em produção e ser removido ou delimitado depois |
| Sandbox | Bloqueado externamente | Deploy pode falhar com `User not found (404)`; é necessário confirmar token, organização e projeto Vercel |
| Testes da rota e do botão público/privado | A validar | O registro consolidado informa testes, mas ainda faltam links e confirmação da cobertura de `setSpaceshipPublic` |

## O que falta para considerar o MVP completo

### P0 — necessário antes da demonstração

1. Implementar o Orbitinho para responder como usar a plataforma e indicar páginas, que foi o objetivo explícito da semana em 35:16.
2. Garantir que consultas relacionadas ao usuário sejam autorizadas no servidor e não exponham dados de terceiros.
3. Abrir e integrar o PR do controle público/privado da Espaçonave.
4. Integrar a aba Portfólio com projetos ou missões autorizados e anonimizados.
5. Anexar uma execução reproduzível: URL do Sandbox ou instruções locais, commits demonstrados e capturas.
6. Executar a regressão integrada e registrar o aceite funcional de Victor.

### P1 — importante, mas pode ser declarado como limitação

1. Integrar Tripulação com consentimento.
2. Integrar navegação por voz; a reunião aceita o foco principal em respostas corretas e trata a integração de rota como ideal.
3. Corrigir acentuação das especialidades.
4. Adicionar testes automatizados da rota pública e de `setSpaceshipPublic`.
5. Resolver o deploy da Vercel para apresentar a versão no Sandbox.

