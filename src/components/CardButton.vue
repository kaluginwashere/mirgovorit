<template>
    <a v-if="type==='seminar'" :href=link>{{ price }}</a>
    <a v-else :href=link>Выбрать тариф</a>
</template>

<script>

export default {
  props: ['type', 'link','price'],
  name: "CardButton",

}

</script>

<style scoped>

</style>