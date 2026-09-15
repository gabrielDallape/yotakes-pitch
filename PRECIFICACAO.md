# Memória de cálculo — preço dos planos e sustentação do app

Base dos quatro slides auxiliares novos (*O que o parceiro enxerga*, *Como a IA lê os
takes*, *Por que R$ 23,90* e *Quantos Chefes sustentam o app*). Serve para responder na
banca de onde veio cada número.

Levantado em **15/09/2026**. Câmbio usado: **US$ 1 = R$ 5,15** (USD/BRL em 14/09/2026).

---

## 1. Por que R$ 23,90 e R$ 9,90

O preço **não saiu do custo**. Saiu de duas âncoras, e a conta de custo (seção 2) mostra
por quê: infraestrutura custa três centavos por usuário, então custo não define preço
nenhum aqui.

### Âncora 1 — o que o nicho já paga lá fora

| | Preço de lista | Convertido |
|---|---|---|
| Letterboxd **Pro** | US$ 19/ano | **R$ 8,15/mês** |
| Letterboxd **Patron** | US$ 49/ano | **R$ 21,03/mês** |

O Letterboxd é o comparável direto: comunidade editorial de nicho, mesma mecânica de
registrar-e-avaliar. Sous Chef (R$ 9,90) fica logo acima do Pro; Chefe (R$ 23,90) logo
acima do Patron.

### Âncora 2 — o que o brasileiro já assina sem pensar

| | Preço/mês |
|---|---|
| Duolingo Super (individual) | R$ 14,99 |
| Netflix Padrão com anúncios | R$ 20,90 |
| **Spotify Individual** | **R$ 23,90** |
| Duolingo Max | R$ 33,33 |
| Netflix Padrão sem anúncios | R$ 44,90 |

**R$ 23,90 é exatamente o Spotify Individual no Brasil.** É o valor de assinatura mensal
que o público-alvo já tem no cartão e não questiona — é o teto confortável da categoria
de app de consumo, não um número escolhido no chute.

### O que ainda falta

A régua justifica **a faixa**, não o centavo. Para fechar o valor de verdade falta teste
de preço com a base real: Van Westendorp (quatro perguntas de percepção de preço) ou A/B
na própria tela de assinatura. Enquanto isso não roda, o número é uma hipótese ancorada,
e o slide diz isso.

---

## 2. Quantos assinantes Chefe sustentam o app

### Receita líquida por assinante

```
R$ 23,90 bruto
 − 15%  loja de aplicativo (App Store / Google Play, Small Business Program,
        válido enquanto a receita anual ficar abaixo de US$ 1 mi)
 − 6%   imposto (Simples Nacional, faixa inicial)
= R$ 19,10 líquidos por Chefe/mês
```

O Sous Chef, pela mesma conta, rende **R$ 7,91 líquidos**.

### Custo de infraestrutura — 10 mil usuários ativos/mês

| Item | US$/mês | R$/mês |
|---|---|---|
| Supabase Pro (banco, auth, storage; 100 mil MAU inclusos) | 25,00 | 129 |
| Vercel Pro (hospedagem e CDN; 1 TB de tráfego) | 20,00 | 103 |
| E-mail transacional (magic link e notificação) | 20,00 | 103 |
| Storage das fotos dos takes | 0,00 | 0 |
| Domínio (rateio mensal) | 1,25 | 6 |
| **Total** | **66,25** | **341** |

→ **R$ 0,034 por usuário/mês.**
→ **18 assinantes Chefe** cobrem a conta inteira (341 ÷ 19,10).
→ São **0,18% da base**. O Letterboxd converte 5% — margem de ~28×.
→ Cada Chefe sustenta **560 usuários gratuitos**.

### O mesmo em 100 mil usuários

| Item | US$/mês |
|---|---|
| Supabase Pro + Vercel Pro | 45,00 |
| Storage (≈420 GB médios, 100 GB inclusos) | 6,72 |
| Egress acima do incluído (≈2,4 TB, cacheado a US$ 0,03/GB) | 57,00 |
| E-mail transacional (volume maior) | 85,00 |
| Domínio | 1,25 |
| **Total** | **194,97** → **R$ 1.004** |

→ **R$ 0,010 por usuário/mês** — a curva melhora com escala.
→ **53 Chefes** cobrem a conta de 100 mil usuários.

### Premissas de consumo (é aqui que a banca pode cutucar)

- 2 takes por usuário por mês, cada um com 1 foto de ~350 KB já otimizada (WebP)
- 15 sessões por usuário por mês, ~20 imagens carregadas por sessão a ~80 KB (thumb)
- Storage acumulando ao longo de 12 meses, média do ano usada no cálculo
- Preços de lista, sem desconto anual e sem crédito de startup

Nenhum desses números veio de uso real — a base hoje é pequena demais para medir. São
estimativas conservadoras e a ordem de grandeza é o que importa: **a infra é barata o
bastante para não ser o que define o preço.**

### O limite honesto desta conta

Ela cobre **só infraestrutura**. Não cobre salário, marketing, suporte nem aquisição.
1.000 Chefes rendem R$ 19,1 mil líquidos/mês — 19× a infra de 100 mil usuários, e é essa
sobra que teria de virar time. É por isso que o lado parceiro (B2B) existe: a assinatura
do consumidor sustenta a operação técnica, não a empresa.

---

## 3. Custo da camada de IA do painel do parceiro

Modelo pequeno (Claude Haiku 4.5: US$ 1,00/milhão de tokens de entrada, US$ 5,00/milhão
de saída), rodando em lote uma vez por semana por parceiro:

```
entrada  ~60.000 tokens (takes do período já agregados)  = US$ 0,060
saída     ~1.500 tokens (a leitura da semana)            = US$ 0,0075
por análise                                              = US$ 0,0675  ≈ R$ 0,35
× 4 semanas                                              ≈ R$ 1,40 / parceiro / mês
```

Com lote (−50%) e prompt cacheado (−90% na entrada repetida) isso cai mais ainda.

**Comparação de mercado:** ReviewTrackers cobra a partir de US$ 89/mês; Birdeye, de
US$ 299 a US$ 449/mês por unidade. O custo de entregar essa análise está no **dado**
(ter massa de takes no bairro), não no modelo.

---

## 4. Como a IA funciona — referência de mercado

O pipeline dos slides não é invenção nossa, é o que o setor já faz:

1. **ABSA (aspect-based sentiment analysis)** — cada avaliação é quebrada em aspectos
   (comida, serviço, ambiente, preço, espera) com sentimento por aspecto. O Yelp lançou
   exatamente isso em dez/2024: review insights com categorias de comida, serviço e
   ambiente, cada uma com score de sentimento de 1 a 100.
2. **Clustering de temas** — os aspectos viram temas recorrentes por período e por
   região. É o que separa ruído de padrão.
3. **Síntese por LLM sobre o agregado** — o modelo lê os temas já agrupados, nunca as
   avaliações cruas. Reduz custo, alucinação e exposição de dado individual.
4. **Contraste com a região** — o mesmo pipeline roda para o bairro, e o parceiro vê o
   próprio número contra a média da rua.

O diferencial do Yotakes no passo 1 não é o modelo: é o **insumo**. O review do Yelp e do
Google é anônimo e sem histórico. O take do Yotakes vem de conta com rede, frequência e
histórico — dá para perfilar quem reclamou, não só o que foi reclamado.

---

## Fontes

- [Supabase Pro — preço e limites (2026)](https://makerkit.dev/blog/saas/supabase-pricing)
- [Vercel Pro — preço e limites (2026)](https://getdeploying.com/supabase-vs-vercel)
- [Claude API — preço por milhão de tokens (set/2026)](https://benchlm.ai/anthropic/api-pricing)
- [Apple App Store Small Business Program — 15%](https://www.revenuecat.com/blog/engineering/small-business-program)
- [Letterboxd Pro — US$ 19/ano](https://screenrant.com/letterboxd-pro-perfect-gift-offer-price/)
- [Letterboxd Patron — US$ 49/ano](https://alittlebithuman.com/is-letterboxd-pro-or-patron-worth-it/)
- [Spotify Premium Brasil — R$ 23,90](https://tecnoblog.net/noticias/spotify-premium-fica-mais-caro-no-brasil-veja-os-novos-precos/)
- [Netflix Brasil — planos e preços (2026)](https://www.techtudo.com.br/guia/2026/02/quanto-custa-a-netflix-hoje-veja-precos-planos-e-como-pagar-menos-streaming.ghtml)
- [Duolingo Brasil — planos e preços](https://fastcompanybrasil.com/news/duolingo-lanca-recursos-de-ia-em-plano-max-veja-quanto-custa-no-brasil/)
- [Yelp — AI review insights com sentimento por categoria (dez/2024)](https://techcrunch.com/2024/12/10/yelp-adds-ai-powered-review-insights-to-restaurants)
- [Birdeye — preço por localidade](https://www.reviewflowz.com/blog/how-much-does-birdeye-really-cost)
- [ReviewTrackers — a partir de US$ 89/mês](https://birdeye.com/tools/reviewtrackers-reviews/)
- [USD/BRL em setembro de 2026](https://tradingeconomics.com/brazil/currency)
