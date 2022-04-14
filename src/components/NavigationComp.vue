<template>
  <nav id="nav">
    <div class="logo">
      <img :src="require(`@/assets/travel.png`)" alt="" />
    </div>
    <ul class="nav-links">
      <li class="link">
        <router-link :to="{ name: 'home' }">Home</router-link>
      </li>
      <li
        class="link"
        v-for="destination in destinations"
        :key="destination.id"
      >
        <router-link
          :to="{
            name: 'DestinationDetails',
            params: { slug: destination.slug },
          }"
        >
          {{ destination.name }}
        </router-link>
      </li>
      <li class="link">
        <router-link :to="{ name: 'user' }">User</router-link>
      </li>
      <li class="link">
        <router-link :to="{ name: 'login' }">Login</router-link>
      </li>
    </ul>
  </nav>
</template>

<script>
import store from "@/store.js";

export default {
  name: "nav-comp",
  data: function () {
    return { destinations: store.destinations };
  },
};
</script>

<style scoped>
#nav {
  display: flex;
  align-items: center;
  justify-content: center;
  position: sticky;
  top: 0;
  background-color: #fff;
  z-index: 9;
  border-bottom: 2px solid #ccc;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
  padding: 2px 0;
}
#nav .nav-links {
  display: flex;
  align-items: center;
  justify-content: center;

  list-style: none;
  text-decoration: none;
}

#nav a.router-link-exact-active {
  color: #ab26ab;
}

.link {
  padding-right: 20px;
  text-decoration: none;
}

.link a:hover {
  text-decoration: underline;
  color: rgb(15, 217, 15);
  transition: all 0.2s ease;
}

.link a {
  text-decoration: none;
}

.logo {
  margin-right: auto;
}

.logo img {
  max-height: 58px;
}
</style>
