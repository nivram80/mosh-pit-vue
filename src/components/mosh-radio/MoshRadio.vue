<template>
  <div class="radio-button">
    <input
      type="radio"
      :id="randomIdKey"
      :value="value"
      v-model="modelValue"
    >
    <label :for="randomIdKey">{{value}}</label>
  </div>
</template>

<script>
  import { generateRandomKey } from '../../utilities/misc.utilities';

  export default {
    name: 'MoshRadio',
    props: {
      label: {
        type: String,
        required: false
      },
      model: {
        type: String,
        required: false
      },
      value: {
        type: String
      },
      isDisabled: {
        type: Boolean,
        default: false
      }
    },
    data() {
      return {
        randomIdKey: generateRandomKey()
      }
    },
    computed: {
      modelValue: {
        get: function() {
          return this.model
        },
        set: function() {
          this.$emit('setValue', this.value)
        }
      }
    }
  }
</script>

<style scoped lang="scss">
  .radio-button {
    margin-top: 5px;
    margin-right: 35px;
  }

  input[type=radio] {
    opacity: 0;

    & + label::after {
      content: none;
    }

    &:checked + label::after {
      content: '';
    }
  }

  label {
    position: relative;
    left: 8px;

    &::before {
      position: absolute;
      left: -25px;
      content: '';
      display: inline-block;
      width: 16px;
      height: 16px;
      border: 1px solid $radio-color;
      border-radius: 50%;
    }

    &::after {
      position: absolute;
      top: 4px;
      left: -21px;
      content: '';
      display: inline-block;
      width: 10px;
      height: 10px;
      border-radius: 50%;
      background-color: $radio-color;
    }
  }
</style>