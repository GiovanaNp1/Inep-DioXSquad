<template>
  <div>
    <div class="navbar">
      <Burger></Burger>
      <a class="logo" href="#home">E-MEC</a>
      <p></p>
    </div>
    <Sidebar>
      <Burger></Burger>
      <ul  class="sidebar-panel-nav">
        <li id="burger" :class="{ 'active' : isBurgerActive }" @click.prevent="toggle" v-for="(link, index) in links" :key="index">
          <router-link :to="link.to">{{ link.name }}</router-link>
        </li>
      </ul>
    </Sidebar>
    <main>
      <router-view/>
    </main>
  </div>
</template>

<style scoped>
  ul {
    list-style: none;
    padding: 0;
  }
  li {
    padding: 5px 15px 5px 0;
  }
  .logo {
    align-self: center;
    justify-content: center;
    padding-right: 25px;
  }
  a {
    text-decoration: none;
    font-family: 'Hammersmith One', sans-serif;
    color: #46599C;
  }
  li a {
    text-decoration: none;
    font-family: 'Hammersmith One', sans-serif;
    color: #46599C;
  }
  li a:hover {
    color: #404040;
  }
  .navbar{
    border: 25px;
    color: #46599C;
    padding-top: 10px;
    display: flex;
    background-color: white;
    justify-content: space-between;
  }
  .main-nav {
  display: flex;
  justify-content: space-between;
  padding: 0.5rem 0.8rem;
}
ul.sidebar-panel-nav {
  list-style-type: none;
}
ul.sidebar-panel-nav > li > a {
  color: #fff;
  text-decoration: none;
  font-size: 1.5rem;
  display: block;
  padding-bottom: 0.5em;
}
</style>

<script>
import Burger from "./components/Burger";
import Sidebar from "./components/Sidebar.vue";
import { store, mutations } from "@/store.js";

export default {
  components: {
    Burger,
    Sidebar
  },
  data: () => ({
    links: [
      {
        name: 'Home',
        to: '/'
      },
      {
        name: 'Page 1',
        to: '/page-1'
      },
      {
        name: 'Bad Link',
        to: '/random-bad-url'
      }
    ]
  }),
   methods: {
    toggle() {
      mutations.toggleNav();
    }
  }
}
</script>