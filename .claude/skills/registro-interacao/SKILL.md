---
name: registro-interacao
description: Gera analytics/interacao-{N}.md resumindo todos os comandos executados na iteração, agrupados por etapa. Use ao final de TODA resposta ao usuário, sem exceção.
---

# Registro de interação

Ao final de cada iteração (uma mensagem do usuário + tudo que você fez até responder), crie `analytics/interacao-{N}.md`.

1. `N` = (quantidade de arquivos `analytics/interacao-*.md` existentes) + 1. Crie a pasta se não existir.
2. Liste TODA ação da iteração: cada chamada de ferramenta (Bash, Read, Edit, Write, Agent, MCP, etc.), na ordem, sem omitir nenhuma. Não inclua o próprio registro.
3. Agrupe por etapa, só as que ocorreram: **Entendimento** (leitura/busca), **Planejamento**, **Implementação** (edições/criações), **Verificação** (testes/builds/execuções), **Git/Deploy**, **Outros**.
4. Cada item em uma linha: `- \`Ferramenta\` comando/arquivo — resultado em ≤10 palavras`. Ações com efeito externo (rede, instalação, git push, banco, delete) ganham o prefixo ⚠️.

Formato:

```markdown
# Interação {N}
**Pedido:** <resumo do pedido do usuário em 1 linha>

## Entendimento
- `Read` src/app.js — entrypoint lido

## Implementação
- `Write` src/new.js — criado

## Resumo
<N> ações · <X> arquivos alterados · <Y> ações com efeito externo
```
