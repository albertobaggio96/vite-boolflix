<script>
export default {
  name: "FilmApp",
  props: [
  "title",
  "originalTitle",
  "originalLanguage",
  "originalLanguageFlag",
  "voteAverage"
  ],
}
</script>

<template>
    <span>{{ title }}, </span>
    <span>{{ originalTitle }}, </span>
    <img :src="originalLanguageFlag" :alt="originalLanguage">
    <span>{{ voteAverage }}</span>
</template>

<style lang="scss">
  
</style>