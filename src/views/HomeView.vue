<template>
  <section class="py-5 text-center container">
    <div class="row py-lg-5">
      <div class="col-lg-6 col-md-8 mx-auto">
        <h1 class="fw-light">Portfolio | jean Sebastien Rakotonirina</h1>
        <p class="lead text-muted">Bienvenue sur mon site, fraîchement diplômé Développeur d'Applications
          OpenClassRooms,
          j'ai trouvé que ReactJs est super, il reste un framework explicite pour de très gros projets.
          Alors en cherchant, j'ai découvert VueJs (Vue Router, VueX) et je me suis lancé dans ce framework, moins
          lourd,
          où les changements d'état sont simples à gérer. Ici, j'utilise essentiellement des directives en inline html.
          Bref, Moins de lignes de code, je code plus vite, c'est un régal. Tout ce dont on a besoin est là, même le
          backend.
        </p>
        <p>Vous trouverez ci-dessous quelques projets validés lors de ma formation.</p>
        <p>
          <a href="#" class="btn btn-primary my-2">Main call to action</a>
          <a href="#" class="btn btn-secondary my-2">Secondary action</a>
        </p>
      </div>
    </div>
  </section>
  <div class="row row-cols-1 row-cols-lg-3 align-items-stretch g-4 py-5" style="width: 85%; margin: 0 auto">
    <div class="col-md-4" v-for="pro in projects" :key="pro.id">
      <div class="card card-3 card-cover h-100 overflow-hidden text-bg-dark rounded-4 shadow-lg"
        :style="{ background: 'url(' + pro.imgSrc + ') no-repeat' }"
        style="background-size: cover;border-radius: 10px !important;padding: 2px;border: 2px solid black;">
        <div class="hidden d-flex flex-column h-100 p-5 pb-3 text-blue text-shadow-1">
          <h3 class="pt-5 mt-5 mb-4 display-6 lh-1 fw-bold" style="text-shadow: 2px 2px 2px green">
            {{ pro.title }}
          </h3>
          <ul class="-flex list-unstyled mt-auto">
            <button @click="handleClick(pro.url)" class="btn btn-success">
              + Détails
            </button>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'HomeView',
  components: {},
  data: function () {
    return {
      projects: {}
    }
  },
  computed: {
    styles: function () {
      return this.projects.map((m) => m.imgSrc)
    }
  },
  mounted: async function () {
    const res = await fetch('https://jeansebastienrakotonirina.github.io/portfolioApi/projects.json')
    this.projects = await res.json()
  },
  methods: {
    handleClick: function (url) {
      window.open(url)
    }
  }
}
</script>
<style>
.card {
  border-radius: 4px;
  background: #fff;
  box-shadow: 0 6px 10px rgba(0, 0, 0, .08), 0 0 6px rgba(0, 0, 0, .05);
  transition: .3s transform cubic-bezier(.155, 1.105, .295, 1.12), .3s box-shadow, .3s -webkit-transform cubic-bezier(.155, 1.105, .295, 1.12);
  padding: 14px 80px 18px 36px;
  cursor: pointer;
}

.card:hover {
  box-shadow: 0 10px 20px rgba(0, 0, 0, .12), 0 4px 8px rgba(0, 0, 0, .06);
}

.hidden {
  visibility: hidden;
  transition: all 4s ease;
}

.card:hover>.hidden {
  visibility: visible;
  background: yellowgreen;
  border-radius: 10px;
  animation: slidein 3s ease-in-out
}

.card h3 {
  font-weight: 600;
}

.card img {
  position: absolute;
  top: 20px;
  right: 15px;
  max-height: 120px;
}

.card-1 {
  background-image: url(https://ionicframework.com/img/getting-started/ionic-native-card.png);
  background-repeat: no-repeat;
  background-position: right;
  background-size: 80px;
}

.card-2 {
  background-image: url(https://ionicframework.com/img/getting-started/components-card.png);
  background-repeat: no-repeat;
  background-position: right;
  background-size: 80px;
}

.card-3 {
  background-image: url(https://ionicframework.com/img/getting-started/theming-card.png);
  background-repeat: no-repeat;
  background-position: right;
  background-size: 80px;
}

.py-lg-5 {
  display: flex;
  flex-direction: column;
  text-align: justify;
}

.col-lg-6,
.col-md-8,
.mx-auto {
  width: 85%;
}

@keyframes slidein {
  0% {
    transform: scale(0) rotate(0deg);
  }

  100% {
    transform: scale(1) rotate(360deg);
    visibility: visible;
  }
}

@media(max-width: 990px) {
  .card {
    margin: 20px;
  }
}
</style>
