<script lang="ts">
import Vue from 'vue';
import TglComponents from '@/tgl-components.vue';

export default Vue.extend({
  name: 'ServeDev',
  components: {
    TglComponents
  }
});
</script>

<template>
  <div id="app">
    <tgl-components />
  </div>
</template>
