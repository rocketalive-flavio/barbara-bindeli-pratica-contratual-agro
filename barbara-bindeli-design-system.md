# Design System — barbarabindeli.com.br

## Fontes

| Uso | Fonte | Fonte alternativa |
|-----|-------|-------------------|
| **Headings** | `Playfair Display` (400, 500) | `ivypresto-display` (Adobe Typekit) |
| **Body** | `Inter` (300, 400, 500, 600) | sans-serif |

**Import Google Fonts:**
```
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@100..900&family=Playfair+Display:wght@400..900&display=swap");
```
**Adobe Typekit:** `https://use.typekit.net/vis7rsk.css` (ivypresto-display)

---

## Paleta de Cores

### Cores principais do tema (CSS Variables)
| Variavel | Hex | Uso |
|----------|-----|-----|
| `--brand-primary-light` | `#F8F6F3` | Fundo claro |
| `--brand-primary-dark` | `#000000` | Textos escuros |
| `--brand-secondary-default` | `#2B2D2D` | Secundario |

### Cores do site
| Cor | Hex | Uso |
|-----|-----|-----|
| Verde escuro (primario) | `#162212` | Background secoes principais |
| Verde escuro (secundario) | `#2b3320` | Background gradientes |
| Verde escuro (footer/texto) | `#273623` | Footer, texto em botoes, texto card |
| Verde musgo | `#80886e` | Labels/spans decorativos (uppercase) |
| Verde sage | `#829a62` | Gradientes de fundo |
| Dourado principal | `#c4af96` | Destaques em headings (`<b>`), checkmarks |
| Dourado claro | `#dac38c` | Badge do banner |
| Dourado medio | `#d7bd8b` | Gradientes dourados |
| Dourado escuro | `#dcc68d` | Gradientes dourados |
| Dourado cobre | `#c1996a` | Gradiente botao (inicio) |
| Bege claro | `#f7f2eb` | Background card de preco |
| Vermelho (live dot) | `#e84131` | Bolinha "ao vivo" no badge |
| Branco | `#fff` | Textos sobre fundo escuro |

### Opacidades de branco
- `rgba(255,255,255,.85)` — titulos H1
- `rgba(255,255,255,.7)` — paragrafos corpo
- `rgba(255,255,255,.65)` — subtextos
- `rgba(255,255,255,.55)` — textos secundarios
- `rgba(255,255,255,.45)` — textos terciarios
- `rgba(255,255,255,.14)` — bordas de cards
- `rgba(255,255,255,.12)` — bordas de lista

---

## Gradientes

| Nome | CSS | Uso |
|------|-----|-----|
| **Botao primario** | `linear-gradient(225deg, #c1996a 0%, #d7bd8b 49.04%, #dcc68d 100%)` | `.btn-primary` |
| **Botao hover** | `linear-gradient(180deg, #dcc68d 0%, #d7bd8b 100%)` | `.btn-primary:hover` |
| **Secao aprender** | `linear-gradient(180deg, #162212 0%, #2b3320 100%)` | `.s-aprender` |
| **Glow decorativo** | `radial-gradient(58.35% 58.35% at 50% 41.65%, #d7bd8b 0%, rgba(215,189,139,0) 100%)` | Efeito glow `.s-paraquem::after` |
| **Footer overlay** | `linear-gradient(180deg, rgba(130,154,98,0) 0%, #829a62 100%)` | `.s-card::after` |

---

## Tipografia (tamanhos)

**Base:** `font-size: 62.5%` no `html` (1rem = 10px)

| Elemento | Desktop | Mobile |
|----------|---------|--------|
| H1 (banner) | `6.4rem` | `5rem` |
| H2 (secoes) | `4.8rem` | `3.8rem` |
| H3 (cards) | `1.8rem` | — |
| Body grande | `1.8rem` | — |
| Body padrao | `1.6rem` / `16px` | — |
| Body pequeno | `1.4rem` | — |
| Labels uppercase | `1.4rem`, `letter-spacing: 2.8px` | — |
| Numeros decorativos | `6rem` (Playfair Display), `opacity: .06` | — |
| Preco grande | `70.396px` | — |
| Preco R$ | `46.931px` | — |
| Preco centavos | `28.158px` | — |

### CSS Variables de tipografia
```css
--font-family-body: "Inter", sans-serif;
--font-family-heading: "Playfair Display", serif;
--font-size-heading-xxl: 7.3rem; /* mobile: 4.2rem */
--font-size-heading-xl: 4.8rem;  /* mobile: 3.2rem */
--font-size-heading-lg: 3.2rem;  /* mobile: 2.4rem */
--font-size-heading-md: 2.4rem;  /* mobile: 2rem */
--font-size-heading-sm: 2rem;    /* mobile: 1.8rem */
--font-size-heading-xs: 1.8rem;  /* mobile: 1.6rem */
--font-size-heading-xxs: 1.6rem; /* mobile: 1.4rem */
--font-size-body-xl: 1.8rem;
--font-size-body-lg: 1.6rem;
--font-size-body-md: 1.4rem;
--font-size-body-sm: 1.2rem;
--font-size-body-xs: 1rem;
```

---

## Botao Primario (`.btn-primary`)

```css
border-radius: 10rem;          /* pill shape */
font-size: 1.6rem;
color: #273623;                 /* verde escuro */
padding: 2.4rem;
background: linear-gradient(225deg, #c1996a 0%, #d7bd8b 49.04%, #dcc68d 100%);
display: inline-flex;
align-items: center;
justify-content: center;
gap: .8rem;
transition: background-position .5s ease, transform .25s ease;
```
**Hover:**
```css
background: linear-gradient(180deg, #dcc68d 0%, #d7bd8b 100%);
transform: translateY(-1px);
```
Icone SVG seta com `stroke: #273623`.

---

## Layout & Espacamento

| Elemento | Valor |
|----------|-------|
| Container max-width | Padrao WordPress (~120rem) |
| Banner padding-top | `7.7rem` |
| Banner padding-bottom | `20rem` |
| Secoes padding vertical | `12.8rem` top e bottom |
| Grid "para quem" | `grid-template-columns: repeat(3, 1fr)` -> `1fr` no mobile |
| Gap entre cards | `2.4rem` |
| Gap entre itens lista | `3.2rem` |

---

## Border Radius

| Elemento | Valor |
|----------|-------|
| Secao mercado (topo) | `24px 24px 0 0` |
| Cards "para quem" | `1.2rem` |
| Icones | `1.4rem` |
| Card de preco | `24px` |
| Botoes | `10rem` (pill) |
| Badges/pills | `33554400px` (full round) |
| Container card CTA | `12px` |

---

## Efeitos & Animacoes

- **AOS (Animate on Scroll):** `data-aos-easing="ease"`, `data-aos-duration="1700"`, `data-aos-delay="0"`
- Tipos: `fade-left`, `fade-right`, `fade-up`, `fade-down`
- **Floating animation:** `translateY(-15px)` com keyframes
- **FadeIn:** `opacity 0->1` + `translateY(20px->0)`
- **Hover botao:** `translateY(-1px)` + mudanca de gradiente
- **Glow:** blur `36.65px`, opacity `.18` no pseudo-element

---

## Imagens / Assets

| Asset | URL |
|-------|-----|
| Logo (branco) | `wp-content/uploads/2026/03/Branco.png` |
| Banner desktop | `wp-content/uploads/2026/03/desktop-scaled.webp` |
| Banner mobile | `wp-content/uploads/2026/03/mobile-scaled.webp` |
| Foto Barbara | `wp-content/uploads/2026/03/sobre-scaled.png` |
| Icones SVG | Calendar, Clock, Users, Award, Briefcase, Shield, Sprout, TrendingUp, Scale, Star |

---

## Breakpoints

| Breakpoint | Comportamento |
|------------|---------------|
| <=1560px | Ajuste posicao background |
| <=1380px | Ajuste posicao background |
| <=1258px | Ajuste posicao background |
| <=1052px | Ajuste posicao background |
| <=990px | **Mobile layout** — colunas viram coluna unica, banner sem imagem de fundo |
| <=530px | Itens de lista empilham vertical |

---

## Estrutura de Secoes (HTML)

1. `.s-banner` — Hero com background image, logo, badge, H1, paragrafo, CTA, info pills
2. `.s-mercado` — Split layout (left heading + right lista com icones)
3. `.s-paraquem` — Grid 3 colunas de cards com icone, numero decorativo, titulo, descricao
4. `.s-aprender` — Lista de checkmarks com titulos bold e descricoes
5. `.s-sobre` — Split (left texto + right lista de info com icones)
6. `.s-quem` — Split (foto + bio com tags de especialidade)
7. `.s-card` — Card de preco centralizado com CTA
8. `footer` — Copyright + creditos

---

## CSS Completo das Secoes Principais

### Banner
```css
.s-banner {
  padding-top: 7.7rem;
  padding-bottom: 20rem;
  background-position: top right;
  background-size: cover;
  background-repeat: no-repeat;
}
.s-banner .container .info { max-width: 52.1rem; width: 100%; }
.s-banner .container .info .logo { max-width: 15.9rem; height: 9.1rem; margin-bottom: 5.1rem; }
.s-banner .container .info span {
  padding: .7rem 1.6rem;
  border-radius: 33554400px;
  background: rgba(215,189,139,.1);
  color: #dac38c;
  font-size: 1.4rem;
  font-weight: 400;
  line-height: 142%;
  letter-spacing: .35px;
  display: inline-flex;
  align-items: center;
  gap: .8rem;
}
.s-banner .container .info span::before {
  content: "";
  border-radius: 33554400px;
  opacity: .5526;
  background: #e84131;
  width: 8px;
  height: 8px;
}
.s-banner .container .info h1 {
  font-size: 6.4rem;
  color: rgba(255,255,255,.85);
  font-weight: 500;
  margin-top: 3.1rem;
}
.s-banner .container .info h1 b { color: #c4af96; }
.s-banner .container .info h1 .style-i { font-style: italic; color: rgba(255,255,255,.85); }
.s-banner .container .info p {
  margin-top: 2.4rem;
  color: rgba(255,255,255,.65);
  font-size: 1.8rem;
  font-weight: 400;
  line-height: 162%;
}
.s-banner .container .info a { margin-top: 5.4rem; }
.s-banner .container .info ul { display: flex; align-items: center; gap: 1.5rem; margin-top: 2.4rem; }
.s-banner .container .info ul li { display: flex; align-items: center; gap: .6rem; }
.s-banner .container .info ul li p { font-size: 1.4rem; color: #fff; margin-top: 0; }
```

### Mercado
```css
.s-mercado {
  border-radius: 24px 24px 0 0;
  background: #162212;
  margin-top: -10rem;
  padding-top: 12.8rem;
  padding-bottom: 10.2rem;
}
.s-mercado .container { display: flex; align-items: flex-start; justify-content: space-between; gap: 2.4rem; }
.s-mercado .container .left { max-width: 43.9rem; width: 100%; }
.s-mercado .container .left span {
  color: #80886e;
  font-size: 1.4rem;
  font-weight: 400;
  line-height: 140%;
  letter-spacing: 2.8px;
  text-transform: uppercase;
}
.s-mercado .container .left h2 { color: #fff; font-size: 4.8rem; font-weight: 500; line-height: 100%; }
.s-mercado .container .left h2 b { font-weight: 500; color: #c4af96; }
.s-mercado .container .right { max-width: 65.8rem; width: 100%; }
.s-mercado .container .right ul { display: flex; flex-direction: column; gap: 3.2rem; }
.s-mercado .container .right ul li { display: flex; align-items: flex-start; gap: 2.4rem; }
.s-mercado .container .right ul li .icone {
  max-width: 4rem; width: 100%; height: 4rem;
  border-radius: 1.4rem;
  background: rgba(128,136,110,.15);
  display: flex; align-items: center; justify-content: center;
}
.s-mercado .container .right ul li p { color: rgba(255,255,255,.7); font-size: 1.6rem; font-weight: 400; }
.s-mercado .container .right ul li p b { font-weight: 400; color: #fff; }
```

### Para Quem
```css
.s-paraquem {
  background: #162212;
  padding-top: 8rem;
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.s-paraquem::after {
  content: "";
  width: 58rem; height: 58rem;
  border-radius: 582.114px;
  opacity: .18;
  background: radial-gradient(58.35% 58.35% at 50% 41.65%, #d7bd8b 0%, rgba(215,189,139,0) 100%);
  filter: blur(36.6500015259px);
  position: absolute;
  bottom: -40rem;
}
.s-paraquem .container span {
  color: #80886e;
  font-size: 1.4rem;
  letter-spacing: 2.8px;
  text-transform: uppercase;
  text-align: center;
}
.s-paraquem .container h2 { color: #fff; font-size: 4.8rem; font-weight: 500; text-align: center; margin-top: 1.6rem; }
.s-paraquem .container h2 b { font-weight: 500; color: #c4af96; }
.s-paraquem .container ul { display: grid; grid-template-columns: repeat(3, 1fr); gap: 2.4rem; margin-top: 6.4rem; }
.s-paraquem .container ul li {
  padding: 3.3rem;
  border-radius: 1.2rem;
  border: 1px solid rgba(255,255,255,.12);
}
.s-paraquem .container ul li .topo .icone {
  max-width: 4.4rem; width: 100%; height: 4.4rem;
  border-radius: 1.4rem;
  background: rgba(128,136,110,.15);
}
.s-paraquem .container ul li .topo .number span {
  color: #c4af96;
  font-family: "Playfair Display", serif;
  font-size: 6rem;
  opacity: .06;
}
.s-paraquem .container ul li .info h3 { font-size: 1.8rem; color: #fff; line-height: 155%; }
.s-paraquem .container ul li .info p { color: rgba(255,255,255,.55); font-size: 1.4rem; line-height: 163%; margin-top: 1.2rem; }
.s-paraquem .container a { padding: 2rem 3.2rem; margin-top: 6.4rem; }
```

### Aprender
```css
.s-aprender {
  padding-top: 12.8rem;
  padding-bottom: 12.8rem;
  background: linear-gradient(180deg, #162212 0%, #2b3320 100%);
}
.s-aprender .container h2 { color: #fff; font-size: 4.8rem; font-weight: 500; text-align: center; margin-top: 1.6rem; }
.s-aprender .container h2 b { font-weight: 500; color: #c4af96; }
.s-aprender .container p { color: rgba(255,255,255,.55); text-align: center; font-size: 16px; }
```

### Sobre
```css
.s-sobre {
  padding-top: 12.8rem;
  padding-bottom: 12.8rem;
  background: #2b3320;
}
```

### Quem (Bio)
```css
.s-quem {
  padding-top: 12.8rem;
  padding-bottom: 12.8rem;
  background: #273623;
}
.s-quem .container { display: flex; align-items: flex-start; gap: 2.4rem; }
.s-quem .container .photo { max-width: 74.1rem; width: 100%; }
.s-quem .container .info { max-width: 52.3rem; width: 100%; }
.s-quem .container .info span {
  color: #fff;
  font-size: 1.4rem;
  letter-spacing: 2.8px;
  text-transform: uppercase;
}
.s-quem .container .info h2 {
  color: #fff; font-size: 4.8rem; font-weight: 500;
  border-bottom: 2px solid #c4af96;
  padding-bottom: 3.2rem;
  margin-top: 1.6rem;
}
.s-quem .container .info h2 b { font-weight: 500; color: #c4af96; }
.s-quem .container .info .text p { color: rgba(255,255,255,.7); font-size: 1.6rem; line-height: 163%; }
.s-quem .container .info ul li {
  color: #fff;
  font-size: 1.4rem;
  padding: .9rem 1.2rem;
  border-radius: 33554400px;
  border: 1px solid rgba(220,198,141,.31);
}
```

### Card de Preco
```css
.s-card {
  padding-top: 12.8rem;
  padding-bottom: 12.8rem;
  background-color: #2b3320;
  position: relative;
}
.s-card::after {
  content: "";
  position: absolute;
  bottom: 0; left: 0;
  width: 100%; height: 68.4rem;
  opacity: .4;
  background: linear-gradient(180deg, rgba(130,154,98,0) 0%, #829a62 100%);
}
.s-card .container {
  position: relative; z-index: 2;
  max-width: 80rem; width: 100%;
  border-radius: 12px;
  padding: 3.4rem 6.4rem;
  border: 1px solid rgba(255,255,255,.14);
  background: rgba(22,34,18,.44);
  display: flex; align-items: center; justify-content: center;
  text-align: center; flex-direction: column;
}
.s-card .container .card-price {
  padding: 4rem 3.2rem;
  border-radius: 24px;
  border: 1px solid rgba(39,54,35,.1);
  background: #f7f2eb;
  margin-top: 4.1rem;
  max-width: 34.6rem; width: 100%;
}
.s-card .container .card-price .price h3 {
  color: #273623;
  font-size: 70.396px;
  font-weight: 400;
  font-family: var(--font-family-heading);
}

```

### Footer
```css
footer {
  background-color: #273623;
  padding: 2.8rem 0;
}
footer .container { display: flex; align-items: center; justify-content: space-between; }
footer .container p { color: rgba(255,255,255,.605); font-size: 14.137px; font-weight: 500; line-height: 140%; }
```
