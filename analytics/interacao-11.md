# Interação 11
**Pedido:** adicionar o grass-ds (https://github.com/raphaelmdcoelho/grass-ds) ao projeto.

## Entendimento
- ⚠️ `Bash` clonou o repo do grass-ds e leu package.json e README
  ```bash
  git clone -q --depth 1 https://github.com/raphaelmdcoelho/grass-ds.git; ls -A grass-ds; cat grass-ds/package.json; head -60 grass-ds/README.md
  ```
- ⚠️ `Bash` confirmou os pacotes no npm e olhou index.css/main.tsx
  ```bash
  npm view @grass-ds/tokens version; npm view @grass-ds/css version; head -12 src/index.css; grep -n css src/main.tsx
  ```

## Implementação
- ⚠️ `Bash` instalou os pacotes e adicionou os 3 @import no topo de src/index.css
  ```bash
  npm i @grass-ds/css @grass-ds/tokens && printf "@import '@grass-ds/tokens/tokens.css';\n@import '@grass-ds/css/fonts.css';\n@import '@grass-ds/css/grass.css';\n\n" | cat - src/index.css > <tmp>/idx.css && cp <tmp>/idx.css src/index.css
  ```

## Verificação
- `Bash` build de produção passou
  ```bash
  npm run build
  ```

## Git/Deploy
- `Bash` commit (sem push)
  ```bash
  git add -A && git commit -q -m "feat: adiciona grass-ds (tokens e css)"
  ```

## Resumo
6 ações · 4 arquivos alterados · 4 ações com efeito externo (rede) · sem push
