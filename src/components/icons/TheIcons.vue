<template>
  <component :is="getIcon"></component>
</template>
<script>
const getName = (name) => `icon-${name}`;
export default {
  name: "Icon",
  props: {
    icon: {
      type: String,
    },
  },
  components: {
    [getName("merge")]: () => import("../icons/IconMerge.vue"),
  },
  computed: {
    getIcon() {
      return getName(this.icon);
    },
  },
};
</script>