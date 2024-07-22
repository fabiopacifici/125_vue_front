<script>
export default {
  name: 'AppContacts'
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


      <form>

        <div class="mb-3">
          <label for="name" class="form-label">Name</label>
          <input type="text" class="form-control" name="name" id="name" aria-describedby="nameHelper"
            placeholder="Luke skywalker" />
          <small id="nameHelper" class="form-text text-muted">Type your full name</small>
        </div>

        <div class="mb-3">
          <label for="email" class="form-label">Email</label>
          <input type="email" class="form-control" name="email" id="email" aria-describedby="emailHelp"
            placeholder="abc@mail.com" />
          <small id="emailHelp" class="form-text text-muted">Type your email</small>
        </div>

        <div class="mb-3">
          <label for="message" class="form-label">Message</label>
          <textarea class="form-control" name="message" id="message" rows="3"></textarea>
        </div>


        <button type="submit" class="btn btn-dark">
          Submit
        </button>


      </form>


    </div>



  </div>
</template>


<style scoped></style>