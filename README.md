# Yotakes — Pitch

Deck do **Yotakes**, o Letterboxd dos restaurantes, feito em São Paulo. Cada *take* é
uma resenha curta com nota de 0 a 5 estrelas, foto e contexto — rede de confiança, não
ranking genérico.

**No ar:** https://gabrieldallape.github.io/yotakes-pitch/

## Como funciona

`index.html` é um arquivo único auto-contido: 30 seções em 16:9, navegáveis pelo teclado —
14 slides de pitch, um separador preto que marca o fim da apresentação, e o material de
apoio (2 slides auxiliares, 8 de Q&A e 5 de dados) guardado para as perguntas. Cada
`<section class="slide sN">` ocupa a viewport e só a que tem `.active` aparece.

A numeração das tags (`Pitch 1 · NN`) é gerada em JS pela ordem no DOM — inserir um slide
no meio não obriga a renumerar os outros na mão.

- `?slide=N` (1-indexed) abre direto no slide N — é o que o batch de screenshot usa.
- O `font-size` do slide é calculado para `1em ≈ 1% da altura`, então todo tamanho
  interno em `em` acompanha a tela. Cuidado: a equivalência não é exata — a moldura
  `.device` usa `height: 86%` + `aspect-ratio` justamente porque em `em` ela estourava
  a altura do slide.

## Assets

- `yo-bubble.png` — mascote Yo em creme, para fundos tomate/garrafa.
- `yo-bubble-red.png` — variante vermelha, para fundos claros.
- `julia-v2.png` — foto de abertura.
- `qr-yotakes.png` — QR do roadmap e do último slide, apontando para a produção.
- `telas/` — prints das telas do app no Figma (feed, avaliação, perfil, descoberta),
  usados dentro da moldura de celular nos slides de produto.

Fontes (Inter + Unbounded) vêm do Google Fonts. Paleta: tomate `#e84b3f`,
garrafa `#1f4d40`, bordô `#5f1b1f`, creme `#f2ead7`.

## Origem

A fonte canônica vive em `yotakes-pitch/index.html` na branch `monorepo` do repositório
principal do produto (privado). Este repositório é a cópia publicada — para editar, mexa
lá e sincronize.
