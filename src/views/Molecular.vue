<script setup lang="ts">
import Nav from "../components/Nav.vue";
import MolecularInput from "../components/Molecular/MolecularInput.vue";
import Render from "../components/Molecular/Render.vue";
import List from "../components/Molecular/List.vue";
import ElementAmounts from "../components/Molecular/ElementAmounts.vue";
import MolarMass from "../components/Molecular/MolarMass.vue";
import ElementMakeup from "../components/Molecular/ElementMakeup.vue";
</script>

<template>
  <main>
    <Nav />
    <div class="p-0 flex gap-8 flex-wrap md:p-8">
      <div class="flex-grow min-30">
        <MolecularInput @input-enter="updateRenderComponent" />
        <Render :inputData="renderInputData" />
        <ElementMakeup :inputData="renderInputData" />
        <MolarMass :inputData="renderInputData" />
        <ElementAmounts :inputData="renderInputData" />
      </div>
      <List :inputData="renderInputData" />
    </div>
  </main>
</template>

<script lang="ts">
export default {
  components: {
    MolecularInput,
    Render,
    List,
    ElementAmounts,
    MolarMass,
    ElementMakeup,
  },
  data() {
    return {
      renderInputData: "",
    };
  },
  methods: {
    updateRenderComponent(data: string) {
      this.renderInputData = data;
    },
  },
};
</script>
<style scoped>
@media screen and (min-width: 1000px) {
  .min-30 {
    min-width: 30rem;
  }
}
@media screen and (max-width: 1000px) {
  .min-30 {
    max-width: 100%;
  }
}
</style>
