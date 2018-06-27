<template>
  <div id="app">
    <section class="component">
      <h1>Dropdowns</h1>
      <Dropdown
        :placeholder="'Best Royals Player'"
        :options="players"
      />
    </section>
  </div>
</template>

<script>
import Dropdown from '@/components/Dropdown.vue'

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
