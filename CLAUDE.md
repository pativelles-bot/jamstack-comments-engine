# Repositório compartilhado de protótipos

Este repositório é um espaço de trabalho do bot. **Cada projeto criado aqui é de um cliente ou
produto diferente e não tem nenhuma relação com os outros.** Um projeto nunca herda marca,
conteúdo, cor, texto, imagem ou endereço de outro.

## Regras obrigatórias

1. **Um projeto por pasta.** Todo projeto novo vive em `public/<slug-do-projeto>/index.html`.
   A raiz `public/index.html` é apenas o índice do repositório, nunca o site de um cliente.

2. **Nada de um projeto entra em outro.** Não reaproveite nome, logo, paleta, tipografia, textos,
   fotos, depoimentos, telefone, redes sociais nem domínio de um projeto anterior. Se precisar de
   dados de exemplo, invente dados fictícios e diga que são fictícios.

3. **Repositório e site Netlify são genéricos: `grupopv-dev`.** Nunca renomeie o repositório nem
   o site com o nome de um cliente. Os previews saem em
   `https://deploy-preview-<n>--grupopv-dev.netlify.app/<slug>/` e a produção em
   `https://grupopv-dev.netlify.app/<slug>/`.

4. **Cliente em produção ganha casa própria.** Quando um projeto sair do protótipo, ele recebe
   repositório e site Netlify próprios, com o nome dele. Não publique o site definitivo de um
   cliente a partir daqui.

5. **Commits, PRs e descrições falam só do projeto em questão.** Não cite outro cliente, outra
   marca ou outro projeto do repositório.

6. **Antes de criar um projeto novo**, confira `public/` para escolher um slug livre e não mexer
   nas pastas dos outros.

## Estrutura

```
public/
  index.html          índice dos protótipos (raiz neutra)
  medida/             protótipo Medida — marcenaria sob medida, Grande Florianópolis
netlify.toml          publica ./public como site estático
```

`src/`, `.eleventy.js` e `package.json` são restos do template original
(jamstack-comments-engine) e não participam do deploy estático. Não construa projetos novos em
cima deles sem necessidade.
