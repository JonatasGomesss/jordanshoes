<template>
  <!-- ── Banner ── -->
  <header class="banner">
    <span>Frete grátis para todo o Brasil</span>
  </header>

  <!-- ── Hero ── -->
  <section class="hero">
    <div class="hero__overlay" />
    <img
      alt="Michael Jordan"
      class="hero__bg"
      src="../img/image-michael-jordan.png"
    >

    <div class="hero__content">
      <div class="hero__brand">
        <img alt="Logo Jordan" class="hero__logo" src="../img/logo-jordan.png">
        <span class="hero__brand-name">JordanShoes</span>
      </div>
      <h1 class="hero__title">
        A MELHOR<br>
        <em>LOJA</em> DE<br>
        JORDAN
      </h1>
      <p class="hero__sub">
        Fruto da velha e forte parceria entre a Nike e Michael Jordan.
      </p>
      <a class="hero__cta" href="#produtos">Ver coleção</a>
    </div>

    <div class="hero__scroll">
      <span>scroll</span>
      <div class="hero__scroll-line" />
    </div>
  </section>

  <!-- ── Frase ── -->
  <section class="tagline">
    <div class="tagline__inner">
      <h2 class="tagline__title">Os melhores<br><span>em um só lugar</span></h2>
      <p class="tagline__desc">
        A marca Jordan na JordanShoes é a escolha certa para os amantes
        de sneakers que buscam estilo, história e conforto.
      </p>
    </div>
    <div class="tagline__divider" />
  </section>

  <!-- ── Produtos ── -->
  <section id="produtos" class="produtos">
    <div class="produtos__header">
      <span class="produtos__label">Coleção</span>
      <h2 class="produtos__title">Destaques</h2>
    </div>

    <div class="cards-grid">
      <div
        v-for="(produto, index) in produtos"
        :key="index"
        class="card"
        :style="`--delay: ${index * 0.08}s`"
      >
        <div class="card__img-wrap">
          <img :alt="produto.nome" class="card__img" :src="produto.imagem">
          <div class="card__overlay" />
        </div>
        <div class="card__body">
          <h3 class="card__nome">{{ produto.nome }}</h3>
          <div class="card__footer">
            <span class="card__preco">R$ {{ produto.preco.toFixed(2) }}</span>
            <button class="card__btn">Comprar</button>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- ── Footer ── -->
  <footer class="footer">
    <p>© {{ ano }} JordanShoes — Todos os direitos reservados</p>
  </footer>
</template>

<script setup>
  import img5 from '../img/imagem (1).png'
  import img1 from '../img/imagem (2).png'
  import img4 from '../img/imagem (3).png'
  import img3 from '../img/imagem (4).png'
  import img2 from '../img/imagem (5).png'
  import img6 from '../img/imagem.png'

  const ano = new Date().getFullYear()

  const produtos = [
    { nome: 'Air Jordan 1 Mid GS "Light Smoke Grey"', preco: 899.9, imagem: img1 },
    { nome: 'Air Jordan 1 Mid Black White', preco: 949.9, imagem: img2 },
    { nome: 'Air Jordan 1 Retro High', preco: 1299.9, imagem: img3 },
    { nome: 'Air Jordan 1 Low', preco: 799.9, imagem: img4 },
    { nome: 'Air Jordan 4 Retro', preco: 1599.9, imagem: img5 },
    { nome: 'Air Jordan 11 Concord', preco: 1899.9, imagem: img6 },
  ]
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Barlow+Condensed:ital,wght@0,400;0,600;0,700;0,800;1,700&family=DM+Sans:wght@300;400;500&display=swap');

/* ══════════════════════════════════════════════════
   TOKENS
══════════════════════════════════════════════════ */
:root {
  --bg:          #090909;
  --surface:     #111111;
  --card-bg:     #141414;
  --border:      rgba(255, 255, 255, 0.07);
  --fg:          #f0f0f0;
  --muted:       #666;
  --red:         #E31837;
  --red-dim:     rgba(227, 24, 55, 0.12);
  --font-disp:   'Barlow Condensed', sans-serif;
  --font-body:   'DM Sans', sans-serif;
  --ease-spring: cubic-bezier(0.16, 1, 0.3, 1);
}

*, *::before, *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

html { scroll-behavior: smooth; }

body {
  background: var(--bg);
  color: var(--fg);
  font-family: var(--font-body);
  -webkit-font-smoothing: antialiased;
  overflow-x: hidden;
}

/* ══════════════════════════════════════════════════
   ANIMATIONS
══════════════════════════════════════════════════ */
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(28px); }
  to   { opacity: 1; transform: translateY(0); }
}

@keyframes fadeIn {
  from { opacity: 0; }
  to   { opacity: 1; }
}

@keyframes scrollBar {
  0%   { transform: scaleY(0); transform-origin: top; }
  50%  { transform: scaleY(1); transform-origin: top; }
  51%  { transform: scaleY(1); transform-origin: bottom; }
  100% { transform: scaleY(0); transform-origin: bottom; }
}

@keyframes cardIn {
  from { opacity: 0; transform: translateY(32px); }
  to   { opacity: 1; transform: translateY(0); }
}
</style>

<style scoped>
/* ══════════════════════════════════════════════════
   BANNER
══════════════════════════════════════════════════ */
.banner {
  background: var(--red);
  color: #fff;
  text-align: center;
  padding: 0.5rem 1rem;
  font-family: var(--font-body);
  font-size: 0.8rem;
  font-weight: 500;
  letter-spacing: 0.04em;
}

/* ══════════════════════════════════════════════════
   HERO
══════════════════════════════════════════════════ */
.hero {
  position: relative;
  height: 100svh;
  min-height: 580px;
  display: flex;
  align-items: flex-end;
  overflow: hidden;
}

.hero__bg {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center top;
  filter: grayscale(20%);
}

.hero__overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(
    105deg,
    rgba(9, 9, 9, 0.88) 0%,
    rgba(9, 9, 9, 0.55) 55%,
    rgba(9, 9, 9, 0.2) 100%
  );
  z-index: 1;
}

.hero__content {
  position: relative;
  z-index: 2;
  padding: 0 6vw 6rem;
  max-width: 640px;
  animation: fadeUp 0.9s var(--ease-spring) 0.1s both;
}

.hero__brand {
  display: flex;
  align-items: center;
  gap: 0.625rem;
  margin-bottom: 1.75rem;
}

.hero__logo {
  width: 36px;
  height: 36px;
  object-fit: contain;
  filter: invert(1);
}

.hero__brand-name {
  font-family: var(--font-disp);
  font-size: 0.9rem;
  font-weight: 600;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: rgba(255, 255, 255, 0.65);
}

.hero__title {
  font-family: var(--font-disp);
  font-size: clamp(4rem, 10vw, 7.5rem);
  font-weight: 800;
  line-height: 0.92;
  letter-spacing: -0.01em;
  text-transform: uppercase;
  color: #fff;
  margin-bottom: 1.5rem;
}

.hero__title em {
  font-style: italic;
  color: var(--red);
}

.hero__sub {
  font-size: 1rem;
  line-height: 1.7;
  color: rgba(255, 255, 255, 0.5);
  max-width: 26rem;
  margin-bottom: 2.5rem;
}

.hero__cta {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.875rem 2rem;
  background: var(--red);
  color: #fff;
  font-family: var(--font-disp);
  font-size: 0.875rem;
  font-weight: 700;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  text-decoration: none;
  border-radius: 0.25rem;
  transition: background 0.2s, transform 0.25s var(--ease-spring);
}

.hero__cta:hover {
  background: #ff1f3e;
  transform: translateY(-2px);
}

.hero__scroll {
  position: absolute;
  bottom: 2.5rem;
  right: 2.5rem;
  z-index: 2;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
  font-family: var(--font-disp);
  font-size: 0.65rem;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: rgba(255, 255, 255, 0.3);
  animation: fadeIn 1s ease 0.8s both;
}

.hero__scroll-line {
  width: 1px;
  height: 48px;
  background: rgba(255, 255, 255, 0.12);
  overflow: hidden;
  position: relative;
}

.hero__scroll-line::after {
  content: '';
  position: absolute;
  inset: 0;
  background: var(--red);
  animation: scrollBar 2s ease-in-out infinite;
}

/* ══════════════════════════════════════════════════
   TAGLINE
══════════════════════════════════════════════════ */
.tagline {
  padding: 5rem 6vw;
  display: grid;
  grid-template-columns: 1fr auto;
  align-items: center;
  gap: 3rem;
  border-bottom: 1px solid var(--border);
}

.tagline__title {
  font-family: var(--font-disp);
  font-size: clamp(2.25rem, 5vw, 3.5rem);
  font-weight: 700;
  line-height: 1.05;
  text-transform: uppercase;
  letter-spacing: -0.01em;
}

.tagline__title span { color: var(--red); }

.tagline__desc {
  max-width: 380px;
  font-size: 0.9375rem;
  line-height: 1.75;
  color: var(--muted);
}

.tagline__divider {
  display: none;
}

@media (max-width: 768px) {
  .tagline {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }
}

/* ══════════════════════════════════════════════════
   PRODUTOS
══════════════════════════════════════════════════ */
.produtos {
  padding: 5rem 6vw 6rem;
  max-width: 1280px;
  margin: 0 auto;
}

.produtos__header {
  display: flex;
  flex-direction: column;
  gap: 0.375rem;
  margin-bottom: 3rem;
}

.produtos__label {
  font-family: var(--font-disp);
  font-size: 0.72rem;
  font-weight: 600;
  letter-spacing: 0.16em;
  text-transform: uppercase;
  color: var(--red);
}

.produtos__title {
  font-family: var(--font-disp);
  font-size: clamp(2rem, 4vw, 2.75rem);
  font-weight: 800;
  text-transform: uppercase;
  letter-spacing: -0.01em;
}

/* ── Cards grid ── */
.cards-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 1.25rem;
}

.card {
  background: var(--card-bg);
  border: 1px solid var(--border);
  border-radius: 0.75rem;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  opacity: 0;
  animation: cardIn 0.7s var(--ease-spring) var(--delay, 0s) forwards;
  transition: border-color 0.3s, transform 0.35s var(--ease-spring);
}

.card:hover {
  border-color: rgba(227, 24, 55, 0.3);
  transform: translateY(-4px);
}

.card__img-wrap {
  position: relative;
  aspect-ratio: 4 / 3;
  overflow: hidden;
  background: #1a1a1a;
}

.card__img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.6s var(--ease-spring);
}

.card:hover .card__img { transform: scale(1.05); }

.card__overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(
    to bottom,
    transparent 50%,
    rgba(9, 9, 9, 0.5) 100%
  );
}

.card__body {
  padding: 1.25rem 1.5rem 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  flex: 1;
}

.card__nome {
  font-family: var(--font-body);
  font-size: 0.9rem;
  font-weight: 500;
  line-height: 1.45;
  color: var(--fg);
}

.card__footer {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 0.75rem;
  margin-top: auto;
}

.card__preco {
  font-family: var(--font-disp);
  font-size: 1.375rem;
  font-weight: 700;
  color: var(--fg);
  letter-spacing: -0.01em;
}

.card__btn {
  padding: 0.5rem 1.125rem;
  background: var(--red);
  color: #fff;
  border: none;
  border-radius: 0.25rem;
  font-family: var(--font-disp);
  font-size: 0.8rem;
  font-weight: 700;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  cursor: pointer;
  transition: background 0.2s, transform 0.2s var(--ease-spring);
  white-space: nowrap;
}

.card__btn:hover {
  background: #ff1f3e;
  transform: scale(1.04);
}

/* ══════════════════════════════════════════════════
   FOOTER
══════════════════════════════════════════════════ */
.footer {
  border-top: 1px solid var(--border);
  padding: 2rem 6vw;
  text-align: center;
  font-size: 0.8rem;
  color: var(--muted);
  font-family: var(--font-body);
}

/* ══════════════════════════════════════════════════
   RESPONSIVIDADE
══════════════════════════════════════════════════ */
@media (max-width: 600px) {
  .hero__content    { padding: 0 1.5rem 4rem; }
  .hero__scroll     { display: none; }
  .tagline          { padding: 3.5rem 1.5rem; }
  .produtos         { padding: 3.5rem 1.5rem 5rem; }
  .cards-grid       { grid-template-columns: 1fr; gap: 1rem; }
  .card__footer     { flex-direction: column; align-items: flex-start; }
  .card__btn        { width: 100%; text-align: center; padding: 0.625rem; }
}

@media (min-width: 601px) and (max-width: 900px) {
  .cards-grid { grid-template-columns: repeat(2, 1fr); }
}
</style>
