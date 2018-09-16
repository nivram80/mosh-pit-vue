<template>
  <button
    type="button"
    class="mosh-button"
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
        type: Boolean
      }
    }
  }
</script>

<style scoped lang="scss">
  @import '../assets/mixin';

  .mosh-button {
    -webkit-appearance: none;
    border: 0;
    border-radius: 2px;
    background-color: gray;
    color: white;
    padding: 0 16px;
    cursor: pointer;
    min-height: 40px;
    font-size: 16px;
    @include box-shadow(2px);
    outline: 0;

    &:hover, &:focus {
      @include box-shadow(4px);
    }

    &:active {
      @include box-shadow(1px);
    }
  }
</style>