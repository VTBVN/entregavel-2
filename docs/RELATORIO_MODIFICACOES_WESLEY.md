# Relatório de modificações — Wesley

> Cópia documental de `RELATORIO_MODIFICACOES.md`, fornecido pela equipe. Os links de PR, commits e execuções da CI ainda precisam ser adicionados ao backlog.

## Escopo

Este documento consolida as alterações realizadas no fluxo de CI, Sandbox e perfil público de Espaçonaves, excluindo o bloqueio externo atualmente identificado na Vercel.

## CI e Sandbox

- O workflow `.github/workflows/quality.yml` foi separado em jobs independentes de lint, typecheck, testes e build.
- Pull Requests direcionados à branch `stage` executam os checks de qualidade.
- Pushes para `stage` executam os checks e, depois do build, tentam publicar no Sandbox.
- O deploy valida `VERCEL_TOKEN`, `VERCEL_ORG_ID` e `VERCEL_PROJECT_ID` antes de continuar.
- O deploy tenta vincular explicitamente a organização e o projeto Vercel, evitando detecção automática de outro projeto.
- O workflow usa o Environment `Production – startellite-sandbox`.

## Perfil público de Espaçonaves

- Foi adicionada a opção de tornar uma Espaçonave pública ou privada.
- A página pública usa a rota `/spaceships/[slug]`.
- O acesso público consulta a view `public_spaceship_profiles` com a chave anônima.
- Perfis privados, inexistentes ou com slug inválido não são exibidos.
- A resposta pública usa um DTO com lista branca de campos.
- Campos internos, como `commander_id`, `invite_code`, e-mails e dados sensíveis da tripulação, não são enviados ao cliente.
- URLs de imagens são aceitas somente quando pertencem ao Storage público do próprio projeto Supabase.
- Foram adicionadas as abas públicas de Portfólio e Tripulação.
- Dados de portfólio e nomes da tripulação respeitam o consentimento exposto pela view.

## Mocks e testes

- Foi criado um mock de `public_spaceship_profiles` para execução local sem credenciais de produção ou acesso ao Supabase.
- Foram cobertos os cenários de perfil público, privado, slug inválido e inexistente.
- Foram adicionados testes para campos proibidos no DTO.
- Foram adicionados testes para anonimização da tripulação e do portfólio.
- Foram adicionados testes para aceitar imagens somente do Storage autorizado.

## Documentação e segurança

- O setup local documenta variáveis de ambiente, comandos de validação e uso de mocks.
- Arquivos `.env`, `.env.*`, `.env.local` e `.vercel` permanecem ignorados pelo Git.
- Nenhuma chave de service role, token da Vercel ou credencial de alto nível foi adicionada ao código ou aos testes.
- As migrations e a view pública continuam sendo responsabilidade do ambiente Supabase já configurado pelo cliente; os testes locais não tentam alterá-las.

## Validação realizada

- Testes: **36 testes aprovados**.
- Typecheck: **aprovado**.
- Teste direcionado do lint no arquivo alterado: **aprovado**.
- Verificação de diff: **sem erro de formatação**.
- O lint completo deve ser confirmado na CI, pois a execução local é muito demorada e o repositório possui muitos avisos preexistentes.

## Pendência conhecida

O deploy da Vercel ainda pode falhar com `User not found (404)`. Esse problema é externo ao código validado e indica que o token, a organização ou o projeto Vercel ainda precisam ser confirmados pelo responsável do Sandbox.

Essa pendência não altera os resultados de lint, typecheck, testes ou build.
