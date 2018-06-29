<template>
  <div
    class="dropdown"
    v-click-outside="hideOptions"
  >
    <div class="label">{{label}}</div>
    <DropdownSelect
      :placeholder="placeholder"
      :model="model"
      @toggleOptions="toggleOptions"
    />
    <DropdownOptions
      :showOptions="showOptions"
      :options="options"
      @setOption="setOption"
    />
  </div>
</template>

<script>
import { ClickOutsideDirective } from '@/directives/ClickOutsideDirective.js';
import DropdownSelect from '@/components/dropdown/DropdownSelect';
import DropdownOptions from '@/components/dropdown/DropdownOptions.vue';

export default {
  name: "Dropdown",
  components: {
    DropdownSelect,
    DropdownOptions
  },
  props: {
    label: {
      type: String,
      required: false
    },
    placeholder: {
      type: String,
      required: false
    },
    options: {
      type: Array,
      required: true
    },
    model: {
      type: String,
      required: false
    }
  },
  directives: {
    ClickOutsideDirective
  },
  data () {
    return {
      showOptions: false
    }
  },
  methods: {
    toggleOptions() {
      this.showOptions = !this.showOptions
    },
    hideOptions() {
      this.showOptions = false;
    },
    setOption(option) {
      this.$emit('setOption', option)
      this.showOptions = false;
    }
  }
}
</script>

<style scoped lang="scss">
.label {
  font-size: 12px;
  margin-bottom: 4px;
}
</style>