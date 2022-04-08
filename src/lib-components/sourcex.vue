<template>
  <source
    :src="src ? imageSrc : undefined"
    :srcset="srcset ? imageSrcset : undefined"
    :media="media || undefined"
    :sizes="sizes || undefined"
  />
</template>

<script lang="ts">
// @ts-nocheck
import Vue from "vue";
export default Vue.extend({
  name: "sourcex",
  props: {
    media: {
      type: String,
      required: false,
    },
    sizes: {
      type: String,
      required: false,
    },
    src: {
      type: String,
      required: false,
    },
    srcset: {
      type: String,
      required: false,
    },

    params: {
      type: String,
      required: false,
    },
  },

  computed: {
    imageSrc() {
      const config = this.$config;
      if (process.env.NODE_ENV === "development") {
        return this.src;
      } else {
        let url = `${config.IMGIX_BASE_URL}/${config.NUXT_SUBFOLDER}/${config.IMGIX_TARGET_BRANCH}${this.src}?v=${config.CACHE_TIME}&auto=format&auto=compress`;

        if (this.params) {
          url = url + "&" + this.params;
        }
        return url;
      }
    },

    imageSrcset() {
      const config = this.$config;
      if (process.env.NODE_ENV === "development") {
        return this.srcset;
      } else {
        let url = `${config.IMGIX_BASE_URL}/${config.NUXT_SUBFOLDER}/${config.IMGIX_TARGET_BRANCH}${this.srcset}?v=${config.CACHE_TIME}&auto=format&auto=compress`;

        if (this.params) {
          url = url + "&" + this.params;
        }
        return url;
      }
    },
  },
});
</script>