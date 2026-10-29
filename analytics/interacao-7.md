# Interação 7
**Pedido:** explicar como o Husky é instalado e o que cada arquivo faz.

## Entendimento
- `Bash` inspecionou hooksPath, pasta .husky, shims e script prepare
  ```bash
  cd /home/rmdcoelho/Documents/repositories/plib && git config core.hooksPath; ls -A .husky .husky/_ | head -20; cat .husky/_/husky.sh 2>/dev/null | head -5; cat .husky/_/commit-msg | head -5; cat .husky/_/.gitignore; grep -n -B1 -A1 prepare package.json
  ```

## Resumo
1 ação · 0 arquivos alterados · 0 ações com efeito externo
