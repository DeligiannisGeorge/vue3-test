<template>
  <ComponentA v-on="events" />
  <ComponentB v-if="isAMounted" />
</template>

<script>
import { defineAsyncComponent } from "vue";

const ComponentA = defineAsyncComponent(() => import("./components/ComponentA.vue"));
// import ComponentA from "./components/ComponentA.vue";
const ComponentB = defineAsyncComponent(() => import("./components/ComponentB.vue"));

export default {
  name: "App",
  components: {
    ComponentA,
    ComponentB,
  },
  data() {
    return {
      isAMounted: false,
    };
  },
  computed: {
    events() {
      return {
        vnodeMounted: this.onAMounted,
      };
    },
  },
  methods: {
    onAMounted() {
      this.isAMounted = true;
    },
  },
};
</script>
