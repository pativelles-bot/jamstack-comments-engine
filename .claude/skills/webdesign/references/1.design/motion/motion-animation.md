# Motion — movimento para site (motion.dev)

Referência condensada da biblioteca **Motion** (antiga Framer Motion) para animar seções e componentes de site. Fonte: motion.dev. Este arquivo é a **caixa de ferramentas**; a **decisão** (anima ou não, propósito, curva, duração) vem sempre de `references/2.animacao/animate/SKILL.md` — rodar a sequência de lá antes de abrir este.

## Regras de ouro (herdadas do animate + craft-floor)

1. **Um momento autoral, orquestrado — não efeito espalhado.** A página tem UMA entrada pensada (quase sempre o hero) e, no resto, movimento só onde ele explica algo (estado, origem, relação). **A mesma entrada "fade + sobe 24px" repetida em toda seção é o tell nº 1 de site gerado por IA** e está proibida.
2. **Conteúdo visível por padrão.** Nada nasce com `opacity: 0` esperando JS. Sem JS, sem `IntersectionObserver`, com leitor de tela ou com `prefers-reduced-motion`, a página tem que estar inteira na tela. Animação de entrada é *acréscimo*, nunca pré-condição pra ler.
3. **Curva e duração das tabelas, nunca inventadas.** UI (botão, menu, acordeão, tooltip) fica abaixo de 300ms com `ease-out` forte. Peça de marketing/explicativa (hero, revelação de imagem, número) pode ser mais longa (400–800ms) — é a exceção prevista na tabela do animate.
4. **Propriedades compostas primeiro** (`transform`, `opacity`); `filter: blur()`, `clip-path`, `mask` e sombra entram na paleta **quando ficam suaves** (medir). Nunca `width`/`height`/`top`/`left`/`margin` (reflow). Nunca `ease-in` em UI, nunca `scale(0)`, nunca bounce fora de gesto lúdico.

## Instalação

```bash
npm install motion
```
React: `import { motion } from "motion/react"` · JS puro (Elementor/WordPress/HTML): `import { animate, inView, stagger, scroll } from "motion"` (ou `<script type="module">` do CDN `https://cdn.jsdelivr.net/npm/motion@latest/+esm`).

## Curvas e durações (tokens — usar sempre os mesmos)

```css
:root {
  --ease-out: cubic-bezier(0.23, 1, 0.32, 1);      /* entrada/saída de UI (ease-out forte, "exponencial") */
  --ease-in-out: cubic-bezier(0.77, 0, 0.175, 1);  /* mover/morfar algo já na tela */
  --ease-drawer: cubic-bezier(0.32, 0.72, 0, 1);   /* gaveta/sheet estilo iOS */
}
```
Em Motion: `ease: [0.23, 1, 0.32, 1]`. Durações: botão 100–160ms · tooltip/popover 125–200ms · menu/select 150–250ms · modal/gaveta 200–500ms · **hero/revelação/marketing 400–800ms** · hover 150ms com `ease` padrão · marquee/progresso `linear`. Mola (`type: "spring", duration: 0.5, bounce: 0.15`) só pra gesto, arrasto ou "coisa viva" — não pra fade.

## API essencial

```jsx
// estado inicial → final (entrada única, uma vez)
<motion.h1 initial={{ opacity: 0, y: 12 }} animate={{ opacity: 1, y: 0 }}
  transition={{ duration: 0.5, ease: [0.23, 1, 0.32, 1] }} />

// gestos
whileHover={{ y: -2 }} whileTap={{ scale: 0.97 }}   // hover leve, press físico

// entrar na viewport — usar com parcimônia (ver receitas)
whileInView={{ opacity: 1 }} viewport={{ once: true, amount: 0.4 }}

// cascata (variants + stagger)
const lista = { show: { transition: { staggerChildren: 0.06 } } }
const item  = { hidden: { opacity: 0, y: 8 }, show: { opacity: 1, y: 0 } }

// saída (elemento removido do DOM)
<AnimatePresence>{aberto && <motion.div key="x" initial={{opacity:0}} animate={{opacity:1}} exit={{opacity:0}} />}</AnimatePresence>

// layout / elemento compartilhado (miniatura → detalhe)
<motion.div layout /> · <motion.img layoutId="capa-1" />

// ligado ao scroll (parallax, barra de progresso)
const { scrollYProgress } = useScroll({ target: ref, offset: ["start end", "end start"] })
const y = useTransform(scrollYProgress, [0, 1], [0, -60])
<motion.div style={{ y }} />   // barra: style={{ scaleX: scrollYProgress, transformOrigin: "left" }}

// reduced motion
const reduzir = useReducedMotion()   // true → sem y/scale/blur; só opacity curta ou nada
```

JS puro:
```js
inView(".hero", ({ target }) => animate(target.querySelectorAll("[data-linha]"),
  { opacity: [0, 1], y: [10, 0], filter: ["blur(6px)", "blur(0px)"] },
  { duration: 0.6, delay: stagger(0.08), easing: [0.23, 1, 0.32, 1] }), { amount: 0.5 })
scroll(animate(".progresso", { scaleX: [0, 1] }))   // barra de leitura sem React
```

## Receitas por bloco de site (o mapa da WELLY)

O princípio: **o hero recebe o momento; o resto recebe estado.** Antes de aplicar qualquer linha, o bloco tem que ter passado pelo portão 1–2 do `animate` (deve animar? qual propósito nomeado?).

| Bloco | O que fazer | O que NÃO fazer |
|---|---|---|
| **Hero (título + sub + CTA)** | UMA entrada orquestrada, uma vez, ao carregar: linhas do título em cascata (`stagger 0.06–0.08`), com `opacity + y 8–12px` (+ `blur(6px→0)` se ficar suave), 500–700ms total, `ease-out` forte. A imagem/produto do hero entra junto no mesmo compasso (não depois). Sem JS, tudo já está visível (CSS de fallback ou `initial` só aplicado após hidratar). | Entrada por seção depois desse momento; `y: 40`; 300ms genérico; `whileInView` no hero (ele já está na tela). |
| **Botão CTA** | `whileTap={{ scale: 0.97 }}` 100–160ms; hover leve (`y: -1` ou mudança de cor 150ms). Reage no `pointerdown`, não no `click`. | `whileHover scale 1.05` (cresce como brinquedo); sombra que "acende". |
| **Cards de serviço / benefícios** | Por padrão, **visíveis sem entrada**. Movimento só de estado: hover com `y: -2` + sombra deslocada, 150ms. Se a seção é o "pico" da página, cascata curta (`stagger 0.05`, `opacity 0→1`, ≤250ms cada) UMA vez. | `whileInView` fade-up em cada card; ícone que gira; borda que brilha. |
| **Prova / depoimentos** | Carrossel: `AnimatePresence mode="wait"` com `opacity` + `x: ±16`, 250ms; arrasto com mola (`drag="x"`, `dragConstraints`, `type: "spring"`). Autoplay pausa no hover/foco. | Fade-up ao rolar; carrossel infinito sem controle. |
| **Números / métricas** | Contagem só se o número é a prova principal e é verdadeiro — usar **NumberFlow** (`pick-ui-library`), 600–800ms, uma vez. | Contagem em toda métrica; sparkline decorativa. |
| **FAQ (acordeão)** | Conteúdo abre com `AnimatePresence` + `height: "auto"` (ou grid `grid-template-rows: 0fr→1fr` em CSS puro), 200ms `ease-out`; seta gira `rotate 0→180`. Interrompível (transição, não keyframe). | Bounce; 400ms+; conteúdo que some antes de fechar. |
| **Imagem editorial / produto** | Revelação por `clip-path: inset(0 0 100% 0 → 0)` ou `mask` ao entrar na viewport, 600–800ms, uma vez — **uma** imagem-âncora por página, não todas. | Todas as imagens com zoom-in; parallax forte no mobile. |
| **Seção longa / fundo** | Parallax leve (`useTransform` -40 a -80px) em desktop; desligar em `pointer: coarse` e em `reduced-motion`. Alternativa sem JS: `animation-timeline: view()` (CSS scroll-driven) com `@supports`. | Parallax em texto; múltiplas camadas no mobile. |
| **Menu / navbar / links** | **Sem animação de entrada.** Estado só: sublinhado que cresce (`scaleX`, `transform-origin: left`, 150ms), menu mobile como gaveta (`--ease-drawer`, 300ms) com saída simétrica. | Menu que "cai" a cada carregamento; hover com atraso. |
| **Modal / sheet / popover** | Escala a partir da origem (`transform-origin` do gatilho, `scale 0.95→1`, `opacity`), 200ms; sheet com `--ease-drawer` e arrasto pra fechar (mola). | `scale(0)`; entrar do centro sem origem; `ease-in`. |
| **Transição entre páginas/estados** | View Transitions API (`vercel/react-view-transitions/`) ou `layoutId` pra elemento compartilhado. | Fade global de página inteira em toda navegação. |
| **Marquee de logos** | `linear`, contínuo, pausa no hover, duplicar a faixa pra loop sem salto. | Ease em movimento constante. |

## Nunca entregar

- A mesma animação de entrada em mais de um bloco (se o teste "removi todas as `whileInView` e nada piorou" passa, elas eram enfeite).
- Elemento com `opacity: 0` no HTML servido sem fallback (quebra LCP, leitor de tela e reduced-motion).
- `ease-in` em UI, `scale(0)`, `bounce` fora de gesto lúdico, `transition: all`.
- Animação de `width`/`height`/`top`/`left`/`margin`/`box-shadow` pesada em loop.
- `whileHover` em alvo de toque como único indicador de estado (mobile não tem hover).
- Parallax/scroll-linked sem checar `pointer: coarse` e `prefers-reduced-motion`.

## Acessibilidade e performance — obrigatório

```jsx
const reduzir = useReducedMotion()
<motion.h1 initial={reduzir ? false : { opacity: 0, y: 12 }} animate={{ opacity: 1, y: 0 }} />
```
CSS/JS puro: envolver em `@media (prefers-reduced-motion: no-preference) { … }` e checar `matchMedia("(prefers-reduced-motion: reduce)")` antes de chamar `animate`.

- `viewport={{ once: true }}` em qualquer entrada — nunca re-animar ao rolar de volta.
- `will-change` só no elemento e só durante a animação; remover depois.
- Medir: `filter`/`clip-path` em imagem grande pode cair de 60fps — testar no Chrome e degradar pra `opacity` se travar (as sub-skills de Core Web Vitals e DevTools ficam na skill `welly`, não aqui — esta skill é a proposta, não a otimização pós-aprovação).
- Foco de teclado nunca é escondido nem atrasado por animação; `AnimatePresence` não pode deixar elemento "saindo" clicável.
