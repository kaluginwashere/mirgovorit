<template>
    <span>{{ topic }}</span>
        <h2>{{ name }}</h2>
        <p>{{ description }}</p>
<!--        <img :src=avatar />-->
</template>

<script>

import axios from "axios";

export default {
  name: "AuthorInfo",
  props: ['topic','name','description','avatar']
}
</script>

<style scoped>

</style>