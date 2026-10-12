# Funcionalidades e critérios de aceite

Este registro acompanha o requisito de listar funcionalidades concluídas e seus critérios. **Até a atualização documental de 12/10/2026, nenhuma conclusão técnica foi comprovada pelos arquivos disponíveis.** A equipe deve preencher evidência, resultado e responsável pelo aceite após verificar a aplicação. “Critério definido” não significa “critério atendido”.

| Funcionalidade candidata | Critérios mínimos para marcar como concluída | Evidência | Resultado |
|---|---|---|---|
| Orbitinho: dúvidas de uso | Responde perguntas prioritárias sobre Satélite, Espaçonave, projetos e épicos conforme fontes aprovadas; diferencia incerteza; não apresenta dado privado | Pendente: fonte aprovada, exemplos de perguntas/respostas e demonstração | Não verificado |
| Orbitinho: orientação de página | Para perguntas do tipo “onde faço X?”, aponta destino existente e correto; destino ambíguo pede esclarecimento | Pendente: exemplos e demonstração | Não verificado |
| Orbitinho: navegação por texto | Comando para destino acordado abre a rota correta; comando inválido não navega | Pendente: PR/commit e demonstração | Não verificado |
| Orbitinho: navegação por voz | Comando de voz usa os mesmos destinos do texto quando o navegador permite; falha de reconhecimento não navega | Pendente: vídeo ou demonstração em navegador compatível | Não verificado |
| Orbitinho: consulta pessoal | A identidade é validada no servidor; só dados do próprio usuário são retornados; tentativa de consultar terceiros é negada | Pendente: revisão de autorização e demonstração com contas de teste | Não verificado |
| Espaçonave: página pública | URL por slug apresenta capa, perfil, descrição e competências com identidade escura/azul; funciona em desktop e mobile | Pendente: URL de homologação, PR/commit e capturas | Não verificado |
| Espaçonave: privacidade | Perfil privado/inexistente não mostra dados; página usa somente lista branca; clientes e tripulantes aparecem apenas com consentimento | Pendente: contrato de dados aprovado e revisão técnica | Não verificado |
| Espaçonave: portfólio e tripulação | Trabalhos e membros autorizados aparecem; estados vazio/erro são compreensíveis; teclado percorre os controles | Pendente: demonstração e revisão de consentimento | Não verificado |

## Registro de aceite a preencher pela equipe

Para cada funcionalidade demonstrada, registrar:

- **Link da mudança:** PR ou commit;
- **Ambiente/URL:** homologação, sem credenciais no documento;
- **Evidência:** captura, gravação curta ou passos reproduzíveis;
- **Critérios observados:** atendidos, não atendidos e ressalvas;
- **Validação:** nome e data do responsável técnico e de Victor como PO; validação do cliente quando envolver decisão de negócio, exposição pública ou nomenclatura.

Uma funcionalidade só deve mudar para **Concluída** se houver prova de funcionamento, critérios atendidos e aceite funcional. O `DEFINITION_OF_DONE.md` da Entrega 1 também prevê PR revisável, checks e revisão de privacidade.
