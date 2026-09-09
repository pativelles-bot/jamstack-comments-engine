---
name: webdesign
description: Construir, redesenhar, implementar, revisar e validar sites completos com qualidade de produção para qualquer nicho, incluindo landing pages, sites institucionais, portfólios, catálogos, eventos, produtos, serviços e negócios locais. Usar quando o pedido exigir estratégia, conteúdo, experiência, implementação responsiva, interações funcionais ou refinamento de um site existente.
---

# Construir sites de produção

Construir uma experiência web completa, coerente com o projeto e pronta para uso real. Entregar implementação funcional, não mockup, wireframe, pseudocódigo ou orientação abstrata.

Usar as informações, arquivos, referências e código fornecidos pelo usuário como fonte de verdade. Tomar decisões autônomas quando houver contexto suficiente. Perguntar somente quando faltar uma informação indispensável que altere materialmente o resultado, envolva risco, exija autorização ou não possa ser inferida com segurança.

## Princípios obrigatórios

1. Adequar a arquitetura ao objetivo do projeto, em vez de forçar uma landing page padrão.
2. Fazer o visitante compreender rapidamente o que é oferecido, para quem e qual ação deve realizar.
3. Tratar conteúdo, experiência, interação e implementação como partes do mesmo produto.
4. Evitar aparência de template, repetição automática de componentes e soluções decorativas sem função.
5. Não inventar resultados, números, clientes, avaliações, certificações, depoimentos, prêmios ou alegações verificáveis.
6. Não exigir Instagram, fotografias pessoais, WhatsApp ou pesquisa sobre uma pessoa quando isso não fizer parte do pedido.
7. Não depender de outra IA, navegador específico, sistema operacional, pasta pessoal ou caminho absoluto.
8. Preservar o projeto existente, suas convenções e tudo que já funciona.
9. Implementar ações reais para menus, links, botões, formulários e controles.
10. Verificar o resultado no ambiente disponível antes de concluir.

## Contrato-mestre obrigatório

Em toda criação, reconstrução ou reformulação completa de site, abrir e aplicar integralmente [references/auditoria-qualidade.md](references/auditoria-qualidade.md) depois da inspeção inicial e antes de formular a estratégia. Essa referência contém o prompt-mestre de execução, o padrão de profundidade e os critérios de auditoria da entrega.

Em correções pequenas e localizadas, consultar somente as partes pertinentes da referência, preservando o escopo solicitado. Não transformar um ajuste isolado em reconstrução completa sem autorização.

O contrato-mestre complementa esta skill e as subskills. O pedido explícito do usuário continua tendo precedência. Não resumir o contrato a uma checklist superficial nem alegar sua aplicação sem executar as verificações cabíveis.

## Precedência

Resolver conflitos nesta ordem:

1. Políticas e instruções superiores.
2. Pedido explícito do usuário.
3. Conteúdo e restrições dos arquivos fornecidos pelo usuário.
4. Convenções e requisitos técnicos do projeto existente.
5. Regras centrais desta skill.
6. Subskills aplicáveis de `references/`, dentro do território de cada uma.
7. Heurísticas e decisões próprias.

Uma subskill especializa a execução. Nunca permitir que ela apague um requisito explícito, imponha uma estrutura incompatível ou substitua evidência do projeto por preferência genérica.

## Resolver e carregar as subskills

Resolver todo caminho `references/...` relativamente à pasta que contém este `SKILL.md`. Nunca usar caminhos pessoais ou presumir uma estrutura externa.

Ao acionar uma subskill:

1. Abrir integralmente seu arquivo de entrada antes de aplicar suas instruções.
2. Resolver links internos relativamente à pasta da própria subskill.
3. Abrir apenas os recursos exigidos para o cenário atual.
4. Seguir a cadeia de referências necessária, sem carregar arquivos irrelevantes.
5. Tratar scripts como procedimentos auxiliares, não como substitutos de julgamento.
6. Registrar internamente quais arquivos foram consultados, sem expor uma auditoria burocrática ao usuário.

Se uma subskill opcional estiver ausente, continuar com o fluxo central e não alegar que ela foi aplicada. Se uma subskill indispensável ao pedido explícito estiver inacessível, informar a limitação com precisão e executar tudo que ainda puder ser concluído com segurança.

## Roteamento das subskills

### Contrato e qualidade

| Referência | Arquivo de entrada | Acionar quando |
| --- | --- | --- |
| **auditoria-qualidade** | [references/auditoria-qualidade.md](references/auditoria-qualidade.md) | Sempre em criação, reconstrução ou reformulação completa. Aplicar o prompt-mestre do início da estratégia até a validação final. Em alteração localizada, consultar apenas os critérios relacionados ao trecho modificado. |

### Estrutura, direção e construção

| Subskill | Arquivo de entrada | Acionar quando |
| --- | --- | --- |
| **BASE-LP** | [references/1.design/BASE-LP.md](references/1.design/BASE-LP.md) | Construir ou revisar landing page ou página única orientada à conversão. Usar como base de alinhamento, medida, respiro e comportamento responsivo. Não transformar valores de referência em regras universais quando o conteúdo ou o projeto exigir outra solução. |
| **impeccable** | [references/1.design/impeccable/SKILL.md](references/1.design/impeccable/SKILL.md) | Criar uma experiência nova, redesenhar, criticar, refinar, simplificar, endurecer ou elevar uma interface. Ler o playbook indicado pela própria subskill para o comando aplicável. |
| **hallmark** | [references/1.design/hallmark-main/skills/hallmark/SKILL.md](references/1.design/hallmark-main/skills/hallmark/SKILL.md) | Definir uma macroestrutura autoral, selecionar arquétipos de hero, navegação e rodapé, combater padrões genéricos e executar o slop test ao final de um build completo. Respeitar a divulgação progressiva indicada pela subskill. |
| **apple-design** | [references/1.design/apple-design/EXTRATO.md](references/1.design/apple-design/EXTRATO.md) | Projetar interações baseadas em gesto, física, arrasto, momentum, sheets ou transições interrompíveis. Ler o arquivo completo apenas quando a própria subskill exigir. |
| **emil-design-eng** | [references/1.design/emil-design-eng/EXTRATO.md](references/1.design/emil-design-eng/EXTRATO.md) | Refinar comportamento, resposta, estados e sensação de componentes interativos. Ler o arquivo completo apenas quando houver interação que justifique a escalada. |
| **pick-ui-library** | [references/1.design/pick-ui-library/SKILL.md](references/1.design/pick-ui-library/SKILL.md) | Escolher biblioteca para um componente especializado ou quando o usuário pedir essa seleção. Não acionar para componentes simples. |
| **prototype** | [references/1.design/prototype/SKILL.md](references/1.design/prototype/SKILL.md) | Criar variantes genuinamente diferentes para comparação quando o usuário pedir alternativas ou quando uma decisão crítica não puder ser resolvida por evidência. Seguir [references/1.design/prototype/PICKER.md](references/1.design/prototype/PICKER.md) apenas se um seletor visual for necessário. |
| **motion** | [references/1.design/motion/motion-animation.md](references/1.design/motion/motion-animation.md) | Implementar transições de estado, entradas pontuais e microinterações depois de decidir o movimento com `animate`. |
| **graphify** | [references/1.design/graphify/graphify.md](references/1.design/graphify/graphify.md) | Mapear um codebase existente antes de uma reestruturação ampla. Não acionar em projeto novo ou em alteração localizada. |
| **website-builder-setup** | [references/1.design/website-builder-setup/SKILL.md](references/1.design/website-builder-setup/SKILL.md) | Instalar ou configurar o ambiente somente quando o usuário solicitar isso ou quando o projeto ainda não tiver uma estrutura executável. |

### Movimento

| Subskill | Arquivo de entrada | Acionar quando |
| --- | --- | --- |
| **animate** | [references/2.animacao/animate/SKILL.md](references/2.animacao/animate/SKILL.md) | Decidir se um elemento deve se mover, qual função o movimento cumpre e como deve responder. Ler [references/2.animacao/animate/RECIPES.md](references/2.animacao/animate/RECIPES.md) somente durante a implementação pertinente. |
| **find-animation-opportunities** | [references/2.animacao/find-animation-opportunities/SKILL.md](references/2.animacao/find-animation-opportunities/SKILL.md) | Identificar oportunidades de movimento em uma interface existente, especialmente em pedidos de exploração ou diagnóstico. |
| **improve-animations** | [references/2.animacao/improve-animations/SKILL.md](references/2.animacao/improve-animations/SKILL.md) | Auditar o movimento de um codebase completo. Quando acionada, seguir também `AUDIT.md` e `PLAN-TEMPLATE.md` da mesma pasta. |
| **review-animations** | [references/2.animacao/review-animations/SKILL.md](references/2.animacao/review-animations/SKILL.md) | Revisar código de movimento, diff ou implementação específica. Consultar `STANDARDS.md` da mesma pasta para critérios exatos. |
| **animation-vocabulary** | [references/2.animacao/animation-vocabulary/SKILL.md](references/2.animacao/animation-vocabulary/SKILL.md) | Traduzir uma descrição vaga de movimento para um padrão técnico reconhecível. |
| **gsap** | [references/1.design/gsap-skills-main/skills/llms.txt](references/1.design/gsap-skills-main/skills/llms.txt) | Implementar timelines longas, movimento controlado pelo scroll, pin, scrub, parallax, SplitText, Flip ou arrasto com inércia. Ler o índice e depois somente a subskill GSAP correspondente. |

Decidir primeiro com `animate`. Implementar depois com `motion`, `gsap` ou recursos nativos, conforme a necessidade. Não escolher uma biblioteca antes de definir propósito, comportamento, interrupção, desempenho e alternativa com movimento reduzido.

O script `references/1.design/impeccable/scripts/concept-seed.mjs`, quando existir e for indicado por `impeccable`, pode gerar um desafiante criativo. Nunca usar sorteio como decisão final. Comparar as alternativas por adequação ao público, clareza, diferenciação, conteúdo disponível, viabilidade e objetivo do site. Não criar arquivos auxiliares no projeto apenas para satisfazer um fluxo opcional.

## Fluxo de execução

### 1. Inspecionar antes de editar

- Localizar instruções do projeto, estrutura, dependências, scripts e arquivos relevantes.
- Verificar se existe `.openai/hosting.json` e seguir as regras do ambiente quando existir.
- Identificar alterações preexistentes e preservar trabalho não relacionado.
- Executar o projeto atual, quando possível, antes de modificar para estabelecer uma linha de base.
- Determinar se a tarefa é criação, continuação, correção, redesign, auditoria ou implementação localizada.
- Depois da inspeção, carregar `auditoria-qualidade` quando o escopo for criação, reconstrução ou reformulação completa.

### 2. Formular a estratégia

Derivar das informações disponíveis:

- Oferta, assunto ou finalidade central.
- Público prioritário.
- Problema, necessidade ou desejo atendido.
- Benefício principal e diferenciais sustentáveis.
- Ação principal e ações secundárias.
- Origem provável do tráfego, quando isso influenciar a página.
- Objeções e informações necessárias para reduzir insegurança.
- Tipo de site e jornada mais adequados.

Não presumir que todo projeto precisa da mesma sequência de seções. Organizar o conteúdo para estabelecer relevância, explicar valor, demonstrar funcionamento, oferecer evidência, resolver objeções e conduzir à ação. Cortar qualquer bloco que não cumpra uma função.

### 3. Planejar conteúdo e experiência

- Criar uma abertura específica que explique o projeto sem frases intercambiáveis.
- Escrever todo conteúdo necessário com base em fatos disponíveis.
- Priorizar benefícios compreensíveis e depois sustentar com detalhes.
- Adaptar o tom ao público e preservar a voz existente quando houver material suficiente.
- Usar chamadas para ação concretas e coerentes com o próximo passo real.
- Não usar Lorem Ipsum, provas fictícias ou controles sem destino.
- Quando um dado real estiver ausente, usar formulação neutra ou centralizar o campo em configuração fácil de substituir. Não publicar uma invenção para preencher espaço.

Tratar regras de escrita como heurísticas. Variar ritmo e estrutura sem proibir recursos linguísticos legítimos. Ler o conteúdo no contexto da página e remover clichês, redundância, abstrações vagas e promessas sem sustentação.

### 4. Construir

- Trabalhar no stack existente e reutilizar componentes adequados.
- Escolher a solução mais leve capaz de entregar o efeito pretendido.
- Usar CSS, SVG, canvas, WebGL ou bibliotecas especializadas apenas quando melhorarem materialmente a experiência.
- Implementar navegação, links, formulários, feedback, estados vazios, carregamento, sucesso e erro conforme aplicável.
- Centralizar dados mutáveis como contatos, endereços, links, serviços, planos, perguntas frequentes e chamadas para ação.
- Evitar dependências desnecessárias e remover código morto introduzido durante a implementação.
- Garantir que a página permaneça utilizável se um efeito avançado falhar.

### 5. Tornar responsivo e acessível

- Projetar para monitores largos, notebooks, janelas mais quadradas, tablets e celulares.
- Reorganizar conteúdo e interações; não apenas reduzir a versão desktop.
- Evitar cortes, sobreposições, linhas órfãs graves, alvos pequenos e rolagem horizontal acidental.
- Oferecer alternativa de toque para interações dependentes de mouse.
- Usar estrutura semântica, textos alternativos pertinentes, foco visível, navegação por teclado e rótulos de formulário.
- Respeitar preferências de movimento reduzido e não depender de animação para transmitir informação essencial.

### 6. Proteger desempenho e estabilidade

- Evitar trabalho contínuo fora da área visível.
- Animar propriedades eficientes e limitar efeitos caros.
- Carregar recursos progressivamente e reservar espaço para evitar saltos de layout.
- Tratar resize, carregamento lento, falhas de mídia e capacidades inferiores do dispositivo.
- Manter interações responsivas e reduzir a complexidade quando o custo técnico superar o ganho percebido.

## Validação obrigatória

Antes de concluir:

1. Executar os comandos relevantes disponíveis no projeto, como build, testes, lint e checagem de tipos.
2. Abrir a implementação no navegador quando essa capacidade estiver disponível.
3. Percorrer a página completa e testar navegação, links, botões, formulários e interações.
4. Verificar console, arquivos ausentes, erros de carregamento e avisos relevantes.
5. Inspecionar pelo menos um viewport largo, um intermediário e um móvel.
6. Capturar os estados principais e revisar hierarquia, composição, legibilidade, alinhamento, espaçamento, enquadramento e continuidade.
7. Testar teclado, foco, movimento reduzido e estados de erro aplicáveis.
8. Refinar automaticamente os problemas encontrados e repetir as verificações afetadas.

Não declarar uma verificação que não foi executada. A ausência de uma ferramenta de validação não deve bloquear o que pode ser concluído; registrar apenas a limitação real.

## Critérios de aceite

Considerar a entrega pronta somente quando:

- A primeira tela comunica o essencial e apresenta uma ação clara.
- A narrativa corresponde ao público, ao objetivo e ao tipo de site.
- O resultado não parece um template apenas preenchido.
- O conteúdo não contém fatos fabricados.
- Elementos interativos funcionam e possuem estados compreensíveis.
- A experiência permanece utilizável em diferentes tamanhos de tela.
- Não há erros relevantes conhecidos no fluxo principal.
- A implementação foi revisada visualmente e tecnicamente dentro das ferramentas disponíveis.

## Encerramento

Entregar de forma concisa:

- Resultado produzido.
- Arquivos principais alterados ou criados.
- Verificações realmente executadas e seus resultados.
- Suposições ou limitações que ainda afetem publicação ou conteúdo real.

Não incluir inventário de leitura, cadeia de raciocínio, mapa interno de cobertura ou relatório cerimonial, salvo quando o usuário solicitar uma auditoria detalhada.

## Onde os sites moram (Google Drive, via conector)

Os sites do Grupo PV ficam no Google Drive, na pasta `GRUPO PV / PROJETOS`.
Esta máquina **não tem o Drive montado como pasta** — o acesso é pelo
**conector do Google Drive** da conta (o mesmo Drive do time).

O conector é o TRANSPORTE, não a bancada:
**baixe → edite no disco local → suba de volta.** Nunca tente editar o arquivo
dentro da conversa: esses `index.html` são arquivo único com imagens em base64
(0,1 a 0,8 MB) e não cabem em contexto.

**Pasta local de trabalho desta máquina:** `<<PREENCHER NA INSTALAÇÃO>>`
(ex.: `C:\sites`)

### Estrutura no Drive

Os sites são separados por quem fez, espelhando o campo "Feito por" da base de
Sites no Notion:

    PROJETOS/
    ├── sites-automacao/   ← EXCLUSIVO da esteira automática. Não suba nada aqui.
    ├── sites-mauricio/    ← ★ destino desta instalação
    ├── sites-pedro/
    ├── sites-kaue/
    ├── sites-patricia/
    └── onboardings/       ← não é site

Nome da pasta do projeto: `LP <Nome Sobrenome>` (iniciais maiúsculas).

### Fluxo 1 — mexer num site que a automação já criou

1. Localize no Drive pelo nome `LP <Nome>` (ele estará em `sites-automacao/`).
2. Baixe o `index.html` para `<pasta local>/LP <Nome>/index.html`.
3. Edite **localmente**. Confira abrindo o arquivo no navegador.
4. Suba de volta **para o mesmo lugar de onde veio** (`sites-automacao/`),
   substituindo o arquivo. Corrigir o site da esteira não muda a autoria dele.
5. No Notion, o `Status do Site` continua **Em revisão** até ser confirmado.

### Fluxo 2 — site novo, feito por você

1. Gere o site na pasta local: `<pasta local>/LP <Nome>/`.
2. **Antes de subir, procure `LP <Nome>` no Drive em TODOS os baldes** — o site
   pode já existir, feito por outra pessoa. Se existir, **não sobrescreva**:
   pergunte primeiro. Sobrescrever site publicado é o pior erro possível aqui.
3. Crie `sites-mauricio/LP <Nome>/` no Drive e suba o `index.html` e o
   `PRODUCT.md`. (`_fotos/` e `_analise/` são material de trabalho: subir é
   opcional.)
4. No Notion, na base de Sites: `Status do Site` = **Em revisão**,
   `Feito por` = **Mauricio**, e o `Link do Site` quando publicar.

### Regras que não se negociam

- Nunca suba nada em `sites-automacao/` que não tenha vindo de lá.
- Nunca sobrescreva um `index.html` que você não baixou nesta sessão.
- Se não achar a pasta no Drive, **pare e pergunte** — não crie pasta nova
  "parecida" nem deixe o site só no disco local. Site que fica só na máquina
  some do time.

### Por que o status importa

O site só aparece no painel da Giovana (SDR) depois que a revisão for
confirmada no myTEAM (botão "✓ Confirmar revisão"). Enquanto estiver
`Em revisão`, o lead não é prospectado.
