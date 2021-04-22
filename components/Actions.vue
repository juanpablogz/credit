<template>
<!-- falta funcionalidad para agregar accionistas -->
  <div class="container-information">
    <div class="titleInfo">Principales Accionistas</div>
    <div class="subtitleInfo">
      Socios con mayor participación o más acciones en la empresa
    </div>
    <hr class="container-full-width" />
    <div v-for="information in info" :key="information.id">
      <p class="prf-info">{{ information }}</p>
    </div>
<!-- Nombre -->
    <div class="container-full-width">
      <h6 class="title-input">Nombre</h6>
      <v-text-field solo flat dense height="54" class="custom"></v-text-field>
    </div>
<!-- Puesto -->
    <div class="container-full-width">
      <h6 class="title-input">Puesto</h6>
      <v-text-field solo flat dense height="54" class="custom"></v-text-field>
    </div>

    <div class="container-flex">
      <div class="container-two-input">
        <h6 class="title-input">Antigüedad en el puesto</h6>
        <v-text-field solo flat dense height="54" class="custom"></v-text-field>
      </div>
      <div class="container-two-input" >
        <h6 class="title-input">Nivel Educativo</h6>
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
      info: [
        "De conformidad a las Disposiciones declaro como representante legal de la Persona Moral, que los siguientes nombres corresponden a las personas físicas que ejercen el control:.",
        "I. 25% de participación accionaria.",
        "II. Poder para nombrar o destituir a miembros  del consejo de administración.",
        "II. Poder para nombrar o destituir a miembros  del consejo de administración.",
        "III. Posibilidad de ejercer funciones de mando sobre personas que tienen a su cargo  la toma de decisiones o la administración. ",
        "IV. Posibilidad de imponer decisiones en las asambleas generales de accionistas"
      ]
    };
  },
  computed: {
    ...mapState("genesys", ["steps"])
  },
  methods: {
    next() {
      let step = { "id": 6, "name": "Crédito Soclitado", "value": false }
      this.$store.commit("genesys/updateSteps", step);
    },
    back() {
      let step = { "id": 4, "name": "Domicilio Anterior", "value": false }
      this.$store.commit("genesys/updateSteps", step);
    }
  }
};
</script>

<style lang="scss" scoped>
@import url(../assets/components/baseForm.scss);
</style>
