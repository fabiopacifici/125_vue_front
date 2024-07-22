<script>
import axios from 'axios';
export default {
  name: 'AppHome',
  data() {
    return {
      base_url: 'http://127.0.0.1:8000',
      latest_endpoint: '/api/projects/latest',
      projects: ''
    }
  },

  mounted() {
    axios
      .get(`${this.base_url}${this.latest_endpoint}`)
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
        <h1 class="display-5 fw-bold">Welcome</h1>
        <p class="col-md-8 fs-4">
          Using a series of utilities, you can create this jumbotron, just
          like the one in previous versions of Bootstrap. Check out the
          examples below for how you can remix and restyle it to your liking.
        </p>
        <button class="btn btn-primary btn-lg" type="button">
          Example button
        </button>
      </div>
    </div>


    <section id="in_evidence">
      <div class="container">
        <h3 class="text-muted">In evidence</h3>
        <div class="row row-cols-1 row-cols-md-2 row-cols-lg-3 g-3">
          <div class="col" v-for="project in projects">
            <div class="card h-100">
              <template v-if="!project.cover_image.startsWith('http')">
                <img class="card-img-top" :src="base_url + '/storage/' + project.cover_image" alt="" loading="lazy">
              </template>
              <template v-else>
                <img class="card-img-top" :src="project.cover_image" alt="" loading="lazy">
              </template>
              <div class="card-body">
                {{ project.name }}
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

  </div>
</template>


<style scoped></style>