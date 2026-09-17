# Yotakes — Pitch

Deck do **Yotakes**, o Letterboxd dos restaurantes, feito em São Paulo. Cada *take* é
uma resenha curta com nota de 0 a 5 estrelas, foto e contexto — rede de confiança, não
ranking genérico.

**No ar:** https://gabrieldallape.github.io/yotakes-pitch/

## Como funciona

`index.html` é um arquivo único auto-contido: 38 seções em 16:9, navegáveis pelo teclado —
18 slides de pitch, um separador preto que marca o fim da apresentação, e o material de
apoio (6 slides auxiliares, 8 de Q&A e 5 de dados) guardado para as perguntas. Cada
`<section class="slide sN">` ocupa a viewport e só a que tem `.active` aparece.

Os números dos slides auxiliares de preço e de sustentação têm memória de cálculo em
[`PRECIFICACAO.md`](PRECIFICACAO.md) — premissas, contas e fontes, para defender na banca.

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
- `julia-v4.png` — retrato da Júlia (decepcionada) no slide da persona.
- `julia-v3.png` — Júlia sorrindo, no medalhão do slide de CTA.
- `julia-v2.png` — retrato anterior da persona, sem uso hoje.
- `julia-casal.jpg` — foto no slide preto, o separador que fecha o pitch.
- `qr-yotakes.png` — QR do roadmap e do último slide, apontando para a produção.
- `telas/` — prints das telas do app no Figma (feed, avaliação, perfil, descoberta),
  usados dentro da moldura de celular nos slides de produto. Duas delas foram editadas
  depois do export: `perfil.png` (o nome do perfil virou "Júlia", a persona do deck) e
  `avaliacao.png` (o restaurante virou Merenda da Cidade e as duas fotos foram
  preenchidas). Os textos foram reescritos em **Parkinsans** — a mesma fonte do design,
  a mesma que o app carrega em `web/src/app/layout.tsx` — nos pesos e tamanhos medidos
  do próprio PNG. O export original e intocado continua em
  `yotakes/docs/figma/telas/` no repositório do produto.

  Foto do Merenda da Cidade: **Rogério Gomes / Divulgação**, publicada pela Exame. É
  material de divulgação usado aqui em contexto acadêmico — se o deck virar peça
  comercial, trocar por foto própria ou licenciada.

Fontes (Inter + Unbounded) vêm do Google Fonts. Paleta: tomate `#e84b3f`,
garrafa `#1f4d40`, bordô `#5f1b1f`, creme `#f2ead7`.

## Origem

O deck nasceu em `yotakes-pitch/index.html` na branch `monorepo` do repositório principal
do produto (privado), mas aquela cópia parou em 03/08/2026, com 26 slides. **Quem manda
hoje é este repositório** — é aqui que o deck evoluiu e é daqui que o GitHub Pages
publica. A cópia na `monorepo` está desatualizada e não deve ser usada como base.
