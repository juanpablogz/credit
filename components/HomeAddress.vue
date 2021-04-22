<template>
<!-- falta una pantalla OJO!!! -->
  <div class="container-information">
    <div class="titleInfo">Domicilio Particular</div>
    <div class="subtitleInfo">Domicilio dónde reside</div>
    <hr class="container-full-width" />
    <!-- País /estado -->
    <div class="container-flex">
      <div class="container-two-input" >
        <h6 class="title-input">País</h6>
        <v-combobox
          rounded
          v-model="model"
          :items="items"
          color="#B8DAF7"
          class="custom"
          auto-select-first
        ></v-combobox>
      </div>
      <div class="container-two-input" >
        <h6 class="title-input">Estado</h6>
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
<!-- minicipio/poblacion -->
    <div class="container-flex">
      <div class="container-two-input" >
        <h6 class="title-input">Municipio</h6>
        <v-combobox
          rounded
          v-model="model"
          :items="items"
          color="#B8DAF7"
          class="custom"
          auto-select-first
        ></v-combobox>
      </div>
      <div class="container-two-input" >
        <h6 class="title-input">Población</h6>
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
<!-- codigo postal/colonia -->
    <div class="container-flex">
      <div class="container-two-input">
        <h6 class="title-input">Código Postal</h6>
        <v-text-field solo flat dense height="54" class="custom"></v-text-field>
      </div>
      <div class="container-two-input" >
        <h6 class="title-input">Colonia</h6>
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
<!-- calle -->
    <div class="container-full-width">
      <h6 class="title-input">Calle</h6>
      <v-text-field solo flat dense height="54" class="custom"></v-text-field>
    </div>
<!-- num int num ext -->
    <div class="container-flex">
      <div class="container-two-input">
        <h6 class="title-input">Num Int</h6>
        <v-text-field solo flat dense height="54" class="custom"></v-text-field>
      </div>
      <div class="container-two-input">
        <h6 class="title-input">Num Ext</h6>
        <v-text-field solo flat dense height="54" class="custom"></v-text-field>
      </div>
    </div>
<!-- cruzamiento 01/ cruzamiento 02 -->
    <div class="container-flex">
      <div class="container-two-input">
        <h6 class="title-input">Cruzamiento 01</h6>
        <v-text-field solo flat dense height="54" class="custom"></v-text-field>
      </div>
      <div class="container-two-input">
        <h6 class="title-input">Cruzamiento 02</h6>
        <v-text-field solo flat dense height="54" class="custom"></v-text-field>
      </div>
    </div>
<!-- Arraigo en el domicilio -->
    <div class="container-full-width">
      <h6 class="title-input">Arraigo en el domicilio</h6>
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
      items: ["Gaming", "Programming", "Vue", "Vuetify"]
    };
	},
  computed: {
    ...mapState("genesys", ["steps"])
	},
	methods: {
    next() {
			let step = { "id": 4, "name": "Domicilio Anterior", "value": false }
      this.$store.commit("genesys/updateSteps", step);
		},
		back() {
			let step = { "id": 2, "name": "Domicilio Fiscal", "value": false }
      this.$store.commit("genesys/updateSteps", step);
		}
	}
};
</script>

<style lang="scss" scoped>
@import url(../assets/components/baseForm.scss);
</style>
