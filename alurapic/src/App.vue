<template>
  <div>
    <h1>{{ title }}</h1>
    <ul>
      <li v-bind:key="photo.id" v-for="photo of photos">
        <img :src="photo.src" :alt="photo.alt" />
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: "Alurapic",
      photos: []
    };
  },
  created() {
    this.$http
      .get("http://localhost:3000/v1/fotos")
      .then(res => res.json())
      .then(
        photos => (this.photos = photos),
        error => console.log(error)
      );
  }
};
</script>

<style></style>
