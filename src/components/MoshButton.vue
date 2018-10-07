<template>
  <button
    type="button"
    class="mosh-button"
    :class="{disabled: isDisabled}"
    @mouseup="$emit('buttonClick')"
  >
    {{label}}
  </button>
</template>

<script>
  export default {
    name: 'MoshButton',
    props: {
      label: {
        type: String,
        required: true
      },
      isDisabled: {
        type: Boolean,
        default: false
      }
    }
  }
</script>

<style scoped lang="scss">
  .mosh-button {
    -webkit-appearance: none;
    border: $primary-button-border;
    border-radius: $border-radius;
    background-color: $primary-action-color;
    color: $primary-button-color;
    padding: $button-padding;
    cursor: pointer;
    min-height: $primary-button-height;
    font-size: $default-font-size;
    @include box-shadow(2px);
    outline: 0;

    &:hover, &:focus {
      @include box-shadow(4px);
      background-color: $primary-button-hover-bg-color;
    }

    &:active {
      @include box-shadow(1px);
      background-color: $primary-button-hover-bg-color;
    }

    &.disabled {
      opacity: .5;
      pointer-events: none;
    }
  }
</style>