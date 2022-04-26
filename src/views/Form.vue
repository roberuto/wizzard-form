<template>
  <div>
    <div>FORM</div>
    <transition name="fade" mode="out-in">
      <component
        :formData="formData"
        :is="currentComponent"
        :activeStep="activeStep"
        @prev="prev"
        @next="next"
      ></component>
    </transition>
  </div>
</template>

<script>
import StepFirst from "@/components/StepFirst.vue";
import StepSecond from "@/components/StepSecond.vue";

export default {
  name: "Form",
  data: () => ({
    activeStep: 1,
    components: [StepFirst, StepSecond],
    formData: {
      firstStep: "",
      secondStep: "",
    },
  }),
  mounted() {
    console.log("MOUNTED!");
  },
  created() {
    const { step, id } = this.$route.params;
    if (step) {
      this.activeStep = parseInt(step);
    }
    this.initForm(id);
  },
  computed: {
    currentComponent() {
      return this.components[this.activeStep - 1];
    },
  },
  methods: {
    next() {
      this.activeStep++;
    },
    prev() {
      this.activeStep--;
    },
    initForm(id) {
      if (id !== "new") {
        this.formData = {
          firstStep: `${id} FIRST STEP`,
          secondStep: `${id} SECOND STEP`,
        };
      } else {
        this.formData = {
          firstStep: "NEW FIRST STEP",
          secondStep: "NEW SECOND STEP",
        };
      }
    },
  },
  watch: {
    "$route.params": function (params) {
      const { id } = params;
      this.initForm(id);
    },
  },
};
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
