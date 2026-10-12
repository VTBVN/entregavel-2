# Backlog atualizado — marco de 11/10/2026

**Atualização documental:** 12/10/2026. **Fonte de prioridade:** reunião de 06/10/2026 com Pedro Antonio Silva; requisitos e plano semanal da Entrega 1 como apoio. O alvo de 11/10 já passou; esta tabela registra o recorte planejado, não certifica o progresso da equipe. Todos os status técnicos permanecem **a confirmar** até receber evidências do quadro, código e demonstração.

P0 = indispensável para demonstrar ou desbloquear o recorte; P1 = importante para qualidade e documentação; P2 = continuidade posterior. Responsáveis são **propostos** conforme o quadro anterior, sujeitos a confirmação por Victor e equipe.

| ID | Frente | Item e resultado esperado | Pri. | Responsável proposto | Status |
|---|---|---|---|---|---|
| E2-01 | Coordenação | Confirmar acessos a repositório, quadros, épicos e ambiente | P0 | Victor + Pedro (cliente) | A confirmar |
| E2-02 | Coordenação | Conferir cards existentes e atribuir responsáveis sem duplicar tarefas | P0 | Victor | A confirmar |
| E2-03 | Coordenação | Reunir evidências e apresentar o recorte funcional | P0 | Victor + equipe | A confirmar |
| E2-18 | Orbitinho | Mapear rotas, voz, fontes de resposta e autorização existentes | P0 | Pedro Pereira + Thiago | A confirmar |
| E2-19 | Orbitinho | Aprovar intents, perguntas prioritárias e limites | P0 | Pedro Pereira + Thiago; aceite Victor/cliente | A confirmar |
| E2-20 | Orbitinho | Responder dúvidas públicas de uso com fonte e incerteza explícita | P0 | Pedro Pereira | A confirmar |
| E2-21 | Orbitinho | Navegação digitada para destinos acordados | P0 | Thiago; revisão Pedro Pereira | A confirmar |
| E2-22 | Orbitinho | Voz aciona os mesmos destinos quando suportada | P1 | Thiago + Pedro Pereira | A confirmar |
| E2-23 | Orbitinho | Consulta do próprio usuário com autorização no servidor | P1 | Pedro Pereira + Thiago | A confirmar |
| E2-24 | Orbitinho | Avaliar respostas, navegação, ambiguidades e acesso indevido | P0 | Thiago; revisão Pedro Pereira | A confirmar |
| E2-12 | Espaçonave | Aprovar conteúdo público, consentimentos e contrato de dados | P0 | Pedro Pereira + Guilherme; aceite Victor/cliente | A confirmar |
| E2-13 | Espaçonave | Expor somente dados aprovados por slug; privado/inexistente sem vazamento | P0 | Wesley + Pedro Pereira | A confirmar |
| E2-14 | Espaçonave | Página pública inicial demonstrável por URL | P0 | Guilherme | A confirmar |
| E2-15 | Espaçonave | Capa, imagem de perfil, nome e descrição em tema escuro/azul | P0 | Guilherme | A confirmar |
| E2-16 | Espaçonave | Projetos, missões e tripulação somente com consentimento | P1 | Guilherme; revisão Pedro Pereira | A confirmar |
| E2-17 | Espaçonave | Estados de erro/vazio, mobile e navegação por teclado | P1 | Guilherme + Thiago | A confirmar |
| E2-10 | Visual | Aprovar conceito visual e componentes necessários | P1 | Guilherme; alinhamento Victor/cliente | A confirmar |
| E2-11 | Visual | Usar componentes reutilizáveis no recorte público | P1 | Guilherme | A confirmar |
| E2-04 | Homologação | Executar aplicação local e registrar setup real | P0 | Wesley | A confirmar |
| E2-05 | Homologação | Isolar schema e dados fictícios do ambiente de produção | P0 | Wesley; revisão Pedro Pereira | A confirmar |
| E2-06 | Homologação | Documentar reconstrução e limites do ambiente | P1 | Wesley | A confirmar |
| E2-07 | Qualidade | CI em PRs para lint, typecheck e testes | P1 | Wesley + Thiago | A confirmar |
| E2-08 | Qualidade | Verificar privacidade, RLS, slug e consentimento | P0 | Wesley; revisão Pedro Pereira | A confirmar |
| E2-09 | Qualidade | Regressão do MVP e registro de evidências | P0 | Thiago + Wesley | A confirmar |

## Ordem recomendada para fechar a entrega

1. Victor confirma acessos, responsáveis e estado real dos cards com a equipe.
2. Equipe informa quais fluxos já existem e fornece PR, commit ou ambiente de demonstração.
3. Critérios de privacidade e autorização são avaliados antes de publicar ou mostrar dados reais.
4. Victor realiza o aceite funcional e registra resultado em [Funcionalidades e aceite](FUNCIONALIDADES_E_ACEITE.md).
5. Itens incompletos recebem nova data e entram no planejamento final.

## Mudanças de prioridade em relação ao plano anterior

- O Orbitinho passa a ser a primeira experiência da revisão: respostas corretas sobre a plataforma e indicação de páginas, conforme fala do cliente em 06/10, 30:32–35:31.
- A página pública é reduzida a um primeiro portfólio visual; consentimentos e dados autorizados continuam como condição para integração, conforme 37:15–42:25.
- Acesso aos quadros e permissões aparece como bloqueio explícito, conforme 04:47–16:09 e 44:02–01:02:36.
- Voz, consulta pessoal, acabamento e componentes avançados continuam relevantes, mas a demonstração de 11/10 deve declarar qualquer parte ainda não entregue.

**Não inferir conclusão:** a reunião de 06/10 descreve intenção e impedimentos. Ela não é evidência de entrega técnica em 11/10.
