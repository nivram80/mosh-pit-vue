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
          :isDisabled="true"
          @setOption="setRestaurant"
        />

        <MoshRadioGroup
          :label="'Best Haircut'"
          :model="bestHaircut"
          :options="haircuts"
          :isInline="true"
          :isDisabled="false"
          @setValue="setHaircut"
        />

        <MoshTextarea
          :label="'Comments'"
          :placeholder="'Optional'"
          :model="comments"
          @setValue="setComments"
        />

        <MoshButton
          :label="'Submit'"
          :type="'primary'"
          @buttonClick="submitForm"
        />

        <MoshButton
          :label="'Change'"
          :type="'secondary'"
          @buttonClick="changeAlert"
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
  import MoshRadioGroup from './components/mosh-radio/MoshRadioGroup';

  export default {
    name: 'app',
    components: {
      MoshTextInput,
      MoshSelect,
      MoshButton,
      MoshTextarea,
      MoshRadioGroup
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
        haircuts: [
          'Buzzcut',
          'Flattop',
          'Mohawk',
          'Bedhead'
        ],
        bestPlayer: '',
        bestRestaurant: '',
        bestHaircut: '',
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
      setHaircut(haircut) {
        this.bestHaircut = haircut
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
      },
      changeAlert() {
        alert('Click change alert!')
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
