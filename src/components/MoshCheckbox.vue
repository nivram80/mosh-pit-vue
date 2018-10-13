<template>
  <div class="checkbox">
    <input
      type="checkbox"
      :id="randomIdKey"
      :value="value"
      v-model="modelValue"
      @click="changeModelValue"
    >
    <label :for="randomIdKey">{{label}}</label>
  </div>
</template>

<script>
  import { generateRandomKey } from '../utilities/misc.utilities';

  export default {
    name: 'MoshCheckbox',
    props: {
      label: {
        type: String,
        required: false
      },
      value: {
        type: String,
        required: false
      },
      model: {
        required: false
      },
      isDisabled: {
        type: Boolean,
        default: false
      }
    },
    data() {
      return {
        modelValue: this.model,
        randomIdKey: generateRandomKey()
      }
    },
    methods: {
      changeModelValue() {
        this.modelValue = !this.modelValue
        this.$emit('setValue', this.modelValue)
      }
    }
  }
</script>

<style scoped>

</style>