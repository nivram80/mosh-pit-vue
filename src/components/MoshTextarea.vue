<template>
  <div class="textarea-container">
    <label
      class="textarea-label"
      :for="randomIdKey"
    >
      {{label}}
    </label>
    <textarea
      class="textarea"
      v-model="value"
      :id="randomIdKey"
      :placeholder="placeholder"
      @keyup="setValue"
    ></textarea>
  </div>
</template>

<script>
  import { generateRandomKey } from '../utilities/misc.utilities';

  export default {
    name: 'MoshTextarea',
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
  .textarea-label {
    font-size: $label-font-size;
    display: block;
  }
  .textarea {
    width: 100%;
    height: $textarea-height;
    box-sizing: border-box;
    padding: $form-element-padding;
    border: $border;
    border-radius: $border-radius;
    cursor: pointer;
    font-size: $default-font-size;
  }
  ::placeholder {
    color: $input-placeholder-color;
  }
</style>