<template>
  <div class="user">
    <h2 class="user-title">Hello, {{ user }}</h2>
    <button class="btn-logout" @click="logOut">Logout</button>
  </div>
</template>

<script>
import store from "@/store.js";
export default {
  methods: {
    logOut() {
      store.user = null;
      this.$router.push({ name: "home" });
    },
  },
  data() {
    return {
      user: store.user,
    };
  },
};
</script>

<style lang="scss" scoped>
.user-title {
  margin-top: 50px;
}

.btn-logout {
  margin: 10px 0;
  padding: 8px 16px;
  cursor: pointer;
  transition: all 0.3s;
  &:hover {
    background-color: rgb(82, 82, 169);
    color: white;
  }
}
</style>
