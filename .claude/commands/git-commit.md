# Commits temáticos (--all | --one | --help)

## Objetivo
Commits em pt-BR seguindo `conventional commits`, agrupando mudanças por **contexto funcional amplo**.

## Opções
- `-a, --all`: Adiciona tudo ao stage (`git add -A .`)
- `-1, --one`: Um único commit com todas mudanças
- Sem opções: Usa apenas arquivos já no stage

## Regra de agrupamento

**Um commit = Um objetivo funcional completo**

✅ **Agrupe** mudanças que:
- Têm o mesmo propósito funcional
- Seriam revertidas juntas
- Formam uma unidade lógica

❌ **NÃO separe** em múltiplos commits:
- Arquivos da mesma feature/fix
- Docs que acompanham código
- Mudanças interdependentes

## Exemplos

**Evitar** (granular demais):
```
docs(entities): documentar entidades
docs(actions): documentar ações  
docs(model): documentar modelo
```

**Preferir** (contexto amplo):
```
docs(spec): atualizar especificação do sistema
- entities, actions, model e schemas
```

## Formato
```
<tipo>(<escopo>): <resumo da mudança>

[opcional] - detalhes relevantes
```

## Tipos
- `feat`: funcionalidade completa
- `fix`: correção relacionada
- `docs`: documentação (múltiplos arquivos OK)
- `refactor`: reorganização de módulo/sistema
- `test`: testes de uma funcionalidade
- `build/chore`: manutenção

## Teste mental
"Essas mudanças fazem sentido como uma única unidade de trabalho?" 
Se sim → Um commit. Se não → Separe.