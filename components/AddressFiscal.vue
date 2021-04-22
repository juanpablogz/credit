<template>
  <div class="container-information">
    <div class="titleInfo">Domicilio Fiscal</div>
    <div class="subtitleInfo">
      Domicilio registrado en la constancia de situación fiscal ante el SAT
    </div>
    <hr class="container-full-width" />
    <!-- País /estado -->
    <div class="container-flex">
      <div class="container-two-input">
        <h6 class="title-input">País</h6>
        <v-combobox
          rounded
          v-model="mexico"
          :items="countries"
          color="#B8DAF7"
          class="custom"
          auto-select-first
        ></v-combobox>
      </div>
      <div class="container-two-input">
        <h6 class="title-input">Estado</h6>
        <v-combobox
          rounded
          @click="municipality()"
          v-model="estado"
          :items="listState"
          color="#B8DAF7"
          class="custom"
          auto-select-first
        ></v-combobox>
      </div>
    </div>
    <!-- municipio/poblacion -->
    <div class="container-flex">
      <div class="container-two-input">
        <h6 class="title-input">Municipio</h6>
        <v-combobox
          rounded
          v-model="municipio"
          :items="municipios"
          color="#B8DAF7"
          class="custom"
          auto-select-first
        ></v-combobox>
      </div>
      <div class="container-two-input">
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
      <div class="container-two-input">
        <h6 class="title-input">Colonia</h6>
        <v-combobox
          rounded
          @click="colonia()"
          v-model="model"
          :items="colonias"
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
      mexico: "México",
      countries: ["México", "colombia"],
      items: ["x"],
      municipio: "",
      listState: [],
      listMunicipality: [],
      estado: "Ciudad de México",
      municipios: [],
      colonias: [],
      model: '',
    };
  },
  computed: {
    ...mapState("genesys", ["steps"]),
  },
  mounted() {
    this.state();
    this.municipality;
  },
  methods: {
    next() {
      let step = { id: 3, name: "Domicilio Particular", value: false };
      this.$store.commit("genesys/updateSteps", step);
    },
    back() {
      let step = { id: 1, name: "Información de la empresa", value: false };
      this.$store.commit("genesys/updateSteps", step);
    },
    async state() {
      const state = await this.$axios.$get(
        "https://api-sepomex.hckdrk.mx/query/get_estados?token=91ca559a-62d5-4e9f-ba78-0bbc3e641104"
      );
      this.listState = state.response.estado;
    },
    async colonia() {
      try {
        const response = await this.$axios.$get(
          `https://api-sepomex.hckdrk.mx/query/get_colonia_por_municipio/${this.municipio}?token=91ca559a-62d5-4e9f-ba78-0bbc3e641104`
        );
        this.colonias = response.response.colonia
        console.log(response)
        return await response;
      } catch (error) {
        throw error;
      }
    },
    async municipality() {
      try {
        const response = await this.$axios.$get(
          `https://api-sepomex.hckdrk.mx/query/get_municipio_por_estado/${this.estado}?token=91ca559a-62d5-4e9f-ba78-0bbc3e641104`
        );
        this.municipios = response.response.municipios
        console.log(response)
        return await response;
      } catch (error) {
        throw error;
      }
    }
  }
};
</script>

<style lang="scss" scoped>
@import url(../assets/components/baseForm.scss);
</style>
