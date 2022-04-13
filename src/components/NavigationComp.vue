<template>
  <nav id="nav">
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
</style>
