# M02 — Aquisição, exploração e qualidade de dados

## Objetivo geral

Adquirir, compreender, avaliar, preparar e validar conjuntos de dados para uso analítico, preservando origem, integridade e rastreabilidade.

## Pré-requisitos de execução

M00 e M01 concluídos e aprovados.

## Resultado esperado

Um conjunto de dados confiável e documentado, acompanhado de diagnóstico que permita decidir sua adequação aos requisitos de negócio.

> Um dataset estar disponível, carregar sem erros ou não conter valores nulos não significa que seja adequado à análise.

## Unidades

### M02-U00 — Fontes de dados e proveniência

Fontes primárias, secundárias, públicas, privadas e sintéticas; autoridade, documentação, licença, atualização, cobertura, metadados e correspondência com requisitos.

**Entrega:** ficha de proveniência e justificativa de seleção.

### M02-U01 — Aquisição e armazenamento

Downloads, CSV, JSON, codificação, delimitadores, compressão, estrutura de diretórios, preservação do original, checksums, versionamento, reexecução e idempotência.

**Entrega:** dados originais preservados ou procedimento reproduzível de aquisição.

### M02-U02 — Estrutura e exploração inicial

Tipos físicos e semânticos, identificadores, granularidade, cardinalidade, domínios, distribuições, cobertura temporal e geográfica e consistência entre fontes.

**Entrega:** relatório de inspeção estrutural.

### M02-U03 — Diagnóstico de qualidade

Completude, ausência, duplicidade, unicidade, validade, integridade, atualidade, valores extremos, unidades, convenções e impactos analíticos.

**Entrega:** relatório com extensão, evidências e consequências dos problemas.

**Questão obrigatória:** por que excluir todas as linhas com valores ausentes pode introduzir distorções?

### M02-U04 — Preparação e transformação

Padronização, conversões, categorias, duplicatas, ausentes, exclusões, datas, transformações determinísticas, preservação do original e testes antes e depois.

**Entrega:** processo reproduzível com regras, justificativas e verificações.

### M02-U05 — Carga e validação no PostgreSQL

Recepção e preparação, tipos, importação controlada, transações, integridade, falhas parciais, contagens, agregações de controle e reexecução.

**Entrega:** dados carregados, scripts e evidências de validação.

A modelagem dimensional definitiva permanece no M03.

### M02-U06 — Adequação analítica e limitações

Rastreabilidade entre requisitos e atributos, universo, representatividade, granularidade, cobertura temporal, relacionamentos, comparabilidade, lacunas e hipóteses.

**Entrega:** matriz de adequação com requisitos atendidos, parciais ou inviáveis.

### M02-U07 — Documentação e homologação

Dicionário, transformações, fontes, qualidade, reprodução, testes, limitações residuais, critérios de homologação e controle de versão.

**Entrega:** pacote de dados homologado com scripts, testes, documentação e limitações.

## Laboratório

O M02 continuará o problema definido no M01. Dados públicos podem ser acompanhados de cópias didáticas com defeitos artificiais, desde que claramente identificadas.

O conjunto deverá permitir estudar relacionamentos, categorias, datas, medidas, cobertura e qualidade, com documentação suficiente para distinguir características legítimas de erros introduzidos.

## Entregáveis do módulo

| Entregável | Finalidade |
|---|---|
| Catálogo de fontes | Origem, versão e condições de uso. |
| Dados ou aquisição | Recuperação das fontes. |
| Diagnóstico | Estrutura, qualidade e limitações. |
| Preparação | Reprodução das transformações. |
| Scripts de carga | Reconstrução no PostgreSQL. |
| Testes e evidências | Integridade e consistência. |
| Dicionário | Semântica dos atributos. |
| Matriz de adequação | Relação entre dados e requisitos. |

Os itens não precisam ser arquivos separados quando a responsabilidade estiver clara e versionável.

## Limites

| Tema | Tratamento |
|---|---|
| Definição do problema | M01; revisão controlada no M02. |
| Qualidade e preparação | M02. |
| Recepção e carga | M02. |
| Esquema estrela e dimensões | M03. |
| SQL analítico avançado | M04. |
| KPIs finais | M05. |
| Perguntas no Metabase | M06. |

SQL, Python e Pandas são instrumentos do módulo, não fins isolados.
