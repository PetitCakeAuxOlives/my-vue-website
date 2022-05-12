import { RouterLink, RouterView } from 'vue-router'

<script setup>

  import { ref } from 'vue'

  const msg = "Coucou les !"
  const portfolio = ref(null);
  fetch('http://127.0.0.1:8000/api/picture?page=1&limit=6')
  .then((res) => res.json())
  .then((json) => {
    portfolio.value = json
    console.log(json);
  })

</script>

<template>
  <h1>
    This is an new page {{msg}}
  </h1>
  <div class="container-fluid">
    <div class="row">
    </div>
    <div class="row"> 
      <div v-for="pic in portfolio" class="col-12 col-md-4">
        <div class="card">
          <img class="card-img-top" :src="pic.url" alt="">
          <div class="card-body text-center">
            <h5>{{pic.author}} {{pic.description}}</h5>
            <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
            <a href="#" class="btn btn-primary">Go somewhere</a>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="about">
    <h1>This is an Portfolio page</h1>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
