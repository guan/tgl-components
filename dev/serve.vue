<script lang="ts">
import Vue from 'vue';
// Uncomment import and local "components" registration if library is not registered globally.
// import { TglComponentsSample } from '@/entry.esm';

export default Vue.extend({
  name: 'ServeDev',
  // components: {
  //  TglComponentsSample,
  // }
});
</script>

<template>
  <div id="app">
    <tgl-components-sample />
  </div>
</template>
