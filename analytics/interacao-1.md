# Interação 1
**Pedido:** apagar tudo (inclusive .git) e recriar o projeto vazio com Vite em vez de Next.js, documentar decisões e commitar.

## Implementação
- ⚠️ `Bash` find -delete na pasta do repo — tudo removido, incluindo .git
- ⚠️ `Bash` npm create vite (react-ts) em pasta temporária — projeto gerado
- `Bash` cp para o repo; sed renomeia pacote para `plib`
- ⚠️ `Bash` npm install — gera package-lock.json
- `Write` skill registro-interacao, CLAUDE.md, docs/decisoes.md, este registro

## Git/Deploy
- `Bash` git init, remote add origin, commit — sem push

## Resumo
~8 ações · 3 ações com efeito externo/destrutivo · sem push
