# Yotakes — Pitch

Deck do **Yotakes**, o Letterboxd dos restaurantes, feito em São Paulo. Cada *take* é
uma resenha curta com nota de 0 a 5 estrelas, foto e contexto — rede de confiança, não
ranking genérico.

**No ar:** https://gabrieldallape.github.io/yotakes-pitch/

## Como funciona

`index.html` é um arquivo único auto-contido: 8 slides em 16:9, navegáveis pelo teclado.
Cada `<section class="slide sN">` ocupa a viewport e só a que tem `.active` aparece.

- `?slide=N` (1-indexed) abre direto no slide N — é o que o batch de screenshot usa.
- O `font-size` do slide é calculado para `1em = 1% da altura`, então todo tamanho
  interno em `em` acompanha a tela.

## Assets

- `yo-bubble.png` — mascote Yo em creme, para fundos tomate/garrafa.
- `qr-yotakes.png` — QR do último slide, apontando para a produção.

Fontes (Inter + Fraunces) vêm do Google Fonts. Paleta: tomate `#e84b3f`,
garrafa `#1f4d40`, bordô `#5f1b1f`, creme `#f2ead7`.

## Origem

A fonte canônica vive em `docs/pitch-1.html` no repositório principal do produto
(privado). Este repositório é a cópia publicada — para editar, mexa lá e sincronize.
