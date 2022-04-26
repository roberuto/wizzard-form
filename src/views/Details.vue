<template>
  <div>
    <div>DETAILS</div>
    <button @click="goToFirstStep">GO TO FIRST STEP</button>
    <br /><br />
    <button @click="goToSecondStep">GO TO SECOND STEP</button>
  </div>
</template>

<script>
export default {
  name: "Details",
  methods: {
    goToFirstStep() {
      this.$router.push({ name: "Form", params: { id: 1, step: 1 } });
    },
    goToSecondStep() {
      this.$router.push({ name: "Form", params: { id: 1, step: 2 } });
    },
  },
};
</script>
