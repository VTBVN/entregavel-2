# Changelog — Guilherme

> Cópia documental do `CHANGELOG.md` fornecido pela equipe. Conforme informação posterior da equipe, as abas Portfólio e Tripulação possuem interface, mas ainda não estão integradas.

## 11/10/2026 — Botão de tornar a Espaçonave pública ou privada (ST-019)

Branch `feat/st-019-spaceship-public-toggle`, commit `512705e`, enviada ao remoto; ainda não está na `stage` porque falta o PR.

### Adicionado

- Card “Página pública da Espaçonave” nos Ajustes da Espaçonave (`SpaceshipPublicToggle.tsx`), visível somente para o comandante.
- Botão “Tornar pública” ou “Tornar privada”, em português e inglês, nos temas claro e escuro.
- Endereço `/spaceships/[slug]` exibido para leitura quando a página está pública.
- Server action `setSpaceshipPublic` em `src/app/actions/spaceships.ts`, que grava `spaceships.is_public`.
- `getSpaceshipsDashboardData` passou a devolver `is_public` e `slug`.
- Com `PUBLIC_SPACESHIP_MOCK=1`, o painel usa uma Espaçonave fictícia e não grava alterações. O mock é ignorado em produção.

### Segurança

- A action filtra por `commander_id`; somente o comandante pode alterar a visibilidade.

## 11/10/2026 — Ajustes visuais da página pública

Commits `005c7ba` e `ba9dad7`, já na `stage` pelo merge `7c08c06`.

### Alterado

- A página passou a usar a `Navbar` e o `Footer` do site.
- Avatar, nome, números e ação foram reorganizados no topo.
- Botão “Fazer Proposta” leva a `/register` enquanto o fluxo ST-027 não existe.
- “Sobre a tripulação” virou um painel responsivo.
- País e continente aparecem em português.
- Especialidades deixam de aparecer como slug cru.
- Classes do Tailwind em `SpaceshipsTab.tsx` foram normalizadas.

### Removido

- `ThemeToggle` foi removido da página pública e não é usado em outras telas.

## 10/10/2026 — Campos públicos e view (ST-014, ST-015)

Branches `feat/st-014-spaceship-public-fields`, commit `f6edeac`, e `feat/st-015-public-spaceship-view`, commit `eeb58da`, já na `stage`.

### Adicionado

- Migration `20261010121500_spaceship_public_fields.sql` com `is_public` e `slug`.
- Slug gerado do nome, único, validado e estável após criação.
- Migration `20261010123000_public_spaceship_profiles_view.sql` com a view pública e os campos do contrato.
- `member_count` e `completed_missions` na superfície pública.

### Segurança

- View somente leitura para `anon` e `authenticated`.
- Tabelas base continuam fechadas ao visitante.
- `commander_id`, `invite_code`, `rules`, `commander_cut_pct` e dados dos membros ficam fora da view.
- Funções de slug não são executáveis pela API.

### Verificado

- A view respondeu 200 com a chave anônima e lista vazia, pois nenhuma Espaçonave estava pública.

## 10/10/2026 — Design System (ST-013, ST-020)

Branch `feat/st-020-ui-primitives`, commit `610e9b9`, já na `stage`. Documentação em `startellite-frontend/docs/design-system.md`.

### Adicionado

- `Button`, `ButtonLink`, `Card`, `CardTitle`, `Badge` e `Tabs` em `src/components/ui/`.
- Navegação por teclado nas Tabs.
- Tokens de cor e elevação para temas claro e escuro.
- Classe de escopo do tema e anéis de foco.

### Alterado

- Página pública passou a usar os componentes compartilhados.
- Tokens saíram de `public-spaceship.css` para `tokens.css`.

## 09/10/2026 — Página pública da Espaçonave (ST-016)

Branch `feat/st-016-spaceship-public-page`, commit `e0974a9`, já na `stage`. Documentação em `startellite-frontend/docs/pagina-publica-espaconave.md`.

### Adicionado

- Rota `/spaceships/[slug]` renderizada no servidor.
- Metadados por Espaçonave, canonical, OpenGraph, Twitter Card e JSON-LD.
- Leitura da view `public_spaceship_profiles` com chave anônima e contrato Zod.
- Capa, avatar, nome, localização, números, apresentação e especialidades.
- Temas claro e escuro.
- Mock de desenvolvimento com `PUBLIC_SPACESHIP_MOCK=1`, ignorado em produção.

### Segurança

- 404 igual para slug inválido, Espaçonave inexistente ou privada.
- `banner_url` e `avatar_url` aceitos somente quando apontam para o Storage do projeto Supabase.
- JSON-LD escapa `<` para proteger a tag `<script>`.

## Portfólio e Tripulação

- As duas abas foram implementadas visualmente.
- A integração com dados ainda está pendente.
- Até a integração, elas não devem ser apresentadas como funcionalidades completas.

## Pendências

- Abrir o PR do ST-019 para a `stage`.
- Integrar dados de Portfólio e Tripulação.
- Remover ou delimitar o mock antes da entrega final.
- Corrigir a acentuação das especialidades.
- Implementar o fluxo real de “Fazer Proposta”.
- Completar os componentes e tokens restantes do Design System.
- Adicionar testes automatizados para a rota e para `setSpaceshipPublic`.
