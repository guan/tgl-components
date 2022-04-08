<template>
  <img
    :src="image"
    :alt="alt || undefined"
    :width="width || undefined"
    :height="height || undefined"
  />
</template>

<script lang="ts">
import Vue from "vue";
export default Vue.extend({
  name: "imgix",
  props: {
    src: {
      type: String,
      required: true,
    },
    alt: {
      type: String,
      required: false,
    },

    width: {
      type: String,
      required: false,
    },

    height: {
      type: String,
      required: false,
    },

    params: {
      type: String,
      required: false,
    },
  },

  computed: {
    image() {
      if (process.env.NODE_ENV === "development") {
        return this.src;
      } else {
        let url = `${this.$config.IMGIX_BASE_URL}/${this.$config.NUXT_SUBFOLDER}/${this.$config.IMGIX_TARGET_BRANCH}${this.src}?v=${this.$config.CACHE_TIME}&auto=format&auto=compress`;

        if (this.params) {
          url = url + "&" + this.params;
        }
        return url;
      }
    },
  },
});
</script>