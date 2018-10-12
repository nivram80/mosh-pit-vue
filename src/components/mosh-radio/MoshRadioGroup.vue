<template>
  <div class="radio-group">
    <label class="radio-group-label">{{label}}</label>
    <MoshRadio
      v-for="option of options"
      :class="{inline: isInline}"
      :key="option"
      :label="'Haircut'"
      :value="option"
      :model="modelValue"
      :isDisabled="false"
      @setValue="setValue"
    />
  </div>
  
</template>

<script>
  import MoshRadio from '@/components/mosh-radio/MoshRadio';

  export default {
    name: 'MoshRadioGroup',
    components: {
      MoshRadio
    },
    props: {
      label: {
        type: String,
        required: false
      },
      model: {
        type: String,
        required: false
      },
      options: {
        type: Array,
        required: true
      },
      isInline: {
        type: Boolean,
        default: false
      },
      isDisabled: {
        type: Boolean,
        default: false
      }
    },
    data() {
      return {
        modelValue: this.model
      }
    },
    methods: {
      setValue(value) {
        this.modelValue = value
        this.$emit('setValue', this.modelValue)
      }
    }
  }
</script>

<style scoped lang="scss">
  .radio-group-label {
    @include form-element-label;
  }

  .inline {
    display: inline-block;
  }
</style>