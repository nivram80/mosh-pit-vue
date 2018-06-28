<template>
  <div
    class="select"
    @click="$emit('toggleOptions')"
  >
    <div class="placeholder">{{placeholder}}</div>
    <KeyboardArrowDownIcon />
  </div>
</template>

<script>
import KeyboardArrowDownIcon from '@/components/icons/KeyboardArrowDownIcon.vue'

export default {
  name: "DropdownSelect",
  components: {
    KeyboardArrowDownIcon
  },
  props: {
    placeholder: {
      type: String,
      required: false
    }
  }
}
</script>

<style scoped lang="scss">
@import '../../assets/mixin';

.select {
  @include flex(row, space-between, center);
  height: 40px;
  box-sizing: border-box;
  padding: 8px;
  border: solid 1px black;
  border-radius: 2px;
  cursor: pointer;
}
</style>