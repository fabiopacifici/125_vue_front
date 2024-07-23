<script>
import axios from 'axios'
export default {
  name: 'AppContacts',
  data() {
    return {
      name: '',
      email: '',
      message: '',
      errors: {},
      loading: false,
      success: false
    }
  },

  methods: {
    sendMessage() {

      // prepare the request payload 
      const data = {
        'name': this.name,
        'email': this.email,
        'message': this.message,

      }
      console.log(data);

      // sent the ajax post request

      axios
        .post('http://127.0.0.1:8000/api/lead', data)
        .then(response => {
          console.log(response);

          if (response.data.success) {
            // show a success message
            this.success = true;
            this.errors = null;

            this.name = '';
            this.email = '';
            this.message = '';

          } else {
            // there are valdation errors
            this.success = false;
            this.errors = response.data.errors
          }

        })


      // handle the response accordingly

    }
  }
}
</script>


<template>
  <div>



    <div class="p-5 mb-4 bg-light">
      <div class="container py-5">
        <h1 class="display-5 fw-bold">Contact me</h1>
        <p class="col-md-8 fs-4">
          Using a series of utilities, you can create this jumbotron, just
          like the one in previous versions of Bootstrap. Check out the
          examples below for how you can remix and restyle it to your liking.
        </p>

      </div>
    </div>


    <div class="container">


      <template v-if="success">
        <div class="alert alert-success" role="alert">
          <strong>Message received</strong> We will get back to you asap
        </div>

      </template>

      <form @submit.prevent="sendMessage()">

        <div class="mb-3">
          <label for="name" class="form-label">Name</label>
          <input type="text" class="form-control" :class="{ 'is-invalid': errors.name }" name="name" id="name"
            aria-describedby="nameHelper" placeholder="Luke skywalker" v-model="name" />
          <small id="nameHelper" class="form-text text-muted">Type your full name</small>
          <p class="text-danger" v-for="(error, index) in errors.name" :key="`name-error-${index}`">
            {{ error }}
          </p>
        </div>

        <div class="mb-3">
          <label for="email" class="form-label">Email</label>
          <input type="text" class="form-control" :class="{ 'is-invalid': errors.email }" name="email" id="email"
            aria-describedby="emailHelp" placeholder="abc@mail.com" v-model="email" />

          <p class="text-danger" v-for="(error, index) in errors.email" :key="`email-error-${index}`">

            {{ error }}

          </p>


          <small id="emailHelp" class="form-text text-muted">Type your email</small>
        </div>

        <div class="mb-3">
          <label for="message" class="form-label">Message</label>
          <textarea class="form-control" :class="{ 'is-invalid': errors.message }" name="message" id="message" rows="3"
            v-model="message"></textarea>
          <p class="text-danger" v-for="(error, index) in errors.message" :key="`message-error-${index}`">

            {{ error }}

          </p>
        </div>


        <button type="submit" class="btn btn-dark">
          Submit
        </button>


      </form>


    </div>



  </div>
</template>


<style scoped></style>