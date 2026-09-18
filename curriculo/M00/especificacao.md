# M00 — Preparação e infraestrutura

## Objetivo geral

Preparar, compreender, validar e documentar um ambiente local reproduzível para os laboratórios da formação, composto por Docker, PostgreSQL e Metabase.

## Resultado esperado

Um ambiente seguro e operacional que possa ser iniciado, verificado, interrompido e reconstruído por meio de procedimentos documentados.

## Unidades

### M00-U00 — Diagnóstico técnico e requisitos

Identificar sistema operacional, recursos disponíveis, ferramentas existentes, permissões, portas, restrições e requisitos do ambiente.

**Evidência:** diagnóstico registrado e requisitos classificados como atendidos, pendentes ou bloqueados.

### M00-U01 — Arquitetura e funcionamento do ambiente

Compreender a relação entre host, Docker Engine, imagens, containers, redes, volumes, PostgreSQL e Metabase.

**Evidência:** representação da arquitetura e explicação do fluxo de conexão e persistência.

### M00-U02 — Docker e infraestrutura reproduzível

Instalar ou validar Docker e Compose; compreender imagens, containers, portas, volumes, redes, ciclo de vida e configuração declarativa.

**Evidência:** operações essenciais executadas e explicadas, sem depender de comandos memorizados sem compreensão.

### M00-U03 — PostgreSQL e segurança de acesso

Provisionar PostgreSQL, validar conexões, compreender usuários, bancos, portas, variáveis de ambiente, persistência e exposição de credenciais.

**Evidência:** conexão funcional, persistência verificada e segredos ausentes do versionamento.

### M00-U04 — Instalação e configuração do Metabase

Provisionar Metabase, configurar persistência da aplicação e estabelecer conexão controlada com o PostgreSQL.

**Evidência:** serviço acessível, configuração preservada após reinício e origem de dados conectada.

### M00-U05 — Integração, testes e recuperação

Validar comunicação entre serviços, interpretar estado e logs, testar reinícios e reconstrução e diagnosticar falhas controladas.

**Evidência:** testes positivos e negativos, recuperação executada e resultados registrados.

### M00-U06 — Documentação e homologação

Consolidar instalação, operação, diagnóstico, segurança e recuperação em documentação reproduzível.

**Evidência:** um revisor consegue reconstruir e validar o ambiente seguindo o procedimento.

## Metodologia

- explicação conceitual;
- demonstração controlada;
- execução pelo aluno;
- testes positivos e negativos;
- diagnóstico de falhas;
- documentação e revisão.

## Documentação prevista

- esta especificação e sua avaliação;
- `ambiente/README.md`;
- arquivos de configuração criados durante as unidades;
- progresso e evidências de sessão;
- decisões arquiteturais quando necessárias.

## Limites

| Tema | Tratamento |
|---|---|
| PostgreSQL | Instalação, conexão, persistência e segurança necessárias ao ambiente. |
| Docker | Operação e infraestrutura necessária. |
| Metabase | Instalação e configuração inicial. |
| SQL analítico | M04. |
| Modelagem dimensional | M03. |
| Criação de dashboards | M08. |
| Publicação externa | M09. |

Introduções conceituais são permitidas quando necessárias, mas não devem antecipar a formação inteira.
