<script>

export default {
  name: 'AppHeader',
  data() {
    return {
      menu: [
        {
          name: 'Home',
          route: 'home'
        },
        {
          name: 'About',
          route: 'about'
        },
        {
          name: 'Projects',
          route: 'projects'
        },
        {
          name: 'Contacts',
          route: 'contacts'
        }
      ]
    }
  }
}
</script>

<template>
  <header>
    <nav class="nav justify-content-center  ">
      <RouterLink :to="{ name: item.route }" class="nav-link" v-for="item in menu">
        {{ item.name }}
      </RouterLink>
    </nav>

  </header>
</template>

<style></style>
