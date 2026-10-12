# Backlog replanejado — Wesley e Guilherme

**Atualização:** 12/10/2026.

**Equipe técnica restante:** Wesley Lima Silva e Guilherme Kenzo Taba Nakamura.

**Fontes:** reunião com o cliente em 06/10/2026, documentos da Entrega 1 e o relatório de modificações fornecido por Wesley.

Victor Barbosa Viana permanece como Product Owner e Scrum Master para priorização, alinhamento e aceite funcional, sem entrar na capacidade de implementação. Pedro Pereira e Thiago Brasileiro de Sousa foram retirados das atribuições técnicas deste backlog.

## Convenções

- **P0:** necessário para demonstrar ou fechar a Entrega 2.
- **P1:** necessário para consolidar qualidade e documentação.
- **P2:** pode seguir para a entrega final.
- **Relatado como concluído:** consta no relatório de Wesley, mas ainda deve receber link de PR ou commit.
- **Pendente de preenchimento:** Guilherme deve informar andamento, evidência e limitações antes do aceite.
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

## 3. Frente de Espaçonaves — pendente de preenchimento por Guilherme

O relatório de Wesley descreve uma base técnica para perfis públicos, DTO, privacidade, Portfólio e Tripulação. Conforme orientação atual da equipe, esta frente permanece aberta até Guilherme registrar sua implementação e as evidências. Nenhum item abaixo deve ser marcado como concluído apenas com o relatório de Wesley.

| ID | Item | Pri. | Responsável | Status | Guilherme deve preencher |
|---|---|---:|---|---|---|
| G-01 | Informar o estado real da rota pública `/spaceships/[slug]` | P0 | Guilherme | Pendente de preenchimento | Branch/PR, commit, telas prontas e limitações |
| G-02 | Informar o estado de capa, imagem de perfil, nome e descrição | P0 | Guilherme | Pendente de preenchimento | Componentes alterados, capturas e comportamento mobile |
| G-03 | Informar o estado das abas Portfólio e Tripulação | P0 | Guilherme | Pendente de preenchimento | Dados exibidos, estados vazio/erro e consentimentos respeitados |
| G-04 | Validar identidade visual escura, azul e espacial | P1 | Guilherme | Pendente de preenchimento | Capturas em desktop/mobile e decisões visuais |
| G-05 | Validar responsividade, teclado, foco e textos alternativos | P1 | Guilherme | Pendente de preenchimento | Checklist ou demonstração dos cenários |
| G-06 | Confirmar integração do frontend com a superfície pública criada por Wesley | P0 | Guilherme | Pendente de preenchimento | URL de homologação ou execução local com mock |
| G-07 | Registrar bugs, limitações e trabalho restante da página pública | P1 | Guilherme | Pendente de preenchimento | Lista priorizada para a entrega final |

## 4. Tarefas de Guilherme fora da frente de Espaçonaves

| ID | Item | Pri. | Critério de conclusão | Status |
|---|---|---:|---|---|
| G-08 | Revisar a interface do Orbitinho para perguntas e navegação por texto | P0 | Usuário entende o que pode perguntar; sucesso, ambiguidade e erro têm retorno claro | A fazer |
| G-09 | Integrar no frontend os destinos priorizados do Orbitinho | P0 | Comandos aprovados abrem as rotas corretas e não navegam em caso ambíguo | A fazer |
| G-10 | Validar o fluxo de voz quando suportado pelo navegador | P1 | Voz usa as mesmas intenções do texto; falha de reconhecimento não dispara rota errada | A fazer |
| G-11 | Preparar capturas e roteiro visual da demonstração | P0 | Evidências mostram somente dados fictícios ou autorizados | A fazer |

## 5. Fechamento conjunto

| ID | Item | Pri. | Responsáveis | Critério de conclusão | Status |
|---|---|---:|---|---|---|
| WG-01 | Integrar as mudanças de Wesley e Guilherme no ambiente de demonstração | P0 | Wesley + Guilherme | Build e fluxos prioritários executam no mesmo ambiente | A fazer |
| WG-02 | Executar regressão do recorte | P0 | Wesley + Guilherme | CI, Orbitinho e página pública são verificados; falhas ficam registradas | A fazer |
| WG-03 | Atualizar funcionalidades e critérios de aceite | P0 | Wesley + Guilherme | Cada item demonstrado tem evidência e resultado real | A fazer |
| WG-04 | Entregar a Victor o roteiro, links e pendências para aceite funcional | P0 | Wesley + Guilherme | Victor consegue reproduzir a demonstração e registrar o aceite | A fazer |

## Ordem de execução

1. Wesley adiciona os links que comprovam as alterações já relatadas e trata o bloqueio da Vercel com o responsável pelo Sandbox.
2. Guilherme preenche toda a seção de Espaçonaves com o estado real e suas evidências.
3. Wesley fecha backend, autorização e testes do Orbitinho; Guilherme fecha interface e navegação.
4. Os dois integram, executam a regressão e entregam as evidências para aceite de Victor.

## Distribuição resumida

| Pessoa | Responsabilidade principal |
|---|---|
| Wesley | CI, Sandbox, segurança, testes, backend e autorização do Orbitinho |
| Guilherme | Espaçonaves, interface, experiência do Orbitinho e evidências visuais |
| Wesley + Guilherme | Integração, regressão e preparação da demonstração |
