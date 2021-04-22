<template>
  <v-app>
    <!-- {{steps}} -->
    <v-row no-gutters>
      <v-col cols="12" lg="4" sm="12" xs="12" class="color">
        <div class="logo">
          <img
            class="image"
            src="https://res.cloudinary.com/dutj1bbos/image/upload/v1618865725/Group_23_2_ee7cvn.png"
            alt=""
          />
        </div>
      </v-col>
      <v-col cols="12" lg="8" md="12" sm="12" xs="12">
        <v-container class="container">
          <h1 class="title">
            Bienvenido(a) a tu Solicitud de Crédito para sector agroindustrial
            para personas morales
          </h1>
          <h5 class="subtitle">Consideraciones al llenar el formulario:</h5>
          <p class="process">
            Te pedimos tener contigo la siguiente información, antes de comenzar
            el proceso:
          </p>

          <div v-for="(item, index) in label " :key="item.id">
            <v-checkbox
              color="success"
              style="margin: 0px"
              class="label"
              v-model="checkbox[index].value"
              :label="`${item}`"
            ></v-checkbox>
          </div>
          <div class="align">
            <nuxt-link to="/form" v-if="checkValidate" class="button mt-4" style="color: white">Siguiente paso</nuxt-link>
            <button class="button enable mt-4" v-else>Siguiente paso</button>
          </div>
        </v-container>
      </v-col>
    </v-row>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      checkbox: [
        {name: 'identity', value: false},
        {name: 'rfc', value: false},
        {name: 'data', value: false},
        {name: 'referencesBank', value: false},
        {name: 'referencesPersonal', value: false}
      ],
      label: [
        "identificación oficial vigente (IFE, INE, Pasaporte)",
        "RFC o constancia de situación fiscal",
        "En caso de persona moral; datos de principales accionistas (Nombre,Puesto, Antigüedad en el puesto, Nivel educativo).",
        "Referencias Comerciales y/o Bancarias (compañía o Banco, Persona a contactar, Teléfono, Relación, Tiempo de conocerlo",
        "Referencias personales NO familiares (nombre, Teléfono,Relación, Tiempo de conocerlo, Domicilio)."
      ]
    };
  },
  components: {},
  methods: {
    redirect () {

    }
  },
  computed: {
    checkValidate() {
      let array = []
      for (let i = 0; i < this.checkbox.length; i++) {
        array.push(this.checkbox[i].value)

      }
      if (array[0] === true && array[1] && array[2] && array[3] && array[4] == true) {
        return true
      } else {
        return false
      }
    }
  },
};
</script>
<style lang="scss" scoped>
.image {
  padding: 20px;
}
.container {
  margin-top: 100px;
  width: 600px;
  margin-left: 60px;
}
.enable {
  background: #9fd178;
}
@media (max-width: 1280px) {
  .container {
    margin-top: 50px;
  }
}
@media (max-width: 600px) {
  .container {
    margin-left: 0px;
    width: 100%
  }
}
</style>
