<template>
<!-- falta funcionalidad para agregar mas informacion -->
  <div class="container-information">
    <div class="titleInfo">Referencias Personales</div>
    <div class="subtitleInfo">
      Información sobre su moralidad
    </div>
    <hr class="container-full-width" />
    <p class="prf-info prf-custom">Referencias Personales NO Familiares</p>
<!-- Nombre -->
    <div class="container-full-width">
      <h6 class="title-input">Nombre</h6>
      <v-text-field solo flat dense height="54" class="custom"></v-text-field>
    </div>
<!-- domicilio -->
    <div class="container-full-width">
      <h6 class="title-input">Domicilio</h6>
      <v-text-field solo flat dense height="54" class="custom"></v-text-field>
    </div>
<!-- telefono -->
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
      <h6 class="title-input">Tiempo de conocerlo</h6>
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
      let step = { "id": 9, "name": "Manifestaciones del declarante", "value": false }
      this.$store.commit("genesys/updateSteps", step);
    },
    back() {
      let step = { "id": 7, "name": "Información Comercial/Bancaria", "value": false }
      this.$store.commit("genesys/updateSteps", step);
    }
  }
};
</script>

<style lang="scss" scoped>
@import url(../assets/components/baseForm.scss);
.prf-custom {
  font-weight: bold;
  margin-top:15px;
}
</style>
