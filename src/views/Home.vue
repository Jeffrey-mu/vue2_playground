<template>
  <div class="home">
    <ElementTable msg="Welcome to Your Vue.js + TypeScript App" />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import ElementTable from "@/components/ElementTable.vue"; // @ is an alias to /src

@Component({
  components: {
    ElementTable,
  },
})
export default class Home extends Vue {}
</script>
