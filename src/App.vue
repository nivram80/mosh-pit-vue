<template>
  <div id="app">
    <Dropdown
      :label="'Best Royals Player'"
      :options="players"
    />
  </div>
</template>

<script>
import Dropdown from './components/Dropdown.vue'

export default {
  name: 'app',
  components: {
    Dropdown
  },
  data () {
    return {
      players: [
        'George Brett',
        'Willie Wilson',
        'Mike Sweeney',
        'Salvador Perez',
        'Amos Otis'
      ]
    }
  }
}
</script>

<style>

</style>
