# Decisões técnicas

Projeto: aplicação web pública para visualizar livros (Markdown, HTML, EPUB e PDF), com login. Apenas ferramentas gratuitas.

| Camada | Decisão | Observação |
|---|---|---|
| Frontend | Vite + React + TypeScript (SPA) | Sem servidor próprio; build estático. |
| Backend | Nenhum servidor Node | Supabase fornece API, auth e storage. Lógica extra, se surgir: Supabase Edge Functions. |
| Banco de dados | Supabase (Postgres) | Plano gratuito pausa o projeto após ~1 semana sem uso. Segurança via Row Level Security. |
| Login | Supabase Auth | E-mail/senha e provedores OAuth (ex.: Google). |
| Arquivos dos livros | Supabase Storage | PDF e EPUB como arquivos; Markdown/HTML no Storage ou no banco. |
| Deploy | Cloudflare Pages | Hospeda o build estático do Vite; deploy via GitHub. SPA precisa de fallback para `index.html`. |
| Repositório | https://github.com/raphaelmdcoelho/plib.git | |

Next.js foi descartado em favor do Vite: como o app é uma SPA que fala direto com o Supabase, não há necessidade de renderização no servidor.

## Formatos de livro suportados
Markdown, HTML, EPUB, PDF. Cada leitor entra em uma etapa separada.

## Processo
- Etapas curtas e simples, um commit por etapa, para facilitar o code review.
- Cada iteração gera `analytics/interacao-{N}.md` (skill `registro-interacao`).

## Etapas previstas (rascunho)
1. Projeto vazio (esta)
2. Deploy na Cloudflare Pages
3. Supabase: projeto, cliente e variáveis de ambiente
4. Login (Supabase Auth)
5. Modelo de dados e listagem de livros
6. Leitores: Markdown, HTML, PDF, EPUB (um por etapa)
