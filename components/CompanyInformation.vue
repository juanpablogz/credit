<template>
  <div class="container-information">
    <div class="titleInfo">Información de la empresa</div>
    <div class="subtitleInfo">Conocer al negocio del solicitante</div>
    <hr class="container-full-width" />
    {{ razonSocial }}
    <!-- razon social -->
    <div class="container-full-width">
      <h6 class="title-input">Razón social</h6>
      <v-text-field
        solo
        flat
        dense
        height="54"
        class="custom"
        v-model="razonSocial"
      ></v-text-field>
    </div>
    <!-- representante legal -->
    <div class="container-full-width">
      <h6 class="title-input">Representante legal</h6>
      <v-text-field
        solo
        flat
        dense
        height="54"
        class="custom"
        v-model="representanteLegal"
      ></v-text-field>
    </div>

    <!-- fecha de constitucion y edad de la empresa -->
    <div class="container-flex">
      <div class="container-two-input">
        <h6 class="title-input">Fecha de constitución</h6>
        <v-text-field
          solo
          flat
          dense
          height="54"
          class="custom"
          v-model="fechaConstitucion"
        ></v-text-field>
      </div>
      <div class="container-two-input">
        <h6 class="title-input">Edad de la empresa</h6>
        <v-text-field
          solo
          flat
          dense
          height="54"
          class="custom"
          v-model="edadEmpresa"
        ></v-text-field>
      </div>
    </div>
    <!-- RFC and RFC con homoclave -->
    <div class="container-flex">
      <div class="container-two-input">
        <h6 class="title-input">RFC</h6>
        <v-text-field
          solo
          flat
          dense
          height="54"
          class="custom"
          v-model="rfc"
        ></v-text-field>
      </div>
      <div class="container-two-input">
        <h6 class="title-input">RFC con Homoclave</h6>
        <v-text-field
          solo
          flat
          dense
          height="54"
          class="custom"
          v-model="rfcHomoClave"
        ></v-text-field>
      </div>
    </div>
    <!-- No. de serie Fiel and entidad federativa de nacimiento -->
    <div class="container-flex">
      <div class="container-two-input">
        <h6 class="title-input">No. de serie Fiel</h6>
        <v-text-field
          solo
          flat
          dense
          height="54"
          class="custom"
          v-model="NoSerieFiel"
        ></v-text-field>
      </div>
      <div class="container-two-input">
        <h6 class="title-input">Entidad Federativa de Nacimiento</h6>
        <v-text-field
          solo
          flat
          dense
          height="54"
          class="custom"
          v-model="entidadFederativaDeNacimiento"
        ></v-text-field>
      </div>
    </div>
    <!-- pais de constitución y entidad federativa de nacimiento -->
    <div class="container-flex">
      <div class="container-two-input">
        <h6 class="title-input">País de constitución</h6>
        <v-text-field
          solo
          flat
          dense
          height="54"
          class="custom"
          v-model="paisConstitucion"
        ></v-text-field>
      </div>
      <div class="container-two-input">
        <h6 class="title-input">Nacionalidad</h6>
        <v-text-field
          solo
          flat
          dense
          height="54"
          class="custom"
          v-model="Nacionalidad"
        ></v-text-field>
      </div>
    </div>

    <div class="container-two-input">
      <h6 class="title-input">Giro Mercantil/Actividad</h6>
      <v-combobox
        rounded
        v-model="giroMercantil"
        :items="items"
        color="#B8DAF7"
        class="custom"
        auto-select-first
      ></v-combobox>
    </div>

    <div class="titleInfo mt-7">Contacto</div>
    <div class="subtitleInfo">Datos de quien llena la solicitud</div>
    <hr class="container-full-width" />
    <!-- nombre completo -->
    <div class="container-full-width mt-7">
      <h6 class="title-input">Nombre Completo</h6>
      <v-text-field
        solo
        flat
        dense
        height="54"
        class="custom"
        v-model="nombreCompleto"
      ></v-text-field>
    </div>
    <!-- correo/numero -->
    <div class="container-flex">
      <div class="container-two-input">
        <h6 class="title-input">Correo Electrónico</h6>
        <v-text-field
          solo
          flat
          dense
          height="54"
          class="custom"
          v-model="correo"
        ></v-text-field>
      </div>
      <div class="container-two-input">
        <h6 class="title-input">Número Móvil</h6>
        <v-text-field
          solo
          flat
          dense
          height="54"
          class="custom"
          v-model="numeroMovil"
        ></v-text-field>
      </div>
    </div>
    <div class="container-two-input">
      <h6 class="title-input">Número Fijo (Trabajo,casa,etc)</h6>
      <v-text-field
        solo
        flat
        dense
        height="54"
        class="custom"
        v-model="numeroFijo"
      ></v-text-field>
    </div>
    <div class="align">
      <button class="button enable mt-4" @click="next()">Siguiente paso</button>
    </div>
  </div>
</template>

<script>
import { mapState } from "vuex";
export default {
  data() {
    return {
      items: [
        "industrial",
        "Extractiva",
        "Manufacturera",
        "Comercial",
        "servicios"
      ],
      razonSocial: "",
      representanteLegal: "",
      fechaConstitucion: "",
      edadEmpresa: "",
      rfc: "",
      rfcHomoClave: "",
      NoSerieFiel: "",
      entidadFederativaDeNacimiento: "",
      paisConstitucion: "",
      Nacionalidad: "",
      giroMercantil: "",

      nombreCompleto: "",
      correo: "",
      numeroMovil: "",
      numeroFijo: ""
    };
  },
  computed: {
    ...mapState("genesys", ["steps"])
  },
  methods: {
    next() {
      let step = { id: 2, name: "Domicilio Fiscal", value: false };
      this.$store.commit("genesys/updateSteps", step);
      let companyInfo = [
        { razonSocial: this.razonSocial },
        { representanteLegal: this.representanteLegal },
        { fechaConstitucion: this.fechaConstitucion },
        { edadEmpresa: this.edadEmpresa },
        { rfc: this.rfc },
        { rfcHomoClave: this.rfcHomoClave },
        { NoSerieFiel: this.NoSerieFiel },
        { entidadFederativaDeNacimiento: this.entidadFederativaDeNacimiento },
        { paisConstitucion: this.paisConstitucion },
        { Nacionalidad: this.Nacionalidad },
        { giroMercantil: this.giroMercantil }
      ];
      console.log(companyInfo)
    }
  }
};
</script>

<style lang="scss" scoped>
@import url(../assets/components/baseForm.scss);
</style>
