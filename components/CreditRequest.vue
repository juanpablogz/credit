<template>
<!-- falta funcionalidad para agregar otro credito -->
  <div class="container-information">
    <div class="titleInfo">Crédito Solicitado</div>
    <div class="subtitleInfo">
Crédito que necesita, monto y tipo de crédito. Puedes solicitar hasta 2 créditos
    </div>
    <hr class="container-full-width" />

    <div class="container-flex">
      <div class="container-two-input">
        <h6 class="title-input">Monto</h6>
        <v-text-field solo flat dense height="54" class="custom"></v-text-field>
      </div>
      <div class="container-two-input" >
        <h6 class="title-input">Tipo</h6>
        <v-combobox
          rounded
          v-model="model"
          :items="items"
          color="#B8DAF7"
          class="custom"
          auto-select-first
        ></v-combobox>
      </div>
    </div>

<!-- Nombre -->
    <div class="container-full-width">
      <h6 class="title-input">Destino</h6>
      <v-text-field solo flat dense height="54" class="custom"></v-text-field>
    </div>
<!-- Puesto -->
    <div class="container-full-width">
      <h6 class="title-input">Obligados solidarios</h6>
      <v-text-field solo flat dense height="54" class="custom"></v-text-field>
    </div>

      <div class="container-two-input">
        <h6 class="title-input">Garantía propuesta</h6>
      <v-text-field solo flat dense height="54" class="custom"></v-text-field>
      </div>
    <div class="align">
      <div class="button back mt-4" @click="back()">paso Anterior</div>
      <button class="button enable mt-4" @click="next()">Siguiente paso</button>
    </div>
  </div>
</template>

<script>
import { mapState } from "vuex";
export default {
  data() {
    return {
      model: "model",
      items: ["Gaming", "Programming", "Vue", "Vuetify"],
    };
  },
  computed: {
    ...mapState("genesys", ["steps"])
  },
  methods: {
    next() {
      let step = { "id": 7, "name": "Información Comercial/Bancaria", "value": false }
      this.$store.commit("genesys/updateSteps", step);
    },
    back() {
      let step = { "id": 5, "name": "Principales Accionistas", "value": false }
      this.$store.commit("genesys/updateSteps", step);
    }
  }
};
</script>

<style lang="scss" scoped>
@import url(../assets/components/baseForm.scss);
</style>
