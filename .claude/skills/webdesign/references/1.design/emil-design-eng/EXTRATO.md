# Emil Kowalski — extrato pra site (leitura padrão da WELLY)

Condensado de `SKILL.md` (27 KB) com o que muda uma página de site. As tabelas de curva/duração e a sequência "deve animar?" já estão em `references/2.animacao/animate/SKILL.md` — não repetidas aqui. Abrir o `SKILL.md` completo só quando o caso pede gesto/arrasto/toast/gaveta em profundidade.

## Filosofia (o que a WELLY carrega em toda entrega)

- **Gosto se treina.** Não é preferência: é enxergar além do óbvio e reconhecer o que eleva. Antes de montar, perguntar por que as melhores interfaces desse tipo *parecem* boas — e reproduzir a causa, não a aparência.
- **Detalhes invisíveis se acumulam.** O usuário nunca nota um detalhe certo; nota o conjunto. Uma página "boa sem saber por quê" é mil detalhes certos ao mesmo tempo. Cada regra abaixo existe por isso.
- **Beleza é alavanca.** Num mundo em que todo software é "bom o suficiente", o acabamento decide. Bons defaults e boa animação diferenciam.
- **Coesão > efeito.** Curva, duração e movimento combinam com a personalidade da página (Sonner é um pouco mais lento e usa `ease` porque quer parecer elegante). Componente lúdico pode ter mola; página profissional é seca e rápida. Movimento casa com o clima — não é uma camada colada depois.

## Princípios de componente (aplicar sem anunciar)

- **Botão responde no toque:** `transform: scale(0.97)` em `:active`, 160ms `ease-out`. Vale pra qualquer coisa pressionável (0.95–0.98). `scale()` leva os filhos junto — é o que faz parecer físico.
- **Nunca nasce de `scale(0)`.** Nada no mundo some por completo e reaparece. Entrada parte de `scale(0.95)` + `opacity: 0`.
- **Popover/menu escala a partir do gatilho** (`transform-origin` no gatilho), não do centro. Modal é a exceção (centrado, sem âncora).
- **Tooltip:** atraso na primeira; as vizinhas abrem instantâneas (sem atraso, sem animação). Percepção de velocidade.
- **Transição, não keyframe, pra tudo que dispara rápido** (toast, toggle, acordeão): transição retoma do valor atual; keyframe recomeça do zero.
- **Blur mascara transição imperfeita:** crossfade que "mostra dois objetos" ganha `filter: blur(2px)` durante a troca. Manter abaixo de 20px (Safari sofre).
- **`@starting-style`** pra animar entrada sem JS (fallback: atributo `data-mounted` após montar).
- **Assimetria:** lento onde o usuário decide (segurar pra apagar: 2s linear), rápido onde o sistema responde (soltar: 200ms ease-out). Saída sempre mais rápida que entrada.
- **Stagger de 30–80ms** entre itens; nunca bloquear interação enquanto a cascata roda.

## Transform e clip-path (ferramentas que fazem "parecer caro")

- `translateY(100%)` é relativo ao próprio tamanho — esconder gaveta/toast sem saber a altura.
- **`clip-path: inset(...)`** é a ferramenta mais subestimada: revelação de imagem ao rolar (`inset(0 0 100% 0) → inset(0)`), abas com troca de cor perfeita (duplicar a lista, estilizar a cópia como ativa e recortar), segurar-pra-apagar, slider de comparação de imagens — tudo acelerado, sem DOM extra.
- `rotateX/rotateY` + `transform-style: preserve-3d` dão profundidade sem JS.

## Performance (o que derruba a sensação de "moderno")

- Só `transform` e `opacity` em animação contínua; `padding/margin/height/width` disparam layout+paint.
- **Os atalhos `x`/`y`/`scale` do Motion NÃO são acelerados por hardware** (rodam em `requestAnimationFrame` na thread principal). Sob carga (página carregando, scripts rodando), use a string completa `transform: "translateX(100px)"` ou CSS/WAAPI. CSS roda fora da thread principal e não perde frame durante o carregamento — pra animação predeterminada, prefira CSS; JS só pro dinâmico/interruptível.
- **WAAPI** (`element.animate([...], {duration, easing, fill})`) = controle de JS com performance de CSS, sem biblioteca.
- Não animar variável CSS no pai (recalcula todos os filhos) — set `transform` direto no elemento.

## Acessibilidade

- Reduced motion = **menos e mais suave, não zero**: manter opacidade/cor que ajudam a entender; tirar deslocamento e mola.
- Hover só atrás de `@media (hover: hover) and (pointer: fine)` — toque dispara hover falso.

## Checklist de revisão (formato obrigatório do Emil: tabela Antes | Depois | Por quê)

| Problema | Correção |
|---|---|
| `transition: all` | propriedade explícita: `transition: transform 200ms ease-out` |
| entrada `scale(0)` | `scale(0.95)` + `opacity: 0` |
| `ease-in` em UI | `ease-out` ou curva custom |
| `transform-origin: center` em popover | origem no gatilho (modal é exceção) |
| animação em ação de teclado | remover |
| UI > 300ms | 150–250ms |
| hover sem media query | `@media (hover: hover) and (pointer: fine)` |
| keyframe em elemento disparado rápido | transição |
| `x`/`y` do Motion sob carga | `transform: "translateX()"` / CSS |
| entrada e saída na mesma velocidade | saída mais rápida |
| tudo aparece de uma vez | stagger 30–80ms |

Ao revisar código de UI, a saída É essa tabela (uma linha por achado), nunca lista com "Antes:/Depois:" em linhas separadas.
