<template>
  <div id="app">
    <section class="component">
      <h1>Dropdowns</h1>
      <form>
        <Dropdown
          :label="'Best Royals Player'"
          :placeholder="'Choose...'"
          :options="players"
          :model="bestPlayer"
          @setOption="setPlayer"
        />

        <Dropdown
          :label="'Best Food in Omaha'"
          :placeholder="'Choose...'"
          :options="restaurants"
          :model="bestRestaurant"
          @setOption="setRestaurant"
        />
      </form>

    </section>
  </div>
</template>

<script>
  import Dropdown from '@/components/dropdown/Dropdown.vue'

  export default {
    name: 'app',
    components: {
      Dropdown
    },
    data() {
      return {
        players: [
          'George Brett',
          'Willie Wilson',
          'Mike Sweeney',
          'Salvador Perez',
          'Amos Otis'
        ],
        restaurants: [
          'Salween',
          'Flemmings',
          'Amsterdam',
          'Maria Bonita',
          'Ray\'s'
        ],
        bestPlayer: null,
        bestRestaurant: null
      }
    },
    methods: {
      setPlayer(option) {
        this.bestPlayer = option
      },
      setRestaurant(option) {
        this.bestRestaurant = option
      }
    }
  }
</script>

<style scoped lang="scss">
  @import '/assets/elements';

  .component {
    width: 40%;
  }

  form > div {
    margin-bottom: 16px;
  }
</style>
