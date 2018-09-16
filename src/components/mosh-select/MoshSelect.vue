<template>
  <div
    class="select"
    v-click-outside="hideOptions"
  >
    <label class="select-label">{{label}}</label>
    <MoshDropdownSelect
      :placeholder="placeholder"
      :model="model"
      @toggleOptions="toggleOptions"
    />
    <MoshSelectOptions
      :showOptions="showOptions"
      :options="options"
      :selectedDropdownId="selectedDropdownId"
      @setOption="setOption"
    />
  </div>
</template>

<script>
  import { ClickOutsideDirective } from '@/directives/ClickOutsideDirective.js';
  import MoshDropdownSelect from '@/components/mosh-select/MoshDropdownSelect';
  import MoshSelectOptions from '@/components/mosh-select/MoshSelectOptions.vue';

  export default {
    name: 'MoshSelect',
    components: {
      MoshDropdownSelect,
      MoshSelectOptions
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
  .select {
    position: relative;
  }

  .select-label {
    font-size: 12px;
  }
</style>