# Funcionalidades e critérios de aceite

Este registro acompanha o requisito de listar funcionalidades concluídas e seus critérios. O relatório de Wesley registra validações técnicas; o changelog de Guilherme registra branches e commits da página pública. Portfólio e Tripulação possuem interface, mas continuam sem integração.

| Funcionalidade candidata | Critérios mínimos para marcar como concluída | Evidência | Resultado |
|---|---|---|---|
| CI: checks independentes | Workflow separa lint, typecheck, testes e build; PRs para `stage` executam os checks | Relatório de Wesley; faltam PR/commit e execução da CI | Relatado como implementado |
| Sandbox: deploy após checks | Push para `stage` executa checks e tenta deploy no projeto correto, validando variáveis antes de publicar | Relatório de Wesley; Vercel retorna `User not found (404)` | Implementado com bloqueio externo |
| Qualidade e segurança | Mocks não usam produção; segredos ficam fora do Git; testes cobrem privacidade, anonimização e imagens autorizadas | Relatório informa 36 testes, typecheck e lint direcionado aprovados | Relatado como implementado |
| Orbitinho: dúvidas de uso | Responde perguntas prioritárias sobre Satélite, Espaçonave, projetos e épicos conforme fontes aprovadas; diferencia incerteza; não apresenta dado privado | Pendente: fonte aprovada, exemplos de perguntas/respostas e demonstração | A fazer — Wesley |
| Orbitinho: orientação de página | Para perguntas do tipo “onde faço X?”, aponta destino existente e correto; destino ambíguo pede esclarecimento | Pendente: exemplos e demonstração | A fazer — Wesley/Guilherme |
| Orbitinho: navegação por texto | Comando para destino acordado abre a rota correta; comando inválido não navega | Pendente: PR/commit e demonstração | A fazer — Guilherme |
| Orbitinho: navegação por voz | Comando de voz usa os mesmos destinos do texto quando o navegador permite; falha de reconhecimento não navega | Pendente: vídeo ou demonstração em navegador compatível | A fazer — Guilherme |
| Orbitinho: consulta pessoal | A identidade é validada no servidor; só dados do próprio usuário são retornados; tentativa de consultar terceiros é negada | Pendente: revisão de autorização e demonstração com contas de teste | A fazer — Wesley |
| Espaçonave: página pública | URL por slug apresenta capa, perfil, descrição e competências; perfil inválido ou privado retorna 404 uniforme | Commits `e0974a9`, `005c7ba`, `ba9dad7`; merge `7c08c06` na `stage` | Implementado |
| Espaçonave: campos e view pública | `is_public` e `slug` existem; view expõe somente contrato aprovado e tabelas base permanecem fechadas | Commits `f6edeac` e `eeb58da`; view respondeu 200 com chave anônima | Implementado |
| Espaçonave: controle público/privado | Somente comandante altera visibilidade; endereço público aparece em modo leitura | Commit `512705e`; falta PR para `stage` | Implementado, aguardando integração |
| Espaçonave: Portfólio | Aba apresenta trabalhos autorizados e estados vazio, carregamento e erro | Interface criada; integração de dados ainda ausente | Parcial — sem integração |
| Espaçonave: Tripulação | Aba apresenta somente membros autorizados e trata estados vazio/erro | Interface criada; integração de dados ainda ausente | Parcial — sem integração |
| Design System | Página usa Button, Card, Badge e tokens; Tabs permite teclado | Commit `610e9b9`, já na `stage` | Implementado parcialmente; componentes restantes seguem pendentes |

## Registro de aceite a preencher pela equipe

Para cada funcionalidade demonstrada, registrar:

- **Link da mudança:** PR ou commit;
- **Ambiente/URL:** homologação, sem credenciais no documento;
- **Evidência:** captura, gravação curta ou passos reproduzíveis;
- **Critérios observados:** atendidos, não atendidos e ressalvas;
- **Validação:** nome e data do responsável técnico e de Victor como PO; validação do cliente quando envolver decisão de negócio, exposição pública ou nomenclatura.

Uma funcionalidade só deve mudar para **Concluída** se houver prova de funcionamento, critérios atendidos e aceite funcional. O `DEFINITION_OF_DONE.md` da Entrega 1 também prevê PR revisável, checks e revisão de privacidade.
