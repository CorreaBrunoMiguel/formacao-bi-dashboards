# Política de alterações

## Classes

### Estrutural

Inclui diretórios canônicos, fontes de verdade, responsabilidades, protocolos e regras fundamentais.

Exige:

- justificativa;
- ADR;
- aprovação explícita de Bruno;
- branch e pull request;
- incremento da versão de governança.

### Curricular

Inclui objetivos, unidades, pré-requisitos, avaliações e limites de módulo.

Correções editoriais podem ser registradas sem nova aprovação curricular. Mudanças que alterem competências, sequência ou critérios exigem revisão formal e incremento da versão curricular.

### Operacional

Inclui estado, progresso, sessões, bloqueios e resultados de avaliação. Orion pode atualizá-la continuamente, desde que a mudança corresponda a fatos e evidências.

### Local ou sensível

Inclui credenciais, `.env`, volumes, bancos locais, dados pessoais e artefatos temporários. Não deve ser versionada.

## Versionamento

Governança, currículo e esquema do estado usam versionamento semântico:

- **MAJOR:** incompatibilidade ou redefinição estrutural;
- **MINOR:** ampliação compatível;
- **PATCH:** correção que não altera intenção.

## Git

A branch `main` representa o estado oficial. O fluxo padrão é:

1. criar branch temática;
2. realizar commits com responsabilidade clara;
3. revisar as alterações;
4. abrir pull request;
5. aprovar e integrar;
6. atualizar o estado quando aplicável.

Convenções principais de commit:

- `docs:` documentação;
- `feat:` nova entrega funcional;
- `fix:` correção;
- `refactor:` reorganização sem alteração de comportamento;
- `test:` testes;
- `chore:` manutenção.

Mudanças estruturais não devem ser misturadas a atividades acadêmicas da unidade.
