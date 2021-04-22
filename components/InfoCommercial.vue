<template>
<!-- falta funcionalidad para agregar mas informacion -->
  <div class="container-information">
    <div class="titleInfo">Información comercial y/o bancaria</div>
    <div class="subtitleInfo">
      Información comercial y/o del negocio, como moralidad crediticia.
    </div>
    <hr class="container-full-width" />

<!-- compañia o banco -->
    <div class="container-full-width">
      <h6 class="title-input">Compañia o banco</h6>
      <v-text-field solo flat dense height="54" class="custom"></v-text-field>
    </div>
      <div class="container-two-input" >
      <h6 class="title-input">Teléfono</h6>
      <v-text-field solo flat dense height="54" class="custom"></v-text-field>
      </div>
    <!-- Relación / tiempo de conocerlo -->
    <div class="container-flex">
      <div class="container-two-input" >
      <h6 class="title-input">Relación</h6>
      <v-text-field solo flat dense height="54" class="custom"></v-text-field>
      </div>
      <div class="container-two-input" >
      <h6 class="title-input">Persona a contactar</h6>
      <v-text-field solo flat dense height="54" class="custom"></v-text-field>
      </div>
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
      let step = { "id": 8, "name": "Referencias Personales", "value": false }
      this.$store.commit("genesys/updateSteps", step);
    },
    back() {
      let step = { "id": 6, "name": "Crédito Soclitado", "value": false }
      this.$store.commit("genesys/updateSteps", step);
    }
  }
};
</script>

<style lang="scss" scoped>
@import url(../assets/components/baseForm.scss);
</style>
