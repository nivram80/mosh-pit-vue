<template>
  <div class="input-container">
    <label
      class="text-input-label"
      :for="randomIdKey"
    >
      {{label}}
    </label>
    <input
      type=text
      class="input"
      v-model="value"
      :id="randomIdKey"
      :placeholder="placeholder"
      @keyup="setValue"
    >
  </div>
</template>

<script>
  import { generateRandomKey } from '../utilities/misc.utilities';

  export default {
    name: "MoshTextInput",
    props: {
      label: {
        type: String,
        required: false
      },
      model: {
        type: String,
        required: false
      },
      placeholder: {
        type: String,
        required: false
      }
    },
    data() {
      return {
        value: this.model,
        randomIdKey: generateRandomKey()
      }
    },
    methods: {
      setValue() {
        this.$emit('setValue', this.value)
      }
    }
  }
</script>

<style scoped lang="scss">
  .text-input-label {
    @include form-element-label;
  }
  .input {
    width: 100%;
    height: $select-height;
    @include form-element-block-styles;
    font-size: $default-font-size;
  }
  ::placeholder {
    color: $input-placeholder-color;
  }
</style>