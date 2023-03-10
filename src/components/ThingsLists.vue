<template>
  <div class="column">
    <thing 
      v-for="(item, idx) in items"
      :key="item.id"
      :name="item.name"
      :class="{
        'm-b': idx + 1 < items.length,
        'bg-grey': getExistIndex(item.id) > -1,
        'cursor-pointer': true
      }"
      @click="onSelect(item)"
    />
  </div>
</template>

<script>
import Thing from '@/components/Thing';

  export default {
    name: 'ThingsLists',
    components: {
      Thing
    },
    props: {
      items: {
        type: Array,
        default: () => ([])
      },
      selected: {
        type: Array,
        default: () => ([])
      },
      maxSelected: {
        type: Number,
        default: 1
      }
    },
    computed: {
      isAvailableSelect() {
        return this.maxSelected > this.selected.length
      }
    },
    methods: {
      onSelect(item) {
        const selectedTmp = this.selected
        const existIndex = this.getExistIndex(item.id)
        // если элемент выбран, то удаляем его
        if (existIndex > -1) {
          selectedTmp.splice(existIndex, 1);
        } else if (this.isAvailableSelect) {
          // если не достигнут максимум по выбору элементов, добавляем новый
          selectedTmp.push(item)
        } else {
          // иначе заменяем последний
          selectedTmp.splice(selectedTmp.length - 1, 1, item);
        }
        this.$emit('onSelected', selectedTmp)
      },
      getExistIndex(id) {
        return this.selected.findIndex(item => item.id === id)
      }
    }    
  }
</script>