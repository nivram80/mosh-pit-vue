<template>
  <div id="app">
    <section class="component">
      <h1>Mosh Pit Components</h1>
      <br>
      <form>
        <MoshTextInput
          :label="'First Name'"
          :placeholder="'Optional'"
          :model="firstName"
          @setValue="setFirstName"
        />

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

        <MoshTextarea
          :label="'Comments'"
          :placeholder="'Optional'"
          :model="comments"
          @setValue="setComments"
        />

        <MoshButton
          :label="'Submit'"
          @buttonClick="submitForm"
        />

        <MoshButton
          :label="'Disabled'"
          :isDisabled="true"
        />
      </form>
    </section>
  </div>
</template>

<script>
  import MoshTextInput from './components/MoshTextInput';
  import MoshButton from './components/MoshButton';
  import MoshSelect from './components/mosh-select/MoshSelect';
  import MoshTextarea from './components/MoshTextarea';

  export default {
    name: 'app',
    components: {
      MoshTextInput,
      MoshSelect,
      MoshButton,
      MoshTextarea
    },
    data() {
      return {
        firstName: '',
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
        bestRestaurant: null,
        comments: ''
      }
    },
    methods: {
      setFirstName(name) {
        this.firstName = name
      },
      setPlayer(option) {
        this.bestPlayer = option
      },
      setRestaurant(option) {
        this.bestRestaurant = option
      },
      setComments(comments) {
        this.comments = comments
      },
      submitForm() {
        const data =
          `
          First Name: ${this.firstName}\n
          Best Royal: ${this.bestPlayer}\n
          Best Restaurant: ${this.bestRestaurant}\n
          Comments: ${this.comments}
          `
        alert(data)
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

  form > button {
    margin-right: 8px;
  }
</style>
