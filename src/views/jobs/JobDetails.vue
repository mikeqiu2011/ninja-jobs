<template>
  <h1 v-if="job">{{ job.title }}</h1>
  <p v-if="job">{{ job.details }}</p>
</template>

<script>
export default {
  props: ["id"],
  data() {
    return {
      job: null,
    };
  },
  mounted() {
    fetch("http://localhost:3000/jobs/" + this.id)
      .then((resp) => resp.json)
      .then((data) => (this.job = data))
      .catch((err) => console.log(err.message));
  },
};
</script>

<style>
</style>