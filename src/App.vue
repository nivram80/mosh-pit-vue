<template>
  <div id="app">
    <section class="component">
      <h1>Dropdowns</h1>
      <Dropdown
        :label="'Best Royals Player'"
        :placeholder="'Choose...'"
        :options="players"
      />
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

<style scoped lang="scss">
@import '/assets/elements';

.component {
  width: 40%;
}
</style>
