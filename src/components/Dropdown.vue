<template>
  <div class="dropdown">
    <div class="select">
      <div class="placeholder">{{placeholder}}</div>
      <KeyboardArrowDownIcon />
    </div>
    <div class="options">
      <div
        class="option"
        v-for="option in options"
        :key="option"
      >
        {{option}}
      </div>
    </div>
  </div>
</template>

<script>
import KeyboardArrowDownIcon from '@/components/icons/KeyboardArrowDownIcon.vue'

export default {
  name: "Dropdown",
  components: {
    KeyboardArrowDownIcon
  },
  props: {
    placeholder: {
      type: String,
      required: true
    },
    options: {
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped lang="scss">
@import '../assets/mixin';

.select {
  @include flex(row, space-between, center);
  height: 40px;
  box-sizing: border-box;
  padding: 8px;
  border: solid 1px black;
  border-radius: 2px;
  cursor: pointer;
}

.options {

  .option {

  }

}
</style>