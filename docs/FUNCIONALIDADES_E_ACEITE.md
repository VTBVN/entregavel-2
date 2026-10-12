# Funcionalidades e critérios de aceite

Este registro acompanha o requisito de listar funcionalidades concluídas e seus critérios. O relatório de Wesley registra alterações e validações técnicas, mas os links de PR, commits e execuções da CI ainda precisam ser anexados. A parte de Espaçonaves permanece pendente de preenchimento por Guilherme, mesmo quando o relatório descreve uma base técnica relacionada à frente.

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
| Espaçonave: página pública | URL por slug apresenta capa, perfil, descrição e competências com identidade escura/azul; funciona em desktop e mobile | Guilherme deve preencher URL, PR/commit, capturas e limitações | Pendente de preenchimento |
| Espaçonave: privacidade | Perfil privado/inexistente não mostra dados; página usa somente lista branca; clientes e tripulantes aparecem apenas com consentimento | Guilherme deve preencher integração e evidências; relatório de Wesley descreve a base técnica | Pendente de preenchimento |
| Espaçonave: portfólio e tripulação | Trabalhos e membros autorizados aparecem; estados vazio/erro são compreensíveis; teclado percorre os controles | Guilherme deve preencher demonstração, consentimento e acessibilidade | Pendente de preenchimento |

## Registro de aceite a preencher pela equipe

Para cada funcionalidade demonstrada, registrar:

- **Link da mudança:** PR ou commit;
- **Ambiente/URL:** homologação, sem credenciais no documento;
- **Evidência:** captura, gravação curta ou passos reproduzíveis;
- **Critérios observados:** atendidos, não atendidos e ressalvas;
- **Validação:** nome e data do responsável técnico e de Victor como PO; validação do cliente quando envolver decisão de negócio, exposição pública ou nomenclatura.

Uma funcionalidade só deve mudar para **Concluída** se houver prova de funcionamento, critérios atendidos e aceite funcional. O `DEFINITION_OF_DONE.md` da Entrega 1 também prevê PR revisável, checks e revisão de privacidade.
