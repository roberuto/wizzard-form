<template>
  <div>
    <div>STEP SECOND</div>
    <div>DATA: {{ formData.secondStep }}</div>
    <button @click="prev">PREV STEP</button>
  </div>
</template>

<script>
export default {
  name: "StepFirst",
  props: {
    formData: Object,
  },
  methods: {
    prev() {
      this.$emit("prev");
    },
  },
};
</script>
