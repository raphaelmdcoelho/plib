# Interação 1
**Pedido:** apagar tudo (inclusive .git) e recriar o projeto vazio com Vite em vez de Next.js, documentar decisões e commitar.

## Implementação
- ⚠️ `Bash` apagou tudo da pasta do repo, incluindo .git; gerou projeto Vite em pasta temporária
  ```bash
  cd /home/rmdcoelho/Documents/repositories/plib && find . -mindepth 1 -maxdepth 1 -exec rm -rf {} + && ls -A && S=<scratchpad> && cd $S && rm -rf app vapp && npm create vite@latest vapp -- --template react-ts --no-interactive 2>&1 | tail -5; ls -A vapp
  ```
- ⚠️ `Bash` copiou o projeto, renomeou o pacote para `plib`, instalou dependências, recriou skill, CLAUDE.md, docs/decisoes.md e este registro, fez git init e commit (sem push)
  ```bash
  S=<scratchpad>; cd /home/rmdcoelho/Documents/repositories/plib && cp -r $S/vapp/. . && sed -i 's/"name": "[^"]*"/"name": "plib"/' package.json && npm install 2>&1 | tail -3; sed -i '0,/"name": "[^"]*"/s//"name": "plib"/' package-lock.json; mkdir -p .claude/skills/registro-interacao docs analytics
  cat > .claude/skills/registro-interacao/SKILL.md <<'EOF' ... EOF
  cat > CLAUDE.md <<'EOF' ... EOF
  cat > docs/decisoes.md <<'EOF' ... EOF
  cat > analytics/interacao-1.md <<'EOF' ... EOF
  git init -q -b main && git remote add origin https://github.com/raphaelmdcoelho/plib.git && git add -A && git status --short && git commit -q -m "chore: projeto Vite + React + TypeScript vazio e decisões técnicas" && git log --oneline
  ```

## Resumo
2 ações · 2 ações com efeito externo/destrutivo · sem push
