<template>
  <div>
    <div class="stepper">
      <div v-for="step in stepper" :key="step.id">
        <div
          class="circle mt-4"
          :class="[
            { color: step.name === steps.name },
            { ready: step.value === true }
          ]"
          @click="changeStep(step)"
        >
          <img
            v-if="step.name === steps.name && step.value != true"
            class="img"
            src="../assets/image/mini-circle.png"
            alt=""
          />
          <img
            v-if="step.value === true && step.name === steps.name"
            class="check"
            src="../assets/image/check.png"
            alt=""
          />
          <div
            :class="[
              { 'line-with-circle': step.name === steps.name },
              { hiddenLine: step.name === 'Confirmación' }
            ]"
            class="line"
          ></div>
        <div
          @click="changeStep(step)"
          class="step"
          :class="[
            { stopped: step.name === steps.name && step.value != true },
            { set: step.value === true }
          ]"
        >
          <div class="nameStep mobile">{{ step.name }}</div>
        </div>
        </div>
      </div>
    </div>

    <div style="padding-top: 35px" class="desktop">
      <div v-for="step in stepper" :key="step.id">
        <div
          @click="changeStep(step)"
          class="step"
          :class="[
            { stopped: step.name === steps.name && step.value != true },
            { set: step.value === true }
          ]"
        >
          <div>{{ step.name }}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapState } from "vuex";
export default {
  data() {
    return {
    };
  },
  computed: {
    ...mapState("genesys", ["stepper", "steps"])
  },
  methods: {
    changeStep(step) {
      this.$store.commit("genesys/updateSteps", step);
    }
  },
  components: {}
};
</script>

<style lang="scss" scoped>
@import url(../assets/components/stepper.scss);
</style>
