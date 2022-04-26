<template>
  <div>
    <div>STEP FIRST</div>
    <div>DATA: {{ formData.firstStep }}</div>
    <button @click="next">NEXT STEP</button>
  </div>
</template>

<script>
export default {
  name: "StepFirst",
  props: {
    formData: Object,
  },
  methods: {
    next() {
      this.$emit("next");
    },
  },
};
</script>
