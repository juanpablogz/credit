<template>
  <!-- falta funcionalidad para agregar mas informacion -->
  <div class="container-information">
    <div class="titleInfo">Información Importante</div>
    <hr class="container-full-width" />
    <p class="prf-info prf-custom">
      El (los) que suscribe (n) manifiesto (manifestamos) que las copias de los
      documentos presentados para procesar la solicitud de crédito adjunta,
      concuerdan fielmente con los originales que he (hemos) tenido a la vista,
      los cuales no presentan a mi (nuestro) leal saber y entender alteraciones
      evidentes de los mismos.
    </p>
    <p class="prf-info prf-custom">
      Asimismo, manifiesto (manifestamos) que he (hemos) verificado la identidad
      del solicitante, Obligado Solidario y demás personas que firman la
      presente solicitud de crédito. “Igualmente declaro, que toda la
      información contenida en la presente Solicitud de Crédito es VERÍDICA, y
      que mi actividad económica es totalmente LÍCITA
    </p>
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
      let step = { "id": 12, "name": "Confirmación", "value": false }
      this.$store.commit("genesys/updateSteps", step);
    },
    back() {
      let step = { "id": 10, "name": "Beneficiarios", "value": false }
      this.$store.commit("genesys/updateSteps", step);
    }
  }
};
</script>

<style lang="scss" scoped>
@import url(../assets/components/baseForm.scss);
.prf-custom {
  margin-top: 15px;
  color: #000000;
}
</style>
