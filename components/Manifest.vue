<template>
<!-- falta funcionalidad para agregar mas informacion -->
  <div class="container-information">
    <div class="titleInfo">Manifestaciones del Declarante</div>
    <div class="subtitleInfo">
      Declaración sobre la participación del solicitante en alguna empresa
    </div>
    <hr class="container-full-width" />
    <p class="prf-info prf-custom">¿Desempeña o ha desempeñado funciones públicas destacadas en un país extranjero o en territorio nacional como son, entre otros, jefe de estado o de gobierno, líder político, funcionario gubernamental, judicial o militar de alta jerarquía, alto ejecutivo de empresa estatal o funcionario miembro importante de partidos políticos?</p>

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
      let step = { "id": 10, "name": "Beneficiarios", "value": false }
      this.$store.commit("genesys/updateSteps", step);
    },
    back() {
      let step = { "id": 8, "name": "Referencias Personales", "value": false }
      this.$store.commit("genesys/updateSteps", step);
    }
  }
};
</script>

<style lang="scss" scoped>
@import url(../assets/components/baseForm.scss);
.prf-custom {
  margin-top:15px;
  color: #000000;
}
</style>
