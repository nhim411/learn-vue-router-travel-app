<template>
  <section class="experences">
    <h1 class="exp-title">Experiences</h1>
    <h2 class="exp-name">
      {{ experience.name }}
    </h2>
    <div class="exp-details">
      <img
        class="exp-img"
        :src="require(`@/assets/${experience.image}`)"
        :alt="experience.name"
      />
      <p class="exp-desc">{{ experience.description }}</p>
    </div>
  </section>
</template>

<script>
import store from "@/store.js";

export default {
  props: {
    slug: { type: String, required: true },
    experienceSlug: { type: String, required: true },
  },
  computed: {
    destination() {
      return store.destinations.find(
        (destination) => destination.slug === this.slug
      );
    },
    experience() {
      return this.destination.experiences.find(
        (experience) => experience.slug === this.experienceSlug
      );
    },
  },
};
</script>

<style scoped>
.exp-title {
  margin: 20px 0;
}
.exp-name {
  margin: 20px 0;
}
.exp-details {
  display: flex;
  justify-content: center;
  align-items: center;
}
.exp-img {
  margin-bottom: 20px;
}
.exp-desc {
  padding: 10px;
  text-align: justify;
}
</style>
