<template>
  <span class="go-back">
    <button @click="goBack">Go Back</button>
    <button @click="goForward">Go Forward</button>
  </span>
</template>

<script>
export default {
  methods: {
    goBack() {
      this.$router.go(-1);
    },
    goForward() {
      this.$router.go(1);
    },
  },
};
</script>
<style>
.go-back {
  display: flex;
}
.go-back button {
  border: none;
}
</style>
