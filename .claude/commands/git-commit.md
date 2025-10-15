# Commits temáticos (--all | --one | --help)

## Objetivo

Registrar mudanças com mensagens de commit concisas, em pt-BR, padronizadas e inequívocas, seguindo o modelo `conventional commits`, **agrupando mudanças relacionadas em commits temáticos separados**.

## Instruções

Leia $ARGUMENTS como opções.

**Opções de comando**:
- `-a`, `--all`: Adiciona todos os arquivos ao stage antes do commit (`git add -A .`)
- `-1`, `-o`, `--one`: Faz um único commit com todas as mudanças (ignora agrupamento temático)
- Sem opções: Trabalha apenas com arquivos já no stage

**Modo de execução**:
1. Se `-1`, `-o` ou `--one` fornecido → **Commit único** com todas as mudanças
2. Caso contrário → **Commits temáticos** agrupados e ordenados

**Agrupamento temático** (quando não usar `--one`):
1. Analise TODAS as mudanças e agrupe por tema/contexto relacionado
2. Ordene os grupos por dependência lógica (ex: refactor antes de feat que o usa)
3. Para cada grupo, execute um commit separado na ordem definida
4. Use `git add` seletivo para adicionar apenas arquivos do grupo atual antes de cada commit

**Mensagem de commit**: Declare claramente **o que foi alterado e por quê** para cada grupo temático, de forma legível tanto para humanos quanto para máquinas.

**Ferramentas extras**: Use o TodoWrite para orientar a execução.

## Estrutura

```bash
<tipo>(<escopo>): <resumo direto da mudança>

- [opcional] bullets com decisões ou exemplos
```

## Fluxo de execução

1. **Identificar grupos**: Separe mudanças por tema (ex: docs, feat-auth, fix-api)
2. **Definir ordem**: Commits base → dependentes → independentes → docs/chore
3. **Para cada grupo**:
   - `git add [arquivos_do_grupo]`
   - `git commit -m "[mensagem_tematica]"`

## Tipos comuns

* `feat`: Adiciona uma nova funcionalidade
* `fix`: Corrige um bug
* `docs`: Alterações na documentação
* `style`: Mudanças de estilo de código sem impacto funcional
* `refactor`: Refatoração de código sem alterar funcionalidade
* `perf`: Melhorias de performance
* `test`: Adição ou atualização de testes
* `build`: Mudanças no sistema de build ou dependências
* `ci`: Alterações em arquivos e scripts de CI
* `chore`: Outras mudanças que não modificam src ou testes
* `revert`: Reverte um commit anterior

## Escopos recomendados

* `system`, `commands`, `blueprint`, `template`
* `domain`, `feature`, `task`
* `docs` (quando transversal)

## Exemplos de agrupamento

Mudanças detectadas:
- README.md modificado
- auth.js refatorado
- login.css estilizado
- api.test.js adicionado
- package.json atualizado

Commits resultantes (em ordem):
```bash
# 1º - Dependências
build(deps): atualizar dependências do projeto

# 2º - Refatoração base
refactor(auth): reorganizar módulo de autenticação

# 3º - Funcionalidade
style(auth): ajustar estilos do formulário de login

# 4º - Testes
test(auth): adicionar testes para novo fluxo

# 5º - Documentação
docs(readme): atualizar instruções de instalação
```

## Restrições

* Não misture temas diferentes no mesmo commit
* Não descreva o passo a passo — declare **o resultado final**
* Evite termos vagos como "ajustes" ou "melhorias"
* Mantenha atomicidade: cada commit deve ser independente e testável
* Escreva texto em pt-BR

## Dica

Commits temáticos facilitam: reverter mudanças específicas, entender o histórico, e fazer cherry-pick quando necessário.
