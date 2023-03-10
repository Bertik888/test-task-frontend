<template>
  <div class="container">
    <div class="row border-dashed height-420">
      <selected-things
        :selected="selectedThingsUser"
        class="col p-t p-b"
      />
      <selected-things
        :selected="selectedThingsOther"
        class="col p-t p-b"
      />
    </div>

    <div class="row">
      <things-lists 
        :items="thingsUser"
        :selected="selectedThingsUser"
        :max-selected="6"
        class="col p-t p-b"
        @onSelected="onSelect($event, 'user')"
      />
      <things-lists 
        :items="thingsOther"
        :selected="selectedThingsOther"
        :max-selected="1"
        class="col p-t p-b"
        @onSelected="onSelect($event, 'other')"
      />
    </div>
  </div>
</template>

<script>
import SelectedThings from './components/SelectedThings.vue'
import ThingsLists from './components/ThingsLists.vue'


export default {
  name: 'App',
  components: {
    SelectedThings,
    ThingsLists
  },
  data() {
    return {
      thingsUser: [
        {
          "id": 1,
          "name": "Shoes 1"
        },
        {
          "id": 2,
          "name": "Shoes 2"
        },
        {
          "id": 3,
          "name": "Shoes 3"
        },
        {
          "id": 4,
          "name": "Shoes 4"
        },
        {
          "id": 5,
          "name": "T-shirt 1"
        },
        {
          "id": 6,
          "name": "T-shirt 2"
        },
        {
          "id": 7,
          "name": "T-shirt 3"
        },
        {
          "id": 8,
          "name": "T-shirt 4"
        }
      ],
      thingsOther: [
        {
          "id": 11,
          "name": "Jacket 1"
        },
        {
          "id": 12,
          "name": "Jacket 2"
        },
        {
          "id": 13,
          "name": "Jacket 3"
        },
        {
          "id": 14,
          "name": "Jacket 4"
        },
        {
          "id": 15,
          "name": "Hoodie 1"
        },
        {
          "id": 16,
          "name": "Hoodie 2"
        },
        {
          "id": 17,
          "name": "Hoodie 3"
        },
        {
          "id": 18,
          "name": "Hoodie 4"
        }
      ],
      selectedThingsUser: [],
      selectedThingsOther: []
    }
  },
  methods: {
    onSelect(items, name) {
      name === 'other' ? this.selectedThingsOther = items : this.selectedThingsUser = items
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.container {
  width: 100%;
  padding-right: 24px;
  padding-left: 24px;
  margin-right: auto;
  margin-left: auto;
  max-width: 1280px;
}

.row {
  display: flex;
  flex-wrap: wrap;
  margin-right: -24px;
  margin-left: -24px;
}

.column {
  display: flex;
  flex-direction: column;
}

.flex {
  display: flex;
}

.col {
  flex: 1 0 0%;
  padding: 0 24px;
}

.bg-blue {
  background-color: blue;
}

.p-t {
  padding-top: 24px;
}

.p-b {
  padding-bottom: 24px;
}

.m-b {
  margin-bottom: 12px;
}

.cursor-pointer {
  cursor: pointer;
}

.bg-grey {
  background-color: #eeeeee;
}

.height-420 {
  min-height: 420px;
}

.border-dashed {
  border: dashed 2px #000000;
}
</style>
