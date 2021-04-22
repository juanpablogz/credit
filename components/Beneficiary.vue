<template>
<!-- falta funcionalidad para agregar mas informacion -->
  <div class="container-information">
    <div class="titleInfo">Beneficiarios</div>
    <div class="subtitleInfo">
      Persona que podrá solicitar sus bienes en caso de ausencia, máximo 3
    </div>
    <hr class="container-full-width" />
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
<!--Fecha de nacimiento / parentesco -->
    <div class="container-flex">
      <div class="container-two-input" >
      <h6 class="title-input">Fecha de nacimiento</h6>
      <v-text-field solo flat dense height="54" class="custom"></v-text-field>
      </div>
      <div class="container-two-input" >
      <h6 class="title-input">Parentesco</h6>
      <v-text-field solo flat dense height="54" class="custom"></v-text-field>
      </div>
    </div>
<!-- porcentaje -->
      <div class="container-two-input" >
      <h6 class="title-input">Porcentaje</h6>
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
      let step = { "id": 11, "name": "Información importante", "value": false }
      this.$store.commit("genesys/updateSteps", step);
    },
    back() {
      let step = { "id": 9, "name": "Manifestaciones del declarante", "value": false }
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
