# Implementado

Este documento consolida as implementações registradas para a Entrega Intermediária 2. A autoria individual foi omitida: os itens estão organizados por funcionalidade e evidência técnica.

Os estados abaixo reproduzem os registros disponíveis. Branch ou PR, checks completos, demonstração e aceite funcional ainda devem ser anexados quando indicados; por isso, o backlog final mantém alguns itens como **A validar**.

## 1. CI/CD e Sandbox

- O workflow `.github/workflows/quality.yml` foi dividido em jobs de lint, typecheck, testes e build.
- Pull Requests direcionados à `stage` executam os checks de qualidade.
- Pushes para a `stage` executam os checks e, depois do build, tentam publicar no Sandbox.
- O deploy valida `VERCEL_TOKEN`, `VERCEL_ORG_ID` e `VERCEL_PROJECT_ID` antes de continuar.
- O workflow vincula explicitamente organização e projeto da Vercel e usa o Environment `Production – startellite-sandbox`.
- O deploy do Sandbox permanece sujeito ao bloqueio externo `User not found (404)`; token, organização e projeto ainda precisam ser confirmados.
- O lint completo ainda precisa ser confirmado em uma execução da CI.

## 2. Página pública de Espaçonaves

### 2.1 Rota, conteúdo e metadados

- Rota pública `/spaceships/[slug]` renderizada no servidor.
- Leitura da view `public_spaceship_profiles` com chave anônima e contrato Zod.
- Capa, avatar, nome, localização, indicadores, apresentação e especialidades.
- Metadados por Espaçonave, URL canônica, OpenGraph, Twitter Card e JSON-LD.
- Temas claro e escuro.
- Uso da `Navbar` e do `Footer` do site.
- Topo reorganizado e painel responsivo de apresentação da tripulação.
- País e continente apresentados em português.
- Especialidades deixam de aparecer como slug cru.
- `ThemeToggle` removido por não ser mais utilizado.

### 2.2 Campos públicos e superfície de dados

- Migration `20261010121500_spaceship_public_fields.sql` com `is_public` e `slug`.
- Slug gerado a partir do nome, único, validado e estável após a criação.
- Migration `20261010123000_public_spaceship_profiles_view.sql` com lista branca de campos.
- `member_count` e `completed_missions` incluídos na superfície pública.
- View somente leitura para `anon` e `authenticated`.
- Tabelas base permanecem fechadas ao visitante.
- `commander_id`, `invite_code`, `rules`, `commander_cut_pct` e dados dos membros ficam fora da view.
- Funções de slug não são executáveis pela API.
- Foi registrada resposta HTTP 200 com chave anônima e lista vazia quando não havia Espaçonave pública.

### 2.3 Controle público e privado

- Card “Página pública da Espaçonave” disponível nos ajustes para o comandante.
- Botão para tornar a Espaçonave pública ou privada, em português e inglês, nos temas claro e escuro.
- Endereço `/spaceships/[slug]` exibido para leitura quando a página está pública.
- Server action `setSpaceshipPublic` grava `spaceships.is_public` e filtra por `commander_id`.
- `getSpaceshipsDashboardData` devolve `is_public` e `slug`.
- A implementação foi registrada fora da `stage` e ainda precisa de PR e integração.

### 2.4 Segurança

- Slug inválido, Espaçonave inexistente e Espaçonave privada retornam a mesma página 404.
- A resposta pública usa somente o DTO com lista branca de campos.
- URLs de avatar e banner são aceitas somente quando pertencem ao Storage público autorizado.
- JSON-LD escapa `<` para impedir fechamento indevido da tag `<script>`.
- Somente o comandante pode alterar a visibilidade da Espaçonave.

### 2.5 Portfólio, Tripulação e proposta

- As abas Portfólio e Tripulação foram implementadas visualmente.
- A integração das abas com dados reais permanece pendente.
- Até a integração, elas não devem ser apresentadas como funcionalidades completas nem como prova de consentimento aplicado em produção.
- O botão “Fazer Proposta” direciona provisoriamente para `/register`; o fluxo autenticado e anônimo ainda não foi implementado.

## 3. Design System

- `Button`, `ButtonLink`, `Card`, `CardTitle`, `Badge` e `Tabs` adicionados em `src/components/ui/`.
- Navegação por teclado adicionada às Tabs.
- Tokens de cor e elevação definidos para temas claro e escuro.
- Classe de escopo do tema e anéis de foco adicionados.
- A página pública passou a usar os componentes compartilhados.
- Tokens foram movidos de `public-spaceship.css` para `tokens.css`.
- A documentação foi registrada em `startellite-frontend/docs/design-system.md`.
- Componentes, tokens e Storybook/equivalente restantes ainda precisam ser concluídos.

## 4. Mocks, testes e documentação

- Mock de `public_spaceship_profiles` criado para execução local sem credenciais de produção ou acesso ao Supabase.
- `PUBLIC_SPACESHIP_MOCK=1` habilita dados fictícios no desenvolvimento e é ignorado em produção.
- Foram registrados testes para perfis público, privado, inexistente e slug inválido.
- Foram registrados testes para campos proibidos, anonimização e URLs restritas ao Storage autorizado.
- O registro técnico informa **36 testes aprovados** e typecheck aprovado.
- O lint direcionado ao arquivo alterado e a verificação de diff foram registrados como aprovados.
- O setup local documenta variáveis de ambiente, comandos de validação e uso de mocks.
- `.env`, `.env.*`, `.env.local` e `.vercel` permanecem ignorados pelo Git.
- Nenhuma chave `service_role`, token da Vercel ou credencial de alto nível foi registrada no código ou nos testes.
- As migrations e a view não são alteradas pelos testes locais.

Os links das execuções e a cobertura específica da rota e de `setSpaceshipPublic` ainda precisam ser confirmados. Até essa confirmação, os testes permanecem como implementação relatada, não como aceite final.

## 5. Referências técnicas registradas

| Data | Entrega | Branch, commit ou merge registrado | Integração registrada |
|---|---|---|---|
| 09/10/2026 | Página pública de Espaçonaves | `feat/st-016-spaceship-public-page`; `e0974a9` | `stage` |
| 10/10/2026 | Campos públicos | `feat/st-014-spaceship-public-fields`; `f6edeac` | `stage` |
| 10/10/2026 | View pública | `feat/st-015-public-spaceship-view`; `eeb58da` | `stage` |
| 10/10/2026 | Design System | `feat/st-020-ui-primitives`; `610e9b9` | `stage` |
| 11/10/2026 | Ajustes visuais | `005c7ba`, `ba9dad7`; merge `7c08c06` | `stage` |
| 11/10/2026 | Controle público/privado | `feat/st-019-spaceship-public-toggle`; `512705e` | Fora da `stage`; PR pendente |

## 6. Pendências para validação ou conclusão

- anexar branches, PRs, commits e execuções da CI em links acessíveis;
- confirmar a integração dos commits registrados com a `stage` atual;
- resolver ou documentar definitivamente o bloqueio da Vercel;
- confirmar lint completo e checks obrigatórios na CI;
- integrar o controle público/privado;
- integrar dados reais e consentimentos de Portfólio e Tripulação;
- implementar o fluxo completo de “Fazer Proposta”;
- remover ou delimitar definitivamente os mocks antes da entrega final;
- corrigir acentuação restante das especialidades;
- concluir Design System e documentação visual;
- executar demonstração reproduzível e registrar o aceite funcional.
