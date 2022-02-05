<template>
<template v-for="listitem in list" v-bind:key="listitem.key">
   <ListItem :listitem=listitem.item />
</template>

</template>

<script>
import ListItem from './ListItem.vue';

export default {
  name: 'List',
  components: {
    ListItem: ListItem
  },
  props: ['list'],
}
</script>

<style scoped>
</style>
