import { RouterLink, RouterView } from 'vue-router'

<script setup>

  import { ref } from 'vue'

  const msg = "Coucou les !"
  const portfolio = ref(null);

  let page = 1;

  let displayPage = ref(page);
  
  const nextPage = (way='') => {
    switch (way){
      case 'next':
        page++;
      break;
      case 'prev':
        page > 1 ? page-- : null;
      break;
    }
    displayPage.value = page;
    console.log(page);
    loadPic(page);
  }

  const loadPic = (page=1) => {
    fetch('http://127.0.0.1:8000/api/picture?page='+page+'1&limit=6')
    .then((res) => res.json())
    .then((json) => {
    portfolio.value = json;
    console.log(json);
    displayPage.value = page;
  })

  }

  (loadPic)()

</script>

<template>
  <h1>
    This is an new page {{msg}}
  </h1>
  <div class="container-fluid">
    <div class="row">
      <nav aria-label="Page navigation example">
        <ul class="pagination justify-content-center">
          <li v-bind:class="{'page-item':true, 'disabled': displayPage ==1 ? true : false}">
            <a class="page-link" @click="nextPage('prev')" href="#">Previous</a>
          </li>
          <li class="page-item"><a class="page-link" @click="loadPic(displayPage)" href="#">{{displayPage}}</a></li>
          <li class="page-item"><a class="page-link" @click="loadPic(displayPage+1)" href="#">{{displayPage+1}}</a></li>
          <li class="page-item"><a class="page-link" @click="loadPic(displayPage+2)" href="#">{{displayPage+2}}</a></li>
          <li class="page-item">
            <a class="page-link" @click="nextPage('next')" href="#">Next</a>
          </li>
        </ul>
      </nav>
    </div>
    <div class="row"> 
      <div v-for="pic in portfolio" class="col-12 col-md-4">
        <div class="card">
          <img class="card-img-top" :src="pic.url" alt="">
          <div class="card-body text-center">
            <h5>{{pic.author}} <br> {{pic.description}}</h5>
            <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
            <a href="#" class="btn btn-primary">Go somewhere</a>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="row">
    <nav aria-label="Page navigation example">
      <ul class="pagination justify-content-center">
        <li v-bind:class="{'page-item':true, 'disabled': displayPage ==1 ? true : false}">
          <a class="page-link" @click="nextPage('prev')" href="#">Previous</a>
        </li>
        <li class="page-item"><a class="page-link" @click="loadPic(displayPage)" href="#">{{displayPage}}</a></li>
        <li class="page-item"><a class="page-link" @click="loadPic(displayPage+1)" href="#">{{displayPage+1}}</a></li>
        <li class="page-item"><a class="page-link" @click="loadPic(displayPage+2)" href="#">{{displayPage+2}}</a></li>
        <li class="page-item">
          <a class="page-link" @click="nextPage('next')" href="#">Next</a>
        </li>
      </ul>
    </nav>
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
