<script>
import axios from 'axios';

export default {
  name: 'ProjectsList',
  data() {
    return {
      base_url: 'http://127.0.0.1:8000',
      projects: ''
    }
  },

  mounted() {
    axios
      .get(`${this.base_url}/api/projects`)
      .then(response => {
        console.log(response);
        this.projects = response.data.projects

      })


  }
}
</script>


<template>
  <div>


    <div class="p-5 mb-4 bg-light">
      <div class="container py-5">
        <h1 class="display-5 fw-bold">My works</h1>
        <p class="col-md-8 fs-4">
          Using a series of utilities, you can create this jumbotron, just
          like the one in previous versions of Bootstrap. Check out the
          examples below for how you can remix and restyle it to your liking.
        </p>

      </div>
    </div>


    <div class="container">
      <div class="row row-cols-1 row-cols-md-2 row-cols-lg-3 g-3">
        <div class="col" v-for="project in projects.data">
          <div class="card h-100">
            <div v-if="project.cover_image">
              <template v-if="!project.cover_image.startsWith('http')">
                <img class="card-img-top" :src="base_url + '/storage/' + project.cover_image" alt="" loading="lazy">
              </template>
              <template v-else>
                <img class="card-img-top" :src="project.cover_image" alt="" loading="lazy">
              </template>
              <div class="card-body">
                {{ project.name }}
                <router-link :to="{name: 'project', params: {slug: project.slug }}">read more</router-link>
              </div>
            </div>
          </div>
        </div>
      </div>


      <nav aria-label="Page navigation">
        <ul class="pagination    ">
          <li class="page-item disabled">
            <a class="page-link" href="#" aria-label="Previous">
              <span aria-hidden="true">&laquo;</span>
            </a>
          </li>
          <li class="page-item active" aria-current="page">
            <a class="page-link" href="#">1</a>
          </li>
          <li class="page-item"><a class="page-link" href="#">2</a></li>
          <li class="page-item">
            <a class="page-link" href="#">3</a>
          </li>
          <li class="page-item">
            <a class="page-link" href="#" aria-label="Next">
              <span aria-hidden="true">&raquo;</span>
            </a>
          </li>
        </ul>
      </nav>



    </div>


  </div>
</template>


<style scoped></style>