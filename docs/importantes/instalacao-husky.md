Instalação

1. npm i -D husky @commitlint/cli @commitlint/config-conventional baixa os três pacotes e os lista em devDependencies.
2. npx husky init faz duas coisas. Cria a pasta .husky/ com um pre-commit de exemplo, que eu apaguei. E adiciona "prepare": "husky" ao package.json.
3. npm install (e o prepare): o npm roda o script prepare automaticamente depois de instalar as dependências. Ele executa husky, que faz o Git usar a pasta de hooks do projeto.
4. Resultado: o Git passa a chamar os hooks da pasta .husky/_ em vez da pasta padrão .git/hooks. É por isso que quem clona o repositório e roda npm install já fica com a validação ativa.

Arquivos

┌──────────────────────────┬────────────────────────────────────────────────────────────────────────────────────────────────┐
│         Arquivo          │                                         Para que serve                                         │
├──────────────────────────┼────────────────────────────────────────────────────────────────────────────────────────────────┤
│ package.json →           │ Reativa o Husky em qualquer máquina após npm install.                                          │
│ "prepare": "husky"       │                                                                                                │
├──────────────────────────┼────────────────────────────────────────────────────────────────────────────────────────────────┤
│ .husky/commit-msg        │ O hook que você escreve. O Git o executa a cada commit, passando o caminho da mensagem em $1.  │
│                          │ Ele roda npx --no -- commitlint --edit "$1". Se o commitlint falhar, o commit é cancelado.     │
├──────────────────────────┼────────────────────────────────────────────────────────────────────────────────────────────────┤
│ commitlint.config.js     │ Diz ao commitlint qual regra usar: @commitlint/config-conventional, que exige o formato tipo:  │
│                          │ descrição (feat, fix, docs, chore e outros).                                                   │
├──────────────────────────┼────────────────────────────────────────────────────────────────────────────────────────────────┤
│                          │ Gerada pelo próprio Husky, não vai para o Git. Tem um atalho para cada tipo de hook            │
│ .husky/_/                │ (pre-commit, pre-push, commit-msg e outros). Cada atalho chama o script h, que procura o seu   │
│                          │ arquivo com o mesmo nome em .husky/.                                                           │
├──────────────────────────┼────────────────────────────────────────────────────────────────────────────────────────────────┤
│ .husky/_/.gitignore      │ Contém *, o que mantém toda a pasta _ fora do Git.                                             │
└──────────────────────────┴────────────────────────────────────────────────────────────────────────────────────────────────┘

O caminho de um commit

git commit → Git consulta core.hooksPath (.husky/_) → o atalho commit-msg → h → seu .husky/commit-msg → commitlint. A mensagem inválida devolve o código 1 e o Git aborta.

Observação: o .husky/_/husky.sh imprime um aviso de "DEPRECATED". É só um arquivo de compatibilidade com versões antigas do Husky. Seus hooks não usam as duas linhas que o aviso manda remover, então ele não tem efeito.

Registrei esta iteração em analytics/interacao-7.md. Ele ainda não foi commitado.