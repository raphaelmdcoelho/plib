# Interação 6
**Pedido:** adicionar Husky para lintar mensagens de commit com Conventional Commits.

## Entendimento
- `Bash` conferiu estado do git (rebase anterior já abortado)
  ```bash
  cd /home/rmdcoelho/Documents/repositories/plib && git status | head -12; git log --oneline | head -5; ls analytics .husky; grep -c husky package.json
  ```

## Implementação
- ⚠️ `Bash` instalou husky e commitlint, configurou hook commit-msg e criou este registro
  ```bash
  npm i -D husky @commitlint/cli @commitlint/config-conventional 2>&1 | tail -2 && npx husky init && rm -f .husky/pre-commit && echo 'npx --no -- commitlint --edit "$1"' > .husky/commit-msg && echo 'export default { extends: ["@commitlint/config-conventional"] };' > commitlint.config.js && cat > analytics/interacao-6.md <<'EOF' ... EOF
  ```

## Verificação
- `Bash` commit inválido deve ser rejeitado
  ```bash
  git add -A && git commit -q -m "mensagem invalida"
  ```

## Git/Deploy
- `Bash` commit válido (sem push)
  ```bash
  git commit -q -m "chore: adiciona husky e commitlint (conventional commits)"
  ```

## Resumo
4 ações · 1 com efeito externo (rede) · sem push
