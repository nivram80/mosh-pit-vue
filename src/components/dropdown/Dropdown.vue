<template>
  <div
    class="dropdown"
    v-click-outside="hideOptions"
  >
    <label class="dropdown-label">{{label}}</label>
    <DropdownSelect
      :placeholder="placeholder"
      :model="model"
      @toggleOptions="toggleOptions"
    />
    <DropdownOptions
      :showOptions="showOptions"
      :options="options"
      :selectedDropdownId="selectedDropdownId"
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
    data() {
      return {
        showOptions: false,
        selectedDropdownId: null
      }
    },
    methods: {
      toggleOptions(id) {
        this.selectedDropdownId = id
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

<style scoped>
  .dropdown {
    position: relative;
  }

  .dropdown-label {
    font-size: 12px;
  }
</style>