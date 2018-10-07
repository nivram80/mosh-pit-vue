<template>
  <div id="app">
    <section class="component">
      <h1>Selects</h1>
      <form>
        <MoshSelect
          :label="'Best Royals Player'"
          :placeholder="'Choose...'"
          :options="players"
          :model="bestPlayer"
          @setOption="setPlayer"
        />

        <MoshSelect
          :label="'Best Food in Omaha'"
          :placeholder="'Choose...'"
          :options="restaurants"
          :model="bestRestaurant"
          @setOption="setRestaurant"
        />

        <MoshButton
          :label="'Submit'"
          @buttonClick="submitForm"
        />
      </form>
    </section>
  </div>
</template>

<script>
  import MoshButton from './components/MoshButton';
  import MoshSelect from './components/mosh-select/MoshSelect';

  export default {
    name: 'app',
    components: {
      MoshSelect,
      MoshButton
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
          'Drover',
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
      },
      submitForm() {
        alert('Sending data into the clouds!')
      }
    }
  }
</script>

<style scoped lang="scss">
  .component {
    width: 100%;

    @media (min-width: 600px) {
      width: 40%;
    }
  }

  form > div {
    margin-bottom: 16px;
  }
</style>
