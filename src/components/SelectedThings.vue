<template>
  <div class="column bg-grey">
    <thing 
      v-for="(item, idx) in selected"
      :key="item.id"
      :name="item.name"
      :class="{ 'm-b': idx + 1 < selected.length }"
    />
  </div>
</template>

<script>
import Thing from '@/components/Thing.vue';

  export default {
    name: 'SelectedThings',
    components: {
      Thing
    },
    props: {
      selected: {
        type: Array,
        default: () => ([])
      }
    }    
  }
</script>