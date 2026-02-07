<template>
  <header class="cabeca">
    <p>Frete grátis para todo o Brasil</p>
  </header>

  <section class="imagem">
    <div class="info">
      <div class="img">
        <img src="../img/logo-jordan.png" alt="Logo Jordan" />
        <p>JordanShoes</p>
      </div>

      <h3>A melhor loja de Jordan</h3>

      <p class="stile-P">
        O tênis Jordan é fruto de uma velha e forte parceria entre a Nike e o
        jogador Michael Jordan.
      </p>
    </div>
  </section>

  <section class="infoJordan">
    <div class="info-text">
      <h2>Os melhores em um só lugar</h2>
      <p>
        A marca Jordan na JordanShoes é a escolha certa para os amantes de
        sneakers que buscam estilo e conforto.
      </p>
    </div>
  </section>

  <section class="cards">
    <v-card
      v-for="(produto, index) in produtos"
      :key="index"
      max-width="315"
      elevation="3"
    >
      <v-img
        height="200"
        :src="produto.imagem"
        cover
      />

      <v-card-title class="titulo">
        {{ produto.nome }}
      </v-card-title>

      <v-card-subtitle class="preco">
        R$ {{ produto.preco.toFixed(2)}}
      </v-card-subtitle>

      <v-card-actions>
        <v-btn color="white" variant="flat" block>
          Comprar
        </v-btn>
      </v-card-actions>
    </v-card>
  </section>
</template>

<script setup>
import img1 from '../img/imagem (2).png'
import img2 from '../img/imagem (5).png'
import img3 from '../img/imagem (4).png'
import img4 from '../img/imagem (3).png'
import img5 from '../img/imagem (1).png'
import img6 from '../img/imagem.png'

const produtos = [
  {
    nome: 'Air Jordan 1 Mid GS "Light Smoke Grey"',
    preco: 899.9,
    imagem: img1
  },
  {
    nome: 'Air Jordan 1 Mid Black White',
    preco: 949.9,
    imagem: img2
  },
  {
    nome: 'Air Jordan 1 Retro High',
    preco: 1299.9,
    imagem: img3
  },
  {
    nome: 'Air Jordan 1 Low',
    preco: 799.9,
    imagem: img4
  },
  {
    nome: 'Air Jordan 4 Retro',
    preco: 1599.9,
    imagem: img5
  },
  {
    nome: 'Air Jordan 11 Concord',
    preco: 1899.9,
    imagem: img6
  }
]
</script>

<style scoped>
.cabeca {
  background-color: #ffffff;
  color: #1f1e2b;
  text-align: center;
  font-weight: 400;
  padding: 10px;
}
.imagem {
  background-image: url(../img/image-michael-jordan.png);
  background-size: cover;
  background-position: center;
  display: flex;
  width: 100%;
  height: 50vh;
}

.info {
  position: relative;
  top: 15%;
  left: 12%;
  color: white;
  max-width: 420px;
}

.img {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 14px;
}

.stile-P {
  margin-top: 12px;
}

.infoJordan {
  display: flex;
  justify-content: center;
  margin: 40px 0 60px;
}

.info-text {
  text-align: center;
  max-width: 500px;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 40px;

  max-width: 1200px;
  margin: 0 auto 60px;
  padding: 0 20px;
}

.titulo {
  font-size: 1rem;
  font-weight: 500;
}

.preco {
  font-size: 1.2rem;
  font-weight: bold;
  color: #000;
}

@media (max-width: 768px) {

  .imagem {
    height: 35vh;
    justify-content: center;
  }

  .info {
    position: static;
    text-align: center;
    padding: 0 20px;
    max-width: 100%;
  }

  .img {
    justify-content: center;
  }

  .stile-P {
    width: 100%;
  }

  .info-text {
    padding: 0 20px;
  }

  .cards {
    grid-template-columns: 1fr;
    gap: 24px;
    padding: 0 16px;
  }

  .titulo {
    font-size: 0.95rem;
    text-align: center;
  }

  .preco {
    text-align: center;
    font-size: 1.1rem;
  }

  .v-card-actions {
    padding: 16px;
  }
}
</style>