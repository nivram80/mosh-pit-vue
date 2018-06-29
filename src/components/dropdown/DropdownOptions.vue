<template>
  <div
    class="options"
    v-show="showOptions"
  >
    <div
      class="option"
      v-for="option in options"
      :key="option"
      @mouseup="setOption(option)"
    >
      {{option}}
    </div>
  </div>
</template>

<script>
export default {
  name: "DropdownOptions",
  props: {
    showOptions: {
      type: Boolean,
      required: true
    },
    options: {
      type: Array,
      required: true
    }
  },
  data () {
    return {
      selectedOption: ''
    }
  },
  methods: {
    setOption(option) {
      this.selectedOption = option
      this.$emit('setOption', this.selectedOption)
    }
  }
}
</script>

<style scoped lang="scss">
@import '../../assets/mixin';

.options {
  position: relative;
  top: -40px;
  background: white;
  border: solid 1px black;
  border-radius: 2px;

  .option {
    @include flex(row, flex-start, center);
    height: 40px;
    box-sizing: border-box;
    padding: 8px;
    cursor: pointer;

    &:hover {
      background: lightgray;
    }
  }
}
</style>