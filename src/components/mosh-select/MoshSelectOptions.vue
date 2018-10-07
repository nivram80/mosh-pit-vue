<template>
  <div
    class="options"
    :style="{top: elementTop}"
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
    name: "MoshSelectOptions",
    props: {
      showOptions: {
        type: Boolean,
        required: true
      },
      options: {
        type: Array,
        required: true
      },
      selectedDropdownId: {
        type: Number,
        required: false
      }
    },
    data() {
      return {
        selectedOption: ''
      }
    },
    computed: {
      elementTop() {
        return document.getElementById(this.selectedDropdownId)
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
  .options {
    position: absolute;
    top: -$option-height;
    width: 100%;
    background: $option-bg-color;
    border: $border;
    border-radius: $border-radius;
    @include box-shadow(2px);
    z-index: 3;

    .option {
      @include flex(row, flex-start, center);
      height: $option-height;
      box-sizing: border-box;
      padding: $form-element-padding;
      cursor: pointer;

      &:hover {
        background: $option-hover-bg-color;
      }
    }
  }
</style>