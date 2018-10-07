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
        value: this.model
      }
    },
    methods: {
      randomIdKey() {
        return Math.floor(1000000000 + Math.random() * 9000000000);
      },
      setValue() {
        this.$emit('setValue', this.value)
      }
    }
  }
</script>

<style scoped lang="scss">
  .text-input-label {
    font-size: $label-font-size;
    display: block;
  }
  .input {
    width: 100%;
    height: $select-height;
    box-sizing: border-box;
    padding: 8px;
    border: $border;
    border-radius: $border-radius;
    cursor: pointer;
    font-size: $default-font-size;
  }
  ::placeholder {
    color: $input-placeholder-color;
  }
</style>