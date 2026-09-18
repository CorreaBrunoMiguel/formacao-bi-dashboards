# Protocolo de continuidade

## Abertura de sessão

Orion deve:

1. consultar o estado oficial;
2. verificar se a branch e o commit registrados ainda correspondem ao repositório;
3. ler os documentos do módulo ativo;
4. consultar o progresso e a evidência mais recente;
5. declarar objetivo, entrega, critério de conclusão e limites da sessão.

Se houver divergência entre conversa e repositório, a atividade fica suspensa até a divergência ser resolvida e registrada.

## Durante a sessão

- Trabalhar em uma unidade principal por vez.
- Separar demonstração, exercício guiado e avaliação.
- Registrar decisões que alterem regra, escopo ou arquitetura.
- Tratar ideias fora do escopo como itens adiados, sem incorporá-las silenciosamente.
- Solicitar saídas reais de comandos e testes quando necessárias à validação.

## Encerramento

Orion deve consolidar:

- resumo objetivo;
- entregas e caminhos;
- evidências verificadas;
- resultado da avaliação;
- correções pendentes;
- bloqueios;
- próxima ação principal;
- alterações necessárias no estado e no progresso;
- checkpoint Git correspondente.

## Interrupções

Se uma sessão terminar sem encerramento formal, o estado anterior permanece válido. Na retomada, a primeira tarefa será reconstruir e validar o que efetivamente ocorreu antes de atualizar o repositório.

## Transferência para outro Work

O novo Work deve receber o repositório como fonte e seguir `INICIAR-AQUI.md`. Não é necessário reproduzir manualmente a conversa anterior quando os registros estiverem atualizados.

## Conflitos de informação

A ordem de precedência é:

1. estado oficial vigente;
2. especificação curricular aprovada;
3. ADR aplicável;
4. revisão ou avaliação registrada;
5. progresso cronológico;
6. conversa.
