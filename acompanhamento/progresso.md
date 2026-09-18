# Progresso da formação

## Estado resumido

| Marco | Descrição | Situação |
|---|---|---|
| CUR-01 | Arquitetura curricular geral | Aprovado |
| CUR-02 | Especificação do M00 | Aprovado |
| CUR-03 | Especificação do M01 | Aprovado |
| CUR-04 | Especificação do M02 | Aprovado |
| GOV-01 | Arquitetura de governança | Aprovado |
| GOV-02 | Implantação do repositório oficial | Concluído |
| M00 | Preparação e infraestrutura | Em andamento |
| M00-U00 | Diagnóstico técnico e requisitos | Aprovado |
| M00-U01 | Arquitetura e funcionamento do ambiente | Em andamento |

## Registro inicial — 2026-09-18

Foi adotado o desenvolvimento em ciclos para evitar detalhar M00 a M11 sem validação prática. O primeiro ciclo contém M00, M01 e M02.

Bruno delegou a Orion a responsabilidade por governança, currículo, avaliação, continuidade, rastreabilidade e administração acadêmica. Bruno participa como aluno e autor das entregas avaliativas.

O repositório público `CorreaBrunoMiguel/formacao-bi-dashboards` foi criado.

## Liberação do M00 — 2026-09-18

A implantação inicial foi revisada e integrada pela PR #1. A branch de implantação foi removida após o merge.

O GOV-02 está concluído. A formação está liberada para iniciar o M00-U00 em um Work exclusivo, seguindo `INICIAR-AQUI.md`.

## Abertura do M00-U00 — 2026-09-18

O clone local e o ambiente foram diagnosticados sem instalação ou alteração de serviços. Docker, Compose e PostgreSQL estão disponíveis. Foram registradas restrições de memória, ocupação da porta 5432 pelo PostgreSQL local e recursos Docker preexistentes.

O diagnóstico factual está em `ambiente/diagnostico.md`.

## Conclusão do M00-U00 — 2026-09-18

Os requisitos foram classificados, as restrições foram registradas e nenhum bloqueio impeditivo foi identificado. A revisão formal está em `acompanhamento/revisoes/2026-09-18-m00-u00.md`.

A M00-U00 foi aprovada. A formação está liberada para iniciar a M00-U01 após a integração do checkpoint no branch `main`.

## Abertura do M00-U01 — 2026-09-18

A unidade foi aberta com o bloco conceitual sobre host, Docker Engine, imagem e container. A primeira verificação guiada confirmou compreensão parcial e identificou a necessidade de consolidar o compartilhamento do kernel do host.

Nenhuma alteração de infraestrutura foi realizada e a entrega acadêmica ainda não foi iniciada.
