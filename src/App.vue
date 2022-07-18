<script setup>
// import { RouterLink, RouterView } from 'vue-router'
// import HelloWorld from './components/HelloWorld.vue'
</script>



<template>
  <div>
    <div id="listUser">
      <h1>List User</h1>
      <div class="list" v-for="user in users" :key="users.id">Nama User: {{ user.name}}</div>
    </div>

    <br><br><hr><br><br>

    <div id="listPhoto">
      <h1>List Photo</h1>
      <div 
        class="list" 
        v-for="photo in listPhoto" 
        :key="listPhoto.id">
        Photo: <img :src='photo.thumbnailUrl' /> {{ photo.thumbnailUrl }}
      </div>
    </div>
  </div>

  
</template>

<script>

import axios from 'axios'
export default {
  name: 'listUser',
  data () {
    return {
      users: '',
      listPhoto: ''
    }
  },
  mounted() {
    axios.get('https://jsonplaceholder.typicode.com/users')
    .then((response) => {
      this.users = response.data
    })

    axios.get('https://jsonplaceholder.typicode.com/albums/1/photos')
    .then((response) => {
      this.listPhoto = response.data
    })
  }
}
</script>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
