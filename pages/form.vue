<template>
  <v-app>
        <!-- {{steps}} -->
    <v-row no-gutters>
      <v-col cols="12" lg="4"  md="6"  sm="6" class="step">
          <Stepper />
        <div class="logo-form">
          <img
            class="image desktop"
            src="https://res.cloudinary.com/dutj1bbos/image/upload/v1618865725/Group_23_2_ee7cvn.png"
            alt=""
          />
        </div>
      </v-col>
      <v-col cols="12" lg="8" md="6" sm="6">
            <CompanyInformation v-if="steps.id == 1"/>
            <AddressFiscal v-if="steps.id == 2"/>
            <HomeAddress v-if="steps.id == 3"/>
            <HomePrevious v-if="steps.id == 4"/>
            <Actions v-if="steps.id == 5"/>
            <CreditRequest v-if="steps.id == 6"/>
            <InfoCommercial v-if="steps.id == 7"/>
            <PersonalReferences v-if="steps.id == 8"/>
            <Manifest v-if="steps.id == 9"/>
            <Beneficiary v-if="steps.id == 10"/>
            <ImportantInfo v-if="steps.id == 11"/>
      </v-col>
    </v-row>
  </v-app>
</template>

<script>
import { mapState } from "vuex";
export default {
  data() {
    return {
    };
  },
  components: {},
  methods: {
  },
  computed: {
    ...mapState("genesys", ["steps"])
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
.align {
  display: flex;
  justify-content: flex-end;
}
.enable {
  background: #9fd178;
}
.step {
    background: $blue-light;
}
.logo-form {
    display: flex;
    justify-content: center;
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
.step {
    min-height: 150px;
    max-height: 150px;
}
}
</style>
