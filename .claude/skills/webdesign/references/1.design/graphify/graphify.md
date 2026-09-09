# Graphify — entender o código de um site existente antes de reescrever

Referência da ferramenta **Graphify** (github.com/Graphify-Labs/graphify — `pip install graphifyy`). É uma ferramenta de análise de código-fonte: constrói um grafo de conhecimento de um codebase (nós, comunidades, "god nodes", wiki navegável) para que se entenda a arquitetura sem ler arquivo por arquivo.

## Onde ela entra no fluxo da WELLY

A WELLY escreve copy e constrói UI. Graphify **não** gera copy nem design — o único uso legítimo dela aqui é o pedido **"otimização/reescrita de página existente"** quando o cliente entrega o código de um site já pronto (React/Next/Vue/etc.) e você precisa mapear rápido a estrutura antes de mexer: quais componentes montam cada seção, onde vive o texto, o que quebra se você trocar um bloco.

Se o pedido não envolve código-fonte de um site existente, **ignore o Graphify** — não force análise de codebase em briefing de copy.

## Uso básico

```bash
pip install graphifyy

# constrói o grafo do projeto (AST, sem custo de API)
graphify build /caminho/do/site

# depois de mexer no código, mantém o grafo atualizado
graphify update .
```

Saída em `graphify-out/`:
- `graphify-out/GRAPH_REPORT.md` — relatório com "god nodes" (componentes centrais que muita coisa depende) e estrutura de comunidades. **Ler isto primeiro** antes de responder qualquer pergunta de arquitetura do site.
- `graphify-out/wiki/index.md` — wiki navegável do codebase (se existir, navegar por ela em vez de ler arquivos crus).

## Regra prática

1. Cliente mandou o repositório de um site pra reescrever/otimizar página → `graphify build .`, ler `GRAPH_REPORT.md`, localizar os componentes das seções que a copy vai tocar.
2. Terminou de editar o código → `graphify update .` pra manter o grafo coerente.
3. Briefing é só copy/design (sem repositório) → não usar.
