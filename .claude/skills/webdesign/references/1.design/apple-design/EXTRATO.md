# Apple Design — extrato pra site (leitura padrão da WELLY)

Condensado de `SKILL.md` (23 KB) — a parte que serve a uma página de site: resposta, materiais, tipografia, fundamentos e reduced motion. As seções de gesto/arrasto/mola (§2–§11 do completo) só entram quando a página tem carrossel arrastável, sheet, comparador de imagem ou qualquer coisa que o dedo puxa — aí abrir o `SKILL.md` inteiro.

## A ideia central

Uma interface parece viva quando o movimento **parte do valor atual na tela, herda a velocidade do usuário, projeta o momento à frente e pode ser agarrada e revertida a qualquer instante**. Mola é a ferramenta porque é interruptível e sabe de velocidade. Tudo serve a quatro necessidades humanas: **segurança/previsibilidade, entendimento, conquista e prazer.**

## 1. Resposta — matar a latência (vale pra todo botão de site)

- **Responder no `pointerdown`, não no `click`.** Botão que só reage ao soltar parece morto.
- Auditar toda latência no caminho do toque: debounce, timer artificial, espera de transição, atraso de 300ms do tap. O que não é essencial é regressão.
- **Feedback contínuo durante a interação**, não só no fim (slider, gaveta, carrossel: 1:1 com o ponteiro).

## 2. Interrupção — o princípio mais importante

- Nunca travar entrada durante uma transição. Modal fechando que o usuário agarra de novo segue o dedo — não termina de fechar pra depois reabrir.
- Animar sempre a partir do valor **apresentado** (o que está na tela), nunca do valor-alvo — senão dá salto visível.
- CSS transition/keyframe não serve pra nada guiado por gesto; mola sim (parte do valor atual por padrão).

## 3. Molas — os dois parâmetros que importam

Apple trocou massa/rigidez/amortecimento por **damping** (0–1: 1.0 = sem sobressalto; <1 = quica) e **response** (segundos até chegar; menor = mais seco). Casa (Motion): `{ type: "spring", bounce: 0, duration: 0.4 }` como padrão; `bounce: 0.2` **só quando o gesto trouxe momento** (flick, arremesso, soltar arrasto). Sobressalto num menu que só apareceu está errado; num card que você arremessou está certo.

| Interação | Damping | Response |
|---|---|---|
| Mover/reposicionar | 1.0 | 0.4 |
| Rotação | 0.8 | 0.4 |
| Gaveta/sheet | 0.8 | 0.3 |

## 4. Consistência espacial (vale pra menu mobile, popover, sheet)

- **Entra e sai pelo mesmo caminho.** Painel que entra da direita sai pela direita.
- **Ancorar na origem:** menu/popover/sheet nasce do elemento que o chamou (`transform-origin` no gatilho).
- Espelhar a curva em transições reversíveis (bezier inverso na volta).
- Bordas macias: **rubber-band** (resistência progressiva) em vez de parede — parede lê como "travou".

## 5. Materiais e profundidade — translucidez conta hierarquia

- Barra/nav/sheet como **camada translúcida** (`backdrop-filter: blur(20px) saturate(180%)` + fundo semitransparente + fio claro no topo = luz batendo no material) com o conteúdo rolando por baixo — não faixa opaca fixa.
- **Peso do material = hierarquia:** material mais pesado/escuro separa regiões estruturais; mais leve chama atenção pro interativo. **Nunca empilhar duas superfícies translúcidas claras** — legibilidade morre.
- Superfície maior lê mais grossa: mais blur, sombra mais funda que um chip.
- **Escurecer pra focar, separar pra manter o fluxo:** modal = scrim + fundo empurrado pra trás; painel paralelo = translucidez + deslocamento sem scrim.
- **Vibrância:** sobre superfície translúcida, texto não é cinza chapado — contraste maior, peso levemente maior, tracking um pouco positivo; cor fica na camada sólida.
- **Borda de rolagem, não divisória:** em vez de `1px` sob o cabeçalho fixo, uma máscara curta de blur/gradiente só onde o conteúdo passa por baixo do cromo flutuante.
- **Materializar, não só esmaecer:** vidro/blur entra animando raio do blur + escala juntos, pra ler como material chegando.

Ressalva do craft-floor: vidro e blur são **efeito específico**, não decoração. Se a superfície não tem conteúdo rolando por baixo, não precisa de blur.

## 6. Tipografia — tamanho muda a forma

- **Tracking é por tamanho, nunca um valor só:** display grande pede tracking negativo (`-0.02em`), corpo perto de `0`, texto pequeno levemente positivo. Um `letter-spacing` fixo está errado em algum lugar.
- **Leading inverso ao tamanho:** apertado no display (`1.05`), folgado no corpo (`1.5`); mais aberto em alfabetos com ascendentes altas, mais fechado em UI densa.
- **Hierarquia = peso + tamanho + leading em conjunto**, não só tamanho. Ênfase por peso ocupa menos espaço.
- Espaçamento em `rem`/`em`, nunca px fixo — o layout escala com o texto do usuário.
- `font-optical-sizing: auto` em fontes variáveis. Fonte de sistema serve pro **corpo** de página operacional; como **voz de display** de uma página com mundo próprio é falha (`craft-floor.md`) — a Fase 0 escolhe a face.

```css
.display { font-size: clamp(2rem, 5vw, 4rem); line-height: 1.05; letter-spacing: -0.02em; font-optical-sizing: auto; }
```

## 7. Os oito fundamentos (nomes pra raciocinar)

1. **Propósito** — decidir o que NÃO construir; cada elemento pede tempo, atenção e confiança.
2. **Agência** — escolha e desfazer fácil; confirmação só pro irreversível (abusar treina a pessoa a clicar sem ler).
3. **Responsabilidade** — pedir só o necessário, na hora certa, transparente; cortar o que o risco não paga.
4. **Familiaridade** — metáfora nem literal nem abstrata demais; o que parece igual se comporta igual e mora no mesmo lugar; quebrar padrão só provando que é melhor.
5. **Flexibilidade** — contexto, dispositivo, habilidade; celular = toque rápido, desktop = fluxo fundo.
6. **Simplicidade ≠ minimalismo** — tirar o desnecessário pra que o propósito brilhe; às vezes *adicionar* contexto simplifica; caminho comum primeiro, avançado um nível abaixo.
7. **Craft** — nada é aleatório: cada espaço, tempo e alinhamento é escolha defensável. Scroll trêmulo, ícone desalinhado, layout que quebra na rotação leem como descuido.
8. **Prazer** — resultado dos outros sete, não confete por cima. Decidir a emoção (calma, confiança, empolgação) e reforçá-la em toda decisão.

Regras táticas: quatro tipos de feedback (status, conclusão, aviso, erro; validar inline, não no envio) · **wayfinding** (onde estou? pra onde vou? o que tem lá? como saio?) · proximidade implica relação — controle perto do que ele afeta; se precisa de rótulo pra explicar, o mapeamento é fraco · **rótulo específico vence genérico** ("Progresso", "Biblioteca" — não "Início").

## 8. Reduced motion e sinais irmãos (baked-in, não depois)

- `prefers-reduced-motion: reduce` → deslize/mola/parallax viram **cross-fade curto ou estático**; sem sobressalto; manter opacidade/cor que ajudam a entender.
- `prefers-reduced-transparency: reduce` → superfície translúcida fica sólida/fosca (subir opacidade, tirar blur).
- `prefers-contrast: more` → fundo quase sólido com borda definida.
- Evitar fundo em movimento na viewport toda, oscilação lenta em loop (~1 ciclo / 5s), salto brusco de brilho (suavizar troca claro↔escuro).

## Processo

- **Protótipo interativo vale "um milhão de telas estáticas"** — a interface se descobre construindo e mexendo; o protótipo vira a régua que impede implementação medíocre.
- **Interação e visual se desenham juntos** — movimento não é camada por cima do pixel.
- Revisar movimento com olhos frescos, em câmera lenta / quadro a quadro.

## Referência rápida

| Precisa | Técnica | Valor |
|---|---|---|
| Mola padrão de UI | crítica, sem sobressalto | `bounce 0`, `duration 0.3–0.4` |
| Mola de flick | leve sobressalto | `bounce ~0.2`, `duration 0.3–0.4` |
| Interromper limpo | partir do valor na tela | ler o transform atual |
| Transição reversível | espelhar a curva | bezier inverso |
| Feedback | no `pointerdown`, contínuo | nunca só no fim |
| Borda | rubber-band | resistência progressiva |
| Cromo translúcido | camada `backdrop-filter` | conteúdo rola por baixo |
| Tracking | por tamanho | display `-0.02em`, corpo `0` |
| Reduced motion | cross-fade | `@media (prefers-reduced-motion)` |
