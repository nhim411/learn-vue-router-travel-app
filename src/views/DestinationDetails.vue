<template>
  <div>
    <GoBack />
    <section class="destination">
      <h1 class="destination-title">{{ destination.name }}</h1>
      <div class="destination-details">
        <img
          :src="require(`@/assets/${destination.image}`)"
          :alt="destination.name"
        />
        <p class="destination-desc">{{ destination.description }}</p>
      </div>
    </section>
    <section class="experiences">
      <h2 class="experiences-title">
        Top experiences in {{ destination.name }}
      </h2>
      <div class="cards" id="experience">
        <div
          class="card"
          v-for="experience in destination.experiences"
          :key="experience.slug"
        >
          <router-link
            :to="{
              name: 'experienceDetails',
              params: { experienceSlug: experience.slug },
              hash: '#experience',
            }"
          >
            <img
              :src="require(`@/assets/${experience.image}`)"
              :alt="experience.name"
            />
            <span class="card-text">{{ experience.name }}</span>
          </router-link>
        </div>
      </div>
      <transition name="fade">
        <router-view :key="$route.path" />
      </transition>
    </section>
  </div>
</template>

<script>
import store from "@/store.js";
import GoBack from "@/components/GoBack";
export default {
  name: "destination-details",
  props: {
    slug: {
      type: String,
      required: true,
    },
  },
  components: { GoBack },
  computed: {
    destination() {
      return store.destinations.find(
        (destination) => destination.slug === this.slug
      );
    },
  },
};
</script>

<style scoped>
.destination-details img {
  max-width: 600px;
  height: auto;
  width: 100%;
  max-height: 400px;
}

.destination-details {
  display: flex;
  justify-content: space-between;
  text-align: justify;
}

.destination-title {
  margin-bottom: 20px;
}

.destination-desc {
  padding-left: 30px;
  padding-right: 10px;
  margin: 0;
}

.cards {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.cards img {
  max-height: 200px;
  display: inline-block;
}

.card {
  position: relative;
  padding: 10px;
}

.card-text {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);

  color: white;
  text-shadow: 2px 2px #000;
  font-size: 25px;
  font-weight: bold;
}

.experiences-title {
  margin: 10px 0;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}
</style>
