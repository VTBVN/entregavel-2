# Backlog replanejado — Wesley e Guilherme

**Atualização:** 12/10/2026.

**Equipe técnica restante:** Wesley Lima Silva e Guilherme Kenzo Taba Nakamura.

**Fontes:** reunião com o cliente em 06/10/2026, documentos da Entrega 1, relatório de modificações fornecido por Wesley e `CHANGELOG.md` fornecido por Guilherme.

Victor Barbosa Viana permanece como Product Owner e Scrum Master para priorização, alinhamento e aceite funcional, sem entrar na capacidade de implementação. Pedro Pereira e Thiago Brasileiro de Sousa foram retirados das atribuições técnicas deste backlog.

## Convenções

- **P0:** necessário para demonstrar ou fechar a Entrega 2.
- **P1:** necessário para consolidar qualidade e documentação.
- **P2:** pode seguir para a entrega final.
- **Relatado como concluído:** consta no relatório de Wesley, mas ainda deve receber link de PR ou commit.
- **Implementado na `stage`:** o changelog informa commit integrado à branch `stage`.
- **Implementado fora da `stage`:** há branch e commit remoto, mas falta PR ou merge.
- **Interface sem integração:** a tela existe, porém ainda não consome os dados reais necessários.
- **Bloqueado externamente:** depende de credencial, acesso ou decisão fora do código.

## 1. Entregas relatadas por Wesley

| ID | Item | Pri. | Responsável | Status | Evidência disponível / pendência |
|---|---|---:|---|---|---|
| W-01 | Separar CI em jobs de lint, typecheck, testes e build | P0 | Wesley | Relatado como concluído | Relatório de Wesley; adicionar PR ou commit |
| W-02 | Executar checks em PR para `stage` e checks + deploy em push para `stage` | P0 | Wesley | Relatado como concluído | Relatório de Wesley; adicionar execução da CI |
| W-03 | Validar variáveis da Vercel e vincular organização/projeto antes do deploy | P0 | Wesley | Implementado; deploy bloqueado externamente | Vercel retorna `User not found (404)`; confirmar token, organização e projeto |
| W-04 | Configurar o Environment `Production – startellite-sandbox` | P1 | Wesley | Relatado como concluído | Adicionar link da configuração ou execução, sem expor segredos |
| W-05 | Criar execução local com mock e sem credenciais de produção | P0 | Wesley | Relatado como concluído | Adicionar comando reproduzível e PR/commit |
| W-06 | Cobrir perfis público, privado, inexistente, slug inválido e campos proibidos | P0 | Wesley | Relatado como concluído | Relatório informa 36 testes aprovados; adicionar saída ou execução da CI |
| W-07 | Cobrir anonimização e restrição de imagens ao Storage autorizado | P0 | Wesley | Relatado como concluído | Adicionar PR/commit e resultado da CI |
| W-08 | Documentar setup, variáveis, validações e uso de mocks | P1 | Wesley | Relatado como concluído | Adicionar link para a documentação no repositório do produto |
| W-09 | Preservar `.env`, `.env.local`, `.vercel` e segredos fora do Git | P0 | Wesley | Relatado como concluído | Confirmar na revisão do PR |

## 2. Pendências técnicas de Wesley

| ID | Item | Pri. | Critério de conclusão | Status |
|---|---|---:|---|---|
| W-10 | Anexar links de PR, commits e execução da CI aos itens W-01 a W-09 | P0 | Cada entrega relatada possui uma referência rastreável | A fazer |
| W-11 | Confirmar lint completo na CI | P0 | Job de lint termina com resultado registrado; avisos preexistentes são separados de erros novos | A fazer |
| W-12 | Desbloquear o deploy do Sandbox com o responsável pelas credenciais | P0 | Deploy para o projeto correto da Vercel termina ou o impedimento recebe responsável e prazo | Bloqueado externamente |
| W-13 | Mapear o Orbitinho atual: respostas, rotas, voz, fontes e autorização | P0 | Documento curto indica o que já funciona e quais arquivos ou serviços participam do fluxo | A fazer |
| W-14 | Implementar ou validar respostas prioritárias sobre o uso da plataforma | P0 | Perguntas aprovadas têm respostas corretas, fonte identificável e tratamento de incerteza | A fazer |
| W-15 | Garantir autorização no servidor para consultas relacionadas ao usuário | P0 | Usuário acessa apenas os próprios dados; tentativa de consultar terceiros é recusada | A fazer |
| W-16 | Adicionar testes do Orbitinho para resposta, rota, ambiguidade e acesso indevido | P1 | Cenários prioritários rodam na CI e têm resultado registrado | A fazer |

## 3. Entregas de Espaçonaves relatadas por Guilherme

O changelog de Guilherme registra a implementação da página pública e do Design System. O relatório de Wesley registra validações, testes e segurança sobre a mesma frente. Os documentos se complementam: o changelog descreve a implementação e seus commits; o relatório de Wesley descreve a cobertura técnica. As abas Portfólio e Tripulação existem na interface, mas ainda não estão integradas.

| ID | Item | Pri. | Responsável | Status | Evidência / pendência |
|---|---|---:|---|---|---|
| G-01 | Criar rota pública `/spaceships/[slug]` com SSR, metadados, OpenGraph e JSON-LD | P0 | Guilherme | Implementado na `stage` | Commit `e0974a9`; documentação `docs/pagina-publica-espaconave.md` no produto |
| G-02 | Criar campos `is_public` e `slug` com geração e validação do slug | P0 | Guilherme | Implementado na `stage` | Commit `f6edeac` |
| G-03 | Criar view `public_spaceship_profiles` somente com dados autorizados | P0 | Guilherme | Implementado na `stage` | Commit `eeb58da`; leitura anônima verificada com resposta 200 |
| G-04 | Implementar capa, avatar, nome, localização, números, apresentação e especialidades | P0 | Guilherme | Implementado na `stage` | Commit `e0974a9`, ajustes `005c7ba` e `ba9dad7`, merge `7c08c06` |
| G-05 | Usar Navbar e Footer do site e reorganizar o topo da página pública | P1 | Guilherme | Implementado na `stage` | Commits `005c7ba` e `ba9dad7` |
| G-06 | Implementar botão “Fazer Proposta” provisório | P1 | Guilherme | Implementado parcialmente | Leva a `/register`; fluxo de proposta ST-027 continua pendente |
| G-07 | Criar Design System com Button, Card, Badge, Tabs e tokens | P1 | Guilherme | Implementado na `stage` | Commit `610e9b9`; documentação `docs/design-system.md` no produto |
| G-08 | Implementar controle público/privado para o comandante | P0 | Guilherme | Implementado fora da `stage` | Branch `feat/st-019-spaceship-public-toggle`, commit `512705e`; falta abrir PR |
| G-09 | Criar abas Portfólio e Tripulação | P0 | Guilherme | Interface sem integração | Abas visuais implementadas; falta conectar dados reais e estados |
| G-10 | Disponibilizar mock local da página e do painel | P1 | Guilherme | Implementado | `PUBLIC_SPACESHIP_MOCK=1`; mock deve ser removido ou delimitado antes da entrega final |
| G-11 | Proteger página pública contra slugs e imagens indevidos | P0 | Guilherme | Implementado na `stage` | 404 uniforme, URLs restritas ao Storage e escape do JSON-LD |

## 4. Pendências de Espaçonaves — Guilherme

| ID | Item | Pri. | Critério de conclusão | Status |
|---|---|---:|---|---|
| G-12 | Abrir e integrar o PR do botão público/privado | P0 | Commit `512705e` entra na `stage` e a action é validada | A fazer |
| G-13 | Integrar dados da aba Portfólio | P0 | Aba exibe trabalhos autorizados, com estados vazio, carregamento e erro | A fazer |
| G-14 | Integrar dados da aba Tripulação | P0 | Aba exibe somente integrantes com consentimento e trata estados vazio/erro | A fazer |
| G-15 | Adicionar testes automatizados da rota e de `setSpaceshipPublic` | P0 | Casos de sucesso, 404 e tentativa por não comandante rodam na CI | A fazer |
| G-16 | Corrigir acentuação das especialidades | P1 | Nomes vêm de fonte traduzida ou mapeamento aprovado | A fazer |
| G-17 | Definir destino final do botão “Fazer Proposta” | P2 | Fluxo ST-027 implementado ou limitação documentada para a entrega final | A fazer |
| G-18 | Remover ou limitar o mock antes da entrega final | P1 | Mock não interfere em produção e sua finalidade fica documentada | A fazer |
| G-19 | Completar componentes e tokens restantes do Design System | P2 | Escopo aprovado para Modal, Input, Textarea, Select, tipografia e espaçamento | A fazer |

## 5. Tarefas de Guilherme fora da frente de Espaçonaves

| ID | Item | Pri. | Critério de conclusão | Status |
|---|---|---:|---|---|
| G-20 | Revisar a interface do Orbitinho para perguntas e navegação por texto | P0 | Usuário entende o que pode perguntar; sucesso, ambiguidade e erro têm retorno claro | A fazer |
| G-21 | Integrar no frontend os destinos priorizados do Orbitinho | P0 | Comandos aprovados abrem as rotas corretas e não navegam em caso ambíguo | A fazer |
| G-22 | Validar o fluxo de voz quando suportado pelo navegador | P1 | Voz usa as mesmas intenções do texto; falha de reconhecimento não dispara rota errada | A fazer |
| G-23 | Preparar capturas e roteiro visual da demonstração | P0 | Evidências mostram somente dados fictícios ou autorizados | A fazer |

## 6. Fechamento conjunto

| ID | Item | Pri. | Responsáveis | Critério de conclusão | Status |
|---|---|---:|---|---|---|
| WG-01 | Integrar as mudanças de Wesley e Guilherme no ambiente de demonstração | P0 | Wesley + Guilherme | Build e fluxos prioritários executam no mesmo ambiente | A fazer |
| WG-02 | Executar regressão do recorte | P0 | Wesley + Guilherme | CI, Orbitinho e página pública são verificados; falhas ficam registradas | A fazer |
| WG-03 | Atualizar funcionalidades e critérios de aceite | P0 | Wesley + Guilherme | Cada item demonstrado tem evidência e resultado real | A fazer |
| WG-04 | Entregar a Victor o roteiro, links e pendências para aceite funcional | P0 | Wesley + Guilherme | Victor consegue reproduzir a demonstração e registrar o aceite | A fazer |

## Ordem de execução

1. Wesley adiciona os links que comprovam as alterações já relatadas e trata o bloqueio da Vercel com o responsável pelo Sandbox.
2. Guilherme abre o PR do botão público/privado e integra Portfólio e Tripulação.
3. Wesley fecha backend, autorização e testes do Orbitinho; Guilherme fecha interface e navegação.
4. Os dois integram, executam a regressão e entregam as evidências para aceite de Victor.

## Distribuição resumida

| Pessoa | Responsabilidade principal |
|---|---|
| Wesley | CI, Sandbox, segurança, testes, backend e autorização do Orbitinho |
| Guilherme | Espaçonaves, interface, experiência do Orbitinho e evidências visuais |
| Wesley + Guilherme | Integração, regressão e preparação da demonstração |
