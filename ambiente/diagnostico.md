# Diagnóstico técnico do ambiente — M00-U00

## Identificação

- **Unidade:** M00-U00 — Diagnóstico técnico e requisitos
- **Data da coleta:** 2026-09-18
- **Responsável pela execução dos comandos:** Bruno
- **Responsável pela consolidação administrativa:** Orion
- **Origem das evidências:** saídas reais apresentadas durante a sessão de abertura da unidade

Este documento consolida fatos observados no ambiente local. Ele não substitui as
evidências conceituais e práticas exigidas para a avaliação acadêmica.

## Sistema e recursos

| Item | Evidência observada |
|---|---|
| Sistema operacional | Linux Mint 21.3 (Virginia), baseado em Ubuntu 22.04 Jammy |
| Kernel | Linux 6.8.0-138-generic |
| Arquitetura | x86_64, com suporte a 32 e 64 bits |
| Processador | Intel Core i5-6287U, 2 núcleos e 4 threads |
| Virtualização | Intel VT-x disponível |
| Memória | 7,6 GiB totais; 2,6 GiB disponíveis na primeira coleta |
| Swap | 2,0 GiB totais; aproximadamente 1,8 GiB ocupados |
| Armazenamento | 916 GiB totais na partição analisada; 597 GiB disponíveis |

A amostra de `vmstat` apresentou atividade de swap-in e espera de I/O durante
parte da coleta. O resultado indica pressão operacional possível, mas não permite
concluir isoladamente que o ambiente seja inviável. O comportamento deverá ser
reavaliado quando os serviços da formação estiverem em execução.

## Ferramentas e serviços

| Componente | Versão ou estado |
|---|---|
| Git | 2.34.1 |
| Docker Engine — cliente | 29.8.0 |
| Docker Engine — servidor | 29.8.0 |
| Docker Compose | v5.5.1 |
| Cliente PostgreSQL (`psql`) | 18.6 |
| Servidor PostgreSQL local | 14.24 |

O cliente `psql` e o servidor PostgreSQL possuem versões diferentes. A versão
informada por `psql --version` identifica somente o cliente; a versão 14.24 foi
confirmada diretamente no servidor.

## Permissões e inicialização do Docker

- O usuário executor pertence ao grupo `docker`.
- O socket `/var/run/docker.sock` pertence a `root:docker` e permite leitura e
  escrita ao grupo.
- `docker info` foi executado sem `sudo`, comprovando acesso efetivo ao daemon.
- `docker.service` estava `active/running`, embora sua unidade estivesse
  `disabled`.
- `docker.socket` estava `active/running` e `enabled`.

O estado `disabled` do serviço não significa que o Docker esteja parado. Neste
ambiente, o socket habilitado pode ativar o serviço quando um cliente solicita
acesso ao daemon.

## Portas e conectividade

| Porta no host | Situação observada |
|---|---|
| 3000/TCP | Sem listener identificado |
| 5432/TCP | Ocupada pelo PostgreSQL local em `127.0.0.1` |

O servidor PostgreSQL local está configurado com `listen_addresses=localhost`
e porta `5432`. Ele foi alcançado por `pg_isready`.

Uma publicação Docker usa a forma `HOST:CONTAINER`. Enquanto o PostgreSQL local
estiver ativo na porta 5432, um futuro container não poderá publicar a mesma
combinação de endereço e porta no host. Um mapeamento como `5433:5432` usaria
a porta 5433 no host e manteria a porta 5432 dentro do container.

Containers na mesma rede Docker podem usar a porta 5432 em seus próprios
namespaces sem conflito. O Metabase deverá se conectar ao nome do serviço
PostgreSQL e à porta interna 5432, por exemplo `postgres:5432`, caso
`postgres` seja o nome definido posteriormente na configuração.

## Recursos Docker preexistentes

Foram identificados:

- 2 containers PostgreSQL parados;
- 3 imagens;
- 3 volumes locais;
- aproximadamente 14,54 GiB de cache de build recuperável.

Esses recursos podem pertencer a projetos anteriores e não serão removidos nesta
unidade. A análise e eventual limpeza ficam adiadas para M00-U02, com inventário
prévio e proteção de dados persistentes.

## Restrições e riscos

1. A porta 5432 do host já está ocupada pelo PostgreSQL local.
2. A memória total atende ao porte inicial do laboratório, mas a baixa memória
   disponível e a swap ocupada exigem controle de consumo.
3. A pressão de memória e I/O deverá ser medida novamente com PostgreSQL e
   Metabase em containers.
4. Recursos Docker anteriores devem ser preservados até que sua finalidade e
   persistência sejam verificadas.
5. O PostgreSQL local não deve ser encerrado abruptamente nem removido como parte
   deste diagnóstico.

## Matriz de requisitos

| Requisito | Evidência | Classificação | Observação |
|---|---|---|---|
| Sistema Linux x86_64 operacional | Linux Mint 21.3 e kernel 6.8 x86_64 | atendido | Base compatível com Docker Engine |
| Capacidade de virtualização | Intel VT-x informado por `lscpu` | atendido | Disponível no processador |
| Armazenamento suficiente | 597 GiB disponíveis | atendido | Sem bloqueio de capacidade |
| Memória para o laboratório | 7,6 GiB totais e 2,6 GiB disponíveis na coleta | pendente | Exige validação sob carga e orçamento de memória |
| Git disponível | Git 2.34.1 | atendido | Repositório local operacional |
| Docker Engine disponível | Cliente e servidor 29.8.0; daemon acessível | atendido | Acesso sem `sudo` validado |
| Docker Compose disponível | Plugin v5.5.1 | atendido | Comando funcional |
| Permissão de acesso ao Docker | Grupo e socket compatíveis; `docker info` funcional | atendido | Permissão efetiva comprovada |
| Inicialização controlada do Docker | Serviço ativo e socket habilitado | atendido | Ativação por socket identificada |
| PostgreSQL local disponível | Servidor 14.24 aceitando conexões locais | atendido | Cliente instalado é 18.6 |
| Porta padrão do Metabase disponível | Porta 3000 sem listener | atendido | Deve ser confirmada novamente no provisionamento |
| Porta para PostgreSQL em container | Porta 5432 do host ocupada | pendente | Definir mapeamento ou política na unidade de arquitetura |
| Exposição local do PostgreSQL existente | `listen_addresses=localhost` | atendido | Serviço não observado em endereço externo |
| Limpeza de recursos Docker anteriores | Inventário preliminar realizado | pendente | Tratamento adiado para M00-U02 |
| Bloqueio impeditivo para continuar | Nenhum identificado | atendido | Ambiente viável com restrições registradas |

## Comandos usados como evidência

A coleta utilizou comandos de consulta, sem alteração de serviços ou dados:

- `uname -a`, leitura de `/etc/os-release` e `lscpu`;
- `free -h`, `df -h .`, `swapon --show` e `vmstat 1 5`;
- `id`, `groups` e inspeção do socket Docker;
- `git --version` e `git status --short --branch`;
- `docker --version`, `docker compose version`, `docker info`,
  `docker ps -a` e `docker system df`;
- consultas de estado das unidades `docker.service`, `docker.socket` e
  `postgresql`;
- `psql --version`, `pg_isready` e consultas administrativas `SHOW`;
- inspeção de listeners nas portas 3000 e 5432.

## Situação da unidade

O diagnóstico factual está consolidado e não há bloqueio técnico impeditivo para
a continuidade. A M00-U00 permanece em andamento até a revisão das evidências de
compreensão, a atualização dos registros operacionais e o checkpoint Git.
