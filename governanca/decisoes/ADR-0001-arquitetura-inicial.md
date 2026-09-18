# ADR-0001 — Arquitetura inicial de governança

- **Data:** 2026-09-18
- **Estado:** aprovado
- **Responsável:** Orion
- **Aprovador:** Bruno

## Contexto

A formação será executada em Works separados e ao longo de várias sessões. Conversas isoladas não oferecem rastreabilidade suficiente para preservar currículo, estado, avaliações e decisões.

A aprovação antecipada de todos os módulos também criaria risco de uma arquitetura extensa não validada pela experiência real.

## Decisão

Adotar:

- GitHub como registro oficial;
- uma fonte canônica para cada responsabilidade;
- `estado-formacao.yaml` como snapshot operacional;
- elaboração curricular progressiva em ciclos;
- M00, M01 e M02 como Ciclo 01;
- branches e pull requests para mudanças estruturais;
- registros de progresso, sessões, revisões e ADRs;
- Orion como responsável por governança e administração acadêmica;
- Bruno como aluno e autor das atividades avaliativas.

## Consequências

### Positivas

- retomada independente do histórico da conversa;
- mudanças auditáveis;
- responsabilidades explícitas;
- redução de divergências;
- currículo ajustável com controle.

### Custos

- necessidade de atualizar registros;
- checkpoints adicionais;
- revisão formal de alterações estruturais.

Esses custos são aceitos porque protegem continuidade, coerência e reprodutibilidade.
