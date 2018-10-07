<template>
  <div
    class="textarea-container"
    :class="{disabled: isDisabled}"
  >
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
      },
      isDisabled: {
        type: Boolean,
        default: false
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
    @include form-element-label;
  }

  .textarea {
    width: 100%;
    height: $textarea-height;
    @include form-element-block-styles;
    font-size: $default-font-size;
  }

  ::placeholder {
    color: $input-placeholder-color;
  }

  .disabled {
    @include disabled;
  }
</style>